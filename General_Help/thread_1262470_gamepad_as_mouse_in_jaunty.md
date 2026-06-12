---
title: "gamepad as mouse in jaunty"
date: 2009-09-09
forum: General Help
---

### Post by r00too on 2009-09-09
Hello. I'm trying to get a video game controller to use mouse and keyboard input in Jaunty. I've tried different combinations of controllers and software, including ps3 controller, xbox controller, jscalibrator (and a couple others whose names I can't remember), qjoypad, and js2mouse.

I'm very much a noob so I apolozige for the pains my ignorange brings forth. But my current issue is with the xbox controller (with a USB adapter) on js2mouse. Js2mouse's instruction are located here: < [http://cedric.vincent.perso.free.fr/Projets/index.html](http://cedric.vincent.perso.free.fr/Projets/index.html) >. I was succesful up to section II/1, but after that I don't know what to do. And I don't understand the directions of the next section (II/2) with the 'Option' commands and such.

 Any help would be appreciated. Thank you very much.

---

### Post by floatingworld on 2009-09-11
Just out of curiosity, what problems were you running into with qjoypad?  I ask because I've aaaaalmost got it working with a PS3/USB Corded Gamepad - it's working with all the buttons but not with the axes.

I didn't get anywhere with js2mouse either so I'm afraid I don't have any answer for you on that front.

btw I have found the package called "Joystick Calibrator" to be handy as at least it shows you that the hardware is working.

(edit) Though come to think of it I can at least tell you that the X Windows configuration mentioned in the js2mouse instructions is now the /etc/X11/xorg.conf file, though things seem to work a bit differently from the way they did in 2004.

---

### Post by floatingworld on 2009-09-11
In case the problem was that you couldn't get qjoypad installed at all, or for anyone else who comes looking, here are the steps I had to take to get it installed.  (Though as I said above it's not really working yet and I don't know why.)
```
wget http://downloads.sourceforge.net/project/qjoypad/qjoypad/QJoyPad-4.0/qjoypad-4.0.0.tar.gz?use_mirror=voxel
tar -zxvf qjoypad-4.0.0.tar.gz
sudo aptitude install build-essential
sudo aptitude install libqt4-dev
sudo aptitude install libxtst-dev

(cd into qjoypad-4.0.0/src)

./config
make
sudo make install
```

---

### Post by floatingworld on 2009-09-11
Got it - someone had already run into this problem four years ago and posted a bug at SourceForge about it:

[http://sourceforge.net/tracker/?func=detail&aid=1112317&group_id=98952&atid=622621]("http://sourceforge.net/tracker/?func=detail&aid=1112317&group_id=98952&atid=622621")

The "Joystick Calibrator" package evidently interferes with the axes in many different applications, so my problem was due to having that open for reference when I was setting up the QJoyPad layout.  I had to close it and then reboot my system and then everything in QJoyPad worked.

---

### Post by stevo1977 on 2010-05-26
I followed the steps described, but when I try to ./config I get "Error: you need at least Qt version 4.2 to use this program"

How do I check what version I currently have?  Why doesn't libqt4-dev include the latest one?  Is there something else wonky that's preventing success?  Thanks for your help.

stevo

---

### Post by Junkieman on 2010-11-23
I also got this error even after [ installing the QT dev kit]("http://qjoypad.sourceforge.net/doc/c64.html#AEN66").

I then ran **sudo apt-get install libqt4-dev** as floatingworld said, ./configure picked up qmake fine, compiled!

Now to figure out how to move the binary from my dev PC to the netbook.

---

