---
title: "x800 AGP install - &quot;Unmet dependencies&quot;"
date: 2006-03-27
forum: General Help
---

### Post by Zooropa on 2006-03-27
New ATI x800VE from upgrading from an ATI 9200.
 
've followed the instructions here:

[http://ubuntuforums.org/showthread.php?p=423589](http://ubuntuforums.org/showthread.php?p=423589)

I am in Gnome through using "Vesa" drivers. I tried picking "ATI" but xserver wouldn't let me in.
Why does VESA seem to work? I don't fully understand.

Anyway, on trying to install the ATI drivers:


~$ sudo apt-get install gcc-3.4 module-assistant build-essential fakeroot dh-make debconf libstdc++5 gcc-3.3-base
Reading package lists... Done
Building dependency tree... Done
module-assistant is already the newest version.
build-essential is already the newest version.
fakeroot is already the newest version.
dh-make is already the newest version.
debconf is already the newest version.
libstdc++5 is already the newest version.
gcc-3.3-base is already the newest version.
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  gcc-3.4: Depends: gcc-3.4-base (>= 3.4.4-6ubuntu8.1) but 3.4.4-6ubuntu8 is to be installed
           Depends: cpp-3.4 (>= 3.4.4-6ubuntu8.1) but 3.4.4-6ubuntu8 is to be installed
  linux-headers-2.6.12-10-386: Depends: linux-headers-2.6.12-10 but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).



I'm really struggling.
I went into Synaptic and tried to insall the cpp-3.4 package, but it wants to remove the Linux headers, which I had to go to a bit of bother installing earlier on my own as the user/src/ link wasn't right.

Can anyone help?

---

### Post by Zooropa on 2006-03-27
I got it!

Somehow, when I restarted, the update manager wanted to update CPP, the headers, and GCC.
I obviously allowed it too, then went back and ran some of the script which installed the drivers!

Now, how do i get back to the terminal so I can reconfigure xserver?

I try and run it from the terminal within Gnome and it won't allow it.
Bit of a newbie question, but I can't see any obvious way!

---

