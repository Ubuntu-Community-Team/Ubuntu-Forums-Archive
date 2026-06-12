---
title: "login as root from login screen"
date: 2009-11-20
forum: General Help
---

### Post by m1rjj00 on 2009-11-20
I've seen the other threads about logging as root from the login screen on Koala.  I'm a long time Unix old school guy who feels quite comfortable logging in as root.  Has 9.10 completely removed that option?!  Sorry to all of the sudo advocates but that's just nonsense.  Be root.  Be careful or learn the hard way.  If there is a way to activate root login from the login screen it would be VERY useful to know it because I'm sure that there are things that need to be and can ONLY be done as root.

---

### Post by scottuss on 2009-11-20
What do you need root for that you can't do with Sudo? 

I'm not saying you shouldn't be able to log in as root, it's your computer after all. As a Sudo fan, I'm just genuinely curious.

---

### Post by realzippy on 2009-11-20
[http://www.jonathanmoeller.com/screed/?p=1199](http://www.jonathanmoeller.com/screed/?p=1199)

---

### Post by pmains on 2009-11-20
I recommend against this, but have you tried sudo passwd root?

[http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html](http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html)

---

### Post by P4man on 2009-11-20
Realzippy you should know better. Its [against forum policies]("http://ubuntuforums.org/showthread.php?t=716201") to explain how to activate root account. 

bTo the OP: Before doing so, do read this first:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by m1rjj00 on 2009-11-20
I don't have a specific example for you at this second but there have been times, especially when attempting to install certain packages or tweak kernel settings that sudo just didn't cut it.  I had to really be root.  Actually I take that back.  The installation of a navigational chart engine was only accomplished as root.  Maybe it could have been done as sudo if you spent the time to adjust the permissions on every location that the engine software needed to touch but then how would you know what all those locations were?  Be root and sysadmin naked!!

---

### Post by scottuss on 2009-11-20
> **P4man said:**
> Realzippy you should know better. Its [against forum policies]("http://ubuntuforums.org/showthread.php?t=716201") to explain how to activate root account. 

bTo the OP: Before doing so, do read this first:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Oh yeah, I forgot about that. I remember someone getting into a lot of trouble for posting a write-up of how to get root. Eek!

---

### Post by m1rjj00 on 2009-11-20
To the folks who suggest adding a root passwd via sudo.  Been there done that.  This tack is convenient for lots of things but again, I'm old school and there are times when (for me) sudo annoys me when hey, if I just login as root I can do it all.  I'm not saying that I never use sudo or htat it's a bad thing.  I do use it and it's schweet but there are times when...

---

### Post by r.mariappan on 2009-11-20
I suppose the hiding of root account is the speciality of *BUNTU which makes us feel a difference from other distributions.

---

### Post by amauk on 2009-11-20
```
sudo -i
```

---

### Post by scottuss on 2009-11-20
If you're an old hat, you might be more comfortable with another distro. Having said that, I consider myself a power-user and I prefer Ubuntu as a desktop distro to any other.

I would suggest Googling for your desired answer.

---

### Post by P4man on 2009-11-20
> **r.mariappan said:**
> I suppose the hiding of root account is the speciality of *BUNTU which makes us feel a difference from other distributions.

Its not hidden. Its disabled. Which is sensible for 99% of the users, and the remaining 1% should have no problem "finding" it.

---

### Post by lavinog on 2009-11-20
> **m1rjj00 said:**
>  Has 9.10 completely removed that option?!

Are you referring to gdm login?  The new gdm doesn't have a complete configuration tool yet.

why wouldn't **sudo -i** suit your needs?
There can be no possible reason why you need to enable root logins.

---

### Post by m1rjj00 on 2009-11-20
> **P4man said:**
> Its not hidden. Its disabled. Which is sensible for 99% of the users, and the remaining 1% should have no problem "finding" it.

Not hidden, disabled.  Rgr that.  I was just hoping that I wouldn't have to get a my big shovel and reinvent the wheel.

Cheers...

---

### Post by m1rjj00 on 2009-11-20
> **lavinog said:**
> Are you referring to gdm login?  The new gdm doesn't have a complete configuration tool yet.

gdm login sounds correct.  On Jaunty you could "activate" the root login via System--> something-or-other.  I'm not seeing that with Karmic but as P4man said "it's in there."  I figured someone else had already found it and could share.  No biggie I'll just keep poking around.

---

### Post by redmk2 on 2009-11-20
> **m1rjj00 said:**
> I've seen the other threads about logging as root from the login screen on Koala.  I'm a long time Unix old school guy who feels quite comfortable logging in as root.  Has 9.10 completely removed that option?!  Sorry to all of the sudo advocates but that's just nonsense.  Be root.  Be careful or learn the hard way.  If there is a way to activate root login from the login screen it would be VERY useful to know it because I'm sure that there are things that need to be and can ONLY be done as root.

As you can see this is a controversial subject.  To answer your your direct question plainly; yes it is possible.  The installation of Ubuntu does not have a login for the root account.  But the account is there and it is working (try ***top ***to see).

The root account can be set up to allow you to use ***su *** to move to it at the CLI.  You can also setup a root account login via Gnome.  These are two separate operations.

I have done this on my desktop, but I don't ever use the GUI root login.  Most of the time I don't su to root either.  maybe I'm too lazy, but I use sudo just like everyone else.

So, the bottom line is yes you can do it.  It's a 2 step process if you want GUI login.  You can Google for it.  Should be easy to find.  That's how I figured it out.

---

### Post by blueridgedog on 2009-11-20
> **m1rjj00 said:**
> ...The installation of a navigational chart engine was only accomplished as root.  Maybe it could have been done as sudo if you spent the time to adjust the permissions on every location that the engine software needed to touch but then how would you know what all those locations were?  Be root and sysadmin naked!!

Sudo -i would have sufficed in this example.  

I am old school and recall never enabling a root login.  Yes, the root account had a password, but you could not login as root.

---

### Post by Simian Man on 2009-11-20
I also think that sudo is stupid and much prefer to run as root.  But logging into the GUI as root *is* a bad idea because a bug in any program you run, including all of the dektop stuff, has the ability to hose your system.  Just not a good idea.

Just unlock the root password, or use "sudo -i" if you want the "Ubuntu way", and open up a root terminal after logging into gdm as a regular user.

---

### Post by redmk2 on 2009-11-20
> **blueridgedog said:**
> ...Yes, the root account had a password, but you could not login as root.

It is a configurable parameter in Gnome (GDM).

---

### Post by redmk2 on 2009-11-20
> **Simian Man said:**
> I also think that sudo is stupid and much prefer to run as root.  But logging into the GUI as root *is* a bad idea because a bug in any program you run, including all of the dektop stuff, has the ability to hose your system.  Just not a good idea...


Not to mention all the config files in *root's* home directory.  :D

---

### Post by Simian Man on 2009-11-20
> **m1rjj00 said:**
> The installation of a navigational chart engine was only accomplished as root.  Maybe it could have been done as sudo if you spent the time to adjust the permissions on every location that the engine software needed to touch but then how would you know what all those locations were?  Be root and sysadmin naked!!

From that comment, it's clear you really don't know what you're talking about when it comes to Unix permissions.  You can do anything with root or sudo, it's just a matter of preference.

---

### Post by aysiu on 2009-11-20
> **P4man said:**
> Realzippy you should know better. Its [against forum policies]("http://ubuntuforums.org/showthread.php?t=716201") to explain how to activate root account. 

bTo the OP: Before doing so, do read this first:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) This. Read the links. Closed.

---

