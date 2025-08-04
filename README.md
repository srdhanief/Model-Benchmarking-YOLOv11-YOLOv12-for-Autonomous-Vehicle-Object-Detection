<h1>Model Benchmarking: YOLOv11 vs YOLOv12 for Autonomous Vehicle Object Detection 🚗📸</h1>

<p>This project compares the performance of <strong>YOLOv11</strong> and <strong>YOLOv12</strong> models on a real-world object detection task relevant to autonomous driving. The focus is on evaluating accuracy (mAP, F1-score), inference speed, and model efficiency using the <strong>Udacity Self-Driving Car</strong> dataset via Roboflow.</p>

<hr>

<h2>📦 Dataset</h2>

<p><strong>Name</strong>: Roboflow Udacity Self-Driving Cars</p>
<p><strong>Classes (11)</strong>:</p>
<pre>
['biker', 'car', 'pedestrian', 'trafficLight',
 'trafficLight-Green', 'trafficLight-GreenLeft',
 'trafficLight-Red', 'trafficLight-RedLeft',
 'trafficLight-Yellow', 'trafficLight-YellowLeft', 'truck']
</pre>

<p><strong>Data Split</strong>:</p>
<ul>
  <li>Train: 20,860 images</li>
  <li>Validation: 4,470 images</li>
  <li>Test: 4,470 images</li>
</ul>

<p><strong>Image input shape</strong>: (1, 3, 640, 640)<br>
<strong>Training duration</strong>: 25 epochs</p>

<hr>

<h2>🧠 Models Compared</h2>

<table border="1">
  <thead>
    <tr>
      <th>Model</th>
      <th>Key Architectural Features</th>
      <th>Typical Trade-offs</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>YOLOv11</strong></td>
      <td>
        - C3k2 Blocks (efficient residual modules)<br>
        - SPPF (Spatial Pyramid Pooling Fast)<br>
        - C2PSA: Parallel Spatial Attention module<br>
        - Optimized for lightweight, real-time use
      </td>
      <td>High accuracy and low latency with lightweight compute</td>
    </tr>
    <tr>
      <td><strong>YOLOv12</strong></td>
      <td>
        - Area Attention (A²) modules for context-aware detection<br>
        - R-ELAN: Residual Feature Aggregation<br>
        - FlashAttention, 7x7 separable convs, no positional encoding<br>
        - Designed for improved global-local reasoning
      </td>
      <td>Higher theoretical accuracy but slower inference and higher compute</td>
    </tr>
  </tbody>
</table>

<hr>

<h2>📊 Evaluation Metrics</h2>

<table border="1">
  <thead>
    <tr>
      <th>Metric</th>
      <th>YOLOv11</th>
      <th>YOLOv12</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>mAP@50</td>
      <td>0.639</td>
      <td>0.571</td>
    </tr>
    <tr>
      <td>mAP@75</td>
      <td>0.398</td>
      <td>0.333</td>
    </tr>
    <tr>
      <td>mAP@50:95</td>
      <td>0.379</td>
      <td>0.329</td>
    </tr>
    <tr>
      <td>Best F1 Score</td>
      <td>0.69</td>
      <td>0.66</td>
    </tr>
    <tr>
      <td>Confidence Threshold</td>
      <td>0.339</td>
      <td>0.285</td>
    </tr>
  </tbody>
</table>

<hr>

<h2>⚡ Inference Speed</h2>

<table border="1">
  <thead>
    <tr>
      <th>Stage</th>
      <th>YOLOv11</th>
      <th>YOLOv12</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Preprocess</td>
      <td>2.8ms</td>
      <td>2.8ms</td>
    </tr>
    <tr>
      <td>Inference</td>
      <td><strong>9.4ms</strong></td>
      <td><strong>17.4ms</strong></td>
    </tr>
    <tr>
      <td>Postprocess</td>
      <td>1.1ms</td>
      <td>1.2ms</td>
    </tr>
  </tbody>
</table>

<hr>

<h2>📈 F1-Confidence Curve Summary</h2>

<ul>
  <li><strong>YOLOv11</strong> reaches <strong>0.69</strong> F1-score at a confidence threshold of <strong>0.339</strong>.</li>
  <li><strong>YOLOv12</strong> reaches <strong>0.66</strong> F1-score at a confidence threshold of <strong>0.285</strong>.</li>
</ul>

<p>These curves show that YOLOv11 maintains a better precision-recall tradeoff, especially at higher confidence levels.</p>

<hr>

<h2>🏁 Conclusion</h2>

<ul>
  <li><strong>YOLOv11</strong> outperforms YOLOv12 in both accuracy and speed for this specific autonomous vehicle object detection task.</li>
  <li>It delivers <strong>higher mAP, better F1-score, and significantly faster inference</strong> on the same hardware.</li>
  <li>While YOLOv12 is more advanced in architecture, its attention-heavy design results in slower performance, which may not be suitable for real-time applications without further optimization.</li>
</ul>

