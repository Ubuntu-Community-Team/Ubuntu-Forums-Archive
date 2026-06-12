---
title: "Add an application to &quot;open with&quot; other application list"
date: 2011-12-17
forum: General Help
---

### Post by huntkey on 2011-12-17
Hi experts,

I have .pcap file, which is wireshark capture files that I saved by my windows box. I want to make linux know to use wireshark to open the file. I have tried to go to property -> Open with -> Show other applications but wireshark is not listed there. Wireshark is installed and I can open the file by dragging the file to the opened wireshark window. How can I link this file type to Wireshark on my Ubuntu 11.10?

Thanks!

---

### Post by ajgreeny on 2011-12-17
Right click on the file ->Properties ->Open With tab, and there you can set the file to open with wireshark.

---

### Post by huntkey on 2011-12-20
Hey [ajgreeny]("http://ubuntuforums.org/member.php?u=27747") sorry for the late reply. I was struggling to get my printer to work these days...

I have tried that but I don't have wireshark listed in the window for me to choose as the program to open this type of file. When I go to "open with" tab, then click on "Show other applications", I don't see wireshark there. I guess my question is how to add wireshark in the application list?

thanks!

---

### Post by ajgreeny on 2011-12-21
Try the custom command setting in the open with tab, and use whjatever custom command you use to start wireshark.  If you have an entry for wireshark in your menus, use alacarte, the menu editor to find the command needed.  I do not use wine so can not help more with the likely command needed, but you should be able to find it easily enough.

---

### Post by mc4man on 2011-12-21
wireshark's .desktop in 11.10 is poorly constructed so just edit it.

```
gksudo gedit /usr/share/applications/wireshark.desktop
```

Find the Exec=line & add a %f to the end, so it looks like - 
```
Exec=wireshark %f
```

Make sure the MimeType= line looks like this
```
MimeType=application/vnd.tcpdump.pcap;
```

---

### Post by huntkey on 2011-12-21
Thank you so much mc4man! Can you tell me what the %f is for? Is it the reason why wireshark shows in my application menu now?

---

