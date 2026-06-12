---
title: "Problems installing MythTV"
date: 2010-03-18
forum: General Help
---

### Post by Lucky75 on 2010-03-18
Hi,

I have an Diamond TV Wonder 650 Theater USB TV Tuner Card which I want to use on my ubuntu machine. I was under the impression that at least basic TV-watching functionality will work for it?

And I seem to be having issues installing the packages.

```

sudo apt-get install mythtv

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythtv: Depends: mythtv-frontend (= 0.22.0+fixes22594-0ubuntu1) but it is not going to be installed
          Depends: mythtv-backend (= 0.22.0+fixes22594-0ubuntu1) but it is not going to be installed
E: Broken packages

```

Any suggestions? Running Karmic with GNOME.

Thanks!

---

### Post by Lucky75 on 2010-03-19
bump

---

### Post by Lucky75 on 2010-03-19
bump

---

### Post by lyall on 2010-03-19
open **Synaptic Package Manager** and install it from there
it will get all the packages it needs

then test MythTv
if you need/want more add ins for MyhtTV install them also from **Synaptic Package Manager**


also see the following thread for  **Become famous, post your MythTV related How-to's here**
[http://ubuntuforums.org/showthread.php?t=751719]("http://ubuntuforums.org/showthread.php?t=751719")

good luck and have fun learning

---

### Post by Lucky75 on 2010-03-20
Thanks for the reply.

Unfortunately, I can't install it through synaptic either.

```

mythtv:
 Depends: mythtv-frontend but it is not going to be installed
 Depends: mythtv-backend but it is not going to be installed

```

So then I tried to install all 3 at the same time...

```

mythtv:
 Depends: mythtv-frontend but it is not going to be installed
 Depends: mythtv-backend but it is not going to be installed

mythtv-frontend:
 Depends: libmyth-0.22-0 but it is not going to be installed

mythtv-backend:
 Depends: mythtv-transcode-utils but it is not going to be installed
 Depends: libmyth-0.22-0 but it is not going to be installed


```

And again, still another problem when I try to install all of those:

```

mythtv:
 Depends: mythtv-frontend but it is not going to be installed
 Depends: mythtv-backend but it is not going to be installed

mythtv-frontend:
 Depends: libmyth-0.22-0 but it is not going to be installed

mythtv-backend:
 Depends: mythtv-transcode-utils but it is not going to be installed
 Depends: libmyth-0.22-0 but it is not going to be installed

libmyth-0.22-0:
 Depends: nvidia-185-libvdpau but it is not going to be installed

mythtv-transcode-utils:
 Depends: libmyth-0.22-0 but it is not going to be installed


```

Any suggestions? Perhaps because I'm using different nvidia drivers? I'd prefer not to use 185. Thanks!

---

### Post by Lucky75 on 2010-03-20
bump

---

### Post by Lucky75 on 2010-03-21
up

---

### Post by Lucky75 on 2010-03-22
bump

---

### Post by cgroza on 2010-03-22
Maybe if you try:
sudo apt-get install -f mythtv

---

### Post by Lucky75 on 2010-03-22
that sounds like a bad idea ;) Is there any way to do it other than brute forcing the install?

---

### Post by markackerman8@gmail.com on 2010-03-23
I am having the same problem with a fresh install of 9.10, anyone have a solution?

---

### Post by Jason Peters on 2010-03-23
I'm having the same problem.  I am configuring a new 9.10 installation on a brand new Meerkat Ion box.  The nvidia 185 driver it shipped with were not displaying properly on my TV.  

I saw this: [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978), but I'm hesitant to completely remove the 185 nvidia drivers before installing the 190.  

Will Ubuntu just use a generic driver after the removal and restart?

---

### Post by Lucky75 on 2010-03-23
up

Edit: Oops, didn't see the 2nd page.

---

### Post by Directive 4 on 2010-03-23
umm, i you really want myth then, good luck....

however there are a lot of other programs that will let you watch and record live tv

lots of them are a lot simpler than myth (ie very little setup)

just enter tv into the software center and have a play around.

imo myth is way overrated

---

### Post by Lucky75 on 2010-03-23
Ok, thanks. Any suggestions though? Preferably one that works with the ATI tv tuner card?

---

### Post by markackerman8@gmail.com on 2010-03-23
i WAS HAVING THE SAME PROBLEMS WITH A fresh install of ubuntu last night.  After trying so many driver changes to my video card with the unsolvable dependendencies, I figured it might be from a messy install as I had first installed alot from a (TO do after install list) with over 20 added repositories.  Well finally I decided to do a fresh install just with the basic repositories enabled, 1 update, install the propietary nvidia 185 driver reboot, 1 more update and then installed mythtv without a hitch. ... phewwww ...  I hope that helps, now just to get a signal from my hvr-950Q!!!!!!!

