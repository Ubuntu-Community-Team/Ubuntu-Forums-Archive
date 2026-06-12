---
title: "Random Crash"
date: 2010-05-30
forum: General Help
---

### Post by jjjjjjj9175@ on 2010-05-30
Ubuntu randomly crashes while I am using it.  The screen goes black for a few seconds and then flashes white lines over and over again.  Does anybody know how to fix this.  It has done this about ten times.

---

### Post by Ichido on 2010-05-30
Sounds to me like a Video Driver and/or Resolution problem.
Check these Forums for your Video Driver Issues.

---

### Post by dino99 on 2010-05-30
> **jjjjjjj9175@ said:**
> Ubuntu randomly crashes while I am using it.  The screen goes black for a few seconds and then flashes white lines over and over again.  Does anybody know how to fix this.  It has done this about ten times.

system/admin/hardware driver: is yours activated ?

look at .xsession-errors into /home (unhide it with menu)
and into system/admin/log viewer  for errors

---

### Post by Rasa1111 on 2010-05-30
Same happens here. 

 It actually stopped doing it for about 5 days and ran perfectly.
I thought the crash was over..
but it happened again last night out of the blue, twice. 

 It is happening to quite a few people...
havent seen a real fix for it yet.

> Dino~ system/admin/hardware driver: is yours activated ?

Activated? 

Whenever i open up hardware drivers in System/Admin>
All I ever get is~
> "No proprietary drivers are in use on this system"

 Is there somethign else that needs to be done here?

---

### Post by jjjjjjj9175@ on 2010-05-30
> **dino99 said:**
> system/admin/hardware driver: is yours activated ?
 
look at .xsession-errors into /home (unhide it with menu)
and into system/admin/log viewer for errors
 
 
On Hardware drivers it is not showing any drivers.

---

### Post by jjjjjjj9175@ on 2010-05-30
Ubuntu has crashed about twenty times today on my computer. :confused:

---

### Post by Rasa1111 on 2010-05-30
> **jjjjjjj9175@ said:**
> Ubuntu has crashed about twenty times today on my computer. :confused:

I know the feeling, mate. 

 I dont think mine crashed quite as many as 20 times in a day~
But there were some days where it happened at least 6-7 times I know it.

  I really have no idea how to fix it, 
Only that, after a couple months of using it, and dealing with it,
sometimes more frequently than others.. 
(that's how much i love lucid!) <3 lol

 It just.... stopped doing it. 
For about 5 days anyway....

then last night i decided to be a tard and try to install gloobus-preview and covergloobus~   which failed by the way....
But I was really only doing it out of boredom so didnt care much that it didnt work out..

however.. about 30 minutes later, I came back to look at the computer...
and it was flashing the black screen/vertical white lines at me again. 

 It then crashed two more times lasst night after that~ so 3 times last night, after 5 days of it not happening once!

 Today though~  It hasnt happened yet.
(knocks on 3 kinds of wood)  lol
I dont get it. 

  i just hope that it 'fixes itself' for all of us. 
i posted about it , here~ [http://ubuntuforums.org/showthread.php?t=1494141](http://ubuntuforums.org/showthread.php?t=1494141)

good luck mate.

Sorry I dont know what to do:confused:

---

### Post by jjjjjjj9175@ on 2010-05-31
Ubuntu seems to be crashing a few seconds after i mount a disk drive

---

### Post by WinRiddance on 2010-05-31
Are you using Ubuntu with your visual effects completely disabled i.e. set to none?
Have you tried a global search (google?) with just your graphic driver chip and the word Ubuntu? This definitely seems to be graphic chip related.

---

### Post by Rasa1111 on 2010-05-31
> **jjjjjjj9175@ said:**
> Ubuntu seems to be crashing a few seconds after i mount a disk drive

hmm...

 I can mount drives ok. 

Since my last post in this thread, my PC has beenon ever since, and still has not crashed yet. 

 The only thing that seems to cause this crash on my PC now~
is attempting to run/open Stellarium.

 as soon as I click it to open it.. bam.. crashed. 

 The last thing I can remember doing in the terminal before this apparently 'fixed itself'.. is typing 
> sudo apt-get update

 and the only crashes since then have been from me toying around with some packages for gloobus~

 but it seems ok again...

 I really dont know man.... :confused:

edit: winRiddance~  compiz is off on this machine, no effects enabled.
never have been.   It's definitely a graphics chip/card issue.

---

### Post by jjjjjjj9175@ on 2010-08-04
I tried reinstalling ubuntu to see if that would help. First I deleted the ubuntu partition and then I tried reinstalling. Now when I try to reinstall white lines start to flash about in the middle of the installation. Is there any way I can successfully reinstall Ubuntu?

---

### Post by deserthowler on 2010-08-04
Have you monitored memory usage?  Sometimes there is a problem with a high memory address and things run OK until this address is used.  If you try to test memory usage, you need to run 'free' in the console repeatedly.

Have you tried a memory test?

Are you using an on-board video card?  Have you tired a different video card?

Earl

---

### Post by jjjjjjj9175@ on 2010-08-05
I finally got Ubuntu to reinstall (when the cd was booting up i pressed F3 and choose acpi=off). But now I can't get into the new installation, it is still giving me white lines.

---

