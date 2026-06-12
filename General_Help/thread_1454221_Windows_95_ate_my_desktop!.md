---
title: "Windows 95 ate my desktop!"
date: 2010-04-14
forum: General Help
---

### Post by Doji Grovesai on 2010-04-14
I had just done the latest recommended updates for ubuntu 9.10 yesterday.  I turned my computer on this morning, and the computer did a filesystem check (it was about time for one), and then I logged in.

It looks like windows 95 barfed all over my screen! Also, I have sounds (all those system noises for when you open programs and stuff).

For the appearance thing, I did the usual: system->preferences->appearance, and changed things back.  Changing icons only works for icons in the panel, changing controls only works for the appearance menu and firefox.  Background changes work fine.

For the sounds, I also did the usual: system->preferences->sounds and turned them all off (selected "no sounds").  This doesn't work.  I still get sounds.

Has anybody had this problem?  Does anybody have an idea about how to fix it?

---

### Post by 98cwitr on 2010-04-14
do you have an nvidia gpu?

---

### Post by hangfire on 2010-04-14
> **Doji Grovesai said:**
> It looks like windows 95 barfed all over my screen!

Please clarify what you mean by this. Has the resolution been lowered to 800x600, giving everything a clunky, oversized and crowded appearance? Has the color scheme changed?

-HF

---

### Post by 98cwitr on 2010-04-14
screenshot would be nice too...

---

### Post by Doji Grovesai on 2010-04-14
Sorry, didn't quite think that through.  Panicked a bit.

I attached a screenshot.  It's the look and feel that has changed.  The resolution is the same as normal, which should be expected, since changing the appearance does work on a limited number of programs (now only Firefox thus far).  Also, some compiz effects still work (cube, expose, show desktop), but others (animations for min/max windows) do not.  The compiz menus, however, show no changes.

Also, I logged into recovery mode and hit "repair broken packages" just to be sure, but nothing has changed.

running lspci in terminal yields:
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

I'm pretty sure it's not nvidia based, but I could be wrong.

Thanks again.

---

### Post by 98cwitr on 2010-04-14
have you tried changing themes around a bit? I'm sorry, but I am not able to see anything particularly wrong here.

---

### Post by Doji Grovesai on 2010-04-14
Yes.  As stated, I've tried changing the themes around.  The appearance of applications looks like win95, and the folder icons are not even the default "Human" icons, but the old gnome-v2 icons.  Trying to change themes does not work.  I can get Firefox to comply, and panel icons, but nothing else.

Also, any changes made to the sound settings have no effect.  At all.

---

### Post by polki@mac.com on 2010-04-14
It looks like mine after it got confused as to what window decorator it should use. I used Emerald and Compiz window manager and that confused it completely.
Fusion Icon is an easy way to tell it what to use.

Hope that works for you too!

---

### Post by PhilGil on 2010-04-14
That looks like a theme engine problem to me.  My windows looks like your screenshot when I try to install a theme that is only supported by a newer version of the Murrine engine. 

Did you install a deb with an newer version theme engine (Aurora, Murrine, Clearlooks, etc)?  Maybe the update rolled your system back to an older version.

Are you root?  If you install themes in your home directory then window rendering can look like that when working as root.

---

### Post by Doji Grovesai on 2010-04-16
Nope, not root.  I'm not sure why the update would have rolled my theme engine back, as I don't recall that being among the updates.  But that's something to look into, thanks!

Problem isn't solved yet, so if there are any other suggestions, I'm open to them!

---

### Post by KeyserSoze93 on 2010-04-16
It looks as if your GTK settings are not being read. Try opening a terminal, and running:

```

gnome-settings-daemon

```

GTK applications get their look and feel either from this (which SHOULD be running with GNOME), or from ~/.gtkrc-2.0

I don't run GNOME, so I have had to put appearance settings in the file, but with GNOME, gnome-settings-daemon should take care of it, provided it's running.

---

### Post by Doji Grovesai on 2010-04-17
Thanks!  I think that did it.  Odd fiddlings had fixed the sound issue a bit ago, but I was still having the icon problem.  Now that seems to be working ok.  Thank you all!:)

---