---

### Post by Lucky75 on 2010-03-23
Yeah, reverting back two drivers ago isn't exactly what I would call a solution though :)

---

### Post by Lucky75 on 2010-03-24
bump

---

### Post by Lucky75 on 2010-03-24
up

---

### Post by Lucky75 on 2010-03-25
up

---

### Post by markackerman8@gmail.com on 2010-03-25
I have found a way to get the latest nvidia driver, vdpau, and mythtv to work on Ubuntu, with alot of searching, here it is and I hope it helps.  And by the way this is from a fresh and updated install (again...arghhh)

wget [http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key](http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key) && sudo  apt-key add ubuntu-repos.key && rm ubuntu-repos.key
• echo "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) karmic release" |  sudo tee /etc/apt/sources.list.d/avenard.list
• wget [http://www.avenard.org/files/ubuntu-repos/release/libvdpau1_0.3-0ubuntu1_amd64.deb](http://www.avenard.org/files/ubuntu-repos/release/libvdpau1_0.3-0ubuntu1_amd64.deb)
• sudo dpkg --force-all -i libvdpau1_0.3-0ubuntu1_amd64.deb
• sudo apt-get update
• sudo apt-get -f install
&#8728; Now you can upgrade to the newer nvidia packages.
&#8728; sudo apt-get install nvidia-glx-195 nvidia-195-libvdpau nvidia-195-kernel-source

now install mythtv if it isn't already .  Good Luck :)

---

### Post by markackerman8@gmail.com on 2010-03-26
An if anyone can help me with my MythTV and HVR-950Q Installation Woes I would sure appreciate it. 

You might see from my previous threads that I am really trying hard, (for 1 1/2 years and now with a new card) but I am still a stupid newbie it seems. The basic problem is trying to watch live TV with MythTV and my new card; the HVR-950Q, (it works with TVTime!) It seems to have time-out issues though that should be solved with the fact that I stopped it from powering off. Up to this point in my many attempts I have unwittingly recorded live TV and viewed the recordings, can peruse channel listings, but NEVER have been able to watch Live TV. And right now nothing is working!

Just recently
- I re-installed Ubuntu (migrated to Opensuse for 2 months and am back to Ubuntu now) as I was having driver and vdpau issues. Now
I have NVidia 195.xx drivers, vdpau, and myth all installed seemingly
happy (not an easy task).

1/And what the heck is vdpau anyway? (in layman terms?)

- I re-installed v4l-dvb and FINALLY did so without error. (a common
problem with a bug in one of the drivers - removed it and it compiled)
(not my distros fault!)

- I set-up mythfrontend and backend and mysql as before (my tuner card
settings were and are fine I think), though my local name had issues
and I have reverted to the 127.0.0.1, though eventually I want it to
be my IPaddress as I want to use another computer as frontend as well)

- and after receiving errors as mentioned below I changed my
mythconverg user/password from mythtv/mythtv to my login name and
password: (ack/##) - though I don't know if this was smart...

2/ Is that ok or should I put it back to user/password: mythtv/mythtv

- anyway that is where I am at; Could anyone please help this
troubleshooting nightmare with any suggestions ... at this point I am
bamboozled! and a little guidance would go a long way!!

3/ Please ask some questions, and I will reply!

This is the frontend complaints when selecting "Watch LiveTV"

2010-03-26 16:33:09.439 MythContext: Connecting to backend server:
127.0.0.1:6543 (try 1 of 1)
2010-03-26 16:33:09.440 Using protocol version 50
2010-03-26 16:33:09.570 Spawning LiveTV Recorder -- begin
2010-03-26 16:33:16.570 MythSocket(298d190:50): readStringList: Error,
timed out after 7000 ms.
2010-03-26 16:33:16.570 RemoteEncoder::SendReceiveStringList(): No response.
2010-03-26 16:33:16.570 Spawning LiveTV Recorder -- end
2010-03-26 16:33:16.571 GetEntryAt(-1) failed.
2010-03-26 16:33:16.572 EntryToProgram(0@Wed Dec 31 16:00:00 1969)
failed to get pginfo
2010-03-26 16:33:16.572 TV Error: HandleStateChange(): LiveTV not
successfully started
2010-03-26 16:33:16.572 We have a RingBuffer
2010-03-26 16:33:16.623 TV Error: LiveTV not successfully started
2010-03-26 16:33:16.626 ScreenSaverX11Private: DPMS Deactivated 1
2010-03-26 16:33:16.626 ScreenSaverX11Private: DPMS Reactivated 1

---

### Post by Flaming_Amarant on 2010-04-01
Hello,

you said that your card is working with TVTime, so it looks like you have some mythtv configuration problems. When you open TVTime, which device is opened? /dev/video0 ?

You need to check in the MythTV backend setup that when you add your card it uses that same device, and then you need to check that configuration.

What about channel scanning in the backend... does it work?

and by the way, why not installing directly the Mythbuntu distribution? It has made me very happy :-)

