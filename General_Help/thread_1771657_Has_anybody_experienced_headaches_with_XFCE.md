---
title: "Has anybody experienced headaches with XFCE?"
date: 2011-05-30
forum: General Help
---

### Post by Roasted on 2011-05-30
I have Ubuntu 11.04 running with XFCE installed (Xubuntu Desktop). I thoroughly enjoy it, but I'm having some issues that I never experienced in Gnome or Unity.

Sometimes my system just locks up. Period. Done. Over. No saving it. Mouse is locked and everything is just frozen. I power off, back on, I'm good for a while. I also had just a few minutes ago all of my icons in the panel turn to a white square. I click on the icon where the logout menu is, thinking I could log out and back in, and it says failed to execute. About 20 seconds later, it did another hard lockup.

Now, I love XFCE, but really? Is anybody else seeing this?

---

### Post by 3xp10r3r|X13 on 2011-05-30
Just switch to K/ubuntu - Installing the kde desktop environment!

Awesome design + useful widgets + very easy to handle = KDE

---

### Post by wolfen69 on 2011-05-30
Have you done memtest? I always try to eliminate hardware as a cause before blaming software.

---

### Post by SushiR on 2011-05-30
> **3xp10r3r|X13 said:**
> Just switch to K/ubuntu - Installing the kde desktop environment!

Awesome design + useful widgets + very easy to handle = KDE

Honestly...someone asks for help with a problem, and you recommend another DE. Sorry, but this isn't helpful at all.

@Roasted: Did you check logs, maybe some error shows up

---

### Post by WorMzy on 2011-05-30
Even SysRq+K or SysRq+REISUB doesn't help?

I haven't used Xfce for that long, but I've never experienced anything like this.

---

### Post by 4Orbs on 2011-05-30
About the icons: I'm gonna guess that you have installed the Xubuntu-desktop on top of your original Ubuntu installation. I saw similar behavior when switching from Unity to a Classic Gnome (no effects) session. But now I have Xubuntu installed from the CD (only Xubuntu) and have not seen any graphics problems with the desktop, although playing videos produces video tearing which occurs whether compositing is turned on or off.

