---
title: "Powermac G5 - FX5200 - Rendering Problems"
date: 2012-07-13
forum: General Help
---

### Post by ozzi789 on 2012-07-13
Good evening community

I own a PowerMac G5 with a 2 Ghz PPC Dualcore and a Gefore FX5200 Ultra (64mb).
Since i was using 10.5.8 (ewwhh) i decided to install 12.04 on it.
But i have some strange rendering issues (in firefox some lines of text dont get rendered & some gui elemtns are just blank).
Since im quite a newbie when it comes to Linux i am kinda lost.
I tried to check the Driver with the "Additional Drivers" Tool but it crashes (Jockey causes the problem, i dont know what that is..)
This person gets the same output when using jockey-text -> [http://ubuntuforums.org/showthread.php?t=1978951](http://ubuntuforums.org/showthread.php?t=1978951)

What do i need to do in order to get all of the stuff rendered properly?

Thank you so much for your help in advance!
-Ozzi

---

### Post by Rexilion on 2012-07-14
Long shot, but maybe just try nouveau?

Install [this]("https://launchpad.net/~xorg-edgers/+archive/ppa") ppa and then do:

```
aptitude update
aptitude -s full-upgrade
aptitude -s install xserver-xorg-video-nouveau
```

But before that, make sure you delete the nvidia proprietary driver or disable it properly.

Especially using the latest git of nouveau helps, I have seen a lot of fixes for foreign machines go in these days.

---

### Post by ozzi789 on 2012-07-14
[FONT=Arial]Hi Rexilion

I deinstalled the nvidia drivers the following: 
[/FONT]```
apt-get purge nvidia-*

```[FONT=Arial]
But i am not sure if that really worked..
Then i installed the PPA, installed aptitude then executed the commands you posted.
The result of:
[/FONT]```
aptitude -s install xserver-xorg-video-nouveau
```[FONT=Arial]
Was that there werent any packages installed, updated or removed.

So are the nouveau drivers already installed?
I dont know what i am doing :confused: :)
[/FONT]

---

### Post by ozzi789 on 2012-07-16
if it helps, ubuntu 12.04 for ppc looks even weirder.
yellow dog 6.2 works perfectly.. 

ideas? :)

---

### Post by ozzi789 on 2012-07-20
desperate bump for help :(

---

### Post by Rexilion on 2012-08-25
If you install a PPA or do any other modification to your 'lists' then you must do:

> aptitude update

In order to get the new information of packages inside aptitude's package database.

---

### Post by lucky_waster on 2012-11-26
I don't know if this helps, I am equally a complete newbie.

Looking at the man page for aptitude, the instructions Rexilion gave you, followed to the letter, appear to only result in a "simulation" of what aptitude would do, owing to the -s switch.

I was having what sounded like the same rendering issues and running Rexilion's code without the -s switches has partially cleared it up.  Now text does not disappear and reappear after scrolling up and down in Firefox and other programs.  However, I don't know whether this was to do with nouveau or with the firefox update.

There is still a strip of constant width at the bottom of the Firefox window in which text is never rendered.  I don't know what is causing this - any help would be appreciated!  (Precise 12.04 on 2003 G4 Powerbook 12", Firefox 17)

Cheers

James

---

### Post by Rexilion on 2012-11-27
> **lucky_waster said:**
> I don't know if this helps, I am equally a complete newbie.

Looking at the man page for aptitude, the instructions Rexilion gave you, followed to the letter, appear to only result in a "simulation" of what aptitude would do, owing to the -s switch.

I was having what sounded like the same rendering issues and running Rexilion's code without the -s switches has partially cleared it up.  Now text does not disappear and reappear after scrolling up and down in Firefox and other programs.  However, I don't know whether this was to do with nouveau or with the firefox update.

There is still a strip of constant width at the bottom of the Firefox window in which text is never rendered.  I don't know what is causing this - any help would be appreciated!  (Precise 12.04 on 2003 G4 Powerbook 12", Firefox 17)

Cheers

James

You are right, I should have made the use of the '-s' switch somewhat more informative for other readers. Thanks for mentioning.

As for the corruption with Firefox, that is highly likely a (nouveau) video driver issue.

Maybe check the bugzilla @ freedesktop.org?

---

### Post by olandesevolante on 2012-12-29
I was having exactly identical problems in Lubuntu 12.04 on an old compaq/hp laptop, a Presario B1013. A bit of a pain since firefox was unusable so I was stuck with chrome. It just happens I really like firefox, and I really hate chrome... ;)

Anyway, I went to check and nvidia's proprietary driver was not in use. Enabling the proprietary driver fixed the problem and resulted in improved display overall =D>

---

