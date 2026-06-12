---
title: "VNC - remote desktop does not refresh"
date: 2010-01-17
forum: General Help
---

### Post by ubername on 2010-01-17
Hi

I have just started playing with VNC and after some trial and error I can access the 'remote' machine (actually it is next to the 'local' one). I get to see the display and can move the mouse and 'send' mouse clicks to the remote machine. This has the expected effect on the remote machine but the display on the local machine stays exactly the same. For example, if I click on the icon for google chrome on the desktop of remote machine, chrome starts on that box, but the display on local stays as the desktop. Any Clues?

TIA

---

### Post by spiky001 on 2010-01-17
Hi not sure what you mean do u expect the program to appear on local machine as well as remote machine?

---

### Post by ubername on 2010-01-17
I mean I expect changes on the remote machine to appear in the local machine window of the vnc client. What happens is that the display on the local machine does not change from how the remote machine looked at the moment of accessing via VNC (this is happening with both vinagre and xvnc4viewer by the way)

---

### Post by Ant01 on 2010-01-17
I have a similar problem and made a post [http://ubuntuforums.org/showthread.php?t=1383388]("http://ubuntuforums.org/showthread.php?t=1383388")

The problem I have is that my remote viewer to Ubuntu doesn't work from my laptop. I am not sure if this is as a result of updating the nvidia drivers. (link to post [http://ubuntuforums.org/showthread.php?t=1379251](http://ubuntuforums.org/showthread.php?t=1379251)

I can view remotely but the mouse cursor only works on the ubuntu machine and not my laptop, the screen doesn't change on my laptop once the viewer is loaded in the ubuntu machine so moving the mouse on the laptop moves on the both machines but doesn't control from the laptop.

Secondly the keypad from my laptop works externally, so I can type on my laptop and it shows on the ubuntu machine.

Lastly, the screen on my laptop doesn't change with the ubuntu machine.

---

### Post by B3Nji on 2010-01-17
> **ubername said:**
> Hi

I have just started playing with VNC and after some trial and error I can access the 'remote' machine (actually it is next to the 'local' one). I get to see the display and can move the mouse and 'send' mouse clicks to the remote machine. This has the expected effect on the remote machine but the display on the local machine stays exactly the same. For example, if I click on the icon for google chrome on the desktop of remote machine, chrome starts on that box, but the display on local stays as the desktop. Any Clues?

TIA

I have been experiencing exactly the same problem with a number of releases of Ubuntu. Whether its when I'm using VNC from my iPhone or logging in from another Ubuntu machine. I see no refresh on the client end, but if I watch the machine which I log into I see the mouse move as normal. 

Would be interested if anyone can come up with a fix for this. Very annoying!

---

### Post by Ant01 on 2010-01-17
I got a solution via my post  [http://ubuntuforums.org/showthread.php?p=8678737#post8678737]("http://ubuntuforums.org/showthread.php?p=8678737#post8678737")

Remove the desktop effects via preferences/appearence/visual effects and it sorts the problem out.

---

### Post by JetPack on 2010-02-08
I had the same problem but turning off visual effects on the remote machine did not fix it.

Both machines are running Ubuntu 9.10.

I solved it by installing gnome-rdp on the local machine, along with having visual effects on the remote machine turned off.

I like this viewer better than the default viewer and it seems to be faster.

---

### Post by ubername on 2010-02-14
Removing Desktop Effects worked for me. Marking as 'Solved'

---

### Post by zeezam on 2010-03-17
> **ubername said:**
> Removing Desktop Effects worked for me. Marking as 'Solved'

Worked for me also.
Is there any workaround if I still want to have desktop effects enabled? I'm running Ubuntu 9.10 64 and connecting with VNC from my windows xp laptop.

---

### Post by sailor420 on 2010-04-06
> **ubername said:**
> Removing Desktop Effects worked for me. Marking as 'Solved'

Worked for me as well. Thanks for the tip.

---

### Post by edroshz on 2010-04-28
I just register (and login) for say :

Worked for me as well in KDE. Thanks for the tip. 	

Saludos desde Mexico DF

---

### Post by daddyfix on 2010-04-30
[SOLVED] For me too but was hard to find Visual Effects.

System->Preferences->Appearance->Visual Effects

---

### Post by chiel-s on 2010-06-24
This is not solved, this is just a work-around. I am not going to disable my beautiful desktop effects so I can make use of the remote desktop option.

Any other suggestions?

---

### Post by v_2ryann on 2010-07-30
Here is the answer guys, on how to do it without changing the effects:

1) Open a terminal o press ALT+F2, then run/type: gconf-editor
2) Go to /desktop/gnome/remote_access and enable "disable_xdamage"

