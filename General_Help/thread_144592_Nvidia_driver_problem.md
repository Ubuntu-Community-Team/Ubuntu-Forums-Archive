---
title: "Nvidia driver problem?"
date: 2006-03-14
forum: General Help
---

### Post by ozzyfreak424 on 2006-03-14
Ok, I installed Americas Army. After which I tryed running it and the logo comes up and it would go away after a few seconds and not load.  I looked around online and found a few posts the recommended I install the latest Nvidia drivers.  So I installed them with automatix.  When i rebooted it goes to black screen.  I can't log in I can't do anything.  Can Anyone help me out? I'm, not sure what Nvidia card I have I just know its a 256 agp.  I can't remember what the model it was.

---

### Post by s|k on 2006-03-14
[QUOTE=ozzyfreak424]Ok, I installed Americas Army. After which I tryed running it and the logo comes up and it would go away after a few seconds and not load.  I looked around online and found a few posts the recommended I install the latest Nvidia drivers.  So I installed them with automatix.  When i rebooted it goes to black screen.  I can't log in I can't do anything.  Can Anyone help me out? I'm, not sure what Nvidia card I have I just know its a 256 agp.  I can't remember what the model it was.[/QUOTE]
I also have an nVidia driver and I followed these instructions to get it to work:
[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

Method 2 worked for me.

---

### Post by NoNo_231 on 2006-03-14
The previous xorg.conf is backuped with name xorg.conf_backup_date.time by automatix. 

Do ctrl-option-F1 to get to a shell prompt

login

cd /etc/X11
ls       (this is so you can see how the backup is named)
sudo cp xorg.conf_backup_date.time xorg.conf

startx to start xserver or reboot to start from the beginning. This will get your system to previous situation.

You can also do ctrl-option-F1 to get to a shell prompt, then type this command:

sudo dpkg-reconfigure xserver-xorg 

Follow instuctions then to get a screen again. Untill you find a solution. This will be like configuing first time.

---

