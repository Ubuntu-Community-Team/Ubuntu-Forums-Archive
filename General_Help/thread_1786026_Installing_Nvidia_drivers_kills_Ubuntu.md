---
title: "Installing Nvidia drivers kills Ubuntu"
date: 2011-06-19
forum: General Help
---

### Post by MG&amp;TL on 2011-06-19
Hi everybody, I hope you can help. :)

Three times so far I have had to re-install ubuntu because I installed an updated or new Nvidia graphics driver for my GeForce FX 5200

The first time, using Natty Narwhal, I installed an updated graphics driver, and upon reboot, I was presented with a blank screen that did nothing. Being a first-time Ubuntu user, I assumed it was me, or a bug in the new release.

So I burnt a Lucid Lynx cd on another pc, and installed that instead. Same problem when I installed a new graphics driver, again via Admin>>Hardware Drivers. Reboot yielded a blank screen.

Booted from cd again, as I had no files yet to worry about, and everything seemed to be fine, providing I stayed away from that tempting hardware drivers button.

I then accidentally installed a new driver when installing the dependencies(via terminal) for OGRE (Object-Oriented Graphics Rendering Engine) This time, my terminal froze, Firefox wouldn't boot, and a reboot yielded a blinking, blank login screen that did not do anything.

Obviously, I'd like to have a graphics driver, as currently I can't run anything that needs 3d acceleration (Games, 3d simulations, even Desktop effects), but it's not absolutely necessary. So if nobody can suggest a fix, short of a new computer, new graphics card etc, can anybody suggest a way that I can stop myself accidentally installing anything driver-ish?

The driver worked fine on windowsXP, but there's two reasons I'm not going back to that:
a) I hate it. Hate, hate, hate.
b) I've lost the activation key that came with computer, so I can't reinstall.

Further detail can be provided on request.

Computer is Dell Dimension 2400, 256Mb RAM, Hard drive is almost empty. Old and slow, but I like it.

If anybody can help me at all, you will have eternal gratitude:D

---

### Post by dragonfly41 on 2011-06-19
Can't help you with your driver problem but ..

> I've lost the activation key that came with computer, so I can't reinstall.on my Dell Inspiron the windows activation key is stuck on a label underneath the Dell.

Attached is a snapshot of my unactivated drivers - ubuntu 10.10


[EDIT]

You might try the tips here in posts #3 and #7

[http://ubuntuforums.org/showthread.php?t=1785336](http://ubuntuforums.org/showthread.php?t=1785336)

> 
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update


---

### Post by MG&amp;TL on 2011-06-19
Thanks dragonfly-will try the posts mentioned...Good idea about the Dell, I looked on the sides and back, but I never looked at the bottom. Sadly, it's not there either:(

I'm not sure what the point of the thumbnail was...did you mean 'I get mine from here', in which case, so do I.

---

### Post by CodyLoco on 2011-06-19
> **MG&TL said:**
> Thanks dragonfly-will try the posts mentioned...Good idea about the Dell, I looked on the sides and back, but I never looked at the bottom. Sadly, it's not there either:(

I'm not sure what the point of the thumbnail was...did you mean 'I get mine from here', in which case, so do I.

Is it a white-label desktop computer?  If so sometimes they put the sticker INSIDE the computer, as in, on the inside of the side panel.  If not, they probably left the sticker stuck to the original Win XP manual.  Either way, XP is fairly easy to install w/o a key - no shame if you know you do have a legit key already purchased...

---

### Post by MG&amp;TL on 2011-06-19
UPDATE:

Tried the repository/PPA referenced by dragonfly, IT HAS NOT CRASHED (yet) :P Thank you!

However, desktop effects, (what I'm currently using to test it) throws error: "desktop effects could not be enabled"
The ubuntu loading screen was abnormally large, if that helps, it shows a  green screen a couple of seconds after the BIOS loading screens, and a  couple of errors too fast to read, something about "phoalp", although I'm not sure about this as it is very fast. It DOES boot though.

Is it likely to be one of the numerous problems surrounding graphics cards/desktop effects, or the same problem, but it's decided not to crash this time?

The hardware drivers window displays a green dot next to "Version 173" and informs me that it is activated and in use. (in use by what?-I'm not using anything 3d at the mo...)

If people think it's a different problem, I'm happy to stamp SOLVED on this thread, or people, ever helpful as they are on this forum, may have a full solution.

---

### Post by MG&amp;TL on 2011-06-19
Thanks for help, Cody.

It's an old, secondhand, computer that was given from a member of family. I didn't look a gift horse in the mouth.

Will try the inside but I will have to be cautious, there is a loose wire somewhere, took it to a computer repair place a couple of times, both times after some rough handling and a bit of a bash, it worked, so I'm just careful not to move it. Taking the side off of it will be...interesting. #-o

Thankyou, any way...will have a careful look on the inside at some point, but as previously mentioned, I've become attached to Linux now. There's no "Access denied" now. :) And since discovering Wine, there's no urgency-most of my windows progs are free.

Also, not having to pay for (Linux)programs is amazing, whoever thought that one up should be a saint in ComputerHeaven...

---