I found it found here:
[http://swiss.ubuntuforums.org/showthread.php?t=1496368](http://swiss.ubuntuforums.org/showthread.php?t=1496368)

---

### Post by jeffrash on 2010-10-05
This worked for me.  Thanks for the real fix v_2ryann.

---

### Post by alanh on 2010-11-19
Many thanks for this - much appreciated.  I have been having the same problem with 9.10.

Alan

---

### Post by gildedtiger on 2010-12-07
Beautiful, thanks very much!

Now I have the best of both worlds.  ;)

---

### Post by bemental on 2011-02-20
> **ubername said:**
> Removing Desktop Effects worked for me. Marking as 'Solved'

Worked for me as well, but now I get a "trailing effect" of gray boxes (mouse cursor sized) on the remote screen in the VNC window.


Hmph.

---

### Post by drevicko on 2011-03-20
> **v_2ryann said:**
> Here is the answer guys, on how to do it without changing the effects:

1) Open a terminal o press ALT+F2, then run/type: gconf-editor
2) Go to /desktop/gnome/remote_access and enable "disable_xdamage"

I found it found here:
[http://swiss.ubuntuforums.org/showthread.php?t=1496368](http://swiss.ubuntuforums.org/showthread.php?t=1496368)

Thanks v_2ryann, works nicely (:
I eventually found this bug on the problem:
 [INDENT] [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126)[/INDENT]
Looks like only the AMD fglrx driver remains unfixed

---

### Post by papampi on 2011-07-28
> **Ant01 said:**
> I got a solution via my post  [http://ubuntuforums.org/showthread.php?p=8678737#post8678737]("http://ubuntuforums.org/showthread.php?p=8678737#post8678737")

Remove the desktop effects via preferences/appearence/visual effects and it sorts the problem out.

there is no remove visual effects in my ubuntu 11.04 !!!
please some one help me !!!!

---

### Post by jrave on 2011-10-07
> **papampi said:**
> there is no remove visual effects in my ubuntu 11.04 !!!
please some one help me !!!!

RTFT :p

> **v_2ryann said:**
> Here is the answer guys, on how to do it without changing the effects:

1) Open a terminal o press ALT+F2, then run/type: gconf-editor
2) Go to /desktop/gnome/remote_access and enable "disable_xdamage"

I found it found here:
[http://swiss.ubuntuforums.org/showthread.php?t=1496368](http://swiss.ubuntuforums.org/showthread.php?t=1496368)

worked perfectly for me. thanks.

---

### Post by digitaltruth on 2012-02-29
I have noticed this is an issue while using the fglrx (ATI proprietary drivers). To get around this if you run the ATI Catalyst admin control program and enable the "tear free" option it resolved the issue for me immediately.

---

### Post by remy215 on 2013-02-20
> 1) Open a terminal o press ALT+F2, then run/type: gconf-editor
2) Go to /desktop/gnome/remote_access and enable "disable_xdamage"

It did not work for me but put me on the way to the solution.

I did not manage to disable visual effects (no such menu) on ubuntu 12.10

Solution:
 on the computer where you want to log in:
1. ask user to logout
2. in login screen, user select its name then click on icon right next to it
3. select "Gnome (No effects")

That's it!
After that, vnc worked like a charm.

---

### Post by wildmanne39 on 2013-02-20
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