---

### Post by Lucky75 on 2010-04-03
> **markackerman8@gmail.com said:**
> I have found a way to get the latest nvidia driver, vdpau, and mythtv to work on Ubuntu, with alot of searching, here it is and I hope it helps.  And by the way this is from a fresh and updated install (again...arghhh)

wget [http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key](http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key) && sudo  apt-key add ubuntu-repos.key && rm ubuntu-repos.key
&#8226; echo "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) karmic release" |  sudo tee /etc/apt/sources.list.d/avenard.list
&#8226; wget [http://www.avenard.org/files/ubuntu-repos/release/libvdpau1_0.3-0ubuntu1_amd64.deb](http://www.avenard.org/files/ubuntu-repos/release/libvdpau1_0.3-0ubuntu1_amd64.deb)
&#8226; sudo dpkg --force-all -i libvdpau1_0.3-0ubuntu1_amd64.deb
&#8226; sudo apt-get update
&#8226; sudo apt-get -f install
&#8728; Now you can upgrade to the newer nvidia packages.
&#8728; sudo apt-get install nvidia-glx-195 nvidia-195-libvdpau nvidia-195-kernel-source

now install mythtv if it isn't already .  Good Luck :)

All that did was break my packages. Now what? I can't even remove it because there's a newer version installed, and if I try and remove it, it tries to remove a whole bunch of other files. I already have the nvidia drivers installed, anyway. Surely there's a way to install this thing without forcing it and breaking all sorts of dependencies and packages?

---

### Post by markackerman8@gmail.com on 2010-04-05
> **Flaming_Amarant said:**
> Hello,

1/ you said that your card is working with TVTime, so it looks like you have some mythtv configuration problems. When you open TVTime, which device is opened? /dev/video0 ?

2/ You need to check in the MythTV backend setup that when you add your card it uses that same device, and then you need to check that configuration.

3/ What about channel scanning in the backend... does it work?

4/ and by the way, why not installing directly the Mythbuntu distribution? It has made me very happy :-)

Thanks a lot for your interest Flamer, haha. Here are the answers to your questions, I hope it helps.

1/ for TVtime to work I had to force it to use my Tuer cards analog video location of /dev/video1, as /dev/video0 is the location of my cam

2/ I am quite sure that my backend setup is at least mostly correct. Here are some related inputs
in General:  TV format - NTSC,  Channel Freq.Table - US Cable.
in Capture Card Setup:  Card Type - Analog-V4L,  Video Device - /dev/video1,  Probed Info is my card - Hauppauge HVR950Q [AU0828],  Audio Device - /dev/dsp?????,  Audio Sampling Rate - None???,  Default input - Television

3/ for NTSC I don't believe I can scan.  I use "ScheduleDirect.org" which offers to "Fetch" the channels, and that works fine for my local cable I believe

4/ and w.r.t Mythbuntu, I use this computer as my desktop mainly and need the normal Ubuntu.  I have just recently read that aft4er installing Mythbuntu you can install Ubuntu on top and have the best of both worlds.  Is that true?   But since I believe I am close to having it configured correctly wouldn't it be pointless?

---

### Post by markackerman8@gmail.com on 2010-04-05
> **Lucky75 said:**
> All that did was break my packages. Now what? I can't even remove it because there's a newer version installed, and if I try and remove it, it tries to remove a whole bunch of other files. I already have the nvidia drivers installed, anyway. Surely there's a way to install this thing without forcing it and breaking all sorts of dependencies and packages?

I wish I could be of some help.  All I know from my experience at the ugly point your computer is at, is that reinstalling Ubuntu, Updating it then doing the aforementioned steps worked for me.   I know its stupid to have to reinstall but thats what worked for me and saved time in the end.  I would love to hear a simpler version.  I wish I could be of more help.

---

### Post by Lucky75 on 2010-05-05
Just thought I would post here with the answer:

> **superm1 said:**
> Then you have the nvidia vdpau PPA activated probably.  You need to enable Mythbuntu autobuilds to get a build that works with that ([http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds))



[http://ubuntuforums.org/showthread.php?t=1446112](http://ubuntuforums.org/showthread.php?t=1446112)

---

