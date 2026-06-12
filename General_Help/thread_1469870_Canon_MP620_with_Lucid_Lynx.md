---
title: "Canon MP620 with Lucid Lynx"
date: 2010-05-02
forum: General Help
---

### Post by Pergun on 2010-05-02
I'm a newcomer to Ubuntu. Have struggled with 9.04 and managed to get my Canon MP620 to work in that version. Now I have upgraded to 10.04 and have problems to get my printer to work again. Can anyone help??

---

### Post by akashiii on 2010-05-02
Click on the link below for step by step commands to install the drivers -

[http://www.nervous.it/lang/en-us/2009/04/canon-pixma-mp620-wireless-on-ubuntu/](http://www.nervous.it/lang/en-us/2009/04/canon-pixma-mp620-wireless-on-ubuntu/)

I'm trying to figure out if Lucid Lynx 10.04 comes with libcups2. Normally the procedure should be the same as with Jaunty. 

Hope the installation succeeds. Cheers!

---

### Post by Pergun on 2010-05-02
It failed already when I tried to install the cnijfilter-common_2.80-i386.deb. The error message was  "libcupsys2 (>=1,2,1)"

---

### Post by ubuking on 2010-05-03
Check this [blog]("http://www.leonatkinson.com/canon-mp620-on-ubuntu-9-10-karmic-koala/"), will likely solve your issues.

If you are on Lucid AMD-64 then watch [this]("http://ubuntuforums.org/showpost.php?p=9208604&postcount=4").

---

### Post by Pergun on 2010-05-03
Thanks a lot guys, this saved my day. This was my first posting in the Forum and it functioned just great thanks to you!

---

### Post by jbblack on 2010-05-09
Disclaimer:  I AM A LINUX NOOB!

Ok, not all of this worked for me.  I went to Luca Gibelli's webpage [here]("http://www.nervous.it/lang/en-us/2009/04/canon-pixma-mp620-wireless-on-ubuntu/").  As everyone has mentioned before this worked up until you had to get libcupsys2.  Fixes are in this forum for how to get that.  My problem came when trying to connect via CUPS.  The version of CUPS I am using is 1.4.3.  This, apparently, is a newer version than what is used in Luca's installation.

What I had to do was select Canon Network Printer.  At that point, you get a device URI that starts with "bjnp."  To bjnp, I added the IP address of my printer.  This worked.  So, mine looks like this:

Device URI:  bjnp://xxx.xxx.x.x/

I just tried this as a last ditch effort before I rebooted into Vista and it worked.  As with anything else, YMMV.

Good luck.

---

### Post by BigBananaMan on 2010-12-17
I'm copy/pasting this to a couple places so please excuse any redundancies.

After getting fed up wasting time re-learning and screwing up setting up multiple computers, I was going to write an install script so I never have to spend an entire day re-learning the whole process again. Kevin Carter beat me to it and did a better job than I would have anyway.  These are good for new users or just somebody that has to install to multiple systems or occasional reinstall.  You can find the scripts [HERE]("http://bkintegration.com/2010/08/install-canon-mp620-on-ubuntu-linux-10-04/")

To make life even easier the proper ppd file is [HERE]("http://sourceforge.net/projects/mp610linux/files/")

If you just bought the printer and are wondering how to get it to connect wirelessly (which Canon says is impossible and then suggested I buy Windows just to set up the kickbacks err printer.  hmm...) You can connect it first to your router with a patch cable and check the IP through the printer interface.  Then punch [http://*printeriphere*](http://*printeriphere*) into your browser and set it up to use your wifi.

---

### Post by Mega_Mike on 2011-03-18
To remove all the complicated commands and get a nice clean install in both x86 or amd64

[http://ubuntuforums.org/showthread.php?p=10575009#post10575009](http://ubuntuforums.org/showthread.php?p=10575009#post10575009)

---

