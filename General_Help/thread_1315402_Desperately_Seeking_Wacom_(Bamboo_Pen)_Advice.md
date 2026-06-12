---
title: "Desperately Seeking Wacom (Bamboo Pen) Advice"
date: 2009-11-05
forum: General Help
---

### Post by one.finefellow on 2009-11-05
I recently upgraded to Karmic and purchased a Wacom Baboo pen tablet. While everything is working great with Karmic the tablet has yet to function. So far I've downloaded and installed the .tar file from the Linux Wacom project, I've installed the xserver.xorg and tools packages and I've edited the xorg.conf file. I still can't get the tablet to work. Any help/advice would be appreciated.

Also, I'm posting in the General Help because I'm not sure which more specific forum, if there is one, would be better.

---

### Post by phillw on 2009-11-05
> **one.finefellow said:**
> I recently upgraded to Karmic and purchased a Wacom Baboo pen tablet. While everything is working great with Karmic the tablet has yet to function. So far I've downloaded and installed the .tar file from the Linux Wacom project, I've installed the xserver.xorg and tools packages and I've edited the xorg.conf file. I still can't get the tablet to work. Any help/advice would be appreciated.

Also, I'm posting in the General Help because I'm not sure which more specific forum, if there is one, would be better.


Hi,

there is a wiki entry over here --> [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

An active thread is over here -->  [http://ubuntuforums.org/showthread.php?t=1290251](http://ubuntuforums.org/showthread.php?t=1290251)

Hope that helps,

Phill.

---

### Post by miniyak on 2010-02-16
I just got a bamboo pen... thinking it might just work out of the box like my tablet...

guess not, lol

did you ever get your bamboo pen working one.finefellow?
You have the ctl-460 right?

I just tried one the solutions in one of the links phillw provided

unfortunately i got kinda lost in the context of all the CLI stuff and definitely missed something along the way. The .fdi file wouldn't go in the right folder via bash so i did it with nautilus as admin.. then I wasn't too sure what exactly i was suppose to be editing inside of it but i copied and pasted something anyway that seemed to make sense...

I probably should return that pad and wait till something gets packaged... But I really want to figure this out. 

Can someone help me take some babysteps with the ctl-460 in particular? I can recap the steps that i was successful with. I've mainly been following this [post]("http://ubuntuforums.org/showpost.php?p=8262965&postcount=541") I should also note that I'm using 64-bit karmic

---

### Post by Favux on 2010-02-16
Hi miniyak,

Kingeri's post should work.  But the LWP just included working Bamboo Pen support in their 0.8.5-10 release!  No patching needed, just compiling.

So maybe a fresh look?  See Ayuthia's [HOW TO]("http://ubuntuforums.org/showpost.php?p=8283168&postcount=1") on the other P & T thread.  If you want a little more information about what you are doing see this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  And it sounds like you already have the link to [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384").

Good luck!

---

### Post by one.finefellow on 2010-02-16
> **Favux said:**
> Hi miniyak,

Kingeri's post should work.  But the LWP just included working Bamboo Pen support in their 0.8.5-10 release!  No patching needed, just compiling.

So maybe a fresh look?  See Ayuthia's [HOW TO]("http://ubuntuforums.org/showpost.php?p=8283168&postcount=1") on the other P & T thread.  If you want a little more information about what you are doing see this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  And it sounds like you already have the link to [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384").

Good luck!

Somehow the first HOW TO link got my tablet working. Awesome!

Thanks, Favux.

;)

---

### Post by miniyak on 2010-02-16
Bam! its working, after compiling the 0.8.5-10 beta

Thanks Fuvux

This was my first time compiling something where I really had good idea of what I was doing...learn something new everyday. I've been using linux for 3 years and have completely relied on the packaging system. haha

That said im sure a lot of ubuntu users in particular are intimidated by the compiling process, because of the fact that it has been mostly abstracted away with synaptic and the "software center". Of course it makes sense for the LWP to just let the users compile so any distro can take advantage of the drivers. Anyhow, I'm glad its working, may be this is a good reason for me to learn more about the packaging process... I'ld love to avoid the ./configure make make install when i upgrade. I felt like i had did something wrong when the result of "clean" was "can not "clean""... but apparently there is only something to clean when ./configure has been run before

---

### Post by Favux on 2010-02-16
Hi one.finefellow and miniyak,

Great!  Two more Bamboos set up.  :)  Remember because you've compiled linuxwacom the wacom.ko (the usb kernel driver/module) won't be in the directory a new kernel download will create.  The tablet will just stop working.  So you need to copy your compiled wacom.ko back into place in the new directory.

