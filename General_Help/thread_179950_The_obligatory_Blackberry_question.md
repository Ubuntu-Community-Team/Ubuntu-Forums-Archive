---
title: "The obligatory Blackberry question"
date: 2006-05-21
forum: General Help
---

### Post by NinjitsuStylee on 2006-05-21
Hi everyone.  So I was browsing the Ubuntu forums and I guess I wasn't satisfied with the threads relating to Blackberry devices...so I created my own.

So it's May of 2006.  I'm using a Blackberry 7100t smartphone...and I would love to sync it and charge it with my new Ubuntu 5.10 install.  I'm migrating away from Windows (for my own reasons...trolls need not respond/applaud) and every time I get something to work right in Linux, it's just one more step closer from total migration.  Heck, I even managed to get World of Warcraft working nicely :) 

So let's discuss the whole Blackberry syncing issue shall we?  So far in my investigations, here's what I've discovered:

[LIST]
[*][Funambol]("http://www.funambol.com") (Sync4j):  Some large mobile open-source package that supposedly syncs anything with anything...what they don't tell you is that it's the complete opposite of intuitive and that it's relatively impossible for 'nix noobs like myself to figure out.
[*] [Barry]("http://sourceforge.net/projects/barry"):  A project started by a company called Netdirect.  They haven't updated on Sourceforge since 2005. 
[*] [XmBlackberry]("http://sourceforge.net/projects/xmblackberry"):  A project with very little (and very weak) documentation that I guess is based on Barry and some other obscure packages that are, once again, difficult and annoying to install for 'nixnoobs.  They do have a fun screenshot on their Sourceforge site though! 
[*] VMPlayer:  I read somewhere on the Ubuntu forums that some people are using VMWare and running a Windows boot in a virtual pc to update their blackberry devices.  I think this is a bit silly and it would be total overkill just to sync my blackberry.  Besides, I want to sync it to Evolution anyways.
[*] [Wine]("http://www.winehq.com"):  Has anyone managed to get the Blackberry software working in Wine?  I'm too nervous to try it...:neutral: 
[/LIST]

Another annoying thing which all of you Blackberry-on-linux-wanters must have discovered is that the USB charging is insufficient when booted in Ubuntu (or Linux in general, I guess?).   I'm not even sure where to begin to solve this issue. :confused: 

We know that RIM has crap (aka no) support for Linux.  But come on guys.  It's been a while and there are loads of smart people out there that are perfectly capable of designing some wicked software, believe me, I've seen it.  I find it kind of hard to understand why nobody has come up with a clean, concise, and functioning package for Blackberry devices.  

So anyways, if anyone else has any insight on this issue, let's discuss.  The only luck I think I've had is that XmBlackberry package, but figuring out how to properly (and manually) install the package and its dependencies (and their dependencies and so on and so forth) is kind of driving me crazy.

Yay for my first post! :mrgreen:

---

### Post by NinjitsuStylee on 2006-05-24
bump......cmon folks, someone has to be interested!

---

### Post by NinjitsuStylee on 2006-06-07
[http://www.ubuntuforums.org/showthread.php?t=190938](http://www.ubuntuforums.org/showthread.php?t=190938)

^ figured it out :)

---

### Post by kast on 2006-08-11
hey new to ubuntu also need to charge the BB could you post how you figured it out? please!

---

### Post by cdfrey on 2006-12-29
Full syncing is still a work in progress being tackled by the Barry project, as linked to above.  We aren't dead! :-)

As for charging, there is a standalone utility called bcharge that was just released, which will do native charging on Linux.  It scans the USB bus using libusb, and talks to each BlackBerry it finds, setting them to 500mA if not already.

The SourceForge news announcement is here: [http://sourceforge.net/forum/forum.php?forum_id=648040](http://sourceforge.net/forum/forum.php?forum_id=648040)

Happy New Year, and happy charging!

---

### Post by NinjitsuStylee on 2007-01-02
Hey, thanks for that info, and I wish you guys good luck in the Barry project!

In the meantime, check out my recently updated tutorial:

[http://ubuntuforums.org/showthread.php?t=190938](http://ubuntuforums.org/showthread.php?t=190938)


Proud to have it ranked #1 @ google (search terms "sync blackberry with linux") :mrgreen:

---

### Post by sateeshpnv on 2007-10-04
I could charge my blackberry from my Ubuntu after I followed the instructions at [http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg17557.html](http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg17557.html)

bcharge alone did not work for me on Ubuntu 7.04. I think it is that CONFIG_USB_SUSPEND that was causing the charging to stop after a few seconds.

As per the instructions in the link mentioned above, I ran '**sleep 3600 < /proc/bus/usb/001/011**' and my blackberry is charging now; quite fast too.

I did not have to recompile kernel to modify CONFIG_USB_SUSPEND.

Now all I need is to automate charging whenever I plug-in my blackberry 8700c via USB.

---

