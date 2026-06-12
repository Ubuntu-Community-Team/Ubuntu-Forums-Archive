---
title: "Ubuntu 11.04 Suspend Problem"
date: 2011-04-28
forum: General Help
---

### Post by MandoJM on 2011-04-28
Hi, I have an Asus U43F.  And the problem that I'm having is that when I
close the laptop or click on Suspend the computer goes into a black
screen and freezes there, I can still hear the fan and the only way to
get it working again is by doing a hard reset. In Ubuntu 10.10 i had the 
same problem and i used this to fix it. [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

---

### Post by MandoJM on 2011-04-29
Bump.......

---

### Post by MacKai on 2011-04-29
Same problem here.... except the hard reset in 10.10 it would resume in 10.10 fine but didn't go fully  to sleep

in 11.4 it doesn't go fully to sleep and a hard reset is required...

---

### Post by MandoJM on 2011-04-30
Yeah.. And nobody helps here.

---

### Post by midwesterndirt on 2011-05-01
Having the same issue on an inspiron 15n, using classic mode. Then again, I'm also getting random disk swapping. :-/

---

### Post by zspali on 2011-05-01
I've had the same problem, and what solved it is the following. Remove the comment sign from the line [FONT="Courier New"]SAVE_VIDEO_PCI_STATE=true[/FONT] in the file [FONT="Courier New"]/etc/default/acpi-support[/FONT].

---

### Post by aljazek on 2011-05-01
I have different problem and I really need help. After suspend (laptop - ubuntu 11.04, same problem in 10.10 and earlier) resume does not work. I have no sound and for example: "youtube resume" doesn't work, also in other apps.

---

### Post by zspali on 2011-05-02
> **zspali said:**
> I've had the same problem, and what solved it is the following. Remove the comment sign from the line [FONT="Courier New"]SAVE_VIDEO_PCI_STATE=true[/FONT] in the file [FONT="Courier New"]/etc/default/acpi-support[/FONT].

... and it's not working again. :(

---

### Post by lotharmat on 2011-05-02
Have you got a FAT filesystem mounted?

I used to get this problem when I had my SD car mounted.

---

### Post by neutro on 2011-05-02
I don't want to be a killjoy but in the past, say, 18 months or so, suspend was hit and miss for me. In all previous versions of Ubuntu, sometimes it would work and sometimes not. Is it because of updates or simply a hard-to-reproduce problem? I don't know, but I'm not surprised anymore my suspend not working.

As for Natty itself, I tried suspending twice. It did not work the first time and I had to hard reset too; the second time it did work, so I'm just going to say "good luck"!

---

### Post by midwesterndirt on 2011-05-02
My laptop actually freezes on its own now, even if I haven't closed the lid. I have suspend turned off. This is quite disappointing. I've never had an upgrade go this badly. :-(

---

### Post by lakerssuperman on 2011-05-02
Did you do a clean install of 11.04 or an update.  If it wasn't a clean install you may want to consider starting over and seeing if that fixes the freezing as sometimes the upgrade process can be hit or miss, especially with all the changes to the interface 11.04 brought.

---

### Post by midwesterndirt on 2011-05-02
As you probably could have guessed, this was an in-place upgrade. I have been considering starting from scratch, I just hate when I have to resort to that.

---

### Post by Novacaptain on 2011-05-03
I tried a fresh install to fix an unrelated issue, still stuck with not being able to suspend/hibernate without eventually having to cold-boot the system at some point. In 10.10 it worked fine as long as I stuck to the fglrx drivers for the video card. Now I'm clueless.

---

### Post by Jordanbadangayon on 2011-05-05
i also have a problem with suspend but of a different sort. when i hit suspend, my computer goes to suspend. but the problem is during waking up. every time i try to to wake it up, it boots up (instead of wake up). after booting up, all the applications that i opened before suspend are all closed. this was the case both in 10.10 and 11.04. i have a sony vaio NW20EF laptop dual booted with windows 7. can anybody help please... is there any workaround for this or any explanation??? :confused: thank you.

---

### Post by vinaydeo on 2011-05-05
I upgraded to natty recently, and neither suspend nor hibernate work properly. However, I found out that when I resume from suspend, the "black and white bricks" screen that I get actually is only a graphics problem. So just type your password when that screen comes, press enter, and you are back to normal. In other words, the only problem is that you cannot see the login box when you resume from suspend, but it "is there" and you can just type your password like you would normally, and press enter. Hope this helps some folks like myself who suspend quite often.

---

### Post by hide117 on 2011-06-19
Hi,
I clean installed 11.04 to my ASUS U30SD and run into the same problem.
Screen goes into black but power does not.
For me, the solution in #1 links works fine. It solves suspend and hibernation on my PC.
It may not work for everybody, but worth to try.
MandoJM, thanks.

Here is the link,
[http://thecodecentral.com/2011/01/18...ot-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug")

---

### Post by curts on 2011-06-25
I did a clean install of the AMD64 11.04 and encountered this problem.  I have a Soltek SL-K890Pro-939 MB with the BIOS set to ACPI Suspend Type S3.  This worked just fine using the AMD64 10.04 release.

Tried the suggested script from Code Central, but it didn't help.

---

### Post by Romualdou on 2011-07-22
Hi, 

having the same issue with a Samsung R522 (ATI graphics). I don't know if this is related to the video driver. I eventually tried to remove the ATI proprietary fglrx driver, but it didn't solve the problem. 
The Ubuntu "help" claims this could be related to incompatible hardware. But I upgraded from 9.04 making a full install and it worked just fine under 9.04. 
The a.m. script didn't help neither. 

I googled a bit, it seems that quite a number of people are encountering the same issue. This should definitively be solved ASAP, it's a basic feature for any laptop user. 

Any further suggestions?

Regards

---

### Post by Romualdou on 2011-07-28
bump

---

### Post by DoneRightI.T. on 2011-07-28
Same issue as outlined:

few notes here:

close the laptop lid, open it back up; the previous behavior was that it was completely black, had to press power and it would resume as normal.

now randomly: I open it and the caps-lock key is flashing, the wifi light is out, the power is solid, and the screen is stuck blank. I am forced to then do a hard boot; which I'm entirely unsatisfied with.

I am using the non-proprietary drivers(video)
Acer TravelMate 8572G-6647
Core i5
4gb ram
geforce GT 330M
Ubuntu 11.04 i386

I have literaly just done 2 things here; installed the code from the []("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug#header-0")

and changed the power pref's to not spin down the hard disks when possible for both ac power and battery power... now to see.

---

### Post by DoneRightI.T. on 2011-07-28
> **DoneRightI.T. said:**
> Same issue as outlined:

few notes here:

close the laptop lid, open it back up; the previous behavior was that it was completely black, had to press power and it would resume as normal.

now randomly: I open it and the caps-lock key is flashing, the wifi light is out, the power is solid, and the screen is stuck blank. I am forced to then do a hard boot; which I'm entirely unsatisfied with.

I am using the non-proprietary drivers(video)
Acer TravelMate 8572G-6647
Core i5
4gb ram
geforce GT 330M
Ubuntu 11.04 i386

I have literaly just done 2 things here; installed the code from the []("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug#header-0")

and changed the power pref's to not spin down the hard disks when possible for both ac power and battery power... now to see.

No joy, I will keep looking and cross my fingers.

---

### Post by Romualdou on 2011-08-19
Bump.

I keep giving it a try after each update. Latest today, but the issue is still not fixed. 
I wonder if I should downgrade two releases back or move to W7.
I don't think I should leave my PC running unnecessarily  for hours just because I think Ubuntu is a nice OS... 

](*,)

---

### Post by Romualdou on 2011-08-20
Try to report a bug, I wonder if this will get things moving...

[https://bugs.launchpad.net/ubuntu/+bug/829346](https://bugs.launchpad.net/ubuntu/+bug/829346)

---

### Post by OpenSage on 2011-09-21
> **MandoJM said:**
> Hi, I have an Asus U43F.  And the problem that I'm having is that when I
close the laptop or click on Suspend the computer goes into a black
screen and freezes there, I can still hear the fan and the only way to
get it working again is by doing a hard reset. In Ubuntu 10.10 i had the 
same problem and i used this to fix it. [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)





I know this is a really late reply, but I think I have this issue figured out.  I have had the same problem running both Ubuntu 10.10 64 bit and Ultimate Edition 9/on Ubuntu 10.10 64 bit.  I came across this fix by accident.  Before suspending the machine, go to a different console by pressing (CTRL+ALT+F2) all at the same time.  You should be in a new console.  Log into that console then press (CTRL+ALT+F7) to take you back to your Graphical User Interface and then Suspend you machine.  This works for me every time.  Hope this helps some people. \\:D/

---

### Post by morticul on 2011-09-22
[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug")
Did work for me. However on resume, the screen is blank. Using the trick CTRL+ALT+F2 followed by CTRL+ALT+F7 allows me to get my screen back. 

(ASUS U43F)

---

### Post by afv on 2011-10-05
Still the same problem on 11.10 (development branch), using an Asus N82Jv.

On suspend the computer freezes with a blank screen and the disk activity led is always on (although there's no disk activity).

It works using the workaround at [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug).

---

### Post by Romualdou on 2011-10-13
Well both the script mentionned in last post as well as the console workaround didn't change anything in my situation. 

I guess that I'm going to downgrade to 10.04 LTS in near future, because this issue is really getting boring.

---

### Post by Romualdou on 2011-10-19
Hello,

things are now settled, with following comments.
- downgrade to 10.04 LTS solves the issue. (But the available software is not matching my needs anymore)
- upgrade to 11.10 also solves the issue. (But Unity and Gnome Shell are really nothing for me, I consider that Nautilus has been _downgraded_ moving from 11.04 to 11.10).

-> Finally I choose to move to Kubuntu 11.10, which solves the issue and leaves me with a reasonably flexible desktop configuration. 

End of the story as far as I'm concerned, thanks to those who tried to help...

---

### Post by Silhalnor on 2012-02-12
This problem happens to me rather often in 11.04 and I would like to add a few details that people seem to have missed. Often when I try to resume and the screen remains blank I have discovered that it is ONLY blank and the log in window is actually there like normal and I can type my password to get in, I just have to do it blind. The screen comes back up after that. Other times it doesn't work however, but once I seem to recall the screen coming up and finding my password typed out a few times in gEdit as if it simply took a little while for the screen to come back.
Graphics card: ATI Mobility Radeon HD 5000 Series
Laptop: Acer Aspire 7552G-6061

---

