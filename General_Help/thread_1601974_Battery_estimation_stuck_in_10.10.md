---
title: "Battery estimation stuck in 10.10"
date: 2010-10-20
forum: General Help
---

### Post by nautica17 on 2010-10-20
I've read some people were having this issue, but I want to hear from Ubuntu directly as to what is going on. On my Toshiba A205 laptop I have Ubuntu installed within Windows, and it works fine except for the battery indicator being stuck at "Laptop battery (estimating...)". Is there a fix coming soon? I've run all updates and still no good. I'd really hate to go back to Windows.. that thing is too slow for me on this computer. Also, I had 10.04 installed and everything was fine.

---

### Post by Quackers on 2010-10-20
Mine used to show "estimating" all the time during beta phase of Maverick Meerkat. Now it shows that only while the battery is charging. When the battery is fully charged it shows "laptop battery is charged"

---

### Post by nautica17 on 2010-10-20
Do you know if there is a fix coming?

---

### Post by Quackers on 2010-10-20
I don't. To be honest I don't really see it as a problem.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-20
I don't know how to help with that because I don't use the battery on my laptop. However, I was watching the Linux Action Show the other day and on their review on Ubuntu 10.10 they mentioned that the performance of Maverick has improved a lot. They said that battery can last up to 5 hours and that a guy from Canonical said  that sometimes the battery estimation is stuck at 3 hours, stays like that for a while and then shows it right. Watch that: [http://www.youtube.com/watch?v=K0KHdHUzqWk](http://www.youtube.com/watch?v=K0KHdHUzqWk)
At about 30 minutes they talk about the power management.

---

### Post by nautica17 on 2010-10-20
> **Quackers said:**
> I don't. To be honest I don't really see it as a problem.

Well.. I don't like draining my battery to the max to know if I have a low battery. And I also don't always have a chance to charge up between classes. So I mean knowing how much battery life I have left is essential for me.

---

### Post by Quackers on 2010-10-20
I see your point.
It's a bit long-winded but you could use a conky display.

---

### Post by nautica17 on 2010-10-20
> **&#24746 said:**
> I don't know how to help with that because I don't use the battery on my laptop. However, I was watching the Linux Action Show the other day and on their review on Ubuntu 10.10 they mentioned that the performance of Maverick has improved a lot. They said that battery can last up to 5 hours and that a guy from Canonical said  that sometimes the battery estimation is stuck at 3 hours, stays like that for a while and then shows it right. Watch that: [http://www.youtube.com/watch?v=K0KHdHUzqWk](http://www.youtube.com/watch?v=K0KHdHUzqWk)
At about 30 minutes they talk about the power management.

I doubt my laptop can even hit 3 hours of battery life. lol. The thing is 3 years old.. and so it's not ancient yet or anything, but I mean I can get about 2.5 hours at most on it. So this battery indicator issue is big for me. I'm taking a look at the video you linked though. I really need to figure something out with this issue.

---

### Post by nautica17 on 2010-10-20
> **Quackers said:**
> I see your point.
It's a bit long-winded but you could use a conky display.

I'm definitely looking into that! Thank-you! Hopefully it pulls me through for the time being.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-20
The video just reviews Ubuntu 10.10. It doesn't provide help with this issue. Do what Quackers suggested. I linked that video to show you that Ubuntu 10.10 has a great power management, so great that even the computer can't believe that the battery can last that long. Also, I thought that your battery estimation just stuck at a certain number.

---

### Post by Quackers on 2010-10-20
You're welcome :-)
If you only want the battery display it will make it easier. But you won't!  :-)

---

### Post by ontwowheels on 2010-10-27
> **Quackers said:**
> I see your point.
It's a bit long-winded but you could use a conky display.

can u post the conky config for that?  I also have the battery monitor problem with 10.10.  And when running off battery I noticed the battery did not last nearly as long with Lucid.  I may go back to LL.

---

### Post by mondechris on 2010-11-03
I had the same problem and could not find a simple solution or fix. So here is what i did.
First i noticed that many people said that the battery indicator was working fine in lucid.
So all i had to do was to downgrade the gnome-power-manager to the version that lucid had.
Maverick's gnome-power-manager version is 2.32.0-0ubuntu1 whereas lucid's 2.30.0-0ubuntu1 . Now the 'hard' part is how to downgrade since its not exactly supported.
This method can be used for any package you want.
First we will check if there is an older version of the package in Maverick's repository.
Open Synaptic Package Manager and choose gnome-power-manager. In the menu bar go to Package/Force Version , you will see all the versions for the package in Maverick's repository. In our case there is only one so... we can't downgrade, at list for now!!!!!!
In the menu bar of Synaptic Package Manager choose Settings/Repositories. On the 'Ubuntu Software' tab uncheck everything, on the 'Updates' tab uncheck the boxes on the 'Ubuntu updates' section (4 boxes). Now go to 'Other Software' tab and Add a new source by clicking the 'Add' button. On the window type '
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted universe multiverse'
and click "Add Source' then 'Close'. After that do a reload to the repository and use the Force Version we mentioned.
That's it!!!!Remember to undo the changes we did to the Sources from the  
Settings/Repositories menu.

---

### Post by pamfletaru on 2010-12-16
Thank you very much. It works like a charm.

---

### Post by anoxi on 2011-02-15
check this bug: [https://bugs.launchpad.net/ubuntu/maverick/+source/upower/+bug/629258](https://bugs.launchpad.net/ubuntu/maverick/+source/upower/+bug/629258)

possible fix, see post #95

---

### Post by Cold Man 1 on 2011-02-25
Just rebooted! Works Great! Is it possible to make the downgrade version into a downloadable tarball for the newbies!! Otherwise this is a slightly long process but still simple :) TY:guitar::
=D>

---

### Post by regeya on 2011-02-26
I saw that one of the devs in that bug report had a power management PPA.  I added that, did a safe-upgrade, rebooted, and viola.

But really?  This thread was started in October 2010, it's nearly March 2011, and I have to add a PPA just to have power management work properly?

---

### Post by beercz on 2011-02-27
> **anoxi said:**
> check this bug: [https://bugs.launchpad.net/ubuntu/maverick/+source/upower/+bug/629258](https://bugs.launchpad.net/ubuntu/maverick/+source/upower/+bug/629258)

possible fix, see post #95
Thanks anoxi

This worked for me.

Much appreciated.

---

### Post by brian334 on 2011-02-27
Sorry new to Linux but how the hell do I post a new question / tread HELP

---

### Post by snakeman21 on 2011-04-04
> **brian334 said:**
> Sorry new to Linux but how the hell do I post a new question / tread HELP

Si

---

### Post by ontwowheels on 2011-04-04
> **regeya said:**
> I saw that one of the devs in that bug report had a power management PPA.  I added that, did a safe-upgrade, rebooted, and viola.

But really?  This thread was started in October 2010, it's nearly March 2011, and I have to add a PPA just to have power management work properly?

Agreed, this issue seems to have been a mess.  Power management on a laptop seems to be the Achilles Hell of Ubuntu, or maybe Linux in general.  I have to use Win7 or Vista when using my Laptop in a two hour class.  Ubuntu would never make it that long, not on any of the laptops I have used before anyway.

---

### Post by pvfjr on 2011-05-31
Just did the downgrade on my hp dv2000, worked great.  I don't know why I lost this functionality when it worked in Lucid, but it's nice to finally have it back.  

As far as battery life goes, my laptop has always lasted a LOT longer during my classes if I'm in Ubuntu as opposed to Win7 or Vista.  Windoze runs hot and kills the battery fast on this laptop.

---

### Post by rugbeeprop on 2011-06-01
> **anoxi said:**
> check this bug: [https://bugs.launchpad.net/ubuntu/maverick/+source/upower/+bug/629258](https://bugs.launchpad.net/ubuntu/maverick/+source/upower/+bug/629258)

possible fix, see post #95

#100 to install ppa:brian-rogers/power works for me as #95 is i386 version and I am running x64

```

sudo add-apt-repository ppa:brian-rogers/power
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by xyepblra on 2011-07-30
> **mondechris said:**
> So all i had to do was to downgrade the gnome-power-manager to the version that lucid had.
Awesome idea, thorough instruction. Thank you, Chris!

---

### Post by Virus666 on 2011-10-31
> **rugbeeprop said:**
> #100 to install ppa:brian-rogers/power works for me as #95 is i386 version and I am running x64

```

sudo add-apt-repository ppa:brian-rogers/power
sudo apt-get update
sudo apt-get upgrade

```

That really works for Ubuntu 10.10 Maverick Meerkat. Thank you... :-)

---

