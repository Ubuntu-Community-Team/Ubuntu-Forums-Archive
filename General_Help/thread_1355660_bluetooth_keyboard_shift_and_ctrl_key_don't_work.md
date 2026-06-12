---
title: "bluetooth keyboard shift and ctrl key don't work"
date: 2009-12-15
forum: General Help
---

### Post by juicestain on 2009-12-15
hi there.

this post is all lowercase because i'm having a problem with my rocketfish bluetooth keyboard.

i've been searching for an answer to this and as a linux n00b i'm kinda stumped. i've tried this on a ubuntu desktop install and now a mythbuntu install, both 9.10. my shift key and my control key just won't work. i've tried changing my keyboard layout, changing my desktop appearance from normal to none, and i've even tried the 'gdesklets configure' command from terminal... even though gdesklets isn't installed. 

i'm not sure if this is a hardware issue or a software issue as i don't know how to test it. 

does anyone know how to fix this

p.s.-that last sentence would have had a question mark on it, but i can't hold shift to make one....

---

### Post by juicestain on 2009-12-15
bump

anyone

---

### Post by juicestain on 2009-12-16
so after some googling, i found xev... and when i press shift, ctrl and the 'winkey' they return as keypresses.... however i noticed that the xstringlookup returns 0 bytes. heres lines from my xev.

