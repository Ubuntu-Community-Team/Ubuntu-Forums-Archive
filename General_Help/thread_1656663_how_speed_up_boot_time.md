---
title: "how speed up boot time ?"
date: 2010-12-31
forum: General Help
---

### Post by rvchari on 2010-12-31
i ve been trying a lot of jugglery and disabled many start up apps to make ubuntu boot faster...
it takes almost 40 secs to 45 secs to log into my account after i get the gdm screen. gdm appears in about 35 secs (including grub menu display time) can anyone suggest me how to identify or clean up juck (if any?)

---

### Post by gandaran on 2010-12-31
> **rvchari said:**
> i ve been trying a lot of jugglery and disabled many start up apps to make ubuntu boot faster...
it takes almost 40 secs to 45 secs to log into my account after i get the gdm screen. gdm appears in about 35 secs (including grub menu display time) can anyone suggest me how to identify or clean up juck (if any?)
sorry about what I am about to post but I cant resist it!:p I'm using linux since 2003, opensuse linux it was then, it took about 4 minutes to fully boot the OS on this computer then so whats 45 seconds now?
people really live the fast life nowadays and expect everything to work fast?
don't take this personally, it's just my view of things!:p

---

### Post by supershin on 2010-12-31
diasble login screen so you get a command line prompt instead?

---

### Post by Quackers on 2010-12-31
I know you see reports of some people's systems booting up in 25 seconds, but mine doesn't :-) It takes about 50 to 55 seconds, which, compared to all my previous Windows installations, is pretty good. Certainly good enough for me.
Methinks you may expect too much :-)

---

### Post by QLee on 2010-12-31
[QUOTE=rvchari]i ve been trying a lot of jugglery and disabled many start up apps to make ubuntu boot faster...
it takes almost 40 secs to 45 secs to log into my account after i get the gdm screen. gdm appears in about 35 secs (including grub menu display time) can anyone suggest me how to identify or clean up juck (if any?)[/QUOTE]

For what it's worth, I agree with both Quackers and gandaran.

However, if you want people to be able to suggest reasonable, possible solutions or to be able to advise you that it's running as fast as it can, you will have to give detail about your hardware.

Probably would also be a good idea to detail what "jugglery" you have done specifically.

---

### Post by kellemes on 2010-12-31
> **gandaran said:**
> sorry about what I am about to post but I cant resist it!:p I'm using linux since 2003, opensuse linux it was then, it took about 4 minutes to fully boot the OS on this computer then so whats 45 seconds now?
people really live the fast life nowadays and expect everything to work fast?
don't take this personally, it's just my view of things!:p

Good point.
Personally I don't really care about boottime since I normally boot ones a day, I'm more interested in responsiveness of applications etc.. when the system is running.

40/45 seconds for booting a big system like Ubuntu isn't bad I think.
GDM by itself needs quit some time to startup, so you may consider getting rid of it and startup from console (as I do.. using Arch-Linux I might add), or use a lighter login-manager like [SLIM]("http://slim.berlios.de/").
Google gave me [this link]("http://www.harddiskdriverepair.com/upgrade/optimize-ubuntu-performance-improve-ubuntu-boot-speed.html") that may help?

By the way, Gnome is a big boy these days so choosing almost any other dm/wm speeds things up.

---

### Post by rvchari on 2011-01-01
thanx for all the comments...
but then what i actually meant was timing keeps changing, sometimes it takes much too long and sometimes the timing i had posted. i think i should ve asked how to tweak the probs (i was wondering my gud ol ubuntu should not behave as windows !!! which is always erratic.. thats all.
felt nice to be enlightened....

---

### Post by Quackers on 2011-01-01
If your boot time varies, you could try to narrow things down a bit by unplugging any usb devices before booting. See if the time improves at all.

---

### Post by rvchari on 2011-01-01
i dont plug in any usb. it usually happens after some security updates... its always nice to keep track of the systema anc changes in behaviour...
i ve been using linux since 1999 but its first time i m onto a forum and the exchange of knowledge is awesome.
will follow what u said.

---

### Post by ninjaaron on 2011-01-01
I have much quicker boot-times if I use one of those long shoe horns.

):P

---

### Post by supershin on 2011-01-03
Just get a solid state hard drive if you haven't done so already.

---

### Post by kellemes on 2011-01-04
> **supershin said:**
> Just get a solid state hard drive if you haven't done so already.

Can you recommend one? I've been thinking about it as well..

---

### Post by Dans564 on 2011-01-04
with an ssd you system will boot like lighting :guitar::guitar::guitar::guitar:

---

### Post by KdotJ on 2011-01-04
To all people saying that the OP is expecting too much... I disagree. The OP states in his post that it takes 40-45 seconds to log in ***after*** reaching the GDM. That is a huge amount of time... I can understand that sort of time frame for the overall boot, but from after the GDM? My system goes from GDM (after I press enter for logging in) to fully loaded desktop in 15 seconds or less.

---

### Post by AuP%*qb!# on 2011-01-04
I would love to reduce the amount of time the grub menu shows
two, three seconds at most really.
With the windows choices menu showing as well before the grub menu, it is very annoying.
I  think that 45secs overall is exceptable but 20secs i would expect at the most as it is still a very light weight os linux is.
I say 20secs for a netbook with 1gb ram.
Windows 7 starts at 20secs one a 2gb ram pc which is lovely.
Ubuntu is about 3 times the speed as xp at starting up on my laptop.
I have to make it go to the logon screen first before loging in as xp is not ready to logon automatically.

you may or you may not of seen this thread but it is for this kind of subject
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

here is another
[http://brainstorm.ubuntu.com/idea/42/](http://brainstorm.ubuntu.com/idea/42/)

[http://ubuntuforums.org/showthread.php4](http://ubuntuforums.org/showthread.php4)

I have not read through them but they are to do with the subject

---

### Post by kellemes on 2011-01-04
> **KdotJ said:**
> To all people saying that the OP is expecting too much... I disagree. The OP states in his post that it takes 40-45 seconds to log in ***after*** reaching the GDM. That is a huge amount of time... I can understand that sort of time frame for the overall boot, but from after the GDM? My system goes from GDM (after I press enter for logging in) to fully loaded desktop in 15 seconds or less.

True indeed.. for me it's about 10 seconds or so..
Maybe he should try another windowmanager? Gnome has become a big boy these days..

---

### Post by rvchari on 2011-01-04
whcih window manager do u suggest ?

---

### Post by kellemes on 2011-01-05
Take your pick..
[http://xwinman.org/](http://xwinman.org/)

You can try Xfce although it's not the lightest of wm's anymore..
Or maybe LXDE, very fast and cool ;-)

---

