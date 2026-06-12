---
title: "Any way to increase speed?"
date: 2011-05-20
forum: General Help
---

### Post by Meiketsu on 2011-05-20
Everyone always told me Ubuntu is a perdy Speedy OS. Im thinking otherwise so far, unless Im missing something. Basic problem where i see the lack of speed compaired to when this same machine is running windows 7 comes to web browsing. Mainly youtube vids. i downloaded Flash from the software center and downloaded java with the help of some commands i looked up. I cant watch more than about 8 seconds of video before it buffers. This common?

---

### Post by bdoe on 2011-05-20
"Buffering" usually means your browser isn't getting data fast enough to keep the player fed. This is usually a network issue. Have you verified your network settings to make sure they're correct? It also wouldn't hurt to check your internet speed through [http://www.speedtest.net](http://www.speedtest.net)

---

### Post by Meiketsu on 2011-05-20
Oh wow that test was dismal. Ive ran that test before on this machine when ive booted with Win7 and it was way better. download was only .80mbs.. shouldnt be like that, my internet on my Desktop is Blazingly fast and its on wireless too. This is also a Brand new laptop.

---

### Post by bdoe on 2011-05-20
Sounds like something might be misconfigured. Do you know what kind of wireless card is in your laptop?  Also, try connecting with an ethernet cable and seeing if your speed results improve.

---

### Post by Meiketsu on 2011-05-20
Just rebooted into Windows7 and ran the test again. Got WAY better results.
ping: 5ms  Download: 19.35mbs  Upload: 3.68mbs

---

