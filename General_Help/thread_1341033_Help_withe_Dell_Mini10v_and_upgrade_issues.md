---
title: "Help withe Dell Mini10v and upgrade issues"
date: 2009-11-29
forum: General Help
---

### Post by mrdfield on 2009-11-29
Hello, I purchased a dell mini 10v with the Dell / Ubuntu 8.04 netbook remix installed.
I am not fond of the Dell OS so I did a clena install of Ubuntu 9.04 desktop, this seemed towork fine except there was no sound only thru headphones , When 9.10 was released I did a clean install of the netbook remix version .I only know had no sound but I was unable to get wifi working as the tab or shortcut was grayed out on the top toolbar I tried to accesss it thru system but when I scrolled down the tab would not let me as it would return to the top,Also when opening a window such as the wirelees connection the tab I belive is the third one when clicking on it to open it it would jump back to the first not allowing me acess.
and again no sound.
Also when opening any other types of windows they behave strange any suggestions woulb appreaciated  .
Right now I reinstalled the dell/ubuntu 8.04  netbook remix and everything is fine ,but i would really like 9.10 if possiable thank you

---

### Post by Brandon Williams on 2009-11-29
You'll get better information if you search/post in the [Dell Ubuntu Support](http://ubuntuforums.org/forumdisplay.php?f=342) forum. You can also find a lot of useful information [here](http://www.ubuntumini.com/), [here](http://groups.google.com/group/UbuntuMini), and [here](http://www.mydellmini.com/forum/). Answers to your questions can be found in each one of those locations.

IIRC, the most common solution to the sound problem on 9.04 is to open the gnome mixer app, make sure that the speaker channel is visible and unmuted, and then raise the volume for the speaker channel to 100%. On my 10v running 9.10, I've never had a sound problem that wasn't associated with pulseaudio (it doesn't play well with Xfce), and the mixer doesn't show all the controls that it showed in 9.04, so there is no separate speaker channel for me to adjust.

The problems you describe controlling windows sound like the typical touchpad issues on the 10v. These went away for me with Karmic due to the default settings for JumpyCursorThreshold and AreaBottomEdge. You can check whether you've got the right setting from the command line:
```
$ synclient -l | grep -e JumpyCursorThreshold -e AreaBottomEdge
    AreaBottomEdge          = 4100
    JumpyCursorThreshold    = 90
```

To get wifi on 9.10, you'll need to connect with ethernet and then 'sudo apt-get install bcmwl-kernel-source'. After that, the broadcom driver should show up in the 'Hardware Drivers' configuration gui.

---

