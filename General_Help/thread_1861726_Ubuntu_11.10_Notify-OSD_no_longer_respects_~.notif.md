---
title: "Ubuntu 11.10 Notify-OSD no longer respects ~/.notify-osd?"
date: 2011-10-15
forum: General Help
---

### Post by Kira Vakaan on 2011-10-15
Hi all,

I just upgraded to 11.10 and immediately I noticed that the pretty notification bubbles that I had configured in 11.04 through the ~/.notify-osd file have reverted to their default settings.  It would seem there is a new way to configure them.  Has anyone else experienced this/found a way to configure the notification bubbles in 11.10?

Thanks!

---

### Post by Kira Vakaan on 2011-10-16
Has anyone at least encountered this problem?  With or without a solution?  I would be helpful to me to know that someone else can still configure notify-osd through ~/.notify-osd.

---

### Post by wayfarer_boy on 2011-10-17
Hi Kira

I *think* the ~/.notify-osd config file is for a patched version of notify-osd which at the time of writing isn't yet available for Oneiric.  As far as I know the default version of notify-osd can't be customised.

[Growl](http://growl.info/screenshots) it most certainly isn't (and yet it so easily could be).  Grr.

---

### Post by Kira Vakaan on 2011-10-17
> I *think* the ~/.notify-osd config file is for a patched version of  notify-osd which at the time of writing isn't yet available for  Oneiric.Ah, thanks for the reply.  That makes some sense, and if it is the case, hopefully the same functionality will be restored soon.  In the mean time, I'll keep an eye out and post back here when/if it's changed.  Thanks!

---

### Post by wayfarer_boy on 2011-10-18
Here's a quick hack to use the Natty version (at least until an Oneiric version is released). It seems to work as per usual.  

*Notes:*
The second-to-last line reinstalls apps that were removed with notify-osd at the start.
The aptitude command at the end locks your version of notify-osd from being 'upgraded' to the official Oneiric version (you'll obviously need aptitude installed if you wish to run that line - sudo apt-get install aptitude).

```
sudo apt-get remove notify-osd
wget https://launchpad.net/~nilarimogard/+archive/webupd8/+files/notifyosdconfig_0.1-6~natty1_i386.deb
wget https://launchpad.net/~leolik/+archive/leolik/+files/notify-osd_0.9.30-0ubuntu4-leolik~ppa1-1_i386.deb
sudo dpkg -i notify-osd_0.9.30-0ubuntu4-leolik~ppa1-1_i386.deb
sudo dpkg -i notifyosdconfig_0.1-6~natty1_i386.deb
sudo apt-get install gnome-power-manager ubuntu-desktop update-notifier
sudo aptitude hold notify-osd
```

---

### Post by Lomok on 2011-10-18
Hi, 

Thanks for the post, it really helped and solved the issue. I just have a tip if anyone else needs reads this post. Never, never just copy-paste the links or commands without reading carefully.
I just copy-paste the commands from above, and i never saw that they are for the i386 arquitecture, and i'm using a 64 bit OS. So you can guess what kind of mess i did, jejeje ROFL

In case someone else need this, here are the links and commands for the 64bit:

```

wget https://launchpad.net/~nilarimogard/+archive/webupd8/+files/notifyosdconfig_0.1-6~natty1_amd64.deb
wget https://launchpad.net/~leolik/+archive/leolik/+files/notify-osd_0.9.30-0ubuntu4-leolik~ppa1-1_amd64.deb
sudo dpkg -i notify-osd_0.9.30-0ubuntu4-leolik~ppa1-1_amd64.deb
sudo dpkg -i notifyosdconfig_0.1-6~natty1_amd64.deb

```

Have a good day!!!

---

### Post by Kira Vakaan on 2011-10-19
Wow, thank you very much to both of you.  This works, well, exactly as it used to! :P  I installed the amd64 packages for my system.  Thanks again!

---

### Post by wayfarer_boy on 2011-10-20
As a follow-up, I found that the aptitude hold command didn't stop my package manager upgrading notify-osd to the newer locked-down version, so I fixed this in synaptic instead.  So, ...

Install Synaptic:```
sudo apt-get install synaptic
```run it, then find notify-osd, highlight it and go to Package > Lock version.  This will lock the better version of notify-osd until Sukochev Roman (Leolik) releases an Oneiric version.

---

### Post by inameiname on 2011-10-20
Awesome. I always prefer Leolik's version of notify-osd and until it gets updated (hopefully), I thank you guys for this workaround.

By the way, I believe this works better to hold a package via the command line: 

```

echo "notify-osd hold" | sudo dpkg --set-selections
 
     rather than:

sudo aptitude hold notify-osd

```

I have used the above for a while for various packages and it hasn't failed me yet.

And don't forget I believe you also need to install this:[FONT=Verdana]

[/FONT]```

[FONT=Verdana] sudo apt-get install libnotify-bin[/FONT]

```
[FONT=Verdana]
[http://www.webupd8.org/2011/05/configurable-notifyosd-bubbles-for.html](http://www.webupd8.org/2011/05/configurable-notifyosd-bubbles-for.html)
[/FONT]

---

### Post by Leolik on 2011-10-24
notify-osd updated for Ubuntu 11.10

---

### Post by ShodanjoDM on 2011-10-24
> **Leolik said:**
> notify-osd updated for Ubuntu 11.10

Many, many, many thanks. Been waiting for this :)

Cheers!

---

### Post by inameiname on 2011-10-24
> **Leolik said:**
> notify-osd updated for Ubuntu 11.10


Excellent. This is always a very important tweaked package for any good Ubuntu installation. Many thanks, Leolik!

---

### Post by Kira Vakaan on 2011-10-24
Ah thank you very much!  It works like a charm. :)

---

### Post by wayfarer_boy on 2011-10-25
Hi all.  Just letting you know that Leolik has now released an Oneiric version of his patched notify-osd, so time to unlock your apts, folks!

---

### Post by inameiname on 2011-10-25
> **wayfarer_boy said:**
> Hi all.  Just letting you know that Leolik has now released an Oneiric version of his patched notify-osd, so time to unlock your apts, folks!

We appreciate the info, wayfarer_boy, but actually Leolik himself already gave us the heads up about it a few replies back on this very thread. Regardless, thanks. I am sure many of us are just so eager to spread the news now. ;)

