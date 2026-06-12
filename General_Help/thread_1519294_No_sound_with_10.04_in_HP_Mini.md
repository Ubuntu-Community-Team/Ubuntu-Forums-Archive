---
title: "No sound with 10.04 in HP Mini"
date: 2010-06-27
forum: General Help
---

### Post by heylookitsmewow on 2010-06-27
I did a fresh install of Ubuntu 10.04 in a new HP Mini. Everything seems to work fine except there is no sound. I have seen a few similar problems on other posts but anyone know of a fix for this that is understandable for a semi noob?

---

### Post by cariboo on 2010-06-28
Check and see if the sound is muted, what model do you have?

---

### Post by heylookitsmewow on 2010-06-28
The sound is not muted, that is the first thing I checked. Model is 1103030NR. And I am using the netbook version of Ubuntu. Although I am still not sure that I am going to stay with it. I may go to the desktop version.

---

### Post by heylookitsmewow on 2010-06-29
Another thing I discovered is there is sound to the headphones just not the speakers.

---

### Post by justasconfusedasb4 on 2010-07-17
Had the same problem when upgraded to 10.04 also using an HP Mini, try;

System / Preferences / Sound / Output tab / Set connector drop down box to: Analog Speakers

Worked for me hope it does the same for you.

---

### Post by heylookitsmewow on 2010-07-21
It's a little different path to my sound preferences. It's just System/Sound/output tab but there is no dropdown box. But there is a "choose a device for sound output" box. In it there is only "Internal Audio Analogue Stereo" and it is selected.

---

### Post by heylookitsmewow on 2010-08-30
Any other ideas?

---

### Post by doobiest on 2010-09-12
bump.

I'm having the same issue with 110-3000

---

### Post by Henry-t on 2010-09-26
[SIZE=2][FONT=Arial]I have just recently started using Ubuntu 10.04.  
I had the same issue with my HP Mini-110 3000 Netbook, with no sound.
After tinkering unsuccessfully with suggestions from other Forum links.

I finally came across the following bug report entry in Launchpad, by akaname which advised how to fix the problem - which was relatively easy.
I now have sound finally.


Website
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/606893](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/606893)


[/FONT][/SIZE]


[akaname]("https://launchpad.net/%7Ebn-launchpad-net")             wrote             on 2010-07-18:                                                             [ #0]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/606893/comments/0")                                                        I report this bug just for information, cause it took me several hours to find out the solution.
 --- System ---
 Description:    Ubuntu 10.04.1 LTS
Release:    10.04
Package: alsa-base 1.0.22.1+dfsg-0ubuntu3
 --- Problem ---
 After installing Ubuntu 10.04 LTS on HP 625 Notebook, you won't get  sound through the internal notebook speaker. Line-out works perfectly.
 The ALSA Information Script reports the wrong hardware:
HDA-Intel - HDA ATI SB
IDT ID 7667
 That's because of the wrong alsa driver version, missing the newest drivers:
Driver version:     1.0.21
 --- Solution ---
 You need alsa driver version 1.0.23 or higher. To install at least driver version 1.0.23 at this time, take the following steps:
* Activate the "Unsupported updates (lucid backports)" repository in  Synaptic Package Manager (Settings -> Repositories -> Updates).
* Reload your package information.
* Install the package "linux-backports-modules-alsa-lucid-generic". This will also install a new linux kernel version.
* Restart and your sound should work properly.
* If not, raise all available volume levels in alsamixer (start alsamixer in terminal).
 Now the ALSA Information Script reports the right hardware:
HDA-Intel - HDA ATI SB
IDT 92HD88B1
 Best regards
Akaname

---

### Post by heylookitsmewow on 2010-09-28
That worked perfectly, thanks Henry-t!

---

### Post by houseisland on 2010-12-15
Yes.  Thank you Henry-t.

:KS:KS:KS:KS:KS

Same problem with my HP Mini 110 3150ca

Sound through head phone jack OK.

No sound through internal speakers.

Config on everything looked OK.

Had XUnbuntu 10.4 installed.  Installed Lucid.  No change.

Tried a lot of other suggestions, most of which were for no sound at all.

Nothing worked.

Except this.

;)

Thanks again.

---

### Post by houseisland on 2011-01-30
Hmmm the last round of updates just killed my sound again.

There was a greyed out recommended update for linux-backports-modules-alsa-lucid-generic that could not be installed.

I have tried removing and reinstalling but no go.

linux-backports-modules-alsa-lucid-generic:
 Depends: linux-backports-modules-alsa-2.6.32-28-generic  but it is not installable

Does anyone have any suggestions?

Thanks

---

### Post by houseisland on 2011-02-01
> **houseisland said:**
> Hmmm the last round of updates just killed my sound again.

There was a greyed out recommended update for linux-backports-modules-alsa-lucid-generic that could not be installed.

I have tried removing and reinstalling but no go.

linux-backports-modules-alsa-lucid-generic:
 Depends: linux-backports-modules-alsa-2.6.32-28-generic  but it is not installable

Does anyone have any suggestions?

Thanks

OK ... It's gone from bad to worse.  Whatever the problem in the repository was that would not allow the update to linux-backports-modules-alsa-2.6.32-28-generic got fixed.  I was able to install the update but I'm kind of wishing it hadn't been fixed because now not only do I not have sound but my wireless is hosed, too.

Nice. 

This little HP beast has Intel hardware most of the way except for the Broadcom wireless NIC - about as vanilla as you can get - weird.

Any suggestions?  Reload?  Load Maverick?  Get out the Windoze 7 Starter recov disks I made?
;)

Edit: And removing the update does not restore Wireless functionality.  The wireless driver can no longer be activated.

---

### Post by houseisland on 2011-02-02
Bump!

---

### Post by houseisland on 2011-02-04
Loading Maverick has solved the problem.

:)

I have both sound and wireless and did not have to fight to get them - all nicely working on the first boot after installation.

---

### Post by livekeen on 2011-03-10
> **Henry-t said:**
> [SIZE=2][FONT=Arial]I have just recently started using Ubuntu 10.04.  
I had the same issue with my HP Mini-110 3000 Netbook, with no sound.
After tinkering unsuccessfully with suggestions from other Forum links.

I finally came across the following bug report entry in Launchpad, by akaname which advised how to fix the problem - which was relatively easy.
I now have sound finally.


Website
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/606893](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/606893)



Thanks Henry! That solved one of the issues I was encountering with my machine. I apologize for breaking forum topic a bit but I noticed you had the same machine/OS combo that I have and was wondering if you encountered issues with your SD card reader not recognizing cards. If so, I was wondering if you had come across a solution.

---

