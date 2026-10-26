WIRESHARK SOC LAB
Lab 5 Follow TCP Stream, part 2
Online lab: https://networkwalks.com/wireshark-lab5/
SCENARIO
You are a SOC analyst. A staff member browsed the company intranet. An admin thinks someone left a secret
inside one of the web pages. Capture the traffic and use Follow TCP Stream to find the hidden text.
TOPOLOGY DIAGRAM
LAB INSTRUCTIONS
How to complete this lab
The lab screen: the task box on the left, the Windows 11 PC with Wireshark on the right.
Networkwalks | www.networkwalks.com Page 1
WIRESHARK SOC LAB
1. Read the scenario and the task in the left box (1). Do one task at a time.
2. On the right PC, sign in with the password hint. Double-click Wireshark, then double-click the WiFi interface to
start the capture (4).
3. Use the filter bar, the packet list and the Statistics menu to find the answer for the task.
4. Type or choose your answer in the box (2), then press Submit. Use Skip to leave a task for later and Previous
to go back. Answers are checked at the end.
5. Stuck? Press Show hint (3). Each hint costs 10% of the marks of that task, only the first time you open it. A
task with no answer scores 0.
6. On task 10 press Submit, add a comment if you like, then press Finish. You get a result card that you can
download as a picture and share. Show complete solution is always available.
TASKS
Sign in to the Windows PC (user Student, the password hint is on the sign-in screen), start a capture in Wireshark
and complete the 10 tasks below. Each task is worth 10 marks (100 in total). Each hint costs 10% of that task’s
marks.
Task 1. Capture the traffic 10 marks
Sign in to the Windows PC and capture the network traffic. How many packets did Wireshark capture?
Hint 1: Sign in with the password networkwalks. Then open Wireshark from the desktop.
Hint 2: Double-click the interface that shows an activity graph.
Hint 3: Read the number after Packets: in the status bar at the bottom of the Wireshark window.
Answer: 282
Solution: Sign in with the password networkwalks, double-click Wireshark on the desktop, then double-click the
WiFi interface. The status bar shows Packets: 282.
Task 2. Find the pages 10 marks
A staff member opened five pages on the company intranet. An admin says one of these pages has a hidden
note inside. Which page is it?
Options: /index.html | /about.html | /staff.html | /contact.html
Hint 1: Type http in the filter bar and press Enter. Right-click a GET packet, choose Follow, then TCP Stream. Change the stream
number at the bottom to see the next page.
Hint 2: Follow each page one by one. The page about staff is a good one to check first. Look for text that is not part of the normal
page.
Answer: /staff.html
Solution: Filter
http
, then follow the streams. In /staff.html you see a line that starts with <!--. That is the hidden note.
Task 3. Where is it hidden 10 marks
The hidden note is not shown to the person who opens the page in a browser. Where is it hidden?
Options: An HTML comment | The page title | An image | A cookie
Hint 1: Open the Follow TCP Stream window for the /staff.html page and look at the line with the note.
Hint 2: The note sits between the signs <!-- and -->.
Answer: An HTML comment
Solution: The note sits between
<!--
and
Networkwalks | www.networkwalks.com Page 2
WIRESHARK SOC LAB
-->
. That is an HTML comment. Browsers hide it, but Wireshark shows it.
Task 4. Find the stream 10 marks
Which TCP stream number carries the /staff.html page?
Options: 3 | 5 | 7 | 9 | 11
Hint 1: Type http in the filter bar and press Enter. Right-click a GET packet, choose Follow, then TCP Stream. Change the stream
number at the bottom to see the next page.
Hint 2: Look at the bottom of the Follow TCP Stream window. It shows Stream and a number.
Answer: 7
Solution: Right-click the GET /staff.html packet, choose Follow › TCP Stream. The bottom of the window shows
Stream 7.
Task 5. The code word 10 marks
The hidden note has an access code word. What is it?
Hint 1: Type http in the filter bar and press Enter. Right-click a GET packet, choose Follow, then TCP Stream. Change the stream
number at the bottom to see the next page.
Hint 2: Read the line inside the comment. The code word comes after the words “access code”.
Answer: Falcon-9921
Solution: The comment says “access code Falcon-9921”. The code word is Falcon-9921.
Task 6. The backup server 10 marks
The note also names a backup server. What is its IP address?
Options: 192.168.10.1 | 192.168.10.20 | 192.168.10.70 | 192.168.10.77
Hint 1: Type http in the filter bar and press Enter. Right-click a GET packet, choose Follow, then TCP Stream. Change the stream
number at the bottom to see the next page.
Hint 2: Read the same comment. The IP address comes after the words “backup server is”.
Answer: 192.168.10.77
Solution: The comment says “backup server is 192.168.10.77”. The IP address is 192.168.10.77.
Task 7. Which direction 10 marks
In the Follow TCP Stream window, the hidden note is in the blue text. Which way did this text travel?
Options: Server to client | Client to server
Hint 1: Type http in the filter bar and press Enter. Right-click a GET packet, choose Follow, then TCP Stream. Change the stream
number at the bottom to see the next page.
Hint 2: Red text is sent by the client (the PC that asked for the page). Blue text is sent by the server.
Answer: Server to client
Solution: The note is in the blue text. Blue is sent by the server, so it travelled from the server to the client.
Task 8. Status code 10 marks
What HTTP status code did the server send for the /staff.html page?
Options: 200 | 301 | 404 | 500
Hint 1: Click the response packet for /staff.html and open the HTTP part in the packet details.
Hint 2: You can also read the first blue line in the Follow TCP Stream window: HTTP/1.1 ...
Answer: 200
Solution: The first blue line is HTTP/1.1 200 OK. The status code is 200.
Networkwalks | www.networkwalks.com Page 3
WIRESHARK SOC LAB
Task 9. The downloaded file 10 marks
The staff member also downloaded a plain text file from the /download/ folder. What is the file name?
Options: report.txt | staff.txt | backup.txt | notes.txt
Hint 1: Filter http.request.uri contains "download" and look at the Info column.
Hint 2: The GET line ends with the file name.
Answer: report.txt
Solution: Filter
http.request.uri contains "download"
. The GET line shows /download/report.txt. The file is report.txt.
Task 10. Who made the report 10 marks
Follow the stream of that text file. Who prepared the report?
Options: Nadia | Sara | Ali | Farhan
Hint 1: Type http in the filter bar and press Enter. Right-click a GET packet, choose Follow, then TCP Stream. Change the stream
number at the bottom to see the next page.
Hint 2: Follow the report.txt stream (the last page). Read the line that starts with “Prepared by”.
Answer: Nadia
Solution: Follow the report.txt stream. The text says Prepared by: Nadia.
SUMMARY
Hidden note page:/staff.html (stream 7)
Hidden text: HTML comment from server to client
Code word: Falcon-9921
Backup server: 192.168.10.77