---

### Post by wayfarer_boy on 2011-10-25
Whoops! Talk about late to the party :/ Note to self, check thread before posting.

---

### Post by Aesso on 2011-10-25
Love this tool.

Is there any way to get the notifications to appear in places besides the left and right edges? At a specific offset, perhaps?

I'm using three monitors and I wish the notifications would appear in the upper-right corner of the middle screen, instead of the upper-right of the "virtual screen".

---

### Post by inameiname on 2011-10-26
> **wayfarer_boy said:**
> Whoops! Talk about late to the party :/ Note to self, check thread before posting.

Haha, no worries. I've done that too. :P

---

### Post by inameiname on 2011-10-26
> **Aesso said:**
> Love this tool.

Is there any way to get the notifications to appear in places besides the left and right edges? At a specific offset, perhaps?

I'm using three monitors and I wish the notifications would appear in the upper-right corner of the middle screen, instead of the upper-right of the "virtual screen".


I am not sure. However, for lots of help, check out this posting (it also links to an older one which I believe might help):


[http://www.webupd8.org/2011/10/configurable-notifyosd-notifications.html](http://www.webupd8.org/2011/10/configurable-notifyosd-notifications.html)

---

### Post by gamblor01 on 2011-10-27
> **Aesso said:**
> Love this tool.

Is there any way to get the notifications to appear in places besides the left and right edges? At a specific offset, perhaps?

I'm using three monitors and I wish the notifications would appear in the upper-right corner of the middle screen, instead of the upper-right of the "virtual screen".

As far as I can tell, this isn't an option.  You only have 6 places that you can set the "gravity" which is the four corners of your entire desktop (treat all 3 screens as one single entity), or the middle of the screen on the very left or very right.

I have 2 screens and wish that I could get it to appear at the top-right of my left screen but have never been able to accomplish this, so I just have them appear on the top-left instead of my left screen instead.  This is definitely a feature I would be interested in though!

---

### Post by Aesso on 2011-10-29
> **gamblor01 said:**
> As far as I can tell, this isn't an option.  You only have 6 places that you can set the "gravity" which is the four corners of your entire desktop (treat all 3 screens as one single entity), or the middle of the screen on the very left or very right.

I have 2 screens and wish that I could get it to appear at the top-right of my left screen but have never been able to accomplish this, so I just have them appear on the top-left instead of my left screen instead.  This is definitely a feature I would be interested in though!

Agreed. Notify-OSD needs to be a little  bit "smarter", i.e., if it could detect that the screen has an unusual aspect ratio (>2 perhaps?) or if it would use xrandr to figure out the number of screens and where the "primary" one is, and then if could readjust the position when there is a change during a session (laptop external monitor anyone?), that would be wonderful.

Definitely a major papercut. Multi-head configurations in Linux need more love and attention. I hope this becomes a major priority for the Wayland project, or it's just going to be a huge mess.  :)

---

