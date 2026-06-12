---
title: "Help - Newbie - Scanner"
date: 2010-04-19
forum: General Help
---

### Post by Quarkrad on 2010-04-19
U 9.10.  Trying to get my HP Scanjet 5200 working.  I have come across this 

[B]NAME
     uscanner - USB Scanners

SYNOPSIS

     To compile this driver into the kernel, place the following line in your
     kernel configuration file:

           device uscanner

     Alternatively, to load the driver as a module at boot time, place the
     following line in loader.conf(5):

           uscanner_load="YES"[/B]

from [http://manpages.ubuntu.com/manpages/karmic/en/man4/uscanner.4freebsd.html](http://manpages.ubuntu.com/manpages/karmic/en/man4/uscanner.4freebsd.html)

I have downloaded the driver(?) and extracted it - it looks like a text file.  I'm not sure what to do now.  The above talks about  '...To compile this driver into the kernel, place the following line in your
kernel configuration file: device uscanner...'  which unfortunately is a bit beyond me.  What do I do now?

---

### Post by dineshs on 2010-04-19
Xsane image scanner is not working?

---

### Post by ad_267 on 2010-04-19
What did you download? Your scanner should already be supported (Unless the ScanJet 5200 is different to the 5200C): [http://www.sane-project.org/sane-backends.html#S-HP](http://www.sane-project.org/sane-backends.html#S-HP)

Just install xsane to scan stuff.

---

### Post by Quarkrad on 2010-04-19
Nothing.  I have installed xsane (0.996) - it runs, looking for scanners and then tells me that No Devices Available.  I have googled and keep seeing references to 'backend' files/configurations

---

### Post by ad_267 on 2010-04-19
Have you seen this page? There are some trouble shooting instructions there: [https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

Your model isn't specifically listed but installing the libsane-extras package might still help.

---

### Post by Quarkrad on 2010-04-19
**APOLOGIES  APOLOGIES**

I feel a fool - I must be operating(?) in another time warp.  I do not have a scanjet 5200 - I have a Cannon canoscan 5200f.  I use to have the HP scanjet many years ago but not anymore. Perhaps I should not be posting if I do not even know what equip I have!

---

### Post by Quarkrad on 2010-04-19
Looks to me it is not possible to get a Canoscan 5200 working under linux/ubuntu.

---

### Post by ad_267 on 2010-04-19
Hmm yeah looks like you're out of luck: [http://www.sane-project.org/unsupported/canon-5200f.html](http://www.sane-project.org/unsupported/canon-5200f.html)

Canon seems to be the worst when it comes to Linux support. I used to have a Canon printer which was a real pain to get working, I had to use a driver that was meant for another model. Now I have an HP that works a lot better.

---

