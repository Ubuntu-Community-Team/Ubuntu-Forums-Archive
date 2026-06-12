---
title: "before buying logitec Touch Mouse M600"
date: 2012-05-14
forum: General Help
---

### Post by IdanSuper on 2012-05-14
before buying Logitech Touch Mouse M600.. is it compatible with ubuntu 12.04? with al the gestures? thanks!

---

### Post by apochry on 2012-05-14
[http://askubuntu.com/questions/110306/can-i-use-the-logitech-touch-mouse-m600](http://askubuntu.com/questions/110306/can-i-use-the-logitech-touch-mouse-m600)

---

### Post by IdanSuper on 2012-05-14
> **apochry said:**
> [http://askubuntu.com/questions/110306/can-i-use-the-logitech-touch-mouse-m600](http://askubuntu.com/questions/110306/can-i-use-the-logitech-touch-mouse-m600)
it's really old.. and I have been saw it.. I want to know if after upgrading to 12.04 it works with all its gestures.. Because I think that I read about the new Ubuntu that it support more touch mouses like apple magic mouse and more..

---

### Post by IdanSuper on 2012-05-15
up!

---

### Post by IdanSuper on 2012-05-20
up!

---

### Post by salinmooch on 2012-11-27
I'm just throwing this info here since this is one of the first findings when searching for support on logitech m600 in ubuntu.

It works fine out of the box, the only negative for me is no middle mouse button (button 2) which can be handy in a unix desktop.

The default swipe commands work fine in browsers and in anything else with a forward/backward option (nautilus, image viewer).  I personally don't find that super useful (for example I tend to open links in new tabs, so I do not use the arrows much in the first place).

I immediately thought it would be cool to use the swipe feature for switching desktops something I do a lot of.  xev finds the swipe feature as 
left swipe = button 8
right swap = button 9

I tried using xinput to remap these "buttons" with no luck.  But I found that [easystroke]("http://sourceforge.net/apps/trac/easystroke/wiki/Documentation") can remap buttons as well as gestures and such.  (as an aside: I had not used easystroke before but it is works well with cinnamon/unity and the gestures are pretty cool).

Its in the 12.10 repositories (probably others)
Do a 
```
sudo apt-get install easystroke
```or try the ppa for the latest version:
```
sudo apt-add-repository ppa:easystroke/ppa
sudo apt-get update
sudo apt-get install easystroke
```Follow the instructions from this [post]("http://ubuntuforums.org/showpost.php?p=10495426&postcount=11")



After setting up your additional buttons (button 8 and 9 - just swipe right or left when asked to enter a mouse button) go to actions and new actions per the post.  I had to try a few times to get it to do the desktop switching commands.

After mapping button 8 and 9 to ctrl+alt+left  and ctrl-alt-right respectively I also mapped a ctrl+right click to a middle mouse button (button 2).  

I turned off the popups in preferences so the swipes work just like the key combinations - it feels very natural to move between desktops this way. 

I also bought a logitech wireless solar keyboard that uses the unifying dongle and found [this post]("https://groups.google.com/forum/?fromgroups=#!msg/linux.kernel/zYS6yddI8yU/9cMvg3k9xTYJ") and [this post]("http://returnfalse.net/log/pairing-logitech-unifying-devices-on-gnulinux/") useful (I copied the code from the first and compiled per the second).  The code allows you to pair multiple devices to one receiver.

Cheers!

---