WIRESHARK SOC LAB
Lab 8 VoIP call replay
Online lab: https://networkwalks.com/wireshark-lab8/
SCENARIO
You are a SOC analyst. A phone call was made through the company VoIP system. Capture the traffic, find the call
and play it back to learn what was said.
TOPOLOGY DIAGRAM
LAB INSTRUCTIONS
How to complete this lab
The lab screen: the task box on the left, the Windows 11 PC with Wireshark on the right.
Networkwalks | www.networkwalks.com Page 1
WIRESHARK SOC LAB
1. Read the scenario and the task in the left box (1). Do one task at a time.
2. On the right PC, sign in with the password hint. Double-click Wireshark, then double-click the WiFi interface to
start the capture (4).
3. Use the filter bar, the packet list and the Statistics menu to find the answer for the task.
4. Type or choose your answer in the box (2), then press Submit. Use Skip to leave a task for later and Previous
to go back. Answers are checked at the end.
5. Stuck? Press Show hint (3). Each hint costs 10% of the marks of that task, only the first time you open it. A
task with no answer scores 0.
6. On task 10 press Submit, add a comment if you like, then press Finish. You get a result card that you can
download as a picture and share. Show complete solution is always available.
TASKS
Sign in to the Windows PC (user Student, the password hint is on the sign-in screen), start a capture in Wireshark
and complete the 10 tasks below. Each task is worth 10 marks (100 in total). Each hint costs 10% of that task’s
marks.
Task 1. Capture the traffic 10 marks
Sign in to the Windows PC and capture the network traffic. How many packets did Wireshark capture?
Hint 1: Sign in with the password networkwalks. Then open Wireshark from the desktop.
Hint 2: Double-click the interface that shows an activity graph.
Hint 3: Read the number after Packets: in the status bar at the bottom of the Wireshark window.
Answer: 1051
Solution: Sign in with the password networkwalks, double-click Wireshark on the desktop, then double-click the
WiFi interface. The status bar shows Packets: 1051.
Task 2. Call setup protocol 10 marks
A phone call was made on the network. Which protocol set up the call (INVITE, Ringing, OK)?
Options: SIP | RTP | DNS | FTP
Hint 1: Open Statistics › Protocol Hierarchy and look for the phone protocols.
Hint 2: Type sip in the filter bar and read the Info column.
Answer: SIP
Solution: Filter
sip
. The Info column shows Request: INVITE, Status: 180 Ringing and Status: 200 OK. The setup protocol is SIP.
Task 3. Voice protocol 10 marks
Which protocol carried the voice itself (the many small packets, one every 60 ms)?
Options: SIP | RTP | ARP | TLS
Hint 1: Type rtp in the filter bar.
Hint 2: Look at the Protocol column. Hundreds of packets show the same protocol name.
Answer: RTP
Solution: Filter
rtp
. About 800 packets show RTP. RTP carries the voice.
Networkwalks | www.networkwalks.com Page 2
WIRESHARK SOC LAB
Task 4. Caller extension 10 marks
Which extension number made the call? Look at the SIP INVITE.
Options: 101 | 102 | 201 | 202
Hint 1: Type sip.Method == "INVITE" in the filter bar and click the packet.
Hint 2: In the packet details open Session Initiation Protocol, then Message Header, and read the From line.
Answer: 101
Solution: Filter
sip.Method == "INVITE"
. The From line shows
sip:101@192.168.10.45
. The caller extension is 101.
Task 5. Caller name 10 marks
What is the name of the caller?
Options: Ali Raza | Sara | Nadia | Farhan
Hint 1: Look at the From line of the INVITE packet.
Hint 2: The name is written in quotation marks before the sip: address. You can also hear it in the call.
Answer: Ali Raza
Solution: The INVITE says
From: "Ali Raza" <sip:101@192.168.10.45>
. The caller is Ali Raza.
Task 6. The codec 10 marks
Which codec carried the voice? Click one RTP packet and look at the payload type.
Options: PCMU | PCMA | G.729 | GSM
Hint 1: Type rtp in the filter bar and click any packet.
Hint 2: In the packet details open Real-Time Transport Protocol and read Payload type.
Answer: PCMU
Solution: In an RTP packet the line says Payload type: ITU-T G.711 PCMU (0). The codec is PCMU.
Task 7. Who answered 10 marks
Who answered the call? Play the call and listen to the first words.
Options: Sara | Nadia | Farhan | Imran
Hint 1: Click Telephony in the Wireshark menu, then VoIP Calls. Click the call in the list, press Play Streams, then press Play and
listen.
Hint 2: The first voice is a woman. She says where she works and gives her name.
Answer: Sara
Solution: The woman answers: “Good morning, Payments desk. Sara speaking.” The answer is Sara. The To
line of the INVITE also says “Sara”.
Task 8. Card number 10 marks
The caller read out a card number to pay an invoice. What are the last 4 digits?
Hint 1: Click Telephony in the Wireshark menu, then VoIP Calls. Click the call in the list, press Play Streams, then press Play and
listen.
Hint 2: Listen to the man. He reads the card number in groups of four digits. Write the last group.
Answer: 2394
Solution: The man says the card number 4213 5588 7710 2394. The last 4 digits are 2394.
Networkwalks | www.networkwalks.com Page 3
WIRESHARK SOC LAB
Task 9. Expiry date 10 marks
What expiry date did the caller say?
Options: 08/27 | 09/28 | 09/29 | 12/28
Hint 1: Click Telephony in the Wireshark menu, then VoIP Calls. Click the call in the list, press Play Streams, then press Play and
listen.
Hint 2: Listen after the card number. Sara asks for the expiry date and the man answers.
Answer: 09/28
Solution: The man says “Zero nine, twenty eight.” The expiry date is 09/28.
Task 10. The fix 10 marks
How can the company stop people from listening to calls like this?
Options: Encrypt the call (SRTP) | Use a longer password | Change the port number | Turn off the phones
Hint 1: Think about the HTTPS lab. The traffic must be unreadable to a sniffer.
Hint 2: Voice packets (RTP) are sent in clear. A secure version of RTP exists.
Answer: Encrypt the call (SRTP)
Solution: Calls must be encrypted. SRTP encrypts the voice packets, and TLS protects the SIP messages. The
answer is Encrypt the call (SRTP).
SUMMARY
Call setup: SIP (UDP port 5060)
Voice: RTP, G.711 PCMU
Caller: Ali Raza, extension 101
Answered by: Sara (extension 202)
Card: ends 2394, expiry 09/28
Fix: SRTP (encrypted calls)
Watch the Wireshark video playlist: https://www.youtube.com/playlist?list=PLG-wUGWU39ro
Networkwalks | www.networkwalks.com Page 4

