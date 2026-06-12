---
title: "Making a Lucid iso with a few little changes."
date: 2010-05-02
forum: General Help
---

### Post by Phrea on 2010-05-02
I want to make an iso for some friends [and maybe friends of friends] that aren't all that tech savvy, so I want to change a few things to the original Lucid iso.

First, I want the option to install Lucid **out** of the boot menu [but the other options should ideally stay].
Second, I want to include the ubuntu-restricted-extras so they can immediately try it out and see that it also plays video/audio etc.

Hope you guys understand what I want, and that this question hasn't been asked a million times before [I checked].

Thanks !

---

### Post by Phrea on 2010-05-02
Shameful self bump.

---

### Post by parm289 on 2010-05-02
Google remastersys - I think there was even a lifehacker feature on it once.  Basically, I think it lets you create a cd/dvd of your current install.

---

### Post by Phrea on 2010-05-02
> **parm289 said:**
> Google remastersys - I think there was even a lifehacker feature on it once.  Basically, I think it lets you create a cd/dvd of your current install.
I know, but I don't want that.
I want to make a new iso with a feature deleted in the boot menu, and one added [the extras].

---

### Post by blueridgedog on 2010-05-02
You can edit the files in the iso:

[http://www.linux.com/archive/feature/137524](http://www.linux.com/archive/feature/137524)

---

### Post by parm289 on 2010-05-02
> **Phrea said:**
> I know, but I don't want that.
I want to make a new iso with a feature deleted in the boot menu, and one added [the extras].

If I correctly understood the question, you want to create a new 10.04 livecd with ubuntu-restricted-extras preinstalled and the install option removed from the livecd boot menu?

To create a new iso with ubuntu-restricted-extras preinstalled, you could install ubuntu-restricted-extras in a fresh 10.04 install and use remastersys to create the iso.  I'm not sure how you'd go about editing the livecd boot menu, if that's what you're asking.

---

### Post by Phrea on 2010-05-02
> **blueridgedog said:**
> You can edit the files in the iso:

[http://www.linux.com/archive/feature/137524](http://www.linux.com/archive/feature/137524)

Oh shi-, what have I started.
Thanks for the link, will this work for Lucid? [obviously changing a few .iso names and stuff]

---

### Post by Phrea on 2010-05-02
> **parm289 said:**
> If I correctly understood the question, you want to create a new 10.04 livecd with ubuntu-restricted-extras preinstalled and the install option removed from the livecd boot menu?

To create a new iso with ubuntu-restricted-extras preinstalled, you could install ubuntu-restricted-extras in a fresh 10.04 install and use remastersys to create the iso.  I'm not sure how you'd go about editing the livecd boot menu, if that's what you're asking.

That is exactly what I'm asking. :)
I know about remastersys, very handy, that's not the problem, removing that install option from the boot menu is the problem.

---

### Post by MCVenom on 2010-05-02
> **parm289 said:**
> Google remastersys - I think there was even a lifehacker feature on it once.  Basically, I think it lets you create a cd/dvd of your current install.
Yeah, that's what I'm using, but its not available right now, their servers were hacked. :(

You can find more info on that here: [http://ubuntuforums.org/showthread.php?t=1469849](http://ubuntuforums.org/showthread.php?t=1469849)

Shoot Frag a PM with your email, he might be to send you a copy of the program.

---

### Post by Phrea on 2010-05-02
> **BlackOtaku said:**
> Yeah, that's what I'm using, but its not available right now, their servers were hacked. :(

You can find more info on that here: [http://ubuntuforums.org/showthread.php?t=1469849](http://ubuntuforums.org/showthread.php?t=1469849)

Shoot Frag a PM with your email, he might be to send you a copy of the program.

I have it locally. :)
Thanks tho.
I wonder why he got hacked. Just read what you linked. Still amazing, but things sometimes happen I guess... Damn [strike]internet[/strike] scriptkiddies.

EDIT: Ah a global godaddy vulnerability.

---

### Post by parm289 on 2010-05-02
> **Phrea said:**
> That is exactly what I'm asking. :)
I know about remastersys, very handy, that's not the problem, removing that install option from the boot menu is the problem.

I see.  The link above describing how to edit files inside the iso seems handy then, good luck!

---

### Post by Phrea on 2010-05-02
> **parm289 said:**
> I see.  The link above describing how to edit files inside the iso seems handy then, good luck!

You mean [http://www.linux.com/archive/feature/137524](http://www.linux.com/archive/feature/137524) that one.
Good luck to me indeed. :D
Scares the heck out of me, but I have to deliver I guess.

---

