# Hoos' Upto No Good: A Comparative Analysis of RE Tools

This project provides a comprehensive and unbiased comparison of three industry-standard software reverse engineering (RE) tools: **Ghidra**, **Angr**, and **IDA Pro**. By analyzing their architecture, usability, and performance across various metrics, this research identifies the systematic differences to help security researchers choose the right tool for specific tasks.

---
## 📌 Project Overview

Reverse engineering is essential for deconstructing binary files to reveal program design, architecture, and vulnerabilities. This study evaluates tools based on five primary metrics:
* **GUI - UI/UX:** Ease of use and interface design.
* **Control Flow Graphs (CFG):** Quality of visual logic representation.
* **Supported Languages:** Breadth of source languages detectable.
* **Supported Architecture:** Range of hardware platforms supported.
* **Fault Tolerance:** Ability to handle and analyze corrupted binaries.
---

## 🛠 Tools at a Glance

### 1. IDA Pro
IDA Pro is a highly reputable, licensed multi-processor disassembler and debugger.
* **Strengths:** Supports over 50 architectures, including x64, ARM64, and various DSP series. It features a massive library of existing plugins and strong developer support.
* **Limitations:** It is expensive compared to free alternatives and lacks an "Undo" button, which can make dynamic changes risky.

### 2. Angr
Angr is a Python-based binary analysis framework developed by researchers at UC Santa Barbara and Arizona State University.
* **Strengths:** It excels at symbolic execution, vulnerability detection, and solving CTF challenges. It offers a "CFGEmulated" mode for highly accurate dynamic control flow analysis.
* **Limitations:** It has the poorest fault tolerance of the three, often failing on corrupted bytes. It lacks a native GUI, relying on third-party visualizers.

### 3. Ghidra
Developed by the NSA, Ghidra is a free and open-source RE suite suite.
* **Strengths:** It supports collaborative projects and non-shared projects, allowing multiple engineers to work on the same code. It offers an "Undo" feature and version tracking.
* **Limitations:** As a newer tool, it has fewer plugins and less developed documentation compared to IDA Pro.

---

## 📊 Comparative Evaluation

| Feature | IDA Pro | Angr | Ghidra |
| :--- | :--- | :--- | :--- |
| **Licensing** | Paid/Licensed  | Open Source  | Open Source  |
| **Primary Language** | C++/Python  | Python  | C++/Java  |
| **Fault Tolerance** | Accurate for most parts  | Poor (ELFParserError)  | Very Good  |
| **UI Experience** | High-level/User Friendly  | CLI/Shell Focused  | Intuitive Component Design  |
| **Symbolic Execution** | Via Plugins  | Native/Core Feature  | Limited |

---

## 🔍 Technical Deep Dive

### Control Flow Analysis
* **IDA Pro** does not split basic blocks at function calls.
* **Angr** splits basic blocks at every control flow instruction, including function calls, for better static analysis accuracy.
* **Ghidra** synchronizes its Function Graph window with the code browser, allowing for real-time link tracing between functions.



### Fault Tolerance Test Results
The tools were tested by corrupting binary bytes using the `dd` command:
* **Ghidra** performed the best, opening and analyzing a file even after it was reduced from 7096 KB to 116 KB.
* **IDA Pro** successfully read corrupted files but with slightly inaccurate information.
* **Angr** was unable to parse binaries even with a single corrupted byte.

---

## 🚀 Conclusion

No single tool is objectively "the best". 
* Use **IDA Pro** if you require a robust native debugger and support for obscure architectures.
* Use **Angr** for automated analysis, vulnerability fuzzing, and CTF challenges.
* Use **Ghidra** for high-speed analysis of large files (>1GB) and collaborative team environments.

---

*Based on the Project Report by Omkar Bhat, Zoya Yeprem, and Vijay Lingesh.*

