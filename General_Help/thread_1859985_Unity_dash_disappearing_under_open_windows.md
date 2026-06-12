---
title: "Unity dash disappearing under open windows"
date: 2011-10-14
forum: General Help
---

### Post by DottorBartolo on 2011-10-14
Hi!

I have just installed Ubuntu 11.10 and I'm struggling with the Unity desktop. When I click on the dash, the dialogue panel opens BEHIND the open windows (so it's quite useless unless I minimize the windows are superimposing on that).
Does anybody know how to make this dialogue windows appear on the top of pre-existing ones?
Thanks

---

### Post by cogcog on 2011-10-14
I have the same issue. Very annoying! I tried playing with the compiz settings manager (ccsm) but couldn't see anything obvious.

Some more information: if you run
unity --reset
in the terminal, the problem goes away. But then it comes back at the next log in, of course.

---

### Post by cerda on 2011-10-15
Same problem here. It's annoying, can't remember having this problem in 11.04.

---

### Post by rtud on 2011-10-15
Same here

---

### Post by tjwilliams on 2011-10-17
I too have this problem .... on one machine I get this problem on the other 2 I installed it on Unity Dash works perfectly .... very odd. If I click on where I believe the icons should be the applications open .... so it may be that the 'opacity' is set to zero. The unity bar shows up as it should. Any clues ??

---

### Post by DottorBartolo on 2011-10-17
I also have got this problem on one machine but not on another... Still a mystery then?
Following cogcog's advice (running "unity --reset") and even re-starting the machine, though, the problem disappeared. Not sure why it works, and not an ideal answer, I know, but while waiting for something better, that might do...

---

### Post by Tails9 on 2011-10-19
Same here.

---

### Post by quazi on 2011-10-19
Same issue, same workaround. 

11.10 32-bit w/ Intel Graphics.

---

### Post by bbrg548 on 2011-10-19
Unfortunately, this is a known issue that seems to have been popping up frequently in 11.10 since at least the beta2 testing. I've found four variations on this in LaunchPad with just a cursory search.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/801351](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/801351)
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/859405](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/859405)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/843679](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/843679)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/831466](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/831466)

As far as I can tell, there hasn't been a confirmed fix released for any of these bugs.

Sadly, the only advice I can offer is to add yourself to the "this affects me" numbers for the appropriate bugs.

I'm running Oneiric as my main OS because I'm a tinkerer, but I have to say that it's not really ready for general release. It should instead be considered a "Beta 3" release. :sad:

Hopefully, they'll have these bugs ironed out by the time 12.04 is released.

---

### Post by a_rojilla on 2011-11-29
Same here. It happens from time to time. Really annoying.

Alt+TAB switcher is also behind the windows so the best way I have found to live with this is to show the desktop with Ctrl+Alt+D (BTW, in 11.04 you could show the desktop with Super+D, not sure why they changed this for 11.10).

---

### Post by zinigor on 2011-12-02
It seems that there is a quick solution to fix this problem when it appears. If you are using Firefox, the description of [this bug]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/801351") suggests you to switch it to full-screen mode by pressing F11 and then switching back to windowed mode.

It worked for me right now, don't know if the problem will appear again.

---

### Post by OrangeCrate on 2011-12-02
Install the Compiz Configuration Settings Manager package from the Software Center. Then open the Compiz dialog through Dash, and scroll down to the Ubuntu Unity Plugin. Then, find - Behaviour > Hide Launcher, and change the setting from Dodge Windows, to Never.

---

### Post by cottfcfan on 2011-12-02
I had the same problem.
Make sure that using Gnome-tweak-tool in the Desktop section, The "have file manager handle the Desktop" is switched to "on".
My problem seemed to disappear after that.

---

