---
title: "Crunchbang &amp; Ubuntu - Same root partition?"
date: 2009-12-31
forum: General Help
---

### Post by Cheesemill on 2009-12-31
Hi there people.

Just wanted to know if anyone has any experience of installing Crunchbang and Ubuntu on the same / partition (not dual booting).

Basically I've just installed Ubuntu on my mums laptop (which she's very pleased with, she finds it way more user friendly than XP). It only has 256 MB of RAM which is no problem for her as she only uses Firefox with one tab open at a time, however with my usage it spends alot of its time swapping.

I thought I would try and install Crunchbang for my use, but don't know how much it would conflict with Ubuntu. My plan is to run the #! install script from the current install but as they use different login managers I'm not sure how well this will work.

I'm going to take a detailed look at the #! install script to see if I can figure this out by myself but in the meantime I would be gratefull for any input people have to offer.

Happy New Year!!!!

PS - Running Jaunty on this system.

---

### Post by lykwydchykyn on 2009-12-31
Why don't you just install openbox or whatever crunchbang uses and then you can select it from the session menu of the login manager?

You can't just install one distro on top of another.

---

### Post by Leppie on 2009-12-31
why don't you install the xubuntu-desktop first? it wouldn't conflict with the current ubuntu install and is in between ubuntu and crunchbang (resource usage wise).

---

### Post by Cheesemill on 2009-12-31
> **lykwydchykyn said:**
> You can't just install one distro on top of another.

True, but they're not actually different distros, #! is just Ubuntu with a different DE and WM.

It should be possible just as you can have Ubuntu and Kubuntu installed on the same /

---

### Post by Leppie on 2009-12-31
> **Cheesemill said:**
> True, but they're not actually different distros, #! is just Ubuntu with a different DE and WM.

It should be possible just as you can have Ubuntu and Kubuntu installed on the same /

i think there's more than just a different de and wm.
the statement:
> With the exception of a few packages, CrunchBang Linux is built entirely from packages available from the Ubuntu repositories.
and:
> CrunchBang Linux is an unofficial branch of Ubuntu; therefore, it is not officially supported by Canonical.
indicate to me, that they're not the same.

AFAIK, from my xubuntu install i can install kubuntu or ubuntu without changing repos which doesn't seem possible with crunchbang.

---

### Post by lykwydchykyn on 2009-12-31
> **Cheesemill said:**
> True, but they're not actually different distros, #! is just Ubuntu with a different DE and WM.

It should be possible just as you can have Ubuntu and Kubuntu installed on the same /

Yeah, that's my point I guess.  The way you put it it sounded like you were going to try to do a full install on top of the current root filesystem.  But I reckon now that's not what you meant.

---

### Post by Cheesemill on 2009-12-31
> **lykwydchykyn said:**
> Yeah, that's my point I guess.  The way you put it it sounded like you were going to try to do a full install on top of the current root filesystem.  But I reckon now that's not what you meant.

Nope. I was going to use the #! install script which is meant to be used from a minimal Ubuntu CLI installation. It basically just adds the Crunchbang repos and installs some packages.

---

### Post by Cheesemill on 2009-12-31
What the hell, It's a newly installed system so it wont take long to re-install if it comes down to it. I'm running the #! install script now.

Fingers crossed everyone, Ill post back when it's finished :)

---

### Post by Leppie on 2009-12-31
yeah, let me know if it works.
still, i would've gone with the xubuntu-desktop first :P

---

### Post by lykwydchykyn on 2009-12-31
You can browse the contents of the crunchbang jaunty repos here:
[http://crunchbang.net/packages-9.04.xx/pool/main/](http://crunchbang.net/packages-9.04.xx/pool/main/)

The script only installs the crunchbang-desktop package, which is a metapackage that installs a good chunk of that repo from what I can tell.

Some of these are modified versions of Ubuntu packages that would already be installed, so it's hard to say what effect that would have on the currently running system.

You might try adding the repo and selecting crunchbang-desktop and just see how many packages will be upgraded or removed.  If it's going to be a lot, it'd be safer to just put openbox on there.

---

### Post by Cheesemill on 2009-12-31
> **Leppie said:**
> yeah, let me know if it works.
still, i would've gone with the xubuntu-desktop first :P

I'm not really into XFCE, Crunchbang is LXDE with the Openbox WM.
IMHO it's lighter than XFCE.

---

### Post by Cheesemill on 2009-12-31
I'm back!

Everything seems to be OK, all I've had to do is change the default sessions for each user (mine to Openbox, my mums to Gnome) and also change the theme back to clearlooks for the Gnome session.

I'm now down to only 77MB in use for the Crunchbang installation giving me much more RAM to play with.

Mission accomplished :)

---

### Post by Leppie on 2009-12-31
> **Cheesemill said:**
> I'm not really into XFCE, Crunchbang is LXDE with the Openbox WM.
IMHO it's lighter than XFCE.
LXDE is lighter than XFCE (I believe the memory footprint difference is about 20megs).
It's just that Xubuntu-desktop is supported by canonical, whereas #! isn't... getting help for issues with your ubuntu system would be more difficult as system behavior is difficult to predict with this combination. as lykwydchykyn said, it might have been better to install lxde and openbox.

---

