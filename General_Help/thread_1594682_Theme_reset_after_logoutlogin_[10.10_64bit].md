---
title: "Theme reset after logout/login [10.10 64bit]"
date: 2010-10-12
forum: General Help
---

### Post by empty79 on 2010-10-12
I experience the following issue with Ubuntu 10.10 x86_64, kernel 2.6.32-25-generic:

When I login after having logged out, the theme is reset from Radiance to a quite coarse one withs grey folders and very basic icons. System|Preferences|Appearance->Theme tab just considers it Custom. No change to window borders, and trying to change the theme just affects the borders.

Does not happen on a Ubuntu 10.10 32 bits installation.

Anyone having the same problem?

---

### Post by Jebtrix on 2010-10-13
Just got done installing 10.10 64-bit and logging out and back does screw up the theme. Changing themes in Appearance Settings does not restore it either. I had to do [COLOR="Red"]sudo service gdm restart[/COLOR] to get theming back without restarting machine. :-(

---

### Post by Jebtrix on 2010-10-13
Narrowed it down to Compiz with Nvidia proprietary drivers installed. At least in my case. If I turn off all effects it works fine.

---

### Post by empty79 on 2010-10-13
Restarting gdm didn't work out for me :(

P.S. I'm using Compiz with the latest Nvidia drivers too.

---

### Post by Jebtrix on 2010-10-13
I messed with it some more and the problem gets worse. You probably have auto-login set like I do. If you turn off auto-login you wont even get proper theming the first time. So the problem is actually between the Graphical Login, Compiz and Nvidia drivers. I changed settings to get a text based login but as soon as I start gdm the graphical login appears anyway. Very nasty bug if you ask me but I can't find any meaningful errors in logs to see whats the problem.

*BTW Restarting gdm doesn't always work for me either :(

---

### Post by Jebtrix on 2010-10-13
I have found the source and a workaround. \\:D/

**Workaround:**
```
sudo mkdir /usr/share/gdm/nostart
sudo mv /usr/share/gdm/autostart/LoginWindow/gnome-settings-daemon.desktop /usr/share/gdm/nostart/
```

Logout and back in.
[B]
Side-effect:[/B]
Login screen gui is unthemed.. the horror ;-)

---

### Post by josephellengar on 2010-11-01
> **Jebtrix said:**
> I have found the source and a workaround. \\:D/

**Workaround:**
```
sudo mkdir /usr/share/gdm/nostart
sudo mv /usr/share/gdm/autostart/LoginWindow/gnome-settings-daemon.desktop /usr/share/gdm/nostart/
```

Logout and back in.
[B]
Side-effect:[/B]
Login screen gui is unthemed.. the horror ;-)

Okay, it worked.  And I was even able to get my login screen themed.  Now what the hell did I do? :confused:

EDIT: login screen does not stay themed on reboot

But thanks so much!  I can finally stand to upgrade and look at my screen without my eyes hurting!

---

### Post by snakesqzns on 2010-11-03
Issue tracked here: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/625670/+activity](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/625670/+activity)

---

### Post by acrobaticman on 2010-12-21
I also have this problem.

Every time I turn on my laptop the theme is auto changed.

When I go to System>>Preferences>>Appearance Both Top and Bottom panel change back to "Ambiance" theme as I set it long time ago.

But the problem is the Icon in the Desktop and the theme when i browse files the theme is still messed up.


Please anyone who knows how to solve this. please reply.

ps. Mine is Ubuntu 10.10 32bit with on-board graphic card.

---

### Post by a4able on 2011-01-18
i am not sure
i also face this problem
i  think it is due to compiz
applications>accesories>terminal>type    $ sudo apt-get --purge remove compiz
will remove compiz completely

---

### Post by qrwe on 2011-01-25
Same here, 32-bit Ubuntu Desktop 10.10.

It happened after running the Update Manager and then doing a mandatory reboot. I can get a few things "back" by simply opening the theme manager, such as the Radiance panels, but the icons are still messed up. It is as something needs to be manually executed for GUI to remember what theme I'm currently using..

---

### Post by oODeanOo on 2011-01-30
I also have the theme change problem from time to time on 10.10.

When going to Appearance and setting theme back to Ambiance I too get the "half and half" theme as shown in previous post.

32 bit version no compwiz as running on Netbook, very frustrating.

Dean

---

### Post by jamiekrug on 2011-01-31
Hi, folks. Since I've noticed a few more "me too" type replies here, I just thought I'd point out that there's a fairly simple [workaround noted in post #6]("http://ubuntuforums.org/showpost.php?p=9969103&postcount=6") and you can also subscribe to [LP Bug #625670]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/625670"), where this is tracked.

---

### Post by oODeanOo on 2011-01-31
> **jamiekrug said:**
> Hi, folks. Since I've noticed a few more "me too" type replies here, I just thought I'd point out that there's a fairly simple [workaround noted in post #6]("http://ubuntuforums.org/showpost.php?p=9969103&postcount=6") and you can also subscribe to [LP Bug #625670]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/625670"), where this is tracked.

I have moved the file as described in Post #6 and it fails to fix this issue when switching between users.

I will add this observation to Launchpad but this issue seems to have been outstanding for far too long and doesn't really help promote Ubuntu which is a real shame.

Dean

UPDATE: the recommend workaround from Post [LP Bug #625670]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/625670") Post #13 works for me.

Now all I need to do is workout how to put "gnome-settings-daemon" and "killall nautilus" in an easy to run script!

---

