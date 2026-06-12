---
title: "Karmic, Monitor gonig to sleep, even though told not to in power options"
date: 2009-11-08
forum: General Help
---

### Post by Primefalcon on 2009-11-08
Even though I have checked both the screensaver options and power management, and have the screensaver turned off and the monitor never to go to sleep, the monitor is still going to sleep after roughly 10 mins or so.

Can anyone offer any advise on this issue?

Also Vlc playing or such playing does prevent this but a flash video playing on a website or such doesn't so I do suspect this is connected to a power saving option or such but.....

---

### Post by Primefalcon on 2009-11-08
Any help at all would be appreciated, thank you

---

### Post by Primefalcon on 2009-11-08
still looking around and no solution yet

---

### Post by girto on 2009-11-08
Did you check the power management options in your BIOS?

---

### Post by Primefalcon on 2009-11-08
> **girto said:**
> Did you check the power management options in your BIOS?
yes and I just double checked it now

---

### Post by Primefalcon on 2009-11-08
also my windows/puppy installations work fine

---

### Post by guestolo on 2009-11-08
May not be any help, but worth a shot
I believe it's mostly aimed at Gnome enviroment
I installed Ubuntu Tweak on my machine
[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

Once installed, you can find it under Applications>System Tools
Under System>Power Management
I forgot that I UNChecked both
"Enable Hibernation"
"Enable Suspend"

Which caused my monitor to always stay on
I wanted mind to shut down after a specific time, so I rechecked both options

---

### Post by Primefalcon on 2009-11-08
> **guestolo said:**
> May not be any help, but worth a shot
I believe it's mostly aimed at Gnome enviroment
I installed Ubuntu Tweak on my machine
[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

Once installed, you can find it under Applications>System Tools
Under System>Power Management
I forgot that I UNChecked both
"Enable Hibernation"
"Enable Suspend"

Which caused my monitor to always stay on
I wanted mind to shut down after a specific time, so I rechecked both options
I know ubuntu-tweak had it installed for a one, just haven't had it since my last clean install, Good thinking I'll let you know how it goes.

---

### Post by Primefalcon on 2009-11-08
Ok doesn't help the issue

---

### Post by martywd on 2009-11-09
> **guestolo said:**
> May not be any help, but worth a shot
I believe it's mostly aimed at Gnome enviroment
I installed Ubuntu Tweak on my machine
[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

Once installed, you can find it under Applications>System Tools
Under System>Power Management
I forgot that I UNChecked both
"Enable Hibernation"
"Enable Suspend"

Which caused my monitor to always stay on
I wanted mind to shut down after a specific time, so I rechecked both options

Hey thanks for that tip.    I was having the same issue in a fresh build of Karmic, too.   My disabling 'Enable Suspend' in Ubuntu Tweak, which I thought would only prevent a computer suspend, was actually preventing the display from suspending.  Re-enabling 'Enable Suspend' again in Ubuntu Tweak has solved this suspend display issue.

---

### Post by Primefalcon on 2009-11-09
> **martywd said:**
> Hey thanks for that tip.    I was having the same issue in a fresh build of Karmic, too.   My disabling 'Enable Suspend' in Ubuntu Tweak, which I thought would only prevent a computer suspend, was actually preventing the display from suspending.  Re-enabling 'Enable Suspend' again in Ubuntu Tweak has solved this suspend display issue.
I ended up reinstalling the screensaver and power management and reinstalling a bunch of those tools (I mean, **a lot**) and I seem to have the issue fixed, must of just been something that went wonky in the karmic upgrade

---

