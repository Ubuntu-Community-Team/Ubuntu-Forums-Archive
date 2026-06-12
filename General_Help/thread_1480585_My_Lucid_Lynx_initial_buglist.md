---
title: "My Lucid Lynx initial buglist"
date: 2010-05-11
forum: General Help
---

### Post by Yako no Kai on 2010-05-11
I gave lucid a try in Virtualbox and at first glance. it's the worst version of Ubuntu I've tried. 

*EDIT: Updates in italics.*
*EDIT2: At the end, I find a workaround.*

*Through researching bug reports and forums, I've since found that the majority of the bugs are all because of bugs in one thing, Plymouth.*

Here are the major bugs that showed up on a new install, after applying all updates:

[LIST]
[*]Freeze on boot if using kdm, unless splash screen is off. [url]https://bugs.launchpad.net/ubuntu/lucid/+source/plymouth/+bug/538524[/url -- *A plymouth bug.*

[*]No virtual terminals. All TTYs are black empty screens. -- *After much research, I found that this is also because of plymouth. Plymouth breaks the framebuffer, which means no console.  This bug states that it is on Nvidia hardware, but I've confirmed that it also exists on Virtualbox "hardware." https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/506717*

[*]Recovery mode gives black screen and blinking cursor. -- *Again, no working framebuffer, no console.  So plymouth again.*

[*]No way to stop kdm. Old init.d method doesn't work, nor does "service kdm stop." 2nd of these silently fails. -- *This might also be because of Plymouth.  I'm not entirely sure.  It might be just a bug in KDE, but if you choose 'Console Login' (Alt-N) at the login screen, instead of going to console, it just restarts X.  That seems quite similar to the no-console bugs I just mentioned.  Not 100%.*

[*]After login, frequent freezes in a console with an endless fsck message. Fsck on this vm takes 1s from live cd but when it triggers on reboot, an hour isn't enough. I'm still not sure how I fixed this.  I tried a lot of things and eventually something stuck.  -- *I think I was wrong about this. The fsck message just happens to be the last thing that appears on screen before KDM starts.  It wasn't in the middle of fsck.  It was at the end of a very quick fsck, which happens on every boot it seems, and KDM couldn't start.  Basically the same bug as the first one: freeze on login with plymouth.*

[/LIST]

*Final updates after here.*

So it seems that the #1 problem with Lucid is plymouth.  It's similar to how the #1 problem I ad with Karmic was grub2, except that there are no alternatives or workarounds for Plymouth.  So all for a pretty login screen, Canonical broke most of the operating system.  This is extremely disheartening.  Plymouth is still not fixed, with the most recent update.

But there seems to be a way to boot without hitting those bugs.  

Thinking that, if Ubuntu Server couldn't show a console, we'd hear about it, I thought it might be working out better.  A lot of servers don't even have a GUI.  Now when I needed a server at work, I stuck with Hardy because of all the bugs in Lucid, but I thought it was worth a try to try out Lucid's server.  And it was.

I installed using the Ubuntu Server ISO (not the desktop ISO, not the alternative ISO, not the mini ISO).  So far, so good.  Then I added ubuntu-desktop.  Still good.  Then kubuntu-desktop.  And still good.  A clean, working boot, just a black screen until gdm/kdm, but all the bugs listed above were fixed.

With the above worked around, this **HUGE** bug, random complete lockups forcing a powerdown, at the moment is my top bug to watch: [http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

If it gets fixed before Karmic goes out of support, then Lucid begins to look attractive again.

---

