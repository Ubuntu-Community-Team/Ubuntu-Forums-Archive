---
title: "My SHIFT key stopped working!"
date: 2010-03-29
forum: General Help
---

### Post by Flexico on 2010-03-29
When typing in a text box (such as in a text editor, in-browser or renaming files) my shift-key, when used with another key, does nothing. No capitols, no symbols, nothing. It DOES, however, still work for GNOME commands, such as Ctrl-Alt-Shift-left/right for workspace navigation.

I can't figure out what might have changed recently that would cause this. HELP!

---

### Post by gmargo on 2010-03-29
Sometimes VMware leaves my shift and control keys non-functional, so I keep a desktop icon link to **setxkbmap** from the x11-xdb-utils package.  Try running **setxkbmap** with no options and see if that helps.  For other terminal initialization stuff, the **reset** command from the ncurses-bin package will reinit the terminal.

---

### Post by Flexico on 2010-03-30
Thanks -- I'll try this when I get back on my comp. =)

---

### Post by Flexico on 2010-03-31
> **gmargo said:**
>  Try running **setxkbmap** with no options and see if that helps.

I tried it and it seems to have no effect. Any other ideas?

---

### Post by gmargo on 2010-03-31
Is this all the time?  Even just after a reboot?  Or does it start sometime later?

---

### Post by Flexico on 2010-03-31
> **gmargo said:**
> Is this all the time?  Even just after a reboot?  Or does it start sometime later?

All the time, I've rebooted, changed settings all over the place, nothing seems to work.

---

### Post by gmargo on 2010-03-31
Can you try booting from a LiveCD?  Then we'll know if it's software or hardware.

---

### Post by Flexico on 2010-03-31
> **gmargo said:**
> Can you try booting from a LiveCD?  Then we'll know if it's software or hardware.

Tried it. Worked fine, definitely software.

---

### Post by gmargo on 2010-03-31
What about a normal console login?  (Ctrl-Alt-F2 type)

---

### Post by Flexico on 2010-04-01
when i did that, i was able to use the shift key -- but then i couldn't figure out how to get back into gnome and ended up rebooting, and then i was right back where i started.

---

### Post by linuxpenguin on 2010-04-01
I was having this same problem yesterday.  (Went to post on here but first I forgot my password and then I didn't type it correctly because of the Shift key, and I got locked out :( .)  I figured out that it was due to some change that was made to my Compiz configuration (I didn't change it, but somehow it got changed).

If you have compizconfig, open it up (System > Preferences > CompizConfig Settings Manager).  Click on "Commands".  When I opened this up last night, I found that Command line 0 was filled in, although I never filled it in.  So I cleared it.  Then click on "Key Bindings" tab.  Yesterday I saw that one of these key bindings (forget which one) was set to "Shift+F19" which isn't really a possible key combination to my knowledge, and I never use these commands anyway so I just cleared it.

That fixed it for me.  So did turning off Compiz and just using Metacity, but I don't like that option as much.

---

### Post by gmargo on 2010-04-01
> **Flexico said:**
> when i did that, i was able to use the shift key -- but then i couldn't figure out how to get back into gnome and ended up rebooting, and then i was right back where i started.

Alt-F7 will get back to the X display.

---

### Post by Flexico on 2010-04-01
> **gmargo said:**
> Alt-F7 will get back to the X display.

Thanks! That actually helped another problem I was having, too. =P

---

### Post by Flexico on 2010-04-01
> **linuxpenguin said:**
> I was having this same problem yesterday.  (Went to post on here but first I forgot my password and then I didn't type it correctly because of the Shift key, and I got locked out :( .)  I figured out that it was due to some change that was made to my Compiz configuration (I didn't change it, but somehow it got changed).

If you have compizconfig, open it up (System > Preferences > CompizConfig Settings Manager).  Click on "Commands".  When I opened this up last night, I found that Command line 0 was filled in, although I never filled it in.  So I cleared it.  Then click on "Key Bindings" tab.  Yesterday I saw that one of these key bindings (forget which one) was set to "Shift+F19" which isn't really a possible key combination to my knowledge, and I never use these commands anyway so I just cleared it.

That's it! THANK YOU! That was *exactly* it, and the command was "grandr". I think I know how it happened now, Lol. Thanks again!

---

### Post by linuxpenguin on 2010-04-25
> **Flexico said:**
> That's it! THANK YOU! That was *exactly* it, and the command was "grandr". I think I know how it happened now, Lol. Thanks again!
Sorry to resurrect an old thread - but was it ever discovered what was causing this to get set in the first place?  I never set that up, it must've happened after an update or something.

---

### Post by Flexico on 2010-04-25
> **linuxpenguin said:**
> Sorry to resurrect an old thread - but was it ever discovered what was causing this to get set in the first place?  I never set that up, it must've happened after an update or something.

> **linuxpenguin said:**
> If you have compizconfig, open it up (System > Preferences > CompizConfig Settings Manager).  Click on "Commands".  When I opened this up last night, I found that Command line 0 was filled in, although I never filled it in.  So I cleared it.  Then click on "Key Bindings" tab.  Yesterday I saw that one of these key bindings (forget which one) was set to "Shift+F19" which isn't really a possible key combination to my knowledge, and I never use these commands anyway so I just cleared it.

:)

---

### Post by linuxpenguin on 2010-04-25
Yeah but I mean, how did these get set in the first place?  One day it was working fine and the next, I couldn't use my Shift key because of some custom key combination I didn't set up.  I cleared it out and everything was back to normal again - but how did it get put there?

I'm not having trouble with this any more - it just makes me wonder why this might've happened.

---

### Post by Flexico on 2010-04-26
> **linuxpenguin said:**
> Yeah but I mean, how did these get set in the first place?  One day it was working fine and the next, I couldn't use my Shift key because of some custom key combination I didn't set up.  I cleared it out and everything was back to normal again - but how did it get put there?

I'm not having trouble with this any more - it just makes me wonder why this might've happened.

I have NO IDEA. But at least we know how to fix it.

---