> KeyPress event, serial 34, synthetic NO, window 0x3c00001,
    root 0x13c, subw 0x0, time 93363526, (-350,-75), root:(521,397),
    state 0x0, keycode 65 (keysym 0x20, space), same_screen YES,
    XLookupString gives 1 bytes: (20) " "
    XmbLookupString gives 1 bytes: (20) " "
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x3c00001,
    root 0x13c, subw 0x0, time 93363668, (-350,-75), root:(521,397),
    state 0x0, keycode 65 (keysym 0x20, space), same_screen YES,
    XLookupString gives 1 bytes: (20) " "
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x3c00001,
    root 0x13c, subw 0x0, time 93369672, (-350,-75), root:(521,397),
    state 0x0, keycode 105 (keysym 0xffe4, Control_R), same_screen YES,
    XLookupString gives 0 bytes: 
  **  XmbLookupString gives 0 bytes:** 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x3c00001,
    root 0x13c, subw 0x0, time 93369673, (-350,-75), root:(521,397),
    state 0x4, keycode 105 (keysym 0xffe4, Control_R), same_screen YES,
   ** XLookupString gives 0 bytes:** 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x3c00001,
    root 0x13c, subw 0x0, time 93371273, (-350,-75), root:(521,397),
    state 0x0, keycode 62 (keysym 0xffe2, Shift_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x3c00001,
    root 0x13c, subw 0x0, time 93371290, (-350,-75), root:(521,397),
    state 0x1, keycode 62 (keysym 0xffe2, Shift_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x3c00001,
    root 0x13c, subw 0x0, time 93377889, (-350,-75), root:(521,397),
    state 0x0, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x3c00001,
    root 0x13c, subw 0x0, time 93378024, (-350,-75), root:(521,397),
    state 0x40, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 36, synthetic NO, window 0x3c00001,
    mode NotifyNormal, detail NotifyNonlinear



how can i map these keys

---

### Post by hydrogen18 on 2009-12-31
i have the same exact keyboard and the same exact problem. what is going on here

---

### Post by hydrogen18 on 2009-12-31
I did some more tests. xev shows X as receiving the event identically to whenever I press a modifier key on my laptop's internal keyboard. In other words, xev doesn't show any difference between pressing shift on my laptop's keyboard and the rocketfish keyboard. However its clear that the one from the rocketfish bluetooth keyboard gets ignored. This happens under multiple environments, a terminal, jwm, gnome. The really interesting part is that if I press shift on my laptop's internal keyboard and press keys on the rocketfish bluetooth keyboard then they get capitalizes. It's like X is just ignoring modifiers from the bluetooth keyboard.

---

### Post by brainsick on 2010-01-02
I just picked one of these up from Best Buy today.  Having the same problem.

I *do* get different results from xev when using one keyboard vs another.

xev output from working keyboard (tested shift-, ctrl-, alt-: /):


```

KeyRelease event, serial 30, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13558850, (-955,530), root:(775,581),
    state 0x10, keycode 36 (keysym 0xff0d, Return), same_screen YES,
"   XLookupString gives 1 bytes: (0d) "
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13563499, (-955,530), root:(775,581),
    state 0x10, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13565323, (-955,530), root:(775,581),
    state 0x11, keycode 61 (keysym 0x3f, question), same_screen YES,
    XLookupString gives 1 bytes: (3f) "?"
    XmbLookupString gives 1 bytes: (3f) "?"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13565491, (-955,530), root:(775,581),
    state 0x11, keycode 61 (keysym 0x3f, question), same_screen YES,
    XLookupString gives 1 bytes: (3f) "?"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13566619, (-955,530), root:(775,581),
    state 0x11, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13568187, (-955,530), root:(775,581),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13568844, (-955,530), root:(775,581),
    state 0x14, keycode 61 (keysym 0x2f, slash), same_screen YES,
    XLookupString gives 1 bytes: (1f) ""
    XmbLookupString gives 1 bytes: (1f) ""
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13569004, (-955,530), root:(775,581),
    state 0x14, keycode 61 (keysym 0x2f, slash), same_screen YES,
    XLookupString gives 1 bytes: (1f) ""
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13569772, (-955,530), root:(775,581),
    state 0x14, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13571228, (-955,530), root:(775,581),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13571676, (-955,530), root:(775,581),
    state 0x18, keycode 61 (keysym 0x2f, slash), same_screen YES,
    XLookupString gives 1 bytes: (2f) "/"
    XmbLookupString gives 1 bytes: (2f) "/"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13571836, (-955,530), root:(775,581),
    state 0x18, keycode 61 (keysym 0x2f, slash), same_screen YES,
    XLookupString gives 1 bytes: (2f) "/"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13572516, (-955,530), root:(775,581),
    state 0x18, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```



xev output from modifier-deprived keyboard:

```

KeyRelease event, serial 29, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13721164, (444,-256), root:(450,616),
    state 0x10, keycode 104 (keysym 0xff8d, KP_Enter), same_screen YES,
"   XLookupString gives 1 bytes: (0d) "
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13724085, (444,-256), root:(450,616),
    state 0x0, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13724578, (444,-256), root:(450,616),
    state 0x11, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 38, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13724578, (444,-256), root:(450,616),
    state 0x10, keycode 61 (keysym 0x2f, slash), same_screen YES,
    XLookupString gives 1 bytes: (2f) "/"
    XmbLookupString gives 1 bytes: (2f) "/"
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13724667, (444,-256), root:(450,616),
    state 0x10, keycode 61 (keysym 0x2f, slash), same_screen YES,
    XLookupString gives 1 bytes: (2f) "/"
    XFilterEvent returns: False

KeyPress event, serial 38, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13727595, (444,-256), root:(450,616),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13728113, (444,-256), root:(450,616),
    state 0x14, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 38, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13728113, (444,-256), root:(450,616),
    state 0x10, keycode 61 (keysym 0x2f, slash), same_screen YES,
    XLookupString gives 1 bytes: (2f) "/"
    XmbLookupString gives 1 bytes: (2f) "/"
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13728223, (444,-256), root:(450,616),
    state 0x10, keycode 61 (keysym 0x2f, slash), same_screen YES,
    XLookupString gives 1 bytes: (2f) "/"
    XFilterEvent returns: False

KeyPress event, serial 38, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13730572, (444,-256), root:(450,616),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13731149, (444,-256), root:(450,616),
    state 0x18, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 38, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13731149, (444,-256), root:(450,616),
    state 0x10, keycode 61 (keysym 0x2f, slash), same_screen YES,
    XLookupString gives 1 bytes: (2f) "/"
    XmbLookupString gives 1 bytes: (2f) "/"
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4c00001,
    root 0xb0, subw 0x0, time 13731261, (444,-256), root:(450,616),
    state 0x10, keycode 61 (keysym 0x2f, slash), same_screen YES,
    XLookupString gives 1 bytes: (2f) "/"
    XFilterEvent returns: False

```

You can see that in the modifier-deprived xev log the modifiers are immediately "released".  That explains why the modifier isn't being applied to the key, but why is the keyboard behaving this way?

---

### Post by brainsick on 2010-01-10
Bump.  Can anyone provide any insight into whether this is a plain 'ol broken keyboard or whether there's something on the software side we can do?

I really like the layout of this keyboard, but I'm going to return it if I can't get the modifiers working correctly.

---

### Post by elrod on 2010-02-05
Wish i had seen this thread before buying this keyboard. Does anyone have an update? If I want to hack where would i start?

---

### Post by sdlynx on 2010-03-07
> **elrod said:**
> Wish i had seen this thread before buying this keyboard. Does anyone have an update? If I want to hack where would i start?

Same here.  I guess I'm bumping this thread as well...

---

### Post by tekoholix on 2010-03-08
I believe that I am having the same trouble, but I'm running Kubuntu Lucid.

Hadn't yet realized that the CTRL was also not working, until finding this thread, and am now aware that ALT has the same issue.

I'd sure like to be able to use this mouse/KBD combo that I've purchased, but I guess I'll wait until this issue can be resolved...

---

### Post by CampDrex on 2010-03-26
same problem running karmic 9.10

---

### Post by tekoholix on 2010-03-29
Oddly enough, search upon search up until now yielded no answers.  Moments ago, I found this thread:

[http://ubuntuforums.org/showthread.php?t=1368160](http://ubuntuforums.org/showthread.php?t=1368160)

There, you'll find a workaround that makes things work better, altho not yet flawless...

---

### Post by freehunt on 2011-03-12
I know this is a very old thread, but no one has responded with an answer and there's many people still waiting. I'd like to throw my hat in as one of them.

---

### Post by tekoholix on 2011-03-25
I'd also like to bump this again, simply for the fact that there's been no real attention to the issue, anywhere that I've seen.  the other thread that I referenced in my last post has been ERRONEOUSLY marked as solved, while the issue still remains, and can be quite frustrating to deal with, at times...

---

### Post by ndstate on 2011-04-27
> **tekoholix said:**
> I'd also like to bump this again, simply for the fact that there's been no real attention to the issue, anywhere that I've seen.  the other thread that I referenced in my last post has been ERRONEOUSLY marked as solved, while the issue still remains, and can be quite frustrating to deal with, at times...

The workaround didn't work for you?  [http://ubuntuforums.org/showpost.php?p=8583661&postcount=2](http://ubuntuforums.org/showpost.php?p=8583661&postcount=2)

---

### Post by ndstate on 2011-04-27
I filed a bug report for this: [https://bugs.launchpad.net/ubuntu/+bug/772116](https://bugs.launchpad.net/ubuntu/+bug/772116)

---

### Post by idoitprone on 2011-04-27
this is a very interesting thread. From those xev logs, the keys could only read the press event but not the release event. You guys should test it on the tty console. So you can isolate it to the xserver. Since xev does not neccessary work without the xserver, a simple test is try to use the console interrupt ^C or ^Z or whatever. Run a long console program and try to stop it If it worked then the xserver has problems.

If you cant use any worth around to enter the tty terminal, you should temporary disable you boot manager so you boot to the console.

---

### Post by tekoholix on 2011-04-29
idoitprone:  My apologies, but it is NOT xorg causing this.  true terminal / grub menu is affected as well.

pmp6nl:  the workaround you refer to is NOT, even by it's own author's description, acceptable.  It requires huge further tweaking of key-repeat settings, so that while you hold the letter you want capitalized, to push shift, you don't get a million lower-case instances of it that must be erased.  tThen, it happens lLiIkKeE tThHiIsS.  oOf course, this then requires deleting the erroneous preceding lower-case letter, before you can get on to typing further...  no bueno, not even really a workaround.  it brings further error than it works around...

thanx to both of you, though, for your attention to this1!

---

### Post by idoitprone on 2011-04-29
then, pmp6nl should also include that in the bug report. More information is better for those maintainers.

---

### Post by alaskabasil on 2011-12-31
Fyi: I had the same problem (using ubuntu studio in xfce) and found that turning on sticky keys resolved the issue.

No worries now. As evidenced by caps in this sentence and punctuation like ?? and >< }{ Etc Etc.

---

### Post by alaskabasil on 2011-12-31
uh...it worked for about an hour, then quit working....doh

---

### Post by vpharry on 2012-01-01
Call customer care and tell them the problem.... CHeck it the keyboard works on windows... most probably its a software related issue

---

