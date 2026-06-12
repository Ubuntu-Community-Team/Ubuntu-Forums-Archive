---
title: "Cant start xServer| Need help  | With log files"
date: 2010-11-10
forum: General Help
---

### Post by TheParadox on 2010-11-10
When I boot up my laptop it goes directly to the command line. I try to start xserver and I get this error. I have reinstalled my OS multiple times and tried installing my video drivers many ways. I keep having this problem. I'm super desperate for help because I have a server and I need my laptop to manage it. Thanks a million guys!

[    86.561] (EE) No devices detected.
[    86.561] 
Fatal server error:
[    86.561] no screens found
[    86.561] 

The log file cant be found here [http://pastebin.com/VMEZKaMG](http://pastebin.com/VMEZKaMG)

---

### Post by dino99 on 2010-11-10
what says:

sudo nano /etc/X11/xorg.conf

need to know which graphic card / chipset is used.

---

### Post by TheParadox on 2010-11-10
Here you go sir
[http://pastebin.com/sk137iZW](http://pastebin.com/sk137iZW)

---

### Post by dino99 on 2010-11-10
ok ive seen it, so i suppose you run maverick. Actual kernel directly deal with X, so no need the oldish xorg.conf by default.

sudo rm -f /etc/X11/xorg.conf

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

then reboot and check driver activation, nvidia-current might be actived (system admin additional driver)

---

### Post by TheParadox on 2010-11-10
Sadly I still boot into the command line. I cant start x either same issue.

---

### Post by dino99 on 2010-11-10
have you installed the driver from nvidia (.run) or from the repo ?

sudo dpkg-reconfigure nvidia-current

---

### Post by TheParadox on 2010-11-10
Yes and I just tried that command and rebooted and tried to start x same thing.

---

### Post by dino99 on 2010-11-10
> **TheParadox said:**
> Yes and I just tried that command and rebooted and tried to start x same thing.

yes to what ?

sudo apt-get --purge remove nvidi*
sudo apt-get update
sudo apt-get install nvidia-current
sudo apt-get install nvidia-common
sudo apt-get install nvidia-settings

then reboot

---

### Post by TheParadox on 2010-11-10
Okay I purged the old drivers and am installing the ones with that command. It is 150mb should take a few mins. Thanks for your help. I cant wait to get ubuntu running smoothly on this laptop. Sorry for any typos im on my iphone 4.

---

### Post by TheParadox on 2010-11-10
Same dang error after all that.

---

### Post by TSJason on 2010-11-10
What does /var/log/Xorg.0.log say?

Have you already tried using the older nvidia driver package (nvidia-glx-96)?

---

