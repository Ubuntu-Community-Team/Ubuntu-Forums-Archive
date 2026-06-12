---
title: "RealPlayer10"
date: 2006-03-21
forum: General Help
---

### Post by pdfcomp on 2006-03-21
I cannot get Real Player to install.  I have downloaded RealPlayer10GOLD.bin.  Then I followed the instructions to start terminal, run the chmod command, etc.  But when I  type ./RealPlayer10GOLD.bin, I get an error message that certain library files are not found.  Any ideas?  BTW, I am a very old Microsoft OS user, but pretty new to linux.

---

### Post by IYY on 2006-03-21
I think real player is in the repositories (**sudo apt-get realplayer** in the terminal, or search for **realplayer** in Synaptic). It's also installed by the Automatix script.

---

### Post by tango_ninja on 2007-08-17
i realise this is an incredibly old post, but i'm having the same problem (installing Realplayer)

when i try to run through terminal i get
```
./RealPlayer10GOLD.bin: error while loading shared libraries: 
libstdc++.so.5: cannot open shared object file: 
No such file or directory
```

running  < sudo apt-get install realplayer >
i get a <package not available> message 

any suggestions?

---

### Post by mszl_1 on 2007-08-17
I Had Trouble Installing Realplayer So Much That I Gave Up In The End. :(
Since I Changed The Desktop Environment To Kde From Gnome I Have Not Tried To Install It Again. I Now Make Do With Otehr Media Players But Would Still Like To Have Real Player Tho. :)

---

### Post by gobbles414 on 2007-08-17
It is very easy to play real player Real files without Real Player. On my system, I use a combination of Gstreamer, W32codecs, and the MPlayer plugin for Firefox.* EDIT: I also have Ubuntu Restricted Extras installed. All of these are available in the Synaptic package manager if you follow the directions listed [here]("https://help.ubuntu.com/community/RestrictedFormats").*

---

### Post by tango_ninja on 2007-08-17
it just seems that installing 1 RealPlayer would be much  easier than installing x amount of other players, codecs, plug-ins etc.

---

### Post by Vince4Amy on 2007-08-17
Try opening a console & typing:

```
sudo apt-get install libstdc++
```

By the way make sure the RealPlayer10.bin file is executable & also I'd install to /usr/lib/realplayer or else it will not install for every user on your system (assuming there is more than one user).

---

### Post by Seisen on 2007-08-17
You can install helix-player which is the open-source version of RealPlayer  which is available in the Universe Repositories.

---

### Post by tango_ninja on 2007-08-17
tried this as well, but libstdc++ is not a package that I can do this with...

---

### Post by tango_ninja on 2007-08-17
ps tried installing Helix, it won't play .SMIL

---

### Post by mali2297 on 2007-08-17
Look for libstdc++5  in synaptic (search by name and you should find it quickly).

I've got both that one and libstdc++6 (which I guess is installed by default).

---

### Post by ugm6hr on 2007-08-17
This comes up all the time - for Fiesty/Edgy - there is a much easier way:
[http://ubuntuforums.org/showpost.php?p=2720883&postcount=4](http://ubuntuforums.org/showpost.php?p=2720883&postcount=4)

Download, and double-click to install.

---

### Post by tango_ninja on 2007-08-17
thanks all for your help, i managed to solve it with a little bit of google research

using adept manager i just added a new repository (debian)

<<<  deb [http://mirror.home-dn.net/debian-multimedia](http://mirror.home-dn.net/debian-multimedia) stable main >>>

and realplayer can be found directly in there

many thanks,

---

