---
title: "can't install some programs in 64 bit lucid"
date: 2010-05-01
forum: General Help
---

### Post by sleepee on 2010-05-01
so i just did a fresh install of lucid last night.  it went relatively well, but there's a few minor issues.. 
one of them being that i can't install certain software from ubuntu software center because it tells me that the program isn't offered for amd64.

for example, when i try to install skype, it tells me
>  Sorry, 'skype' is not available for this type of computer (amd64).

i even downloaded the 64 bit skype from the website, but when it doesn't want to install that either and just leaves me with a broken package.

the thing is, these programs that won't install with lucid worked perfectly with karmic.. so i guess it has something to do with lucid..
can anybody point me into the right direction to fix this??
thanx in advance

---

### Post by CoreyB. on 2010-05-01
Is the version you installed for 64-bit from here --> [http://www.skype.com/download/skype/linux/choose/]("http://www.skype.com/download/skype/linux/choose/")?

When you try to install the .deb, what error do you get exactly?

I don't actually use Skype, but I'll see what I can do.

---

### Post by sleepee on 2010-05-01
well, when i try to install it from Ubuntu Software Center, i get the message that i put in quotes...

i did try to download the 8.10+ 64 bit version from that page, but i get this error message

```
sleepee@sleepee-laptop:~/Downloads$ sudo dpkg -i skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb 
(Reading database ... 125761 files and directories currently installed.)
Preparing to replace skype 2.1.0.81-1 (using skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb) ...
Unpacking replacement skype ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on lib32stdc++6 (>= 4.1.1-21); however:
  Package lib32stdc++6 is not installed.
 skype depends on lib32asound2 (>> 1.0.14); however:
  Package lib32asound2 is not installed.
 skype depends on ia32-libs (>= 1.6); however:
  Package ia32-libs is not installed.
 skype depends on libc6-i386 (>= 2.7-1); however:
  Package libc6-i386 is not installed.
 skype depends on lib32gcc1 (>= 1:4.1.1-21+ia32.libs.1.19); however:
  Package lib32gcc1 is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 skype

```

i find it odd, because in karmic i had absolutely no problems..  i installed it from both the software center, and also the skype page (when i wanted to upgrade skype) with no problems at all..

---

### Post by sleepee on 2010-05-01
never mind...
i have no idea what happened, but i've been messing with synaptic and ubuntu software center, and apparently now skype is installed, as well as the pokerth game, which was not installing earlier..

weird... maybe i had to install some other packages first or something.  but it works now..  sorry for the false alarm..

---

### Post by CoreyB. on 2010-05-02
> **sleepee said:**
> never mind...
i have no idea what happened, but i've been messing with synaptic and ubuntu software center, and apparently now skype is installed, as well as the pokerth game, which was not installing earlier..

weird... maybe i had to install some other packages first or something.  but it works now..  sorry for the false alarm..

Yeah, from your post above, it seems that the problem is that it depended on: lib32stdc++6, lib32asound2, ia32-libs, libc6-i386, and lib32gcc1.  Maybe you installed those packages?  Good to know it is working.

---

