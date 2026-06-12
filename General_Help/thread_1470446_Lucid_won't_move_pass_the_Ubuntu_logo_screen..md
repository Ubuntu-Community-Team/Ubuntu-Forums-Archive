---
title: "Lucid won't move pass the Ubuntu logo screen."
date: 2010-05-02
forum: General Help
---

### Post by Buying_Some_Time on 2010-05-02
I've been trying to boot up ubuntu all day and I can never get it to move pass the logo screen it just seems stuck there for some reason, even though it was working fine yeterday. 

I do belive that the probelm is in the Xorg.config file though, because I was trying to hook my laptop up to my TV and I maybe messed up something in there. Can someone please help me? I am a noob to Ubuntu and I really like it but I just need to fix this fast. Thanks.

---

### Post by GSF1200S on 2010-05-02
> **Buying_Some_Time said:**
> I've been trying to boot up ubuntu all day and I can never get it to move pass the logo screen it just seems stuck there for some reason, even though it was working fine yeterday. 

I do belive that the probelm is in the Xorg.config file though, because I was trying to hook my laptop up to my TV and I maybe messed up something in there. Can someone please help me? I am a noob to Ubuntu and I really like it but I just need to fix this fast. Thanks.

What video card do you have? When the grub menu shows in the beginning (hold left shift if it doesnt show), highlight your Ubuntu install. Then, hit 'e' and move down to the boot line which ends with something like:
> ro quiet splash

Put in that line:
```
xdriver=vesa
```

IF and only IF you have an Nvidia card, you can also add:
```
nomodeset
```

So, as an example, the boot line ending would look something like:
```
ro quiet splash nomodeset xdriver=vesa
```

Then, hit Ctrl+X to boot that edited version. If that works, let me know the situation in this thread and well try to get everything setup :)

---

### Post by Buying_Some_Time on 2010-05-02
> **GSF1200S said:**
> What video card do you have? When the grub menu shows in the beginning (hold left shift if it doesnt show), highlight your Ubuntu install. Then, hit 'e' and move down to the boot line which ends with something like:


Put in that line:
```
xdriver=vesa
```

IF and only IF you have an Nvidia card, you can also add:
```
nomodeset
```

So, as an example, the boot line ending would look something like:
```
ro quiet splash nomodeset xdriver=vesa
```

Then, hit Ctrl+X to boot that edited version. If that works, let me know the situation in this thread and well try to get everything setup :)

Thanks for your reply, and yes I have a Nvidia card but that didn't work it still just stops at the ubuntu logo screen :( anything else I could/should try?

---

### Post by GSF1200S on 2010-05-02
> **Buying_Some_Time said:**
> Thanks for your reply, and yes I have a Nvidia card but that didn't work it still just stops at the ubuntu logo screen :( anything else I could/should try?

Ok.. it works for some people and doesnt work for others (it didnt work for me). Do you have another install to use or a liveCD to use so you can get access to the partition? If so, you can try my first post on the first page of this thread:
[http://ubuntuforums.org/showthread.php?t=1466337](http://ubuntuforums.org/showthread.php?t=1466337)

It worked for 5-6 people (as well as for me), while some others still had issues. Alot of this is due to Plymouth still giving some people problems.

**EDIT** If you want, you can just try removing quiet splash from the boot line as well. So, your line would look like:
> ro nomodeset
Make sense? Remember to hit Ctrl+X to boot that revision...

---

### Post by Buying_Some_Time on 2010-05-02
Okay thanks again, after a few tries I finally got what you told me to do in your first post to work, but now my screen resolution is messed up, and when I try to go the the Nvidia settings it gives me this:    (You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.)  What do I do now? Sorry and thank you again.

---

### Post by GSF1200S on 2010-05-02
> **Buying_Some_Time said:**
> Okay thanks again, after a few tries I finally got what you told me to do in your first post to work, but now my screen resolution is messed up, and when I try to go the the Nvidia settings it gives me this:    (You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.)  What do I do now? Sorry and thank you again.

Its because I had you put the xdriver=vesa on the bootline ;) Its basically forcing X to use VESA instead of your Nvidia drivers, but at least you are booting ;). Now that youve figured out how to get it booting, lets get your boot process working for next time:

Open a terminal and run:
```
sudo gedit /etc/default/grub
```
Then, look for the line that says:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
and make it:
> GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
Save and exit gedit.

Then do the following commands for good measure:
```
sudo dpkg --configure -a
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth
sudo apt-get update
sudo apt-get install -f
sudo apt-get install ubuntu-desktop
```

Finally, run these two commands:
```
sudo update-initramfs -u
sudo update-grub2
```
and reboot the computer. You will notice a bunch of text instead of the flashing cursor you likely saw before. This is due to removing quiet and splash from the line in /etc/default/grub before updating grub. If you want a pretty splash screen on boot (as many have had issues with this on this release), then try this link (which worked for me):
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by Buying_Some_Time on 2010-05-03
Wow thanks a bunch everything is working fine now, you're amazing. Thanks again!

---

### Post by Sefianix on 2010-05-09
I just wanted to say thanks!  This also worked on my stuck Kubuntu Lucid 64bit Desktop.  It used to work before; I'm not sure what changed.  It would just get stuck on the Kubuntu logo screen and never come to the login screen.  I SSH'd into the box and ran the commands you provided and it works now.

---

### Post by GSF1200S on 2010-05-09
Glad it worked for both of you :)

---

