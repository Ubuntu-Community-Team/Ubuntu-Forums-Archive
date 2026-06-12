---
title: "I AM FREAKING OUT - Please help!!!"
date: 2009-12-27
forum: General Help
---

### Post by dxtac1 on 2009-12-27
I took the plunge and went with Ubuntu on EVERY computer in my house EXCEPT the work computers about 4-5 weeks ago. I have had not any problems whatsoever until last week. My main PC began freezing occasionally. Not knowing the proper procedures at the time and still not 100% sure I did a few hard shut-downs. When I say frezing I mean just sopping. The screen looked normal except the mouse would not move and not key combos would do anything. Tonight I started it up and it seemed all was going well until it began to install upgrades. About half way through installing the screen went black and froze. I did a hard shut down and all H%LL has broken loose!! 
 
When I start it now it goes to a screen that says the following:
Grub loading (a Ubuntu symbol in the middle of the screen)
Then it says:
Ubuntu 9.10 dxtac-homepc tty1
dxtac-homepc login:
I enter my login and password then this appears:
Last login: Mon Dec 28 03:31:53 cst 2009 on tty1
Linux dxtac-homepc 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
 
To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
 
0 packages can be updated
0 updates are security updates
 
dxtac@dxtac-homepc:~$
 
I know most of you will know what this may mean but I do not and to be quite honest I'm a little freaked out as I don't know what to do!! I took the plunge to Linux, in particular Ubuntu, under the impression that it was/is less prone to goofy stuff like this. ANY and ALL help would be greatly appreciated!!
 
Thanks in advance,
 
Derek

---

### Post by abeisgreat on 2009-12-27
> **dxtac1 said:**
> I took the plunge and went with Ubuntu on EVERY computer in my house EXCEPT the work computers about 4-5 weeks ago. I have had not any problems whatsoever until last week. My main PC began freezing occasionally. Not knowing the proper procedures at the time and still not 100% sure I did a few hard shut-downs. When I say frezing I mean just sopping. The screen looked normal except the mouse would not move and not key combos would do anything. Tonight I started it up and it seemed all was going well until it began to install upgrades. About half way through installing the screen went black and froze. I did a hard shut down and all H%LL has broken loose!! 
 
When I start it now it goes to a screen that says the following:
Grub loading (a Ubuntu symbol in the middle of the screen)
Then it says:
Ubuntu 9.10 dxtac-homepc tty1
dxtac-homepc login:
I enter my login and password then this appears:
Last login: Mon Dec 28 03:31:53 cst 2009 on tty1
Linux dxtac-homepc 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
 
To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
 
0 packages can be updated
0 updates are security updates
 
dxtac@dxtac-homepc:~$
 
I know most of you will know what this may mean but I do not and to be quite honest I'm a little freaked out as I don't know what to do!! I took the plunge to Linux, in particular Ubuntu, under the impression that it was/is less prone to goofy stuff like this. ANY and ALL help would be greatky appreciated!!
 
Thanks in advance,
 
Derek

What is happening is you are being dropped to a "shell", essentially a text based interface. I would guess this issue is caused by something like bad graphics card drivers or a glitch in GDM (the login screen)

Once you see
```

dxtac@dxtac-homepc:~$

```
try typing
```

startx

```

what happens when you do this?

---

### Post by ST3ALTHPSYCH0 on 2009-12-27
I see two things that need addressed.
1. safe shutdown or reboot. Hold alt+print screen/sys req and enter this sequence r-e-i-s-u-o (for shutdown) or r-e-i-s-u-b (for reboot, but this hasn't ever worked for me)
2. You've interrupted and update you'll need to run a couple commands from the command line
```

sudo apt-get update
sudo apt-get upgrade

```
Those commands will get and install the current upgrades and should put you back to right.

---

### Post by PsychoDevon on 2009-12-28
A similar thing happened when I tried to install Wubi on my mom's computer. As far as I know, it was just a bad hardware compatibility for my case, as the login would start up fine but then on the desktop main screen it would freeze. I'm thinking of trying to install Xubuntu on hers, as it has been known to be good for low-spec hardware. Also, next time try installing Wubi on your machines if you're not 100% sure about installing Ubuntu.

---

### Post by 3rdalbum on 2009-12-28
Try:

```
sudo gdm
```

(it might be "sudo service gdm start" these days, I'm not sure).

It looks like you might need to run this command too at some point:

```
sudo dpkg --configure -a
```

to get the updates to continue to install.

---

