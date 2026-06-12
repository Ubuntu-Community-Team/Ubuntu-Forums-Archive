---
title: "Ubuntu 11.04 upgrade + Lotus 8.5 + Downgrading Libs."
date: 2011-05-02
forum: General Help
---

### Post by KajiMaster on 2011-05-02
Upgraded Ubuntu last week from 10.10. I do this with my work computer and we use Lotus notes here.  I had Lotus notes 8.5 working on 10.10 just fine before upgrading.  Once i did lotus notes will run, however, I couldn't read e-mails.  After a bit of researching i found a fix.  The fix was running:
libgdk-pixbuf2.0-0_2.22.0-0ubuntu1_i386.deb 
and
libgtk2.0-0_2.22.0-0ubuntu1_i386.deb

I had to run these in the terminal with sudo dpkg -i.  This downgraded my current version and put the old versions back on.  Lotus then works GREAT!!! Even better than before.  However, once I reboot Ubuntu it will start up like normal.  But at the splash screen no box comes up with the users to log in.  It makes the drum sound it usually makes before the log in accounts display but they never display.  The only way around this is to go into recovery mode and repair broken installs.  This forces upgrades to these packages and then I can log back in with no problems.  At that point however I have to re-downgrade them to get lotus to work.

Anyone have any advice on this topic?

---

### Post by DarKnyht on 2011-05-02
I just experienced the same problem, but I am running 8.5.2.  I am preparing to download the latest fix pack from IBM (FP2) to see if this will correct the issue.  

However, most likely I see this requiring a fix from IBM more than one from the Ubuntu community.  Most likely, IBM will suggest that users stick to the latest LTS version (10.04).

---

### Post by KajiMaster on 2011-05-04
Did the fix pack work for you?

---

### Post by DarKnyht on 2011-05-04
Unfortunately, I could not seem to get a copy of it downloaded from IBM that Ubuntu would allow to install.  Every download attempt turned out corrupted somehow.

---

### Post by KajiMaster on 2011-05-09
Still having this issue... Grated I can get 8.5 to work because I had it installed before updating to 11.04.  

@Dark, have you tried downgrading these:
libgdk-pixbuf2.0-0_2.22.0-0ubuntu1_i386.deb
and
libgtk2.0-0_2.22.0-0ubuntu1_i386.deb

to see if that lets you install?  

Also does anyone know more details of these packages?  Are they specific to Unity?  Could I get around needing them if i switched to Gnome 3? Would Gnome 3 not load the log in screen if I had the old version on?

Another note.  When I do sudo apt-get install -f after i have downgraded them it keeps suggesting to install the newer version.

---

### Post by Davor &#268;engija on 2011-05-12
> **DarKnyht said:**
> Unfortunately, I could not seem to get a copy of it downloaded from IBM that Ubuntu would allow to install.  Every download attempt turned out corrupted somehow.

Hi,

I have the same problem with LN after upgrading (kubuntu) from 10.10 to 11.04. My LN was working perfectly:

Release 8.5.2 
Revision 20100811.1131 (Release 8.5.2) 
Standard Configuration

I maneged to download the FP2 (btw its version number is broken and cannot be installed, needed to use deb-reversion to fix it) and install it, now my LN version is:

Release 8.5.2FP2 
Revision 20110323.0837-FP2 (Release 8.5.2FP2) 
Standard Configuration

Still the same problems, unfortunatelly. Unusable.

EDIT:
 
See here for the solution: [http://usablesoftware.wordpress.com/2011/04/05/lotus-notes-8-5-2-fp2-in-ubuntu-11-04-natty-narwhal-64bit-beta-1/](http://usablesoftware.wordpress.com/2011/04/05/lotus-notes-8-5-2-fp2-in-ubuntu-11-04-natty-narwhal-64bit-beta-1/)
Works on my 32-bit installation as well.

---

