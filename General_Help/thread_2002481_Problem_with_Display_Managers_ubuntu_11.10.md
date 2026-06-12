---
title: "Problem with Display Managers ubuntu 11.10"
date: 2012-06-12
forum: General Help
---

### Post by lin194 on 2012-06-12
Dear forum members!

Ive found posts about this topic, but it says in the forum rules that if they are old you should create a new thread if I understood right. Also this case is a little different from those.

**Ill post what Ive written in another forum with no answers so far down below, and if you read those lines it explains my problem**, especially the last part with the newly installed Display Manager.

Id like to thank anyone who reads this and can help me in advance!

---

### Post by lin194 on 2012-06-12
I have a Toshiba Satelite L650-108 laptop, I have multiple versions of ubuntu on it as well as windows 7.
 
 Since the last restart, it wont boot, the grub menu comes up, I select 11.10, then it hangs on this screen: [http://dl.dropbox.com/u/5983311/IMG_20120612_162928.jpg](http://dl.dropbox.com/u/5983311/IMG_20120612_162928.jpg)
 Everything used to work fine, I havent updated packages lately (except I installed kTorrent).
 I can boot into other ubuntu installs I have on the laptop without any problems.
 I think something might have gone wrong with the video drivers, I have  installed and uninstalled the ATI drivers many times before, but I might  be wrong.
 
 Any help or ideas that could help bring up this system would be highly  appreciated, since I have everything set up the way I want it, I wouldnt  like to reinstall and set up everything again.
 Thx in advice!




UPDATE: Ive chrooted into the system from another copy of ubuntu,  uninstalled the ATI drivers, reinstalled the open-source drivers, the  system still hangs at
 * Stopping System V runlevel compability          [ OK ]




UPDATE2: installed ATI drivers, still hangs at the same point





UPDATE3: The problem seems to be with the display manager, I chrooted  into the system, installed GDM, then booted it, and it booted into GDM,  but when I tried to log in (I selected ubunutu as the session=unity 3D),  put in my password, hit enter it didnt log in, I was greeted with GDM  again just like I didnt put in my login info.
 
 Then I installed XDM, it booted into XDM, but I had the same issue, when  I put my login info and hit enter, like nothing happened. I was  prompted to put in my username and password again.
 
 Them I installed LXDM, it booted into LXDM, I still had the same issue:  when I put in my username and pass and hit enter it asks for everything  again like I didnt put it in.
 
 So far I now know the reason why it hung at * Stopping System V runlevel  compability [ OK ] was because of the display manager, now ive tried 3  different display managers and have the same problem with all 3 as  described above. If anyone knows how to fix that pls reply! Thx

---

### Post by lin194 on 2012-06-12
UPDATE4: When I select a display manager that doesnt work (lightdm), and press CTRL + ALT + F1, then log in and type startx this is what I get: [http://dl.dropbox.com/u/5983311/IMG_20120612_211424.jpg](http://dl.dropbox.com/u/5983311/IMG_20120612_211424.jpg)

It looks like my X fails to start, that might be the reason why none of the display managers let me log in.

---

### Post by lin194 on 2012-06-13
Problem solved by reinstalling system.

---

