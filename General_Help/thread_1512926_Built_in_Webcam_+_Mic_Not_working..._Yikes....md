---
title: "Built in Webcam + Mic Not working... Yikes..."
date: 2010-06-18
forum: General Help
---

### Post by Lookabird on 2010-06-18
Hi guys, new to Ubuntu here, just installed 10.4 and did the updates. The built in mic doesnt seem to work via sound recorder and the built in webcam, well i have absolutely no idea how to even access that. I used to skype and MSN/Vid Chat with my friends and kinda need the webcam+mic... So... Any suggestions or remedies? Thanks in advance for any response

---

### Post by Lookabird on 2010-06-18
Bump

---

### Post by chrismitt2002 on 2010-06-18
im having a similar problem 
[http://ubuntuforums.org/showthread.php?t=1512939](http://ubuntuforums.org/showthread.php?t=1512939) but mine is not a built in min its a usb cam and the mic doesnt seem to want to work in skype

---

### Post by no2498 on 2010-06-20
on/in 910 and up cheese webca booth is/should be installed
look for it in sound & video

try the cam in cheese first
if not installed look in add/remove install it

you may need this for cheese and skype

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype


put that in a terminal


good luck

---

### Post by YannBuntu on 2010-07-05
As Microsoft changed their MSN protocol in March, it is now impossible to do voice&video calls with this protocol on Linux.

To do voice/video calls with Windows interlocutors, I recommend :
- Ekiga (which exists also on Windows)
- Empathy (with Telepathy PPA , and ubuntu-restricted-extras package, and of course a Jabber account e.g. gmail address), that can do voice&video calls with Windows Gtak interlocutors
- Skype (which exists also on Windows), but this one is not open-source

---

