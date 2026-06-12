---
title: "Playing DVD's 10.10"
date: 2011-01-27
forum: General Help
---

### Post by 4042966262 on 2011-01-27
i insert a DVD and ubuntu will show a Icon on desktop as well as let me know i have inserted a movie. however opening with the default player gives me a ''ubuntu will not read from resource'' what gives?:confused:

---

### Post by wilee-nilee on 2011-01-27
> **4042966262 said:**
> i insert a DVD and ubuntu will show a Icon on desktop as well as let me know i have inserted a movie. however opening with the default player gives me a ''ubuntu will not read from resource'' what gives?:confused:

Open synaptic and install ubuntu-restricted-extras,and libdvdread.

Add this repository and do a update from synaptic or in the terminal and install libdvdcss2, and w32.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Install vlc, and smplayer to see if they work better the stock player does not always work.

---

### Post by 4042966262 on 2011-02-04
i swapped operating Systems.. now using Lubuntu. are the directions the same?):P

---

### Post by 3rdalbum on 2011-02-04
> **4042966262 said:**
> i swapped operating Systems.. now using Lubuntu. are the directions the same?):P

Yes, I don't see anything Gnome-specific about it.

---

### Post by 4042966262 on 2011-02-05
Open synaptic and install ubuntu-restricted-extras,and libdvdread. 
did that.
Add this repository and do a update from synaptic or in the terminal and install libdvdcss2, and w32.

well i installed  libdvdcss.. w32? didn't find that. and add what?? whats a repository? 
when i load a DVD i get a prompt to open in VLC or package manager. i select VLC and it lists options, i select the DVD (i can see the name) VLC then ''pops out'' and shows a black movie screen for an instant then snaps back into the small title bar for vlc.. whats going on?

---

### Post by coffeecat on 2011-02-05
Did you install the libdvdcss2 package successfully? It's not clear from your post. If not, go to the link wilee-nilee posted and follow the instructions to add the Medibuntu repository. Then you will be able to install libdvdcss2. A repository is simply a - well - repository where you can get software online. Some packages cannot be included in the official Ubuntu repositories because of licensing issues. Hence the need for Medibuntu which I add routinely to all my (many) Ubuntu installations.

---

### Post by 4042966262 on 2011-02-05
my apologizes for not being clear. yes i installed  libdvdcss2 with no errors. ;)

---

### Post by coffeecat on 2011-02-05
Ubuntu-resticted-extras (which includes libdvdread) and libdvdcss2 (for unscrambling DVD encryption) should be all you need to play commercial DVDs. If VLC is failing you, what about the default Movie Player app? Have you tried more than one DVD? Have you ever changed the region code on your DVD drive? This shouldn't be an issue in Linux, but if you've changed the region code 5 times in Windows, then the DVD drive gets stuck to the last region or becomes inoperable - I can't remember which.

---

### Post by 4042966262 on 2011-02-05
i never messed with regional codes. whatever they are.

---

### Post by 4042966262 on 2011-02-05
i don't know how to explain it. putting a DVD in player (there are two CD Drives a DVD one and a CD one) loads a prompt to open DVD with.. i select VLC and the choose media box plays, i click browse, the CD name, Video_TS file.. and when i click play VLC blinks the name of DVD and expands (like its playing) then blinks blank and  shrinks to the small title bar.

---

### Post by 4042966262 on 2011-02-05
i got DVD playing figured out in Ubuntu.. its lubuntu im having trouble with.

---

