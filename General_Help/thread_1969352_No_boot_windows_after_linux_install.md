---
title: "No boot windows after linux install"
date: 2012-04-29
forum: General Help
---

### Post by JPfan on 2012-04-29
Hello, I installed Lubuntu earlier today selecting the option to
install it along with windows.

Windows is still on my hard drive, however will not boot:confused:. I have inserted the Windows 7 repair cd and ran all available utilities.

Is there any GUI bootloader settings besides startupmanager?

I need the closest thing to a silver bullet to tackle this issue because I have so much stuff on my windows and also need the nt right now.I need to boot windows, the partition is still there. Also, there seems to be various grub problems as I get different weird messages with cursors not allowing entries at startup. I have located some threads about this and tried them, I can't remember them right now though, I am spent.

---

### Post by oboedad55 on 2012-04-30
> **JPfan said:**
> Hello, I installed Lubuntu earlier today selecting the option to
install it along with windows.

Windows is still on my hard drive, however will not boot:confused:. I have inserted the Windows 7 repair cd and ran all available utilities.

Is there any GUI bootloader settings besides startupmanager?

I need the closest thing to a silver bullet to tackle this issue because I have so much stuff on my windows and also need the nt right now.I need to boot windows, the partition is still there. Also, there seems to be various grub problems as I get different weird messages with cursors not allowing entries at startup. I have located some threads about this and tried them, I can't remember them right now though, I am spent.

Did you overwrite the MBR? Can you boot Windows or Ubuntu? If the latter go to a command prompt and type in "sudo update-grub". It should find your Windows install. In the future, I suggest before you panic to post a note here asking for help. Most things are easily dealt with, but if you start trying things out of desperation then the situation can get out of hand quickly.

---

### Post by JPfan on 2012-04-30
Yes I ran the supergrubdisk iso to fix the mbr.

Sometimes when rebooting I get a blank screen that says

MBR 12:

will not accept any input from that point.

---

### Post by oboedad55 on 2012-04-30
> **JPfan said:**
> Yes I ran the supergrubdisk iso to fix the mbr.

Sometimes when rebooting I get a blank screen that says

MBR 12:

will not accept any input from that point.

Need more info; can you boot into any OS at any time or you always get the MBR error?

---

### Post by zdeuyo on 2012-04-30
> **JPfan said:**
> Hello, I installed Lubuntu earlier today selecting the option to
install it along with windows.

Windows is still on my hard drive, however will not boot:confused:. I have inserted the Windows 7 repair cd and ran all available utilities.

Is there any GUI bootloader settings besides startupmanager?

I need the closest thing to a silver bullet to tackle this issue because I have so much stuff on my windows and also need the nt right now.I need to boot windows, the partition is still there. Also, there seems to be various grub problems as I get different weird messages with cursors not allowing entries at startup. I have located some threads about this and tried them, I can't remember them right now though, I am spent.

Hello,


This should solve your problem

Link: [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

Please let me know if this solves your problem.

All the best.

---

### Post by garvinrick4 on 2012-04-30
In ubuntu or live cd (ubuntu install cd using Try Ubuntu) open a terminal and copy and paste this:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
```
```
chmod +x bootinfoscript
```
```
sudo bash bootinfoscript
```

Now go to Home and will be a RESULTS file open it and copy and paste whole thing into message box.
Highlight whole thing again and click on # in upper right of message box and will put in nice little box to read from.
Now submit reply.

##This will show whole boot info so as to see what problem is.

---

### Post by JPfan on 2012-04-30
Thanks for all the help. On my last restart (I was booting several different os's and repair tools from a usb) I decided to just put in the windows cd again and found this on my android browser:  

[http://pcsupport.about.com/od/fixtheproblem/ht/rebuild-bcd-store-windows.htm](http://pcsupport.about.com/od/fixtheproblem/ht/rebuild-bcd-store-windows.htm)

So I opened the NT CMD and did the commands to fix mbr and fix boot as well as followed his instructions on how to rebuild the cmd, I am now booting back into windows just fine
and will now look at  ways to safely access my other partitions. This process was very fast and easy because I had the cd.

This was all before I could get back to this thread. In the future I will use the BootRepair 
utility as you suggested and install it right away to resolve any issues. So  yes,"don't panic" would be the moral of the story.

SOLVED

---

