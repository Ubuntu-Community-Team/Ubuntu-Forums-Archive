---
title: "ubuntu installation too slow to even use"
date: 2010-05-27
forum: General Help
---

### Post by CaptainWraith on 2010-05-27
i have a dual installation of ubuntu and XP on older laptop (2.6 celron single core 60 gig hard drive)  ubuntu is so slow it takes a couple minutes to open a folder.  i dont care if i just get rid of ubuntu and dont reinstall it but if anyone knows how to fix the problem that will work too.  

i am currently trying to copy the windows partition of the HD onto an external harddrive that way i could just format the drive and copy windows back onto it if nothing else works out but ubuntu is no longer recognising the external.  any help would be much appreciated.

---

### Post by CaptainWraith on 2010-05-27
i should mention that its ubuntu 9.10

---

### Post by mindpowerz on 2010-05-27
Did you try booting Ubuntu off a Live CD or USB Flash drive, and see if you get the same results?

---

### Post by CaptainWraith on 2010-05-27
i tried once but it was taking forever to start up  (the cd drive on that computer isnt that great) but i'll try again.

---

### Post by CaptainWraith on 2010-05-27
i should also note that windows works fine

---

### Post by CaptainWraith on 2010-05-27
i tried running it off the cd and it would not work for whatever reason.  again windows xp works just fine though

---

### Post by Joe of loath on 2010-05-27
How much memory does it have? IIRC laptops come with a tiny amount of memory compared to what they should have (Or what I think they should have :lol:)

---

### Post by CaptainWraith on 2010-05-27
i think it has 1 gig of memory.  before it was installed i used the memory test option and it came back fine.  again XP works just fine so i doubt its a hardware problem.

---

### Post by CaptainWraith on 2010-05-27
anyone have any ideas on whats going on?

---

### Post by mr clark25 on 2010-05-27
seems odd... do you have compiz enabled?

---

### Post by CaptainWraith on 2010-05-28
no.  there has only been a few programs installed using software center (firestarter, clam antivirus etc.)

---

### Post by CaptainWraith on 2010-05-28
no.  there has only been a few programs installed using software center (firestarter, clam antivirus etc.)

---

### Post by CaptainWraith on 2010-05-28
sorry about the double post

---

### Post by geet89 on 2010-05-28
try installing kubuntu and see if the same problem exists

---

### Post by Spr0k3t on 2010-05-28
What is the laptop make/model.  Also, copy and paste this into a terminal once the system is up and running:

```
lshw >> ~/lshw.txt && lspci >> ~/lspci.txt && dmesg >> ~/dmesg.txt
```

After that, attach the three text files found in your home folder.  This will give people something to go on other than stabbing at the dark hoping for a solution.  To help further troubleshoot the issue right down to the installation, remove any extra software you have added.

---

### Post by CaptainWraith on 2010-05-28
i tried to remove the software but it would nt give me the remove option... just upgrade.  is there another way to remove it than using software center?

---

### Post by EarlGrey167 on 2010-05-28
I don't know if this helps or not but I installed Ubuntu 10.04 on my laptop, it ran but wasn't very peppy. I then downloaded Xubuntu for my PC (my kids mostly play games on it). I tried the live CD on my laptop and couldn't believe the difference. You might try Xubuntu so you can keep your Linux partition.

---

### Post by Serpher on 2010-05-28
I don't think installing Xubuntu or Kubuntu will really fix anything. Xubuntu would be logical of the computer was really old, and had something like a 800MHz processor and 64MB of RAM. Ubuntu is a lot less resource intensive than Windows XP, it seems like your hardware just doesn't really like Linux. It's fairly common on laptops. Before judging Linux as being garbage because of this, it's the makers of the hardware. They make it to run Windows, and don't work Linux which has a way more flexible kernal (Easily put just think of it as a driver at the lowest level) than Windows anyway.

---

### Post by Joe of loath on 2010-05-28
> **Serpher said:**
> I don't think installing Xubuntu or Kubuntu will really fix anything. Xubuntu would be logical of the computer was really old, and had something like a 800MHz processor and 64MB of RAM. Ubuntu is a lot less resource intensive than Windows XP, it seems like your hardware just doesn't really like Linux. It's fairly common on laptops. Before judging Linux as being garbage because of this, it's the makers of the hardware. They make it to run Windows, and don't work Linux which has a way more flexible kernal (Easily put just think of it as a driver at the lowest level) than Windows anyway.

Actually xubuntu uses more memory than ubuntu in some tests. With 64MB You're hard pressed getting a full desktop distro running.

---

### Post by Spr0k3t on 2010-05-28
> **CaptainWraith said:**
> i tried to remove the software but it would nt give me the remove option... just upgrade.  is there another way to remove it than using software center?

Go to the "Installed Software" selection on the left side of the software center pane.  Verify the extra software you have already installed (such as firestarter and clam AV) and select "Remove".  Be sure you are not removing the default loaded software for now, it will help hammer out the problems.

---

### Post by marshag63 on 2010-05-28
You could try disabling lots of the extra stuff - like Tomboy, calendar, update manager icons on panel bar and set wallpaper to just a color and see if performance changes.  Also, turn off compiz if you tweaked any of the fun extra and see what happens.

Another way to see what is using the most cpu power is to run htop in a terminal.  Firefox and Openoffice do take lots of ram and can be slow on first load.

Hope this helps you troubleshoot the problem.

MarshaG.

---

### Post by CaptainWraith on 2010-05-29
when it was installed it wasnt this bad but it had some problems still.   sprocket  i tried to go that route but the only option it gave me was upgrade... it DID NOT give the the remove option like it should.   the laptop is a toshiba a45-s120.  the computer is actually my dads and he doesnt care if he keeps linux or not.  if it would be easier is rather uninstall it. 

serpher  dont worry i have Ubuntu on a desktop that  i use everyday and it works fine except pidgin likes to quit at random times.

---

### Post by Spr0k3t on 2010-05-29
So what's the status of the files?  Also, can I get some screen shots of the Ubuntu Software Center not showing the "Uninstall" button?

---

### Post by Spr0k3t on 2010-05-29
> **CaptainWraith said:**
> pidgin likes to quit at random times.

There's a bug in pidgin that causes it to quit like you mentioned.  A way around it is to use the Empathy client.  Very similar in design and function.

---

