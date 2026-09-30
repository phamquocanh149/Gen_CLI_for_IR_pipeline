# Gen CLI for IR Pipeline 🚀

Một công cụ trực quan (Web UI) độc lập giúp người dùng dễ dàng tạo câu lệnh CLI cho hệ thống **Information Retrieval (IR) Pipeline** mà không cần nhớ cú pháp phức tạp.

---

## 🌟 Tính năng chính

- **Hỗ trợ đa dạng Retriever**:
  - **BM25** (Sparse Retrieval)
  - **Dense** (Single-Vector Embedding)
  - **Late Interaction** (ColBERT Multi-Vector)
  - **Cross-Encoder** (2-Stage Reranking với Stage 1 tùy chọn BM25 hoặc Dense)
  - **Hybrid** (Kết hợp BM25 và Dense)
- **Presets mô hình thông dụng**:
  - Tích hợp sẵn các mô hình phổ biến (BGE, MiniLM, ColBERT, BGE-Reranker,...) hoặc nhập model ID tùy ý từ HuggingFace.
- **Stage-specific Configuration**:
  - Tách biệt cấu hình `batch_size` và `candidate_top_k` cho từng stage (Stage 1 Candidate Retriever & Stage 2 Cross-Encoder Scoring).
- **FAISS Index Persistence (Save / Load Offline)**:
  - Hỗ trợ lưu (`--save-index`) và tải (`--load-index`) FAISS vector index cho các retriever có sử dụng Dense: **Dense**, **Hybrid**, **Cross-Encoder (Stage 1 Dense)**.
  - Tự động gợi ý tên index thông minh theo Dataset và Model.
- **Tùy chỉnh linh hoạt**:
  - Chọn dataset mẫu (`data/toy`, `data/fiqa/test`,...) hoặc đường dẫn riêng.
  - Chọn các chỉ số đánh giá đa dạng: NDCG@k, MRR@k, Recall@k, Precision@k, MAP@k hoặc tự thêm metric tùy chỉnh.
  - Đặt tên lượt chạy (`--name`), output directory (`--output`), seed, verbose mode.
- **Giao diện hiện đại & tiện lợi**:
  - Dark-mode, responsive, trực quan.
  - Tự động validate các trường bắt buộc.
  - Copy câu lệnh chỉ bằng một cú click.

---

## 🖥️ Hướng dẫn sử dụng

Công cụ hoàn toàn độc lập, không yêu cầu cài đặt thêm thư viện (Zero Dependencies).

### Cách 1: Mở trực tiếp bằng trình duyệt
Nhấp đúp chuột vào file `index.html` để mở trong trình duyệt web (Chrome, Edge, Firefox, Safari,...).

### Cách 2: Chạy qua HTTP server cục bộ (tùy chọn)
Trong thư mục `gen_CLI`, mở terminal và chạy:
```bash
python -m http.server 8000
```
Sau đó truy cập: [http://localhost:8000](http://localhost:8000)

---

## 📋 Cấu trúc thư mục

```text
gen_CLI/
├── index.html     # Giao diện Web UI và toàn bộ logic tạo lệnh CLI
└── README.md      # Tài liệu hướng dẫn sử dụng
```
