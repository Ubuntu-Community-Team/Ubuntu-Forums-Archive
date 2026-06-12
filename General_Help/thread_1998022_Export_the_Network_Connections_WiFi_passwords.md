---
title: "Export the Network Connections WiFi passwords"
date: 2012-06-06
forum: General Help
---

### Post by hanzj on 2012-06-06
The Network Connections applet saves the WiFi passwords. We only have to enter the password for a network once. Going forward on the same SSID, we are automatically connected.

How can we export the list of WiFi networks (SSIDs) and their passwords?

Several reasons why exporting is valuable:
1. To import into Windows 7 OS partition
2. When upgrading the Linux partition.
3. For use on other computers.


Bonus question for the eager: Where are the WiFi passwords  saved on my computer?

---

### Post by Bucky Ball on 2012-06-06
You don't know the passwords already? What is your situation exactly?

The SSID (networks) in range of you wirless router/access point will be shown in the other OSs without having to import them (unless you are talking about something else; custom settings or other).

---

### Post by hanzj on 2012-06-06
Bucky Ball,
Thanks for your reply.
Yes we know the passwords. We have gone through upgrade after upgrade. And every time, we have to enter all the passwords, several dozen of them. This chore could be avoided if we could export and later import the passwords.

---

### Post by leopoldbirkholm on 2012-06-06
What I do is open an text document in gedit or notepad or similar and type in the password and use CTRL+C and CTRL+V. That's how I do it.

---

### Post by steeldriver on 2012-06-06
for the network-manager service, the connection definitions (including credentials) are stored in /etc/NetworkManager/system-connections/ so you could backup and restore those files 

for obvious reasons you will need root permissions to read them

---

### Post by hanzj on 2012-06-08
steeldriver, 
Thanks for your helpful post. You've solved the problem.

---

