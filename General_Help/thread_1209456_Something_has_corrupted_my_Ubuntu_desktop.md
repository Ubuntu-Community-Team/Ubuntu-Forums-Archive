---
title: "Something has corrupted my Ubuntu desktop"
date: 2009-07-10
forum: General Help
---

### Post by shelbyvision on 2009-07-10
This happened after rebooting after installing several updates; I don't know if it's related. My system has been downgraded to something that looks more like a gnome desktop rather than Ubuntu, like gparted. My touchpad has been set to tap to select mode, which is so sensitive I can't navigate across the screen without inadvertently selecting things. But when I go to System/Preferences/Mouse, there is no way to change it. Also, it's not possible to change appearance of the desktop. All windows have a stripped top bar: no buttons for closing, minimizing, etc. and any text that would be much right of center is missing. Many things work normally, but clicking on menu items causes a very long wait for something to happen, and trying to change workspaces is like pulling teeth. Is there any way to fix this problem, short of completely re-installing Ubuntu?
Thank you,
Steve
Computer: HP Omnibook xe4400s, P4 2GH, 512 MB RAM
OS: Ubuntu Hardy Heron 8.04

---

### Post by shelbyvision on 2009-07-11
bump

---

### Post by carml on 2009-07-11
Can you give as a screenshot or more info about your system?

---

### Post by shelbyvision on 2009-07-11
Yes, here's a screenshot. Notice the top menu bar, ho many of the icons are different from normal, and in the open window, the lack of buttons on the top bar. Also, the whole color scheme was changed, from orange tones to blue. The directory has folders mixed in with files, which it won't let me change. I also had a background picture, which was replaced by a plain orange blank, and it jumbled my desktop icons on top of one another.

---

### Post by carml on 2009-07-11
It seems to be 8.10 0r 9.04,are you sure you didn't tell the system to perform a full upgrade?

---

### Post by shelbyvision on 2009-07-11
No, I didn't perform a full upgrade. Here are the updates I installed before everything went haywire:

Upgraded the following packages:
base-files (4.0.1ubuntu5.8.04.4) to 4.0.1ubuntu5.8.04.7
libnm-glib0 (0.6.6-0ubuntu5.8.04.1) to 0.6.6-0ubuntu5.8.04.2
libnm-util0 (0.6.6-0ubuntu5.8.04.1) to 0.6.6-0ubuntu5.8.04.2
libpurple0 (1:2.4.1-1ubuntu2.4) to 1:2.4.1-1ubuntu2.5
libtiff4 (3.8.2-7ubuntu3.1) to 3.8.2-7ubuntu3.2
libvlc0 (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2) to 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.3
linux-headers-2.6.24-24 (2.6.24-24.53) to 2.6.24-24.55
linux-headers-2.6.24-24-generic (2.6.24-24.53) to 2.6.24-24.55
linux-image-2.6.24-24-generic (2.6.24-24.53) to 2.6.24-24.55
linux-libc-dev (2.6.24-24.53) to 2.6.24-24.55
linux-restricted-modules-2.6.24-24-generic (2.6.24.17-24.1) to 2.6.24.18-24.1
linux-restricted-modules-common (2.6.24.17-24.1) to 2.6.24.18-24.1
network-manager (0.6.6-0ubuntu5.8.04.1) to 0.6.6-0ubuntu5.8.04.2
pidgin (1:2.4.1-1ubuntu2.4) to 1:2.4.1-1ubuntu2.5
pidgin-data (1:2.4.1-1ubuntu2.4) to 1:2.4.1-1ubuntu2.5
vlc (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2) to 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.3
vlc-nox (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2) to 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.3
vlc-plugin-pulse (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2) to 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.3

---

### Post by philinux on 2009-07-11
Open a terminal and try this for starters.

```
metacity --replace
```

---

### Post by carml on 2009-07-11
Maybe you can go back to your previous theme by right clicking on the desktop and selecting Set desktop background (should be so,mine is in italian :) ).

---

### Post by shelbyvision on 2009-07-11
> **philinux said:**
> Open a terminal and try this for starters.

```
metacity --replace
```

OK, I tried that, it didn't seem to do anything. What's it supposed to do?
Steve

---

### Post by shelbyvision on 2009-07-11
> **carml said:**
> Maybe you can go back to your previous theme by right clicking on the desktop and selecting Set desktop background (should be so,mine is in italian :) ).

Nothing happens when I try to change the background. This appearance thing is just a symptom of a much larger problem.

---

### Post by carml on 2009-07-11
I meant that from there you can choose also your theme look,but don't know if it helps anyway.

---

### Post by shelbyvision on 2009-07-11
I re-installed metacity with synaptic, and since I restarted the computer, the windows now have a normal bar at the top. That's all that changed. That's a good start. The BIG problem is the behaviour of the touchpad, and especially the way that any click on a menu item requires a very long wait until anything happens. Maybe there some things for those problems that should be re-installed?

---

### Post by shelbyvision on 2009-07-12
I was able to fix one more thing: the touchpad. I reinstalled gsynaptics, and installed gsynaptics-mcs-plugin, then had to add a line to xorg.config. That gives me a way to adjust the behaviour of the touchpad, like getting rid of that annoying tap mode.
I still have the biggest and most perplexing problem: every time a menu item is clicked, instead of getting instant results, it takes several seconds. since a lot of processes require many menu clicks, this makes things v-e-r-y  s-l-o-w . For some reason, anything clicked WITHIN A WEB PAGE works with normal speed. The same goes for working within Thunderbird email. This is probably a clue, but I don't understand it. :confused:
Steve

---

### Post by carml on 2009-07-12
Did you try to choose on boot the recovery mode? If you have got only Ubuntu press Escto open the menu of kernels on boot and choose Recovery,so you can check for brken packages and attempt to repair them.

---

### Post by shelbyvision on 2009-07-12
No, I haven't, but I have used synaptic to look for broken packages, and it showed none. Would recovery mode give different results?
Steve

---

### Post by VastOne on 2009-07-12
> **shelbyvision said:**
> No, I haven't, but I have used synaptic to look for broken packages, and it showed none. Would recovery mode give different results?
Steve

Since there was a kernel update, can you boot into your previous kernel and tell us the results there?

---

### Post by shelbyvision on 2009-07-12
> **VastOne said:**
> Since there was a kernel update, can you boot into your previous kernel and tell us the results there?

I tried the previous kernel (2.6.24-23) and the one before that (2.6.22-16), no difference. I also tried 2.6.24-24 recovery mode, and tried fix broken packages, and nothing changed. :(
Steve

---

### Post by carml on 2009-07-13
Maybe yes,the recovery option checks all the dependences and fix the broken packages if there are any.

---

### Post by shelbyvision on 2009-07-13
Well, I tried it and it didn't change anything.
Steve

---

