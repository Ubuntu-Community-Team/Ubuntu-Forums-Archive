---
title: "Nvidia Drivers."
date: 2009-10-22
forum: General Help
---

### Post by nemiux on 2009-10-22
Hey,

I've downloaded my graphics card drivers for linux (NVIDIA-Linux-x86-185.18.36-pkg1.run). I chmod +x it, and I was able to run. The only one problem was:

It asked me to run it as root. Idk how to do it, It automaticlly starts entering scrips, so I dont have time to write su and my psw. Could anyone tell me how to open it? Thank you.

---

### Post by falconindy on 2009-10-22
Do you have a specific reason for wanting to install the 185 driver? Installing video drivers manually requires dismantling and rebuilding a part of your Xorg. If you haven't already, I would recommend installing the 180 driver that's included in the repositories.

Assuming you're on GNOME, go to System (on the main menu) -> Administration -> Hardware Drivers

You should see 2 options listed here relating to nvidia -- version 173 and 180. Pick 180, and let it download and install. You'll need to reboot after its finished to allow it to activate.

---

### Post by DeMus on 2009-10-22
> **nemiux said:**
> Hey,

I've downloaded my graphics card drivers for linux (NVIDIA-Linux-x86-185.18.36-pkg1.run). I chmod +x it, and I was able to run. The only one problem was:

It asked me to run it as root. Idk how to do it, It automaticlly starts entering scrips, so I dont have time to write su and my psw. Could anyone tell me how to open it? Thank you.

Just do this:

From the website: [_nVidia drivers_]("http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers-190/") download these files suited for Jaunty:

```
nvidia-190-kernel-source_190.36-0ubuntu1~jaunty~nvidiavdpauppa1_amd64.deb
nvidia-190-libvdpau_190.36-0ubuntu1~jaunty~nvidiavdpauppa1_amd64.deb
nvidia-190-modaliases_190.36-0ubuntu1~jaunty~nvidiavdpauppa1_amd64.deb
nvidia-glx-190_190.36-0ubuntu1~jaunty~nvidiavdpauppa1_amd64.deb
```

and install them in that order. Save the files to disk and in the mentioned order double-click the deb file which will open gdebi to install the files.
Then after a reboot all will be fine and you have the latest nVidia proprietary driver.

---

### Post by P4man on 2009-10-22
just put 

```
sudo
```

in front of the command to run it with root privileges. However, I agree with falconindy; stick with the drivers offered by "hardware drivers" unless you have a specific reason not to.

---

### Post by Dougie187 on 2009-10-22
> **P4man said:**
> just put 

```
sudo
```

in front of the command to run it with root privileges. However, I agree with falconindy; stick with the drivers offered by "hardware drivers" unless you have a specific reason not to.

Well, there are plenty of reasons not to. I mean personally I haven't had great luck with any of the more modern nvidia drivers in the repositories, but I have had a lot of success from the manual install ones. They are very easy to install and there are plenty of guides for updating them when your kernel changes.

---

### Post by bruno9779 on 2009-10-22
185 drivers installed automatically as an update for me this morning.

I have tried them out with my most graphically demanding apps, and I haven't found any issue.

I couldn't test for too long, but it also seems that temp control on my GPU has gotten a tad better. Just an impression though.

---

### Post by P4man on 2009-10-22
> **Dougie187 said:**
> Well, there are plenty of reasons not to. I mean personally I haven't had great luck with any of the more modern nvidia drivers in the repositories, but I have had a lot of success from the manual install ones. They are very easy to install and there are plenty of guides for updating them when your kernel changes.

Well, you *had* troubles with the default ones apparently, and you know what a kernel update is (and how to fix it). Since the OP isnt aware of the sudo command, I suspect that makes 2 potentially big differences between you and him  ;)

---

### Post by Dougie187 on 2009-10-22
> **P4man said:**
> Well, you *had* troubles with the default ones apparently, and you know what a kernel update is (and how to fix it). Since the OP isnt aware of the sudo command, I suspect that makes 2 potentially big differences between you and him  ;)

I understand, I'm just saying, he's probably asking because he has a reason. I mean would you expect someone who didn't know what sudo was to ask for help manually installing a video driver if he didn't need it?

Also I'm just trying to point out that there are some issues with the drivers for certain cards/people and it's not like the manual drivers are significantly more difficult than the repo ones, granted the repo ones are really easy, and already there, but there are threads in these forums with scripts to auto-update in the event of a kernel upgrade. But as was mentioned earlier installing these doesn't require the user to dismantle their kernel and rebuild it. All the user has to to is ./NVIDIA.sh or what ever.

But I do understand your point.

---

### Post by P4man on 2009-10-22
> **Dougie187 said:**
> I understand, I'm just saying, he's probably asking because he has a reason. I mean would you expect someone who didn't know what sudo was to ask for help manually installing a video driver if he didn't need it?

I figured a recently converted windows user who has a habit of going to websites to download the latest drivers of everything. 

Either way, I guess the OP has the answers whatever the case, not much point arguing the unknown :)

---

### Post by coastkid on 2009-10-25
im a newb at linux. just installed ubuntu on my laptop and came to this forum to find a way to install the latest drivers for my video card.  I am guessing it really is a windows thing to do that.  Well something to get used to.  

I did have success using this thread: [http://ubuntuforums.org/showthread.php?t=1125400&highlight=installing+video+drivers](http://ubuntuforums.org/showthread.php?t=1125400&highlight=installing+video+drivers)

went through the steps and it worked like a champ.

give it a whirl.

Newb

---

