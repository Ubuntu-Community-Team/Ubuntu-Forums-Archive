---
title: "Dual Boot without logging off windows"
date: 2009-12-16
forum: General Help
---

### Post by OverEasy on 2009-12-16
I know this seems like it's unrelated to linux, BUT seeing as I'm trying to log into linux, it fits in my eyes =p 
So is there any way to shut down my machine without logging off windows? I have 2 hdd's, one with vista and the other with the much better ubuntu, but I hate having to lose my windows workspace whenever I want to switch! Same goes for ubuntu i guess! I find this strange because I have an ASUS EeePC laptop which I also dual boot with xp and ubuntu (albeit that one is on only 1 hdd) I use the hibernate function on that one a lot, and every time I power back up, I get shown the boot menu in the bios! which is super convenient, because I can switch between both operating systems without ever having to log out!! So how would I do a similar operation on my desktop with the 2 hdd's? Hibernate obviously doesn't work the same because it only loads back into the OS that it was last using, and I have to log off to switch. So any way even to get to the boot menu, or bios, without logging out of either windows or ubuntu, would be super helpful. Thanks guys!

---

### Post by PseudoLemon on 2009-12-16
Hibernate would work if you have GURB loaded. I haven't tried it, but I recommend not having anything open, hibernate, then boot to Kubuntu, shut that off and then go to Windows. If it works, try it with notepad or something little open. Methinks you're thinking of sleep mode.

---

### Post by OverEasy on 2009-12-16
well, yes and no.  I actually use sleep mode to shut it off, but I have it set so if it sits for more than an hour it hibernates.  If i use sleep it just boots right to where i was on either computer.  Is there no program to switch between hard drives or anything? As I said they're separate so that would be ideal, but any way to get between one operating system to another while having the sessions saved.

---

### Post by Chesamo on 2009-12-16
You can force Windows Vista to Hibernate by selecting it from the Shut Down menu (the arrow next to the Start Menu's power button).
[http://bloggingabout.net/UserFiles/Erwyn%20van%20der%20Meer/WindowsLiveWriter/WindowsVistaHibernateMystery_2B42/image%7B0%7D%5B8%5D.png](http://bloggingabout.net/UserFiles/Erwyn%20van%20der%20Meer/WindowsLiveWriter/WindowsVistaHibernateMystery_2B42/image%7B0%7D%5B8%5D.png)

---

### Post by oldfred on 2009-12-16
I think you are talking about VirtualBox which lets you install windows to a virtual system running inside Ubuntu. It works best on a faster system with lots of memory.
[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

You do not want to hibernate a windows partition and boot into Ubuntu. If you do any activity from Ubuntu on the windows partition you will corrupt the windows partition  as the hibernation now will not match the changed system.

---

### Post by Chesamo on 2009-12-16
> **oldfred said:**
> You do not want to hibernate a windows partition and boot into Ubuntu. If you do any activity from Ubuntu on the windows partition you will corrupt the windows partition  as the hibernation now will not match the changed system.
This is not true. Hibernation in windows is achieved by dropping the contents of memory onto a file stored on the Windows hard partition (C:\hiberfil.sys); thus, anything happening on Ubuntu could not and would not affect the Hibernated system. Primarily because Windows can't read ext filesystems without external help.

That is, unless files in use on the sleeping system are modified while in Ubuntu. That's different.

---

### Post by smilingfrog on 2009-12-17
> **oldfred said:**
> I think you are talking about VirtualBox which lets you install windows to a virtual system running inside Ubuntu. It works best on a faster system with lots of memory.
[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)


This is what finally made me able to never boot my windows partition. You can install windows into a virtual machine running inside Linux, and then if you install the guest additions, you can move seamlessly between a windows environment and a linux environment.

I have an older machine with 1.5GB of RAM and it runs windows XP without a problem. It's also a great way to test out new distros before burning them to CD or to your hard drive.

---

### Post by OverEasy on 2009-12-17
okay, well then I'll change my question a little bit.  First, may sound advanced, but could I run my entire windows hard drive through the emulator? As in basically "Alt-tabbing" between hard drives essentially.  Although if this makes a difference my windows hdd is the primary and linux is on the slave.  The thing i love about ubuntu is that I can see every single bit of my windows hard drive from within linux, even all the programs and games it cant run.  So will a windows emulator be able to see and use all these files as well? So I wont have to reinstall the my windows programs and waste a bunch of new hard drive space? I really hope this is possible, and that you guys know what im talking about by running my entire windows drive through the emulator =p

---

### Post by oldfred on 2009-12-17
I found this and plan to try it with my XP install but have not yet.

HowTo: Install VirtualBox 2.1.4 PUEL version
[http://ubuntuforums.org/showthread.php?t=1074160](http://ubuntuforums.org/showthread.php?t=1074160)

Howto: Windows XP in both VM and native
[http://forums.virtualbox.org/viewtopic.php?t=9697](http://forums.virtualbox.org/viewtopic.php?t=9697)

---

