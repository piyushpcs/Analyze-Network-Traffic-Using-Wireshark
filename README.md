# Analyze-Network-Traffic-Using-Wireshark
# Network Traffic Analysis with Wireshark

This guide provides a step-by-step process for capturing and analyzing live network traffic using Wireshark. It is designed for beginners in networking or cybersecurity.

## Objective

Capture live network packets from a local machine and identify basic protocols and traffic types.

## Tools Required

*   **Wireshark**: A free and open-source packet analyzer. Download from the [official Wireshark website](https://www.wireshark.org/download.html).

## Deliverables

1.  A packet capture file (e.g., `capture.pcapng`).
2.  A short report detailing the protocols identified during the analysis.

---

## Step-by-Step Guide

### Phase 1: Preparation & Setup

#### **Step 1: Install Wireshark**

1.  Download the appropriate installer for your operating system (Windows or macOS) from the [Wireshark website](https://www.wireshark.org/download.html).
2.  Run the installer.
3.  **On Windows**, you will be prompted to install **Npcap**. This is a mandatory component that allows Wireshark to access network interfaces. Ensure you check the box to install it. The default options are suitable for most users.

#### **Step 2: Plan Your Traffic Generation**

To ensure you capture interesting data, prepare to perform the following actions *after* you start the capture:

1.  **Generate DNS and HTTP traffic**: Open a web browser and visit a non-encrypted website like `http://example.com`.
2.  **Generate DNS and HTTPS (TLS) traffic**: Visit a secure website like `https://google.com`.
3.  **Generate ICMP traffic**: Open Command Prompt (Windows) or Terminal (macOS/Linux) and run the command `ping 8.8.8.8`.

---

### Phase 2: Capturing Live Network Packets

#### **Step 3: Start the Capture in Wireshark**

1.  Open Wireshark. It is recommended to **Run as Administrator** on Windows to ensure all interfaces are visible.
2.  On the welcome screen, you will see a list of available network interfaces (e.g., "Wi-Fi", "Ethernet").
3.  Identify your active network interface. It will be the one with a "sparkline" graph showing live traffic.
4.  **Double-click the name of your active interface** to begin capturing packets. You will see a new window with packet data scrolling in real-time.

#### **Step 4: Perform Network Activities and Stop the Capture**

1.  With the capture running, perform the actions you planned in Step 2:
    *   Browse to `http://example.com`.
    *   Browse to `https://google.com`.
    *   Run `ping 8.8.8.8` a few times.
2.  Allow the capture to run for approximately **30-60 seconds**.
3.  Click the **red square "Stop" button** on the toolbar to end the capture.

---

### Phase 3: Saving the Capture File (Deliverable 1)

#### **Step 5: Save the Packet Capture File**

1.  From the menu, navigate to `File -> Save As...`.
2.  Choose a location on your computer to save the file.
3.  Name your file (e.g., `MyFirstCapture`).
4.  The default "Save as type" is `pcapng (*.pcapng)`, which is the standard format. This is perfect.
5.  Click **Save**.

You have now created the first deliverable.

---

### Phase 4: Analyzing the Traffic

#### **Step 6: Use the Wireshark Interface**

*   **Packet List (Top Pane)**: A summary of each packet. Pay close attention to the `Protocol`, `Source`, and `Destination` columns.
*   **Packet Details (Middle Pane)**: A detailed, layered view of the currently selected packet.
*   **Packet Bytes (Bottom Pane)**: The raw packet data in hexadecimal.

#### **Step 7: Identify Protocols**

The easiest way to get an overview of the protocols you captured is by using the **Protocol Hierarchy** tool.

1.  Navigate to the menu: `Statistics -> Protocol Hierarchy`.
2.  This window provides a statistical breakdown of all protocols found in the capture, showing the percentage of packets and bytes for each.

This view will clearly show protocols like **TCP, DNS, HTTP, TLS, ICMP, and ARP**.

---

## Deliverable 2: Sample Analysis Report

Create a simple text file (`report.txt`) or a Markdown file (`report.md`) with your findings. Use the template below.

```markdown
# Network Traffic Analysis Report

**Date of Capture:** YYYY-MM-DD

**Summary of Activities Performed:**
During the packet capture, the following actions were performed to generate network traffic:
1.  Opened a web browser and navigated to `http://example.com`.
2.  Navigated to the secure site `https://google.com`.
3.  Used the command prompt to ping the IP address `8.8.8.8`.

## Identified Protocols and Traffic Types

Based on the analysis of the `MyFirstCapture.pcapng` file, the following primary protocols were identified:

*   **DNS (Domain Name System):** Observed when the browser requested the IP addresses for `example.com` and `google.com`. This protocol is responsible for name-to-address resolution.

*   **HTTP (Hypertext Transfer Protocol):** Observed in clear text when requesting the webpage from `http://example.com`. This is the foundational protocol for the World Wide Web.

*   **TCP (Transmission Control Protocol):** This protocol was used to establish stable connections for both the HTTP and HTTPS web browsing sessions. It ensures reliable data delivery via a three-way handshake.

*   **TLS (Transport Layer Security):** Observed as `TLSv1.2` or `TLSv1.3`. This protocol encrypted the application data for the session with `https://google.com`, providing a secure and private connection (HTTPS).

*   **ICMP (Internet Control Message Protocol):** Generated by the `ping 8.8.8.8` command. Packets of this type were "Echo (ping) request" and "Echo (ping) reply," used to test network connectivity.

*   **ARP (Address Resolution Protocol):** Observed performing lookups to map local IP addresses to physical MAC addresses on the local network.

### Conclusion

The capture successfully recorded traffic corresponding to the activities performed. Basic web browsing (HTTP/HTTPS) and network diagnostics (ICMP) were clearly identified, demonstrating the roles of DNS, TCP, and TLS in modern web communications.