### Post by Meiketsu on 2011-05-20
I dont know what kind of Wireless card is in this machine but this is what i have:
[http://www.google.com/products/catalog?hl=en&q=msi+a6200&sqi=2&cid=2317547610331964069&os=tech-specs](http://www.google.com/products/catalog?hl=en&q=msi+a6200&sqi=2&cid=2317547610331964069&os=tech-specs)

---

### Post by 5149.5 on 2011-05-20
[IMG]http://www.speedtest.net/result/1305364162.png[/IMG]

That's with a low end netbook with an atom running Ubuntu 11.04.

---

### Post by wojox on 2011-05-20
Post pictures like 5149.5 has done with both Windows and Linux. I have a hard time believing that your that off.

---

### Post by bdoe on 2011-05-20
> **Meiketsu said:**
> I dont know what kind of Wireless card is in this machine but this is what i have:
[http://www.google.com/products/catalog?hl=en&q=msi+a6200&sqi=2&cid=2317547610331964069&os=tech-specs](http://www.google.com/products/catalog?hl=en&q=msi+a6200&sqi=2&cid=2317547610331964069&os=tech-specs)

Hmmm... There could be any number of different WLAN cards in there. Could you open a terminal, type "lspci" (without the quotes), and post the output?

---

### Post by Meiketsu on 2011-05-20
[[IMG]http://www.speedtest.net/result/1305386326.png[/IMG]]("http://www.speedtest.net/result/1305386326.png")


No command 'Ispci' found, did you mean:
 Command 'lspci' from package 'pciutils' (main)
Ispci: command not found

---

### Post by Meiketsu on 2011-05-20
Same computer, Same wireless connection, Same location as the test with Unubtu but on Win7 instead.. heres the results: 
[IMG]http://www.speedtest.net/result/1305390733.png[/IMG]

---

### Post by jawilljr on 2011-05-20
> **Meiketsu said:**
> [[IMG]http://www.speedtest.net/result/1305386326.png[/IMG]]("http://www.speedtest.net/result/1305386326.png")


No command 'Ispci' found, did you mean:
 Command 'lspci' from package 'pciutils' (main)
Ispci: command not found

You had a typo... you should have typed 

```
lspci -nn
```

You typed an "I" not an "l".

Jerry

---

### Post by 5149.5 on 2011-05-20
I use to have a similar issue due to a configuration problem on ubuntu. If you have an intel wlan card, it is probably the same problem.

---

### Post by Meiketsu on 2011-05-20
my bad.. heres what the terminal said.

00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 05)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
05:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
3f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
3f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
3f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)

---

### Post by 5149.5 on 2011-05-20
You have the same problem that I did.

```
Create a file called     /etc/modprobe.d/ath9.conf 

in this file enter this: ath9k nohwcrypt=1
```

---

### Post by Meiketsu on 2011-05-20
> **5149.5 said:**
> You have the same problem that I did.

```
Create a file called     /etc/modprobe.d/ath9.conf 

in this file enter this: ath9k nohwcrypt=1
```
Pardon me for being a novice at Linux but where/with what do i create said file? :???:

---

### Post by 5149.5 on 2011-05-20
> **Meiketsu said:**
> Pardon me for being a novice at Linux but where/with what do i create said file? :???:

Your favorite text editor is all you need.

---

### Post by Meiketsu on 2011-05-20
Ok wow, Everyone else is being very helpful. You on the other hand. not even going to go there. I appreciate everyone else helping and on the Note about that file i need to create, its not allowing me to save it even though im logged in as admin. Its saying I dont have permission necessary to save the file. -_-

---

### Post by 5149.5 on 2011-05-20
> **Meiketsu said:**
> Ok wow, Everyone else is being very helpful. You on the other hand. not even going to go there. I appreciate everyone else helping and on the Note about that file i need to create, its not allowing me to save it even though im logged in as admin. Its saying I dont have permission necessary to save the file. -_-

You obviously don't have admin rights. How did you login as admin? 
 I just use the sudo cmd. If you are using a gui editor, you would have to use gksudo to open it.

---

### Post by 5149.5 on 2011-05-20
Try it this way, You'll have to put in your password after the sudo command and your password is not echoed to the screen.

```
cd /etc/modprobe.d 

sudo echo "ath9k nohwcrypt=1" > ath9k.conf
```

---

### Post by bdoe on 2011-05-21
> **Meiketsu said:**
> Ok wow, Everyone else is being very helpful. You on the other hand. not even going to go there. I appreciate everyone else helping and on the Note about that file i need to create, its not allowing me to save it even though im logged in as admin. Its saying I dont have permission necessary to save the file. -_-
Just to clarify a point: Being logged in with an administrative account in Linux does not automatically confer administrative permissions. You still need to explicitly elevate your access level each time you need to. This is typically done by typing "sudo" before any command needing admin rights. For example, typing:```
sudo gedit /etc/modprobe.d/ath9k.conf
```will launch gedit (the Gnome text editor) with full admin (root) access. This is necessary to be able to write to a file outside your home directory.

Also worth remembering: Modifying, creating, or deleting any file outside of your home directory in Linux almost always requires root access.

---

### Post by Meiketsu on 2011-05-21
Ok, update. What you guys are trying to get me to do, im sure could work (it seems it fixes others problem) but I found this code was the answer for me. 
Worked great, heres my new speed test result and the code used. Again, appreciate the help guys =]
[IMG]http://www.speedtest.net/result/1305803718.png[/IMG]
```
sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update && sudo apt-get dist-upgrade -y
```

---

### Post by silentD on 2011-05-23
Meiketsu,

What an interesting thread.  I've been experiencing a similar issue.  I ran this speed test before running your suggested commands.  I'm going to post again after I reboot.  Hoping for similar results.

[IMG]http://www.speedtest.net/result/1309339276.png[/IMG]

---

### Post by silentD on 2011-05-23
Well crap!!!  Now my laptop won't boot.  It simply makes it to the screen with UBUNTU and the dots under that,  Moments after that the screen switches off then on again and quickly filled with what looks like boot sequence checklist items.  That's only up for about 2 seconds max.  Then the screen switches off and then on again quickly followed by even shorter screen with what looks to be different items but it's on for less than a second before this terrible sequence repeats again.

I know this is not the right forum for this but thought I'd post here first since this is where I started tonight.  If anyone has any suggestions I would love to hear them.  I won't learn a thing if I just reload the OS.

Take care all.

---

### Post by 5149.5 on 2011-05-23
Hopefully you learned to be more careful about trying things just because they are posted here. The correct answer to your problem could have been a simple modification instead of switching to a new bleeding edge kernel.

---

### Post by silentD on 2011-05-23
Any chance you have something constructive to say?  Most of the time I don't even know what I'm looking at but I'm not afraid to break something to learn.  It's just a computer.  I know I can always boot from a CD or USB so this can be fixed.  So again I ask can you point me in the right direction?

---

### Post by 5149.5 on 2011-05-23
> **silentD said:**
> Any chance you have something constructive to say?  Most of the time I don't even know what I'm looking at but I'm not afraid to break something to learn.  It's just a computer.  I know I can always boot from a CD or USB so this can be fixed.  So again I ask can you point me in the right direction?

I already tried. 

Like you said, you can always boot from a CD or USB.

---

### Post by silentD on 2011-05-23
Wow!!!!!  Do you by any chance do this professionally?  I hope not.  You've been on here about 5 seconds longer than me but relatively speaking you've posted a ton of stuff.  Has it all been as actionable as the wisdom you've laid on me?   If someone throws up a tip and SHOWS that it fixed their issue I'm going with it.  On the other hand all you've said is "you loaded the wrong kernel".  I'm looking into the ACTIONS to take to fix it right now.  So please unless you have something worth reading please go "help" someone else and quit wasting my time.

---

### Post by linuxinstalledfromhdd on 2011-05-23
Have you tried a nice hill and brick with duck tape? My old laptop that I didn't need anymore is now the fastest laptop I've ever seen. 

Seriously, though.  It's always prudent to have a backup disc of Ubuntu handy when you are making changes to your system. I've
seen some users here lately that are interested in getting over-clocked systems running in Ubuntu and having issues, so it's the same
thing but with the OS. Anything beyond the recommended settings, you always have to cover your end of it by having a backup disc ready to go.

---

### Post by backu on 2011-05-23
> **silentD said:**
> Wow!!!!!  Do you by any chance do this professionally?  I hope not.  You've been on here about 5 seconds longer than me but relatively speaking you've posted a ton of stuff.  Has it all been as actionable as the wisdom you've laid on me?   If someone throws up a tip and SHOWS that it fixed their issue I'm going with it.  On the other hand all you've said is "you loaded the wrong kernel".  I'm looking into the ACTIONS to take to fix it right now.  So please unless you have something worth reading please go "help" someone else and quit wasting my time.

Wow, can you be any more RUDE to people that are trying to help you? The point and LESSON TO LEARN here was 'DON'T ASSUME EVERYTHING WORKS AS POSTED'. Your system is likely different than the OP's, and we have no way of knowing -EXACTLY- what you did to your system. You want help, lose your attitude and start doing as people tell you to do.

---

### Post by silentD on 2011-05-23
THAT'S THE PROBLEM THERE IS NO "DO".  Just a bunch of "you made a mistake".   And second of all you are unbelievable!!  This guy is the one that start with the crappy attitude.  Do you guys actually offer any suggestions or just get on here and talk trash?  I don't follow complainers, whiners or know-it-alls.  I follow "do"ers.  People that take action.  So far Meiketsu and I are the only ones in here DOING anything.

---

### Post by linuxinstalledfromhdd on 2011-05-23
Relax. It's free advice. Nobody is forcing you to take any of it. This is all voluntary information AFIAK. If you really want to get "business" done, hire someone that you "pay" to help you and then you can complain.

---

### Post by silentD on 2011-05-23
Nice!!  Haven't got to that yet.  I'm sure I'll be booting from an alternative source and fixing my kernel as soon as learn how to do that.  Too busy keeping up this thread and watching the Thunder game.  BTW OKC up 99-84 with 5:04 left.  GO THUNDER!!!

---

### Post by linuxinstalledfromhdd on 2011-05-23
If you get really stuck. And you have no other computer available to use. Just go to your local community college. Pay some kid 10 bucks to make you installation disc of Ubuntu. I'm sure they will do it. People are pretty hard up for money these days and will work for peanuts.

---

### Post by silentD on 2011-05-23
Can any of you read?  There has been NO advice offered.  Just confirmation that a mistake has been made.  I take that back; one guy suggested a big hill and duct tape.  I like that.  At least he is funny.

---

### Post by linuxinstalledfromhdd on 2011-05-23
Attitude is everything. Seriously though, just make a recovery disc and you can undo the changes you made. Let us know when you are ready to get serious.

---

### Post by silentD on 2011-05-23
I'm not hard up.  I've got about four other computers and all kinds of discs available and I think I still have an 11.04 image on my Windows box.  I agree with your suggestion though.  A college would be a great place to make a new Linux buddy.  I'm really interested in becoming more fluent in speaking linux so I can first of all fix this and not make this mistake in the future.

Thanks again for the suggestion but I like your first one the best.  I actually smiled when I read that.

---

### Post by linuxinstalledfromhdd on 2011-05-23
:D  Yes, a class in Unix would be a great idea too. It helps to speak a moderate level of geek to get stuff communicated sometimes.  And in the meantime we will leave the light on for you.

---

### Post by silentD on 2011-05-23
> **linuxinstalledfromhdd said:**
> Attitude is everything. Seriously though, just make a recovery disc and you can undo the changes you made. Let us know when you are ready to get serious.
Seriously!!!  Let you guys know when I'm serious!!!!  ATTITUDE!!!  I didn't start it with the attitude.  If you think for one second that I'm going to take the time to take something off of here and then try to offer the guy that solved his own problem a little more feedback and in the process take a bunch of BS from the likes of you people YOU ARE CRAZY!!!  I will fix this like I fix all my cell phones, laptops, PC's and all kinds of other electronics on my bench.  I'm going to understand the problem (wether my error or no) and fix it accordingly.  I'm going to master it.  That's serious.  So I'm done with this thread and all of it's useless sensitivities.  I'll be scouring other threads and Internet sources to learn how to do this.  Cheers.

---

### Post by linuxinstalledfromhdd on 2011-05-24
Now that's the spirit. :guitar:

---

### Post by cariboo on 2011-05-24
Seeing as silentD has left the thread I'll close it.

---

