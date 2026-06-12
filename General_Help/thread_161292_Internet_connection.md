---
title: "Internet connection"
date: 2006-04-16
forum: General Help
---

### Post by rgentry on 2006-04-16
Hello I just recently installed ubuntu.

Here is my situation.

I have a wireless router downstairs that links to an upstairs computer.  Now, since I don't have a wireless card for the computer with ubuntu, I'm wondering if I can have the internet connection go through this computer while it's turned on and go to the computer with ubuntu.

If not, what other options could i do without having to go get a wireless card/adapter for the ubuntu computer.  That is my last option.

---

### Post by PriceChild on 2006-04-16
I take it you're running Windows XP on the computer you're using right now?

If so, then bridge the wireless and ethernet connections and start up the ubuntu machine after being connected via ethernet to the xp machine.

This should work ok if you enable the ethernet port in ubuntu.

---

### Post by rgentry on 2006-04-18
After I boot up the Ubuntu machine what would i have to do?

I tried setting up the ethernet connection but i am still unable to get onto the internet.:confused:

---

### Post by PriceChild on 2006-04-18
ok so you want:

                                             air                         ethernet
Internet ----->   wireless    -----> xp computer ------------> ubuntu computer
                       access point

To do the first, then bridge your wireless and ethernet connections on the xp computer, and then change the network settings on the ubuntu machine to

ip: 192.168.0.10
Subnet mask: 255.255.255.0
Gateway address: 192.168.0.1

Why don't you just connect the ubuntu machine to the wireless access point too instead?

---

### Post by rgentry on 2006-04-18
EDIT: I pinged the Ubuntu computer and I got replys so it is technicly connected.  I just don't know what I'm doing wrong with the internet connection.

Alright,

Internet -----> wireless -----> xp computer ------------> ubuntu computer

Is what I plan on doing.

I tried what you said and it did not work.

I'm using a D-link router and D-link adapter if that has anything to do with the problem.

I would just switch the adapter to the Ubuntu computer but I couldn't figure out how to install the adapter.  I have the CD and put it in and it wouldn't let me run the exe...I'm pretty new to this, so i may of been going the wrong way trying to install it.

If using the adapter would work and I was just doing that the wrong way I could use the adapter.  It would be a lot easier if I could connect through my XP computer though.

---

### Post by PriceChild on 2006-04-18
I definately know how to share an internet connection from an ubuntu computer:
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

However, the wireless from the ubuntu may be a bit harder. What's your wireless card model and make?

Have you checked that the xp computer hasn't got a firewall on? Maybe right clicking on the wireless connection, going to advanced or something, then clicking "share this internet connection" might work too.

---

### Post by rgentry on 2006-04-18
I run Norton on the xp computer, so windows firewall is disabled.  The wireless is a D-Link Airplus Xtreme G DWL-G132 Wireless USB Adapter.  There is also a CD with it that has drivers on it.

---

### Post by PriceChild on 2006-04-18
Norton Firewall?

That'll probably be it! Disable the firewall for a few minutes, and reboot the ubuntu machine to try again.

If it works, then you we'll set about sorting out the Norton firewall to allow things from the ubuntu machine.

---

### Post by rgentry on 2006-04-18
EDIT: I can also ping back to the XP computer from the Ubuntu computer.

Doesn't seem to be Norton...

I can repeat exactly what my settings are because everything looks correct.  Is there a file on the Ubuntu machine that i may need to edit?

---

### Post by salman16 on 2006-04-18
Any one knows how to put windows in boot screen i have installed abuntu in my 1 of the partions on my hard drive and windows was in 1 of the partions and i have installed abuntu but i cant go on windows because in boot screen there is no windows but i didint remove windows someone help me please:(

---

### Post by rgentry on 2006-04-18
Uh, Why did you post in my thread?

F8, F12, or F1 is the boot screen.  Forgot which one off the top of my head.

Get a boot disc so you can change the active partition on the drive.

---

### Post by salman16 on 2006-04-18
which boot dics abuntu?

---

### Post by rgentry on 2006-04-18
Any disc (floppy or CD) that you can edit the partitions with it.  I use Partition Magic and it created a boot disc so i can change active partitions that way.  

And once again, Why are you posting in my thread?

---

### Post by salman16 on 2006-04-18
i didnt know where to post anyway sry.

---

