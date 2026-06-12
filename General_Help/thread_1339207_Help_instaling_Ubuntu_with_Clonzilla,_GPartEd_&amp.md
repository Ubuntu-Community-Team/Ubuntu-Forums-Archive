---
title: "Help instaling Ubuntu with Clonzilla, GPartEd &amp; SysRescue on top"
date: 2009-11-27
forum: General Help
---

### Post by c77 on 2009-11-27
I am new to Linux, but a former BSD user. I want to install a fresh Ubuntu boot partition on a mostly-XP machine. The Ubuntu side boot is for fun :D and for cloning the XP partition pretty often since its a virus magnet and breaks from its own bugs. I want Clonezilla, GPartEd, "SysRescue CD" tools, and Smartctrl GUI to SmartMon Tools easily visible on the Ubuntu boot. I won't be on-site, and will be directing a secretary on-site via telephone and maybe remote-access, to clone the XP partition to another data partition or Fileshare on another XP box now and then. Or telling her how to do other disaster recovery. 

It is likely easier to use Live CDs for this. But If I leave 2 or 3 bootable CDs there, the staff will loose them within a month. And they are very bad at booting CDs from the BIOS. So I want to put an alternate boot for all this on the hard disk. (Only one HDD).

I'd like to "help" the secretary with VNC or something. 

Would anyone be so kind as to suggest my steps? Thank you in advance! 

My questionmarks are things like: Are all these applications (Clonezilla,GPartEd, Smartmon Tools, etc) part of Ubuntu out of the box? How would I make VNC (x11vnc since helping/teaching) and SSH daemons start automatically? With a strong password, is it stupid to use x11vnc naked (no ssh encryption) since I don't understand how to close off the ability to connect to 5900 (or altered) without ssh even if I get ssh to work as an alternative connection path to VNC? I generally like to put XP's user-data in a separate NTFS partition to reduce Windows blowing out the data on power failure or BSOD. If I want emergency and for-fun use of Ubuntu to work with this user-dat, should I make it FAT32? (Web reading opinions warn writing NTFS from Ubuntu is flakey, maybe in file permission attributes, not sure that matters. And some say the XP driver for ext3 is flakey. But I am not happy with the no journalling of FAT32. NTFS and ext3 are both journalling, and hold up to power failures well. )

I've never installed Linux, and my only Linux use has been Putty-SSH a lot to a CentOS webserver. I was good at BSD command prompt and C programming in previous centuries. This is my first post to any Linux forum...  I did study and search many hours before posting so no RTFM please.  Thanks in advance.  chris :popcorn:

---

### Post by krunge on 2009-11-27
> **c77 said:**
> How would I make VNC (x11vnc since helping/teaching) and SSH daemons start automatically?

I believe when you add the ssh server package (apt-get install openssh-server) then it will start automatically at boot.

Regarding x11vnc, it is a little trickier because it requires an X session already running for it to attach to.  Some info and ideas are here:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-service](http://www.karlrunge.com/x11vnc/faq.html#faq-service)
[http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)
[http://www.karlrunge.com/x11vnc/faq.html#faq-inetd](http://www.karlrunge.com/x11vnc/faq.html#faq-inetd)[/INDENT]
Often it is as easy as adding a line to /etc/gdm/Init/Default. If you decide to go with any of these I can try to help you if you need it.

Perhaps simpler, even if a couple more steps that one could script, is to not have x11vnc start automatically, but rather you start it through your ssh shell each time you need it (I assume you have root permission once logged in.)  Again, if you need help on that let me know.
> 
With a strong password, is it stupid to use x11vnc naked (no ssh encryption) since I don't understand how to close off the ability to connect to 5900 (or altered) without ssh even if I get ssh to work as an alternative connection path to VNC? 

Well, if you set up SSH, the safest way would be through a tunnel:
[INDENT][http://www.karlrunge.com/x11vnc/#tunnelling](http://www.karlrunge.com/x11vnc/#tunnelling)[/INDENT]

With a strong VNC password the only problem w/o encryption is that the entire session is sent in plaintext.  So if any subsequent su/sudo passwords that were used they could be sniffed. Also, without encryption it is at least in principle possible for an attacker to hi-jack the session.  I'm not sure how real a risk that is these days.

I'm not sure I understand the part about closing off port 5900. Please elaborate.  All I can say at this point is if the machine has ssh working, one should use that for all network connections and not enable any more services (tip: x11vnc has -localhost option to only listen on the loopback interface.)

---