> Of course it makes sense for the LWP to just let the users compile so any distro can take advantage of the drivers.
The odd number versions like 0.8.5 are the development versions.  The default Karmic linuxwacom version is 0.8.4-1, which is a production (stable) one.  Lucid will have Xorg's xf86-input-wacom as the Xserver driver, not the linuxwacom X driver.  The kernel driver will still be linuxwacom.
> I'd love to avoid the ./configure make make install when i upgrade. I felt like i had did something wrong when the result of "clean" was "can not "clean""... but apparently there is only something to clean when ./configure has been run before
That's right.

---

### Post by one.finefellow on 2010-03-06
> **Favux said:**
> Remember because you've compiled linuxwacom the wacom.ko (the usb kernel driver/module) won't be in the directory a new kernel download will create.  The tablet will just stop working.  So you need to copy your compiled wacom.ko back into place in the new directory.


So I missed this, and after updating my software the tablet stopped working. I recomplied the driver to get it going again but was wondering how to copy the compiled wacom.ko back in the new directory (links to appropriate threads would be most appreciated). Thanks for helping a n00b like me.

---

### Post by miniyak on 2010-03-06
Yea, i saw the kernel update and decide to ignore everything.. haha. I think im going to set the update manager to only check for security updates for now on an then just wait for releases for everything else.

one.finefellow, im curious if you have tried getting the eraser 
functionality working? The wacom site seems to point to the functionality being present in the pen.

I've been trying to get the eraser working with gimp and no luck so far. just wondering is this is a user error :D

ive been also having a bunch of other issues with the pen. One i found to be sort of what i would call a issue-feature, where gimp recognizes the mouse and the tablet as 2 separate tools. That is something that i could get used to i guess... but when the tablet in unable to open a new photo and it has to be done w/ my laptops horrid track pad. 

i guess ill be able to do more about it once i really figure out whats going on. sometimes i just have problems like this because i never restart

---

### Post by one.finefellow on 2010-03-06
> **miniyak said:**
> one.finefellow, im curious if you have tried getting the eraser 
functionality working? The wacom site seems to point to the functionality being present in the pen.

ive been also having a bunch of other issues with the pen. One i found to be sort of what i would call a issue-feature, where gimp recognizes the mouse and the tablet as 2 separate tools. That is something that i could get used to i guess... but when the tablet in unable to open a new photo and it has to be done w/ my laptops horrid track pad. 

The eraser never really worked for me. I kind of gave up on it. If I could get into the code I wouldn't mind toying with it, but the xorg.conf is a bit beyond my skills. As for opening a new file I just tap the top button on the broad side of the pen and then navigate the quick menu. Although, I've come to find it's too cumbersome to navigate solely by the pen. I'm still getting used to it but using the pen and the keyboard (plus the mouse to do some additional scrolling) is the easiest way to function.

---

### Post by Qualia on 2010-03-11
cool! Now I can go buy that Bamboo Pen tablet I was saving up for and get it to work on Ubuntu 9.10! :cool: i won't have to use that slow old XP machine after all for it!

---

### Post by Nattydread69 on 2010-03-15
Thanks guys my new bamboo pen works well on ubuntu!
Cheers

---

### Post by Qualia on 2010-03-28
same here! :D That first HOW TO link finally made m pen tablet work!

---

### Post by Rany Albeg on 2010-04-02
removed.

---

### Post by Drayx9293 on 2010-04-19
Favux You are my Hero.  Thank you much for your post.

---

### Post by Favux on 2010-04-19
Hi Drayx9293,

Thank you for the thanks!


Hi everyone,

The eraser should be working.  Just in case you don't already know here are the basics.  It only works in programs that support it.  Make sure in Gimp, or Inkscape, or whatever, you've assigned the extended input devices.  See near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").  Then just like you can assign different tools to the stylus tip you can point the eraser to the littled eraser icon.  Once assigned, Save it.

---

### Post by miniyak on 2010-05-08
ok, now i want to get things working in lucid and have forgotten all the intricate steps to get this puppy working... i dont think what i did the last time will work anyhow

there is way too much info in some of the wacom threads for me to have the time to go through but ill look anyhow. if anyone sees something, please link

---

### Post by Favux on 2010-05-08
Hi miniyak,

All you should need to do is compile linuxwacom 0.8.6-1 for the wacom.ko.  See Section 1 in the [linuxwacom How TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Notice in Lucid there's an extra directory change.  That's so the config doesn't pick up the /src/xdrv directory and make doesn't try to build the X driver which doesn't work with the Xserver 1.7 in Lucid.  So after you copy the wacom.ko in place you just proceed to:
```
sudo depmod -a
```
You don't need to clone xf86-input-wacom.

---

