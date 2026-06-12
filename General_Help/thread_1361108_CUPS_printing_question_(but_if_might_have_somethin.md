---
title: "CUPS printing question (but if might have something to do with hosts)"
date: 2009-12-21
forum: General Help
---

### Post by allerretour on 2009-12-21
Hello,

I've got a question that's specifically about CUPS printing, but might eventually be a networking-hosts question (read on). Here's the situation:

Have a Mac with USB attached HP printer.  Want to print to it through two laptops that connect through a wireless router.  One laptop has Ubuntu Jaunty; the other Xubuntu (not sure which version, but very recent).  I had some initial problems with both of them not being able to print, but I made some additions to the cupsd.conf file on the Mac - basically just adding the "Allow From 192.168.1.*" line to the location - and the Xubuntu laptop now prints fine.  Unfortunately, the Ubuntu Jaunty machine still has some authentication problem.  I'm using the same method to add the printer on both machines, although the interface is slightly different from Ubuntu to Xubuntu. For both of them, I select new network printer with ipp protocol.  I enter the host ip address (192.168.1.152 in this case), and look for the print queue.  They both find the printer with the correct queue name and the correct URI.  But when I do the last verification step, the Xubuntu machine connects while the other gives me permission denied.

Now the only difference between the two machines at this point (and I think it could be the root of the problem) is this: when Xubuntu searches for the printer queue, it changes the ip address 192.168.1.152 into the name of the mac computer, my-computer.  The Ubuntu machine does the same thing, but it registers the name as my-computer.local.  It appends this ".local" at the end.  I can't figure out why or where it does this, but I figure that this might be the problem.  I thought maybe there might be a line in /etc/hosts for this, but I couldn't find anything.  Anyone out there know why Ubuntu adds this ".local" to the machine name and how I can stop it?   Thanks.

---

### Post by hugmenot on 2009-12-21
Actually the .local business is related to something Apple invented: [Bonjour network discovery]("http://en.wikipedia.org/wiki/Bonjour_(software)"). Ubuntu and Cups support it. In theory it should be enough to toggle the "discover network printers" option in one of the menus. 

Normally the magic should happen behind the scenes.

---

### Post by allerretour on 2009-12-21
Thanks for the response.

Where do I toggle this "discover network printers"?  On the mac side or the linux side?  Remember that the printer is already attached to the mac, so it doesn't have to discover anything.  And on the linux side, my Xubuntu machine can already see it as is.  The Ubuntu machine can "see" it, but gets denied access.  So the mac appears to be set up correctly (since at least one machine can print on it).  It's the Ubuntu machine that has problems, I think - as I said - because of the .local thing.  Maybe I'm not reading you correctly though.

---

### Post by chenxiaolong on 2009-12-21
You can go to [https://localhost:631](https://localhost:631) in your web browser and add it manually. You will have to choose the IPP (http) protocol and the address will be [http://your.mac.ip.address:631/printers/the_printer_name](http://your.mac.ip.address:631/printers/the_printer_name) .

---

### Post by allerretour on 2009-12-23
Hi,

Just thought I'd post what I found in the event that it might help someone else.

What I found is that the printer works from Ubuntu, even though it's not able to authenticate correctly during setup and it gives an error message about needing the MacOS PrintJobMgr.  Also, it doesn't retain the name of the printer when you select the queue (Xubuntu did this all correctly for some reason, but Ubuntu doesn't).  Anyway, if you continue past the error messages and manually enter the printer name, it does create the printer and you can print to it.  So just ignore the Ubuntu error messages.  Once again, this is Ubuntu jaunty.

---

