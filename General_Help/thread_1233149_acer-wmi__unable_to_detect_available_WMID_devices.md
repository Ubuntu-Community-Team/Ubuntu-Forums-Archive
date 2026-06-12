---
title: "acer-wmi:  unable to detect available WMID devices"
date: 2009-08-06
forum: General Help
---

### Post by ssaint04 on 2009-08-06
I'm running UNR 9.04 on an Acer Aspire One D150-1920. On my most recent bootup, my usplash screen failed to load, instead being replaced with terminal script. it indicated that WMID devices were not detected.

I pulled my dmesg.log and confirmed it:

> 
[   17.880771] acer-wmi: Acer Laptop ACPI-WMI Extras
[   17.956594] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   18.009321] acer-wmi: Unable to detect available WMID devices
Any ideas on a fix/workaround, so I get my usplash back?

---

### Post by TechVamp on 2010-01-27
Yeah, I'm having nearly the same problem.
Only I'm running the desktop edition of 9.10 on my acer
aspire one.
Any suggestions?

---

### Post by extc on 2010-02-02
The fix was this: you need to run this at the command line:
 
fsck
 
It will run a disk check just like in Windows, then repair the error.
 
It worked for us - problem sorted immediately!
 
Take care!

---

### Post by wilee-nilee on 2010-04-11
> **extc said:**
> The fix was this: you need to run this at the command line:
 
fsck
 
It will run a disk check just like in Windows, then repair the error.
 
It worked for us - problem sorted immediately!
 
Take care!

This is a dangerous thing to do if not done correctly, read this wiki.
[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)

and this paragraph.

A system administrator can also run fsck  manually if there is believed to be a problem with the file system. Because running fsck to repair a file system which is mounted for read/write operations can potentially cause severe data corruption/loss, the file system is normally checked while unmounted, mounted read-only, or with the system in a special maintenance mode that limits the risk of such damage.

---

### Post by Jordanwb on 2010-04-13
I'm having this problem too on an Aspire 5515. I doubt a fsck will fix it.

---

### Post by jlking3 on 2010-04-30
a forced fsck does not fix this. It appears that the battery is being detected improperly, as I see the model number change. I wonder if there's a way to force the model number and Energy (Design) attributes to be at a certain value regardless of what's detected by the power manager or the battery manager? That should solve all issues and be a decent workaround until a permanent fix is available.

---

### Post by palihapiz on 2010-05-02
im having this problem also...can some help to fix it?im make fresh installation and using aspire one AO532h..

---

### Post by reluttr on 2010-05-08
I am having this issue as well. A fix would be appreciated.

---

### Post by dino99 on 2010-05-08
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

will force a fsck on next boot:

sudo shutdown -F -r now

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560464?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560464?comments=all)

---

### Post by reluttr on 2010-05-08
> **dino99 said:**
> sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

will force a fsck on next boot:

sudo shutdown -F -r now

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560464?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560464?comments=all)

That didnt do anything for me... I dont even think the fsck command worked.

---

### Post by lou002 on 2010-05-23
I'm getting this problem with all of the editions of Ubuntu on my Acer Aspire one 532H. Getting annoying. I've tried Mint and Jolicloud; I don't get this problem. Only with Ubuntu.

---

### Post by yolucid on 2010-05-27
Same here, aspire one 532h. At first Lucid works fine, since I installed about 5 days ago. Then I got the latest upgrade about 1 hour ago, and got this error of WMID device ever since.

---

### Post by joker31174 on 2010-05-27
I get the same error.
Is it possible to skip the step entirely?

---

### Post by exchaoordo on 2010-06-02
Same Problem, most annoying on an Acer Aspire 532h.

---

### Post by c64wood on 2010-06-26
I installed EasyPeasy on my 532h.  I got the WMID message only during the first reboot after the initial updates.  It did not hang the OS.  It has not done it since. I do however get a message during a shutdown, but it flashes so quick I can't read it.

---

### Post by ssaint04 on 2010-06-27
> **yolucid said:**
> Same here, aspire one 532h. At first Lucid works fine, since I installed about 5 days ago. Then I got the latest upgrade about 1 hour ago, and got this error of WMID device ever since.

Get the error on a D250 running Lucid (non-netbook) too.

---

### Post by leorolla on 2010-06-30
Same problem here.

Acer Aspire One D150.

---

### Post by ccaaee on 2010-07-01
Same thing here on an Acer apsire one D150-1055

---

### Post by leorolla on 2010-07-02
It's the same laptop, I think. The 1055 is just the color ;)

---

### Post by mike555 on 2010-07-02
You might try [ gksu gedit  ] then open Etc/Modprobe-d/blacklist.conf   and add the line  " blacklist acer-wmi " without the quotes...........

---

### Post by leorolla on 2010-07-02
Or just copy-paste this to the terminal
```
echo blacklist acer-wmi | sudo tee -a /etc/modprobe.d/blacklist-acer-wmi.conf
```
and press enter.

---

### Post by Mikaast on 2011-02-04
I have the same problem on an eMachines mini-laptop.
I've tried the blacklisting trick, but is there another solution?

---

### Post by lou002 on 2011-02-04
I get this issue on my Acer Aspire 7741z-5731 

I only get it in Ubuntu had no problem with Mint except for random freezes, switched to Ubuntu, I get the WMID issue but otherwise works fine.

---

### Post by leeconne on 2011-09-09
reviving an old thread teorolla's fix above worked for me. i have also  had to blocklist intel_ips to fix the failed to i915 symbols graphic turbo disabled. there are couple of fixes i have to do to get my touchpad scroll etc to work. ubuntu does not play nice with gateway and acer laptops it seems. touchpad problem for me is only happens in ubuntu but the graphics problem and wmid problem has happened in various distros of various kernels up to the latest kernel 3

---

### Post by aciddesir on 2011-09-22
Confirmed the same error on Acer Aspire 5560 running natty.  However leorolla's fix from above worked.

---

### Post by rez-i-dent on 2011-10-20
Using an Acer Aspire One and both UNR and EasyPeasy have both lost the menu bar after upgrade, 400mb on clean installs, today and yesterday.
The only thing I tried installing in both installs was MeTV.
The top left logo is there but it cannot be clicked. Hovering over it gives the message "Click here to hide all windows..." but there is nothing else.
I can only get programs open by plugging in an external drive and creating a document, then creating a hyperlink to open the Internet. Other than that it is inoperable. No Terminal, nothing, so I can't even uninstall.
I'm guessing another clean install is needed... third time lucky...
Funny how it's been the same issue on 2 operating systems though and both times after the upgrade (that took several hours both times... grrrrr)

---

### Post by rez-i-dent on 2011-10-20
> **rez-i-dent said:**
> menu bar The Title Bar is still there, but the drop down menu for Remix and EasyPeasy just doesn't open

---

