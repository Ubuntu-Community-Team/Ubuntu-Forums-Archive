---
title: "Ubuntu 11.04 k9copy problem (dvd to avi)"
date: 2011-04-29
forum: General Help
---

### Post by Peedelberryjb on 2011-04-29
yes im a noob, so bare with me...
upgraded ubuntu 10.10 (64bit) to 11.04 (32bit). had k9copy in 10.10 but never tried to convert dvd iso to avi untill after i upgraded to ubuntu 11.04. every time i try k9copy crashes..is this a know problem? or am i missing codecs or something? 

im trying to convert dvd iso to avi to play on ps3. i know i can just burn iso to dvd but i dont want to make hundreds of dvd's when i could just use usb stick or windows media play steam to ps3. 

or any other way to convert encrypted dvd to avi?

---

### Post by dino99 on 2011-04-29
you cant do that without a fresh new install: "upgraded ubuntu 10.10 (64bit) to 11.04 (32bit)"

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Peedelberryjb on 2011-04-29
i failed to mention that i am running a fresh install. as i deleted old ubuntu 10.10(64bit) partition and made a fresh new partition and installed ubuntu 11.04(32bit) with fresh new boot disk

---

### Post by SilentSeven on 2011-05-01
Same problem here.  K9 crashes on a fresh 11.04 install.

---

### Post by ctomayer on 2011-05-02
same here, k9copy locks up after selecting source of backup.

---

### Post by SilentSeven on 2011-05-02
Can anyone on the thread get VLC or Movieplayer to play an encrypted, standard distribution DVD?  

I can play from files ripped and decrypted to my hard drive but can't get the DVD to play.

---

### Post by SilentSeven on 2011-05-02
I think this solves the problem.

Follow the instructions here to add the medibuntu library and libdvdcss package.  K9copy stopped crashing for me after I did this.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[edit] - can now fully confirm this solves the problem.  You will need to install a couple other libs but the application will tell you vs. bombing

---

### Post by 3rdalbum on 2011-05-03
When I installed 11.04 I forgot to install the libdvdcss2 library, and was wondering why K9Copy was crashing. So I tried Acidrip and that didn't work. Finally realised that libdvdcss2 was missing, so I installed it and my ripping worked.

---

### Post by coacharnold on 2011-06-28
Thank you!!!!!!!!!!!

THis has been driving me NUTZ .... I was using a script to sort of get it done.......

Totally forgot !!!!!!!!!!

t

---

### Post by LordDelta on 2011-07-10
@coacharnold Could you outline what steps you took to get this to work? My k9copy is still crashing, I tried running those scripts on medibuntu, I have libdvdcss2 installed, and nadda same issue as original poster, as soon a I finish loading the dvd/iso unexplained bug crash.

---

### Post by CompBio on 2011-07-24
I'm having the exact same problem.  I have everything listed above installed on my machine running 11.04.  I have completely removed and reinstalled k9copy.  It will start to back up a DVD, but after about 10 seconds it simply dies.  No warning messages, nothing.

---

### Post by soluckytouselinux on 2011-08-24
Hi everyone. I had the same problem. the way i fixed it was to get all my extra files and  libdvdcss2. I had to reload my synaptic package manager twice and there it was. now everything works fine!!!:guitar:

---

