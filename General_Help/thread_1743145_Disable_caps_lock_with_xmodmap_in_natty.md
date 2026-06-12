---
title: "Disable caps lock with xmodmap in natty"
date: 2011-04-29
forum: General Help
---

### Post by noteventime on 2011-04-29
I just upgraded machine to natty, after which the xmodmap configuration remapping capslock stopped working (as in not doing anything at all). Running xmodmap manually (-e "clear Lock") doesn't have any visible effect either. 

I haven't tried doing this on another machine (I'm only close to one machine running ubuntu and reinstalling seems rather overkill), but the same config worked before the upgrade, and is working on another machine running arch.

Is anyone else having these issues and, if so, has anybody found a solution? The line of interest is, simply, "clear Lock".

---

### Post by bernieke on 2011-04-30
I'm having the same problem. I'm remapping Caps_Lock to mod5 for use by xmonad, and it's simply not working, even though the xmodmap output seems to be correct.
Caps lock still acts like caps lock.

```

bernieke@hermes:~$ xmodmap                                                                                                                                              
xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock      
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Alt_R (0x6c),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        Caps_Lock (0x42),  ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)
```

---

### Post by xanderaech on 2011-05-02
Same exact issue. Has something changed with xmodmap in Natty?

---

### Post by superhick on 2011-05-03
Doesn't work for me either, however, you can disable it by going to:

keyboard > layouts > options > caps lock key behavior 
and disable it.


cheers

---

### Post by noteventime on 2011-05-05
> **superhick said:**
> Doesn't work for me either, however, you can disable it by going to:

keyboard > layouts > options > caps lock key behavior 
and disable it.


cheers

Very nice indeed! There's also an option to remap caps lock to mod4, solving (generally anyway) the problem of using caps lock as mod key when running xmonad in gnome. 

Marking this as solved, even though the question is not strictly solved (still no information on why xmodmap has no effect).
Thanks!

---

### Post by bernieke on 2011-05-16
I found a solution to my problem as well.

in gnome-keyboard-properties I just had to set caps lock as the key to choose the 3th level modifier, this corresponds to mod 5.

That gave me my old behavior back.

---

### Post by CodeFarmer on 2011-05-17
This isn't solved for me at all.

Background: I have a smallish laptop, and I've built my installation up with a base install and adding packages as I go. I can't use Unity, and I don't want Ubuntu Classic; I was very happy with Awesome as my window manager in Maverick. I've reinstalled with Natty, and my specific layout was mapping Caps Lock to the Control key. I had this in my .xsession:

xmodmap -e "remove lock = Caps_Lock"
xmodmap -e "add control = Caps_Lock"

and life was good.

My problems, in chronological order, are these:

1) gnome-keyboard-config has over a hundred megabytes of dependencies that aren't already on my machine.

2) Swallowing this and installing it, then resetting my default window manager (Ubuntu has installed Unity
as one of the dependencies, as well as Ubuntu Classic, thanks for that), I run gnome-keyboard-config. It turns out that I can do a lot of different things to my Caps Lock key, but *mapping it to Control is not one of those things. *If I look under Control options though, I can swap them. This isn't what I want, but it's close. But it's not over yet:

3) Restarting X loses the settings. Until I run gnome-keyboard-properties again! I don't have to manually reset them, just start the program. Then click 'OK'.

3a) gnome-keyboard-properties has an --apply option! According to the documentation, it just runs it from the command line and does the settings. This seems good, I can tuck this into my .xsession. Except *it's completely ignored.* It starts the GUI anyway, and pauses my X session until I click 'OK'

So my current situation is that I have 100Mb of crap I will never use on my hard drive, my keyboard mapping is still not quite what I actually want, and I have to click 'OK' every time I start an X session. Not feeling very SOLVED.

(I also had to symlink .xsession to .xprofile, for reasons known only to GDM, but that's a minor inconvenience.)

Anyway, all advice gratefully received. I'm not quite annoyed enough to go back to Maverick; Natty is much better in many regards that matter to me, but this is pretty frustrating.

---

### Post by CodeFarmer on 2011-05-18
All right, a little closer to SOLVED.

Although gnome-keyboard-settings --apply doesn't work (will file a docs bug), it turns out the reason I needed to start it up was because it then triggered gnome-settings-daemon.

Adding 'gnome-settings-daemon' to my .xprofile removed the annoying config panel from my X session startup. Awesome WM now works as it should.

I still want xmodmap back. Needing to install GNOME so I can control my keyboard in X is not so hot, especially when I still don't end up with exactly the layout that I had before :P

---

### Post by gmargo on 2011-05-18
> **CodeFarmer said:**
> mapping Caps Lock to the Control key.

To map Caps-Lock to be an additional Control key, try the following input to **xmodmap(1)**:
```

keycode 66 = Control_L
clear Lock
add Control = Control_L

```

---

### Post by CodeFarmer on 2011-05-18
Aha. Thankyou!

So mapping via keycodes still works, but the names don't (necessarily)? That's interesting.

Anyway, issue is definitely SOLVED for me, am following the bug report ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/777882]("http://https//bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/777882")) in the meantime to see what's happened.

Thanks again :)

---

### Post by dr_leviathan on 2011-06-18
As far as I can tell the xmodmap stuff is legacy - none of the helpful tips from 2006 worked for me.  I finally found a working solution in this forum thread:

[http://ubuntuforums.org/showthread.php?t=1782212](http://ubuntuforums.org/showthread.php?t=1782212)

---