The only other problems I have with Xubuntu are either sound related (distorted sound - fixed with [THIS]("http://ubuntuforums.org/showpost.php?p=9948061&postcount=2")) (sound disappears after logout>login to another account - fixed only by reboot) or Thunar related (Thunar doesn't unmount my storage partition when logout; so that partition becomes inaccessible when login to another account) and (Thunar very slow to load the first time it is opened).

EDIT: Oh, I forgot about these problems - no sound, even though I selected my preferred sound card in the mixer settings (fixed by installing gnome-media package and then using gnome-mixer to turn-off the other, unwanted sound device). Thunar - someone removed the Trash icon from Thunar-root. Why would they do that?

To sum it up: I agree with post #2... at this moment Kubuntu is the least buggy of those three Natty releases, but I still love Xubuntu the most.

---

### Post by linuxinstalledfromhdd on 2011-05-30
> **Roasted said:**
> I have Ubuntu 11.04 running with XFCE installed (Xubuntu Desktop). I thoroughly enjoy it, but I'm having some issues that I never experienced in Gnome or Unity.

Sometimes my system just locks up. Period. Done. Over. No saving it. Mouse is locked and everything is just frozen. I power off, back on, I'm good for a while. I also had just a few minutes ago all of my icons in the panel turn to a white square. I click on the icon where the logout menu is, thinking I could log out and back in, and it says failed to execute. About 20 seconds later, it did another hard lockup.

Now, I love XFCE, but really? Is anybody else seeing this?

The only other system that I have that environment running on is in Pure Debian. And it works great.  If you want to install Debian and compare the results you can find out more here:

[http://crunchbanglinux.org/downloads/statler/20110207/](http://crunchbanglinux.org/downloads/statler/20110207/)

---

### Post by notoriousdbp on 2011-05-30
I have xubuntu 11.04 and it's a bit buggy to be honest.  I click shut down and all it does is log out for some reason.  Playing a dvd maxes out the CPU on my machine too.  Considering it's supposed to be aimed at older hardware it's not great.

---

### Post by linuxinstalledfromhdd on 2011-05-30
I tried the Ubuntu version, and I had the same problems. I switched to debian it was resolved. I don't why that is though.

---

### Post by 4Orbs on 2011-05-30
@linuxinstalledfromhdd
Do you have xfce 4.8 installed on Crunchbang? There have been some serious changes since ver 4.6.

---

### Post by linuxinstalledfromhdd on 2011-05-30
No, I'm still using 4.6  Xfce. I wouldn't install over it with 4.8 either.  It would be better just to completely recompile it.

---

### Post by 4Orbs on 2011-05-30
Agree. I tried upgrading to xfce 4.8 on my Linux(unspoken)debian installation and it was so squirrily, I almost went blind.

---

### Post by linuxinstalledfromhdd on 2011-05-30
I bet it would work better if you completely recompiled it and installed it with Pure Debian.  As for myself, I'm totally cool with 4.6 for now.  How much different is it really going to be? And is it worth that kind of time?  It would probably be different if I wanted to debug it. I just want it to work for now.

---

### Post by 4Orbs on 2011-05-30
Things are always gonna change, whether we like it or not.

---

### Post by kerry_s on 2011-05-30
i found xubuntu to be buggy, went to lubuntu instead, so far just works.

---

### Post by linuxinstalledfromhdd on 2011-05-30
I put togather a Lubuntu from stratch, minimal install with the alternative disc of Ubuntu.  64-bit. Then I installed openbox and removed everything else I didn't need anymore.. And used Tint2 as my task bar.  Worked really well for a while, and then I noticed issues starting to creep in, and then after I tried to use it on 9.10, the gdm started to really get in the way and I had to switch to Slim.  Debian was the only real option at that point.

---

### Post by 4Orbs on 2011-05-30
Think I'll stick with Xubuntu for a while and see what future updates will bring about. Actually, I'm almost certain that I'll try installing a dozen different distros over the summer months.

---

### Post by linuxinstalledfromhdd on 2011-05-30
If you have never tried crunchbang xfce, you should. It is well worth the effort.:p

---

### Post by 4Orbs on 2011-05-30
Tried it. Loved it. Gonna give it to my wife for our anniversary.

EDIT: That sounds a little sarcastic, but I'm being honest. It's one of the top five that I've ever installed.

---

### Post by 4Orbs on 2011-05-30
@kerry_s
A 64bit version of Lubuntu would be cool. Maybe not necessary, but cool anyway.

---

### Post by Bonster on 2011-05-30
yea got few bugs on Xubuntu 11.04 also

1. I cant save sound settings, after reboot it gets reseted
2. Click Reboot and it takes u to the login screen? no idea
3. Sometimes it shutters when i browse the net
4. Random freeze other times also

This was on a fresh install everything is updated

---

### Post by Roasted on 2011-05-30
I gotta admit, this is quite disappointing. We were banking on using XFCE because it was simple, stable, and did the job well. I cannot see myself pushing to distribute XFCE into our environment when we move forth with Ubuntu. I didn't want to push Unity because of how new it was, which is why I looked elsewhere.

And KDE. No thanks. I love KDE, but I'm not feeling it at work.

Maybe it's time I start using Unity a bit more... Hmm...

---

### Post by 4Orbs on 2011-05-30
Is it possible Ubuntu might abandon Unity and go straight for Gnome3? I would rather trust that Xubuntu will be fixed soon, but then again, I'm not installing it on hundreds of computers...

---

### Post by WorMzy on 2011-05-30
> **4Orbs said:**
> Is it possible Ubuntu might abandon Unity and go straight for Gnome3? I would rather trust that Xubuntu will be fixed soon, but then again, I'm not installing it on hundreds of computers...

Unity and GNOME3 are just as bad as each other imo. You're best off sticking with GNOME2 on 10.04 (supported until 2013 on desktops), or sticking with Xfce. I doubt that Ubuntu will ever have GNOME3 as an option, especially if GNOME go ahead with [making systemd a dependency]("http://www.omgubuntu.co.uk/2011/05/gnome-to-drop-support-for-bsd-solaris-unix"), since Ubuntu uses Upstart.

If you're having problems with Xfce, chances are there's something in your home folder that's causing them. So either sort through all your config files, or create a new user and see if that helps.

At the moment, I'm getting acquainted with both Openbox, and Compiz as a stand-alone window manager.

---

### Post by linuxinstalledfromhdd on 2011-05-30
I totally agree with that.  Gnome 2 or Classic Ubuntu is the only way to go at the moment.  Everything else is still under development. :P

---

### Post by 4Orbs on 2011-05-30
I agree with the Openbox part. After using Openbox for a while, everything else just seem so.. fluffy.

---

### Post by linuxinstalledfromhdd on 2011-05-30
It's not that I think everything else is "fluffy" per say..  More like unnecessary. I'm one of those types of users that isn't into "tricking out" their display to the point where people walking pass me at barns and noble bookstore want to ask me about what kind of computer I'm using..   I just want to get the job done, and I don't really want all that extra stuff.  I'm not really trying to impress other people.  Some wallpaper, and that's it.  :) lol

Yeah, Openbox rocks.  XFCE is good great too.  That way you don't have to give up everything you normally expect from an environment.  Openbox can be somewhat sparse.

---

### Post by 4Orbs on 2011-05-30
If I know company is coming to visit, I'll switch to the fluffy desktop session. Is that vanity or "passing along the good news"?

---

### Post by linuxinstalledfromhdd on 2011-05-30
I do that sometimes if I am on a date with a girl that want to impress.  I remove the wallpaper of gwen stephani, and hide my anime collection, and remove the icon for pokeman II.  Most of the girls I go for don't really know how to use a computer so it's all good. :)

---

### Post by 4Orbs on 2011-05-30
I put the fluffy desktop on my wife's account once, and she just bitchslapped me. She wasn't impressed. Fair warning.

---

### Post by 3xp10r3r|X13 on 2011-06-01
> **SushiR said:**
> Honestly...someone asks for help with a problem, and you recommend another DE. Sorry, but this isn't helpful at all.

@Roasted: Did you check logs, maybe some error shows up

so here we are.. in the end - the user has switched to another DE..hmm let me think..wasn't that stupid to recommend another DE?

Personally I made the experience, that threads ,related to desktop environments, usually don't end up being solved, because there are just so many packages to cover, where the error might exist in. 

So don't blame me, while you are just moaning around and give some vague advices concerning logs. In the most cases, the user has already checked them before he posts a thread, or , if you are suggesting that he didn't, just tell him how to(well you know, if he didn't check them, he - the user having the problem - probably doesn't know how to) . (just referring to "sry, but this isn't helpful at all")

Sorry but you just made me angry

---

### Post by Roasted on 2011-06-03
Just to recap on some issues I'm having, I feel like XFCE isn't usable for more than 20 minutes without issues. These issues have been duplicated on two different laptops. Both setups are 11.04 Ubuntu w/ XFCE installed, using the Xubuntu Session option at the login screen.

Some users told me they think that might be it, and that I should use "XFC" at the login screen or else install a vanilla Xubuntu instance. I've heard several people say now that the root of my issue could be the Xubuntu desktop clashing with the fact I'm on an Ubuntu machine. Seems a little ridiculous, but nonetheless, if that's the issue, that's the issue.

I'm going to begin further testing by using the XFCE Session from here on out at the login screen. Considering the frequency of issues I've been seeing, that should tell me relatively quickly whether or not it's the solution.

Pop quiz question for absolutely no reason at all - can anybody tell me what the difference is from XFCE Session and Xubuntu Session? Does a vanilla Xubuntu install have this? Or is this just with Ubuntu w/ Xubuntu-Desktop installed?

---

### Post by 4Orbs on 2011-06-03
System Lockups: I am wondering if you have enabled the proprietary driver for your graphics card? The only time I have ever experienced lockups is when the screensaver kicks-in while the driver is not enabled. Some of those screensavers are graphics-intensive. The lack of a driver might also be to blame for the icons becoming white squares. Since you are using an xubuntu session, you may want to go into the xfce settings manager and into "Window Manager Tweaks" and turn-off compositing.

---

### Post by Roasted on 2011-06-06
Both laptops are running Intel graphics cards, so everything should be included.

I am beginning to have significant issues with one of the two laptops, which makes me think my issue there isn't XFCE specific. I'm beginning to get failures to boot as if it cannot find the disk half the time. I also began using Unity and experienced the exact same thing there.

I'm on my other laptop for now, and I intend to do a full format of the problematic one and do a scan of the hard drive to make sure it responds without issue. (I assume you can do that with solid state drives?)

Nonetheless, I'm continuing on using XFCE on my other laptop for now. We'll see what happens.

---

### Post by irv on 2011-06-06
> **Roasted said:**
>  Pop quiz question for absolutely no reason at all - can anybody tell me what the difference is from XFCE Session and Xubuntu Session? Does a vanilla Xubuntu install have this? Or is this just with Ubuntu w/ Xubuntu-Desktop installed?

Maybe I can help with somewhat of an answer. I got tired of Unity and Gnome 3, and was going back to Ubuntu 10.10 when I decided to go to Xubuntu 11.04 with Xfce 4.8. And that is what I am using right now. Over all it has been running great for almost two weeks now. The only issues I have had were some of my apps running in the panel disappeared so I had to re-install them. I have a video problem but only in Firefox 4 and only with Hulu. The video runs OK, it is in the Hulu menu where the display problem is. Out side of this it is really running great. For the record I just did a clean install of xubuntu with a format of a Ubuntu 10.10 partition. I keep all my files on a separate partition so it really was a nice clean install.
Hope this helps.

---

### Post by bhold on 2011-07-02
I've been looking for an Ubuntu-based alternative to Unity / Gnome3 as I don't have much confidence that Gnome2 will continue to be an option. I liked Xubuntu 11.04 and the XFCE option at login, but got so many hangs from the Thunar file manager that I gave up. It is definitely worth another try after the fix is available in Xubuntu, I think it is Launchpad bug 775117.

---

### Post by Roasted on 2011-07-03
Turns out the SSD I had in my one problematic laptop was indeed... bad. That solved that issue. The other laptop seems to have been fixed by a reinstallation. Perhaps my install got borked?

All I read about was the success people have with XFCE, so it was frustrating to see issues on 2 different systems like this. However, I think my issues are pretty much subsided, and I intend to use XFCE more into the future to see what kind of results I get. After all, it very well may be implemented as the main desktop environment. That is, at least, my intention. :guitar:

---

