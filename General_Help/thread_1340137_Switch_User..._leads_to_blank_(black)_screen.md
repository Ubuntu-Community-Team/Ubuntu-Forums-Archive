---
title: "Switch User... leads to blank (black) screen?"
date: 2009-11-28
forum: General Help
---

### Post by ian2112 on 2009-11-28
Hello,

When I try to use "Switch User..." it leads to a blank (black) screen.  What would be the expected result?  I am trying to switch between two users I have created.  

Related question - what key combination can I try to reset / restart / reboot safely (i.e., the equivalent to window ctr-alt-del)?  When I was stuck in the above situation (blank screen) I powered down by pressing the power button... I'd prefer a safer / softer option.

Any help is much appreciated.

---

### Post by gweinstein on 2009-12-09
I used to have the same problem in openSuSE.  I thought then that it must be a graphics card issue since even Ctrl-Alt-F1 (to go to a terminal session) didn't work (plus I had some weird patterns showing on the monitor).  If you get the terminal session after Ctrl-Alt-F1, you could kill the gnome session.  Login as root and enter:

```
skill -KILL -u <user>
```Then logout, and return to the graphical interface by pressing Ctrl-Alt-F7

When I try Switch User in Karmic, I get a blank screen.  After a second or two, if I try to wake up the system, I get the locked session dialog.  I wish I could get switch user to work.

---

### Post by sepius on 2009-12-10
I have the same issue.  But I cannot enter a shell or switch back to the desktop, my system basically stops with a blank screen and I have to reboot.  I left it for about half an hour while I had dinner, and had to reboot.

I have AMD64 with ATI card.

Are we the only ones who switch users?

---

### Post by gweinstein on 2009-12-10
ian2112:

I think this is a video card issue.  On my work desktop (ATI X1300), I am able to switch users.  Are you using an ATI video card?  Which chip?

Edit: On my home desktop (on which switch user doesn't work), I have an ATI HD 4850.

---

### Post by sjeapes on 2009-12-13
I have this problem too on an HP Laptop with an ATI graphics chip (it's a HP NX6325 with a ATI Radeon Xpress 200M chip)

As above I get a black screen and can't switch to a terminal screen to do anything. This seems to happen mostly on switching users but I think it also happens coming out of suspend (but not hibernate)

---

### Post by ian2112 on 2009-12-19
Hello,

Indeed, like others above I'm using a ATI Radeon 3870 (and AMD64).  Now... has anyone been successful in solving this?  Any thoughts on further diagnosing and solving the problem?

Thanks all!

Ian.

---

### Post by joes7 on 2009-12-19
LIVECD'S REPAIR CONSOLE. That's your friend.

---

### Post by hoki_goujons on 2010-01-06
Has anyone worked out a fix for this? I'm trying to switch to Ubuntu at home and this is kind of a showstopper. I'm on an AMDx64 (32bit Karmic) with an ATI Radeon HD 2400 PRO and the restricted drivers.

---

### Post by DemonCat1992 on 2010-01-06
I have not, personally had this problem, but I have been reading everyone's replys and I feel that maybe there may be a problem with the profile itself. On Windows, however, I have had this problem and I saw that there was something wrong with the profile. Have you tried, maybe, going onto the profile right after you boot up and see if that works? You might want to try and do a sort of virus check on it because not all systems are virus free even if it is Ubuntu The Invincible. Better to be safe than sorry. If you find that the profile is all hunky dory then you might want to try and do a check up on your video card, as in, makeing sure everything is hooked in right under the hood. Make sure that the mother board is hooked in right and all that, as well as, being dust free because that may have an effect to it too. Hope that works.:KS

---

### Post by hoki_goujons on 2010-01-06
Thanks for the reply. It's a fresh install and the profiles all work fine when you log out of one and into another, or log into one fresh from boot.
All the hardware's fine - it was running XP yesterday and had been doing so happily for a year or two.

---

### Post by hoki_goujons on 2010-01-10
I've taken off the ATI restricted drivers and now I can switch user. It's not a cure, but it'll do for now - I need the ATI drivers really.

---

### Post by vancouverite on 2010-03-09
I have this same problem.  Has anybody filed a lauchpad bug yet?  Are you all using the no-back-fill or back-clear patchs for the slow maximizing bug?

Cheers,
Van

---

### Post by pastalavista on 2010-03-09
Just some info regarding the 'hard' shutdowns. I've had this problem before and it isn't good for the filesystem. When the system freezes, you can usually reboot safely with this key-sequence:

Press and hold Alt + PrtSc(SysRq) then press, one-at-a-time in this order r,s,e,i,n,u,b

---

### Post by gweinstein on 2010-05-13
Problem seems to have resolved itself with upgrade to 10.04.

---

