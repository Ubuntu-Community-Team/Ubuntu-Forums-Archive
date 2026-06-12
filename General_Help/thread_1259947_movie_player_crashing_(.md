---
title: "movie player crashing :("
date: 2009-09-07
forum: General Help
---

### Post by sububtu on 2009-09-07
any application that related to video is crashing,I think i badly missed something,,
while i tried to check gstreamer-properties, i selected x window System (No xv), it also got crashed,mine is on-board videochipset(intel xtreme graphics-- on windows)

---

### Post by irockonguitar on 2009-09-07
I'm having this same problem, and I'm completely clueless how to solve it, so I hope you get a response soon!

---

### Post by davidryderuk on 2009-09-08
Hi,
You probably need to know what graphics chip you have in order to get more help with this problem. Go to terminal and run the command "lshw -short". The response will include a reference to the graphics card. 

Additionally if you haven't already done so, you might want to try disabling visual effects (compiz) to see if it makes a difference.

---

### Post by Exodist on 2009-09-08
> **sububtu said:**
> any application that related to video is crashing,I think i badly missed something,,
while i tried to check gstreamer-properties, i selected x window System (No xv), it also got crashed,mine is on-board videochipset(intel xtreme graphics-- on windows)

Whats your graphics card and what driver do you have installed?
Also are you running Compiz?

---

### Post by sububtu on 2009-09-08
82865G Integrated Graphics Controller;
i havnt installed any drivers manually,for my dekstop environments, resolutions its quiet fine; & i noticed one more thing, i was able to play videos in VLC, but not a smooth rendering, i dnt remember which output mode i selected,
And actually im not aware about this COMPIZ-:confused:

---

### Post by davidryderuk on 2009-09-09
Hi,
If you want to turn Compiz off then you can do the following.

1. Go to System > Preferences > Apperance

2. In the newly opened window click on the Visual Effects tab

3. Choose the None option.

Compiz is basically a 3D window decorator which requires good, well supported graphics cards. It looks nice but can be quite slow on some computers. 

Anyway I found a bug report for your problem on launchpad.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/352760](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/352760)

It seems the only confirmed way of fixing the problem is to downgrade to an older version of the Intel graphics drivers. 

[http://webupd8.blogspot.com/2009/05/reverting-xorg-video-intel-driver-of.html](http://webupd8.blogspot.com/2009/05/reverting-xorg-video-intel-driver-of.html)

---

### Post by sububtu on 2009-09-09
my visual Effects tab is already set to "none"
As i mentioned earlier i can play videos in VLC , but if i switch to fullscreen mode its terrible , in windowed mode its fine,,,,

---

### Post by davidryderuk on 2009-09-09
Okay, but you seem to have missed the second half of my message though. Like I said before there is a bug report for your problem on launchpad, the link to which is shown below. 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/352760](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/352760)

The only person on that bug report to have solved the problem seems to have done it by downgrading their Intel video drivers from the 2.6 to 2.4 version. There are instructions for doing this in the following link. 

[http://webupd8.blogspot.com/2009/05/reverting-xorg-video-intel-driver-of.html](http://webupd8.blogspot.com/2009/05/reverting-xorg-video-intel-driver-of.html)

Basically what you have to do to downgrade your video drivers is the following:

1. Open *System > Administration > Software Sources* and click on the "Third Party Software" tab. 

2. Use the "Add" button to add the following two software sources.

```
deb http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
```

3. Close the Software Sources window and open terminal.

4. Import the GPG key for the repository by entering the following command into terminal.

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xce90d8983e731f79
```

4. Then install the older Intel driver by entering the following command into terminal.

```
sudo apt-get update && sudo apt-get install xserver-xorg-video-intel
```

5. After that your computer should have the older Intel video drivers installed. Restart your machine and check the video performance again. 

6. If your video card is working well then you should be able to get Movie player to work with the "X Window System (X11/XShm/Xz)" option (in gstreamer-properties) or with the "XVideo extension video output" option in VLC player.

---

### Post by sububtu on 2009-09-10
i think this one will work!, let me check :)

---

