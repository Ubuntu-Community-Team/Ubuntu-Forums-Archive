---
title: "Flash sound suddenly broke"
date: 2009-08-18
forum: General Help
---

### Post by mechaxl on 2009-08-18
Hey,

So I was listening to pandora.com last night, and it worked great. I came back the next morning, and all of a sudden, flash videos and apps completely do not have sound. It's not a problem with soundcard, pulseaudio etc, as all other apps such as totem/rhythmbox work just fine. Now I remember having to fix this before by installing libflashsupport, and I went to go see if it was still installed. It wasn't installed, and when I went to install it, it had a dependent package that couldn't be installed. I went to check on that one, libgnutls13, and it gives me an error that says this:

Package libgnutls13 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

It looks like there was an updated version (libgnutls26), but libflashsupport doesn't support it, and I can't find an installable libgnutls13.

Does anyone know how I can fix this? I've got Ubuntu 9.04 32-bit btw

---

### Post by DougieFresh4U on 2009-08-18
I was visiting youtube a while ago and sound didn't work for me either, where as it worked yesterday.:confused: . Works with amarok and other sound events work. I just blew it off as some thing I did. 
Running 64bit Karmic though.

---

### Post by mechaxl on 2009-08-20
So does anybody have a clue what went wrong/what I can do to fix this? I'm still not able to find anything that would fix this.

---

### Post by XxionxX on 2009-08-20
Have you tried re-installing flash? I know that it's very obvious but sometimes simple things help.

---

### Post by brashley46 on 2009-08-21
Flash sound suddenly broke on my machine as well, after installing the newest kernel upgrade tonight. Running 9.04 on a Cybertron box with an AMD X2 64 processor, and an Nvidia VT 1708B soundcard.

---

### Post by mechaxl on 2009-08-21
Well, thanks for the attempt at helping me. I got it fixed thanks to kostkon in this thread: [http://ubuntuforums.org/showpost.php?p=7205818&postcount=6](http://ubuntuforums.org/showpost.php?p=7205818&postcount=6)

brashley46, i'd recommend checking that thread out. my problem was that flash was sending sound to the wrong device, so installed a program that let me choose where flash was sending sound to

---

