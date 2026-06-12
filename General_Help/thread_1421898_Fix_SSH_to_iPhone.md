---
title: "Fix SSH to iPhone"
date: 2010-03-04
forum: General Help
---

### Post by tron153 on 2010-03-04
[SIZE=3][FONT=Times New Roman]I had connected to the phone via ssh before without any problems 
but later I got [/FONT][/SIZE][SIZE=3][FONT=Times New Roman]a message saying:"Server unexpectedly closed network connection"

After trying different solutions to enable ssh to my iphone again I found my own 

I reinstalled openssh client through synaptic package manager on ubuntu
Uninstalled openssh on my iphone 
I noticed a warning in cydia saying /etc/ssh was not empty so it would not be removed
I deleted the directory myself using ifile and restarted the phone
After it booted up I opened the terminal in ubuntu and established a ssh connection as root
It took about 20 seconds before I got a message printing the RSA key fingerprint 
I answered yes when it asked if I wanted to continue connecting 
I was prompted for the iphone's root password and connected successfully

Hope this works for you too
[/FONT][/SIZE]

---

