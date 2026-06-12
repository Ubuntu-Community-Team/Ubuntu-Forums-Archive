---
title: "Video mode not supported"
date: 2010-08-07
forum: General Help
---

### Post by sniperbond on 2010-08-07
Hello,
I have windows 7 64 bits and i'm trying to install ubuntu 10.04 amd64. The installation was good but when i'm trying to boot on ubuntu i have a black screen with a message "mode not supported".
I've looked for the problem on google. The solution is to change the frequency of the monitor. Mine supports only 75htz max and on the error message I have 77htz, what's why it's not supported.
The problem that to change the frequency for lunux i have to be logged in linux in order to type commands in the terminal.
But I can't see a thing, only the message about the mode not supported, so I can't type anything. 

i found some solutions here but i can't do what they ask, because I can't boot and the message doesn't disappear.
[http://ubuntuforums.org/showthread.php?t=358409](http://ubuntuforums.org/showthread.php?t=358409)

Do you have another solution please ?

Thanks by advance.

---

### Post by Mark Phelps on 2010-08-07
Can you boot from an Ubuntu LiveCD?

IF so, you could then edit the /etc/default/grub file, look for the GRUB_CMDLINE_LINUX= line and change the vga mode number.

When done, run "sudo update-grub" and when you reboot, you should be OK.

The link below provides details on the vga mode numbers:

[http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes]("http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes")

---

### Post by sniperbond on 2010-08-07
hello,
thank you for the reply. Where can I see the folders or access the terminal ? Because the screen goes black just after i choose: ubuntu in stead of windows 7.
I have installer ubuntu on windows 7, it's not really a live cd where there is no saves.
the one you get here, is it a livecd for you ?
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

do you know how to open the terminal before launching ubuntu ?

---

