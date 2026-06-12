---
title: "Numlock Weirdness"
date: 2009-08-03
forum: General Help
---

### Post by mr_skater99 on 2009-08-03
I have spent a day or two searching the forums - but no one seems to have the same problem as me - so i am starting a new thread.

Running 9.04 64bit.

When i boot up - my numlock led is on and i can type numbers on the keypad.

This continues through to the gnome login screen - led still on and can still type numbers.

BUT once i have logged in the numlock stays "on" but the led turns off.  So the led and actual numlock are out of sync.  

Here's the kicker:  I could maybe live with that - but i use ubuntu in a corporate environment - and use citrix quite a lot.  When i load up a citrix app - it thinks the numlock is off (like the keyboard led says) and i have to turn it on.

So LED is now on - numlock is on in citrix app - but off on any gnome app.

Can someone help me out - this is driving me insane.  I have tried the ****+numlock thing - wasn't on in the first place.  As well as having a play with numlockx - didn't change a thing.

Cheers.

---

### Post by SuaSwe on 2009-08-03
This is all I could find on that subject of any relevance:

[https://bugs.launchpad.net/ubuntu/+source/numlockx/+bug/218202](https://bugs.launchpad.net/ubuntu/+source/numlockx/+bug/218202)

Obviously it's in Hardy but perhaps some of it could be of use? :)

---

### Post by mr_skater99 on 2009-08-03
Thanks for the suggestion - i've trid most of that already.

What is also interesting, if i open gconf-editor, and got to desktop-gnome-peripherals-keyboard-host-[hostname]-0

There is a numlock setting there.  It matches with the LED - ie when ticked (on) the LED is on.  And if i untick it the led turns off.  But the actual behaviour of hte numlock is reversed still - ie led on - numlock off - and vica versa...

---

### Post by SuaSwe on 2009-08-04
Isn't there a Num Lock setting in the BIOS you can fiddle with? I seem to recall seeing it there at some point.

---

### Post by Tteddo on 2009-08-04
Yes, but that's only to set it on or off at boot. I saw your problem one time on a faulty keyboard. Can you try a different one?

---

