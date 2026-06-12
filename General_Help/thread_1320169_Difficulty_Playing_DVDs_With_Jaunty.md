---
title: "Difficulty Playing DVDs With Jaunty"
date: 2009-11-09
forum: General Help
---

### Post by marlanc4 on 2009-11-09
I have a laptop and when I had Windows it wouldn't burn DVDs; now with Jaunty 9.04, it burns DVDs, no problem; so for the most part, very happy with Jaunty.  
 

 I have a problem playing DVDs though. Jaunty doesn't play my DVDs all the way through. At some point Movie Player returns the message  
 

 “*could not read from source*” or  
 

 “*the source seems encrypted and can't be read. Are you trying to play an encrypted DVD without libdvdcss?*”   
 

 With VLC it stalls, and then just Xs out. I've been enjoying a measure of success with everything else though.
 

 In addition I found a great site which instructed typing this command in terminal: 
 *wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update *
  
 However, the message returns: 
 *W: Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs *
 
 *W: Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs *
 
 *E: Some index files failed to download, they have been ignored, or old ones used instead.*

---

### Post by arnab_das on 2009-11-09
try installing ubuntu restricted extras or even mplayer could do the job.

---

### Post by cariboo on 2009-11-09
You need to comment out the cd-rom in System-->Administration-->Software Sources. Just remove the check mark. You may need to install libdvdcss2 from the Medibuntu repositories. To enable the repositories, go [here]("https://help.ubuntu.com/community/Medibuntu").

---

### Post by marlanc4 on 2009-11-10
Cheeers mate. I'll give it another shot.

---

### Post by marlanc4 on 2009-11-10
[FONT=Times New Roman][SIZE=4]I tried installing ubuntu resricted extras. I have the latest and newest version already. The same with mplayer.[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=4]
[/SIZE][/FONT] 
 [FONT=Times New Roman][SIZE=4]I've commented out the cd-rom and that takes care of the above error message, however after executing  sudo apt-get install libdvdcss2, the message returns[/SIZE][/FONT] 
 [FONT=Times New Roman][SIZE=4]
[/SIZE][/FONT] 
 [FONT=Times New Roman][SIZE=4]*libdvdcss2 is already the newest version, *furthermore why do I now get [/SIZE][/FONT] 
 [FONT=Times New Roman][SIZE=4]
[/SIZE][/FONT] 
 [FONT=Times New Roman][SIZE=4]*W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_karmic_free_binary-i386_Packages) *[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=4]*W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_karmic_non-free_binary-i386_Packages) *[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=4][I]W: You may want to run apt-get update to correct these problems. 
[/I][/SIZE][/FONT]

---

### Post by theiron on 2010-03-27
Give the following a try:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2

I got this from another thread, and it fixed all of my DVD playback woes.

---

### Post by NightwishFan on 2010-03-27
Most codecs can be found in the repositories, however the libdvdcss2 encryption library needs to be found in Medibuntu.
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