WIRESHARK SOC LAB
Lab 5 Follow TCP Stream, part 2
Online lab: https://networkwalks.com/wireshark-lab5/
SCENARIO
You are a SOC analyst. A staff member browsed the company intranet. An admin thinks someone left a secret
inside one of the web pages. Capture the traffic and use Follow TCP Stream to find the hidden text.
TOPOLOGY DIAGRAM
LAB INSTRUCTIONS
How to complete this lab
The lab screen: the task box on the left, the Windows 11 PC with Wireshark on the right.
Networkwalks | www.networkwalks.com Page 1
WIRESHARK SOC LAB
1. Read the scenario and the task in the left box (1). Do one task at a time.
2. On the right PC, sign in with the password hint. Double-click Wireshark, then double-click the WiFi interface to
start the capture (4).
3. Use the filter bar, the packet list and the Statistics menu to find the answer for the task.
4. Type or choose your answer in the box (2), then press Submit. Use Skip to leave a task for later and Previous
to go back. Answers are checked at the end.
5. Stuck? Press Show hint (3). Each hint costs 10% of the marks of that task, only the first time you open it. A
task with no answer scores 0.
6. On task 10 press Submit, add a comment if you like, then press Finish. You get a result card that you can
download as a picture and share. Show complete solution is always available.
TASKS
Sign in to the Windows PC (user Student, the password hint is on the sign-in screen), start a capture in Wireshark
and complete the 10 tasks below. Each task is worth 10 marks (100 in total). Each hint costs 10% of that task’s
marks.
Task 1. Capture the traffic 10 marks
Sign in to the Windows PC and capture the network traffic. How many packets did Wireshark capture?
Hint 1: Sign in with the password networkwalks. Then open Wireshark from the desktop.
Hint 2: Double-click the interface that shows an activity graph.
Hint 3: Read the number after Packets: in the status bar at the bottom of the Wireshark window.
Answer: 282
Solution: Sign in with the password networkwalks, double-click Wireshark on the desktop, then double-click the
WiFi interface. The status bar shows Packets: 282.
Task 2. Find the pages 10 marks
A staff member opened five pages on the company intranet. An admin says one of these pages has a hidden
note inside. Which page is it?
Options: /index.html | /about.html | /staff.html | /contact.html
Hint 1: Type http in the filter bar and press Enter. Right-click a GET packet, choose Follow, then TCP Stream. Change the stream
number at the bottom to see the next page.
Hint 2: Follow each page one by one. The page about staff is a good one to check first. Look for text that is not part of the normal
page.
Answer: /staff.html
Solution: Filter
http
, then follow the streams. In /staff.html you see a line that starts with <!--. That is the hidden note.
Task 3. Where is it hidden 10 marks
The hidden note is not shown to the person who opens the page in a browser. Where is it hidden?
Options: An HTML comment | The page title | An image | A cookie
Hint 1: Open the Follow TCP Stream window for the /staff.html page and look at the line with the note.
Hint 2: The note sits between the signs <!-- and -->.
Answer: An HTML comment
Solution: The note sits between
<!--
and
Networkwalks | www.networkwalks.com Page 2
WIRESHARK SOC LAB
-->
. That is an HTML comment. Browsers hide it, but Wireshark shows it.
Task 4. Find the stream 10 marks
Which TCP stream number carries the /staff.html page?
Options: 3 | 5 | 7 | 9 | 11
Hint 1: Type http in the filter bar and press Enter. Right-click a GET packet, choose Follow, then TCP Stream. Change the stream
number at the bottom to see the next page.
Hint 2: Look at the bottom of the Follow TCP Stream window. It shows Stream and a number.
Answer: 7
Solution: Right-click the GET /staff.html packet, choose Follow › TCP Stream. The bottom of the window shows
Stream 7.
Task 5. The code word 10 marks
The hidden note has an access code word. What is it?
Hint 1: Type http in the filter bar and press Enter. Right-click a GET packet, choose Follow, then TCP Stream. Change the stream
number at the bottom to see the next page.
Hint 2: Read the line inside the comment. The code word comes after the words “access code”.
Answer: Falcon-9921
Solution: The comment says “access code Falcon-9921”. The code word is Falcon-9921.
Task 6. The backup server 10 marks
The note also names a backup server. What is its IP address?
Options: 192.168.10.1 | 192.168.10.20 | 192.168.10.70 | 192.168.10.77
Hint 1: Type http in the filter bar and press Enter. Right-click a GET packet, choose Follow, then TCP Stream. Change the stream
number at the bottom to see the next page.
Hint 2: Read the same comment. The IP address comes after the words “backup server is”.
Answer: 192.168.10.77
Solution: The comment says “backup server is 192.168.10.77”. The IP address is 192.168.10.77.
Task 7. Which direction 10 marks
In the Follow TCP Stream window, the hidden note is in the blue text. Which way did this text travel?
Options: Server to client | Client to server
Hint 1: Type http in the filter bar and press Enter. Right-click a GET packet, choose Follow, then TCP Stream. Change the stream
number at the bottom to see the next page.
Hint 2: Red text is sent by the client (the PC that asked for the page). Blue text is sent by the server.
Answer: Server to client
Solution: The note is in the blue text. Blue is sent by the server, so it travelled from the server to the client.
Task 8. Status code 10 marks
What HTTP status code did the server send for the /staff.html page?
Options: 200 | 301 | 404 | 500
Hint 1: Click the response packet for /staff.html and open the HTTP part in the packet details.
Hint 2: You can also read the first blue line in the Follow TCP Stream window: HTTP/1.1 ...
Answer: 200
Solution: The first blue line is HTTP/1.1 200 OK. The status code is 200.
Networkwalks | www.networkwalks.com Page 3
WIRESHARK SOC LAB
Task 9. The downloaded file 10 marks
The staff member also downloaded a plain text file from the /download/ folder. What is the file name?
Options: report.txt | staff.txt | backup.txt | notes.txt
Hint 1: Filter http.request.uri contains "download" and look at the Info column.
Hint 2: The GET line ends with the file name.
Answer: report.txt
Solution: Filter
http.request.uri contains "download"
. The GET line shows /download/report.txt. The file is report.txt.
Task 10. Who made the report 10 marks
Follow the stream of that text file. Who prepared the report?
Options: Nadia | Sara | Ali | Farhan
Hint 1: Type http in the filter bar and press Enter. Right-click a GET packet, choose Follow, then TCP Stream. Change the stream
number at the bottom to see the next page.
Hint 2: Follow the report.txt stream (the last page). Read the line that starts with “Prepared by”.
Answer: Nadia
Solution: Follow the report.txt stream. The text says Prepared by: Nadia.
SUMMARY
Hidden note page:/staff.html (stream 7)
Hidden text: HTML comment from server to client
Code word: Falcon-9921
Backup server: 192.168.10.77
Report: report.txt, prepared by Nadia
Watch the Wireshark video playlist: https://www.youtube.com/playlist?list=PLG-wUGWU39ro
Networkwalks | www.networkwalks.com Page 4
Report: report.txt, prepared by Nadia
Watch the Wireshark video playlist: https://www.youtube.com/playlist?list=PLG-wUGWU39ro
Networkwalks | www.networkwalks.com Page 4
