---
title: "Better Ubuntu Distro for Netbooks?"
date: 2009-11-28
forum: General Help
---

### Post by DirtyGTO on 2009-11-28
I just finished installing Ubuntu Netbook Remix on my Netbook. Before I get too far into this, my only Linux experience is with Linux Mint. I have Mint 7: Gloria installed on my Desktop and love everything about it, IMO, it trumps the XP experience. I still have XP functioning on a separate HD just for programs / services that require Windoze. So needless to say, this is why one of my first actions with my new Netbook was to install a version of Linux over the XP it came with. I opted for the "Netbook Remix" even though certain models of my Netbook came out of the box with standard Ubuntu.

My reason for stating all of that is because I haven't used standard Ubuntu, so my comparisons are between this and Mint. First thing I noticed was that the interface is different, and I didn't like it one bit. I want my desktop to resemble a normal desktop, this interface gave me flashbacks of my Dad's early 90's Windows machine. 

The speed seems out of whack for an OS that is supposed to be optimized for Netbooks. Everything is piss slow, it takes a couple seconds just to guide through the start menu. I'm also having problems with my connection that I haven't experienced with any of the Linux or Windows applications I have used previously. I don't really know what the problem could be, all of the information mirrors the setup I have on my desktop, yet it's "just not working" on the Netbook. It says I have a connection, but when I try to go to a website it just sits there and loads, nothing happens until I exit the window. Not even an error window saying there is no connection. 

My biggest gripe though, is the speed. I really can't believe how slow it's reacting. I fiddled around with XP for a couple hours after getting the machine, and everything on that seemed to run fine, in fact it was quicker than what I had expected from a Netbook running XP. So I guess the questions I have now is, is there a reason why UNR seems to run so slow? I was around on the Mint forums and people were suggesting other distro's over Mint for a Netbook application, would Mint run poorly if installed? 

I'll probably switch back to XP. It's not a huge deal that I get Linux on my Netbook as I can already think of one crucial application I bought it for that requires Windows. I'm more or less curious as to why Mint wouldn't work well and why UNR just seems so handicapped. This of course brings up another issue as I'm not sure which version of XP was installed, or for that matter, where I can get it back.

---

### Post by rudy.b on 2009-11-28
Which model of netbook are you using?

---

### Post by fluffman86 on 2009-11-28
and what program do you need XP for?

Anyway, that's not the main point.  Did you do a full UNR install, or a WUBI install?  Are you running UNR Karmic?  

I personally like the UNR interface, but if you want to see what the standard gnome interface looks like, you can go to System > Prefernces and select Switch Desktop Mode.  Some of the Windows are too big for the screen in the standard gnome mode, though.

If standard gnome is more for you, then you can install standard Ubuntu, or you can install Kubuntu, or I think Kubuntu is also working on a netbook remix, if KDE is more your thing.

---

### Post by DirtyGTO on 2009-11-28
It's an Asus 1101HAB. 

I wanted to use the Netbook to watch NFL Game Rewind on and the streamer only supports Windows. That's pretty much the only purpose XP has served on my computer in the last few months. 

I'll take a look at the desktop mode. I'm still not sure whats wrong with the internet connection. I set everything up, it says it's connected with a strong signal, but when I load up the browser is does nothing. The home page loads but it will just continually search if you enter an address, no "failed to connect" screens indicating there is no connection.

I downloaded Ubuntu, do you need an external disk drive to install it? I tried using the same method I used with UNR and a USB card but it didn't work.

---

### Post by tlois on 2009-11-28
Check out eeebunutu.  They have a forum.  I used it on my eee701 for a while, but now have 9.04 on there running fine.  But eeebuntu has its own kernel for the eees.  I liked it mainly because everything just worked, an I can't remember why I moved to regular Ubuntu- maybe it was Skype related...

Use Unetbootin to get distros on the netbook using your usb flash drive.

---

### Post by ed-koala on 2009-11-28
You can run windows in virtualbox and watch your nfl rewind too, the demo works, i tried it.

---

### Post by SteveNorman on 2009-11-28
crunchbang is a very light version of ubuntu, but you need to be able to use the command line and be able configure menus to take full advantage of it. 
[http://news.softpedia.com/news/First-look-CrunchBang-A-faster-Ubuntu-77535.shtml](http://news.softpedia.com/news/First-look-CrunchBang-A-faster-Ubuntu-77535.shtml)

also xubuntu

[http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by DigitaLink on 2009-11-29
I don't see any "Switch Desktop Mode" on my UNR 9.10 install.  Is it hidden somewhere?  I'd like to give classic Gnome a try on the netbook (Aspire One AOD150, 8.9", 160GB, 1GB RAM) to see which way I prefer.

---

### Post by DirtyGTO on 2009-11-29
Downloading Eeebuntu now. Anyone know if I can use "USB startup disc creator" to put this on a USB thumb drive so I can install it that way? I installed UNetbootin through the terminal but every time I try to open it I get an error "Could not grab your mouse" and something like "malicious content may be eavesdropping on your session." 

Edit: After the 5th time getting that error UNetbootin loaded up.

Edit2: I also didn't see the desktop mode option when I looked under System - Preferences.

---

### Post by rudy.b on 2009-11-29
If you're interested, here's a thread discussing work-arounds for the slowness issue with the UNR desktop on certain netbooks (including the Asus 1101hab):  [http://ubuntuforums.org/showthread.php?t=1308792](http://ubuntuforums.org/showthread.php?t=1308792)

---

### Post by DirtyGTO on 2009-11-29
I installed Eeebuntu, after viewing their forums it seems to be the best choice for an EeePC. I could be wrong, but I was sold on the idea that everything is focused specifically on the line of PC I'm using.  

Now I've ran into another problem, but there is a solution. Newer EeePC Netbooks have to switch kernels for compatibility with the wireless card. I took a glance at what is needed to be done to do this process, it seemed long and very confusing, but I only browsed over the tutorial. It's late/early though and my football team is playing the morning game so I will reply back tomorrow after I attempt to upgrade the kernel.

---

### Post by snowpine on 2009-11-29
The problem with using EEEbuntu at this moment is that version 4.0 is coming out real soon, and [it will not be based on Ubuntu any more]("http://forum.eeebuntu.org/viewtopic.php?f=25&t=4492"). So installing 3.0 at this point is a dead end (support will end Oct 2010).

---

