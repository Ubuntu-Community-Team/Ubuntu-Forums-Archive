---
title: "Browsers keep going back"
date: 2010-10-03
forum: General Help
---

### Post by MetalMikey666 on 2010-10-03
Hi,

I've been using ubuntu on my PC for a few months now. Really love it, so decided to install it on my wife's PC too (she, also, loves it!). Only problem is that (and I've tried reinstalling it twice now) the browsers on her PC keep going "back a page" after a few seconds of bringing up any web page.

We used the WUBI installer to install the OS. Weird thing is that this happens in both firefox and chromium (I thought it was a firefox bug at first but as it's happening in both browsers I'm thinking it's something else)

I am a total Ubuntu newbie myeslf too, but I love the OS and really want to find a way to work on this other PC. Does anyone have any insight into what this might be or how I could fix it?

Thanks guys (first post!)

-Mikey

---

### Post by MetalMikey666 on 2010-10-07
Nobody any idea what could be causing this? Iv'e tried a fresh install again and the same thing keeps happening :( 

It's definitely not a mouse glitch because I've tried two mice in there now.

---

### Post by lovinglinux on 2010-10-07
> **MetalMikey666 said:**
> Nobody any idea what could be causing this? Iv'e tried a fresh install again and the same thing keeps happening :( 

It's definitely not a mouse glitch because I've tried two mice in there now.

Fresh install of Ubuntu or Firefox?

---

### Post by MetalMikey666 on 2010-10-08
I've tried three fresh installs of ubuntu, and the problem occurs in both chromium AND firefox.

---

### Post by MetalMikey666 on 2010-10-08
I've tried pretty much everything now. 

[LIST]
[*]Browsers completely up to date.
[*]I have managed to recreate when both mouse and keyboard are unplugged.
[*]I have googled this to death now and there doesn't seem to be anyone having the same problem as us.
[/LIST]
As I've said above, I have succesfully managed to install this OS on my own PC without a hitch. It's just this other one that has the problem :(

---

### Post by JoyousDeath on 2010-10-08
How very interesting...

Do you have a shortcut key that somehow got linked to the browser back button?

I'm sorry, that's the only thing I can think of. :confused:

System>Preferences>Keyboard Shortcuts

**Edit**:Then again, it may be the keyboard. Try using a different one.

---

### Post by lovinglinux on 2010-10-08
> **JoyousDeath said:**
> How very interesting...

Do you have a shortcut key that somehow got linked to the browser back button?

I'm sorry, that's the only thing I can think of. :confused:

System>Preferences>Keyboard Shortcuts

**Edit**:Then again, it may be the keyboard. Try using a different one.

I thought about that too, but the OP managed to reproduce the problem with the keyboard unplugged.

I guess you have some hardware issue or driver issue, otherwise it wouldn't behave like that after a fresh install.

---

### Post by MetalMikey666 on 2010-11-13
This is the most frustrating thing ever :D

The only progress I've made is that it doesn't do it if you don't have the browser window selected, so if you go to google, search for "Hello" and then instantly click the desktop, the page stays on the "Hello" search results page. 

Not that it does me any good like!

I'm going to try a USB keyboard to see if that's what the issue is. Although I did reproduce the problem with the keyboard unplugged, I haven't tried booting from scratch with a completely different keyboard (clutching at straws though) 

Will let you know if I have any luck.

-MIkey

---

### Post by matt_symes on 2010-11-13
Hi

This is a strange issue. Might be worth checking the logs. Maybe check the .xsession-errors file in your home directory. That may contain some clue as to what is happening.

Kind regards

---

