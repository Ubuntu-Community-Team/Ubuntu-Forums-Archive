---
title: "Ctrl+Alt+SysRq+....RSEIUB?"
date: 2009-11-05
forum: General Help
---

### Post by HousieMousie2 on 2009-11-05
I am on Kubuntu Hardy KDE3 and am having fits with Adobe CRASH Player.  I can't keep exiting the system using the power button.

I read about RSEIUB a couple of years ago and a few times since then... lol none of those mentioned which Alt key to use, they just said Ctrl+Alt+SysRq.  Of all places, I read about there being a difference between the Alt keys on a bug report, and that the correct one is the Right Alt...  It seems SysRq is not working on Jaunty in the X environment.

Is there also a preference on the Ctrl key?

Also, the instructions say wait 'a little while' between key combos... what exactly constitutes 'a little while'?  I know it will vary from machine to machine, but what is a safe amount to wait?  30 seconds? 5 minutes?  Is there such a thing as waiting too long?

Thank you for your time!

---

### Post by lswb on 2009-11-05
Usually just <alt> + <sysrq>, both kept pressed down at the same time while cycling through the R E I S U B keys, is adequate. About 5 seconds between keys is plenty or until the hard drive activity light goes out.

Some laptop and non-standard keyboards may require using Fn or other keys to produce the Alt-sysreq combination. Just google "REISUB" and you'll find lots of info.

---

### Post by HousieMousie2 on 2009-11-05
> **lswb said:**
> Usually just <alt> + <sysrq>, both kept pressed down at the same time while cycling through the R E I S U B keys, is adequate. About 5 seconds between keys is plenty or until the hard drive activity light goes out.

Some laptop and non-standard keyboards may require using Fn or other keys to produce the Alt-sysreq combination. Just google "REISUB" and you'll find lots of info.

lol I did Google REISUB and RSEIUB, that's why I had to come ask here.

(Right) Alt+SysRq, gotcha, 5 seconds/hard drive light, GREAT tip! thank you loads!

Which one is better?  Raising Skinny Elephants Is Utterly Boring, or, Raising Elephants Is So Utterly Boring?  Shifting the snyc has what effect?

---

### Post by wildweathel on 2009-11-05
Press and hold alt(just tested it, either one works on my computer)and sysrq/printscreen while you tap the buttons.  Here's what they do:

**R**aw - keyboard in raw mode.  Don't bother, you're going to be rebooting soon, so it doesn't matter.

**S**yncronize - write all data that's scheduled to go to the disk, to the disk.  You'll notice the disk light flicker after this.  Wait for it to stop.

t**E**rminate - ask all programs to quit.  Some will write data, wait for disk light to stop.  After this, you have to reboot to get a working system.

k**I**ll - tell all programs to quit and don't take "no" for an answer.   

**U**nmount - stop accepting data to be written to disk drives.  Writes all scheduled data (like Sync).  Wait for drive light to turn off.

re**B**oot - instant reboot. 

You can replace B with O to turn your computer **O**ff if you're frustrated enough.  

So, what I use is: E <10 second pause for syslog> IU <wait for disk light to turn off> S <light shouldn't turn on, but check again to be safe> B

Other possibility:
 
ctrl+alt+backspace -- force logout -- You have to enable this one in keyboard preferences (system -> preferences -> keyboard -> layout -> layout options -> key sequence to kill the X server), and there's no sysrq button in it.  This one is gentle enough that you can log back in and keep using your computer without a reboot.  You'll lose all unsaved documents, though.

---

### Post by HousieMousie2 on 2009-11-06
> **wildweathel said:**
> Press and hold alt(just tested it, either one works on my computer)and sysrq/printscreen while you tap the buttons.  Here's what they do:

**R**aw - keyboard in raw mode.  Don't bother, you're going to be rebooting soon, so it doesn't matter.

**S**yncronize - write all data that's scheduled to go to the disk, to the disk.  You'll notice the disk light flicker after this.  Wait for it to stop.

t**E**rminate - ask all programs to quit.  Some will write data, wait for disk light to stop.  After this, you have to reboot to get a working system.

k**I**ll - tell all programs to quit and don't take "no" for an answer.   

**U**nmount - stop accepting data to be written to disk drives.  Writes all scheduled data (like Sync).  Wait for drive light to turn off.

re**B**oot - instant reboot. 

You can replace B with O to turn your computer **O**ff if you're frustrated enough.  

So, what I use is: E <10 second pause for syslog> IU <wait for disk light to turn off> S <light shouldn't turn on, but check again to be safe> B

Other possibility:
 
ctrl+alt+backspace -- force logout -- You have to enable this one in keyboard preferences (system -> preferences -> keyboard -> layout -> layout options -> key sequence to kill the X server), and there's no sysrq button in it.  This one is gentle enough that you can log back in and keep using your computer without a reboot.  You'll lose all unsaved documents, though.

Thank you for replying!  I had read those descriptions (more or less) while researching RSEIUB, but the timing helps give me a good frame of reference.

Ctrl+Alt+Backspace is enabled in Kubuntu by default... it just doesn't do anything when Adobe causes a system crash.

Thank you for your time!

---

### Post by P4man on 2009-11-06
ctrl alt backspace to restart x is configured through an option called dontzap. You can edit it in xorg.conf

[https://wiki.ubuntu.com/X/Config/DontZap](https://wiki.ubuntu.com/X/Config/DontZap)

scroll down to jaunty. I imagine it will work for older versions too (although I believe it was on by default an anything pre jaunty?)

---

### Post by mcduck on 2009-11-06
> **wildweathel said:**
> Press and hold alt(just tested it, either one works on my computer)and sysrq/printscreen while you tap the buttons.  Here's what they do:

**R**aw - keyboard in raw mode.  Don't bother, you're going to be rebooting soon, so it doesn't matter.

**S**yncronize - write all data that's scheduled to go to the disk, to the disk.  You'll notice the disk light flicker after this.  Wait for it to stop.

t**E**rminate - ask all programs to quit.  Some will write data, wait for disk light to stop.  After this, you have to reboot to get a working system.

k**I**ll - tell all programs to quit and don't take "no" for an answer.   

**U**nmount - stop accepting data to be written to disk drives.  Writes all scheduled data (like Sync).  Wait for drive light to turn off.

re**B**oot - instant reboot. 

You can replace B with O to turn your computer **O**ff if you're frustrated enough.  

So, what I use is: E <10 second pause for syslog> IU <wait for disk light to turn off> S <light shouldn't turn on, but check again to be safe> B

Other possibility:
 
ctrl+alt+backspace -- force logout -- You have to enable this one in keyboard preferences (system -> preferences -> keyboard -> layout -> layout options -> key sequence to kill the X server), and there's no sysrq button in it.  This one is gentle enough that you can log back in and keep using your computer without a reboot.  You'll lose all unsaved documents, though.
I'd say that **REISUB** is the correct order. It's pointless to sync the disks (**S**) before you end all the running programs (**E**) which might still want to write to disks, meaning that you end with more data scheduled for writing to disk and would need to sync again...

X session can be killed like any other login session, with SysRq-K (so this works for both X sessions and TTY sessions, unlike the Ctrl-Alt-Backspace shortcut which only works for zapping X).

---

### Post by HousieMousie2 on 2009-11-06
> **mcduck said:**
> I'd say that **REISUB** is the correct order. It's pointless to sync the disks (**S**) before you end all the running programs (**E**) which might still want to write to disks, meaning that you end with more data scheduled for writing to disk and would need to sync again...


REISUB, thank you.  I had wondered at that, from my uneducated point of view, it seemed backwards to ask it to perform an action like that when the troublesome program was still 'active'.

> 
X session can be killed like any other login session, with SysRq-K (so this works for both X sessions and TTY sessions, unlike the Ctrl-Alt-Backspace shortcut which only works for zapping X).


To be clear... that is SysRq + k on the keyboard?  Or are you signifying something else with a capitalized k?

---

### Post by HousieMousie2 on 2009-11-06
> **P4man said:**
> ctrl alt backspace to restart x is configured through an option called dontzap. You can edit it in xorg.conf

[https://wiki.ubuntu.com/X/Config/DontZap](https://wiki.ubuntu.com/X/Config/DontZap)

scroll down to jaunty. I imagine it will work for older versions too (although I believe it was on by default an anything pre jaunty?)

lol Sorry P4man, clearly you caught my post *before* the edit.  All I can say is that I have not slept much this past week.  I knew of Ctrl+Alt+Backspace and had even tried it out once (when I first started using Linux, in Gutsy) but had not used it since with any success.  I totally missed it the first time.

So yes, you are absolutely right, it is on by default in Hardy... it just still doesn't help me when Adobe bites the big one.

---

### Post by mcduck on 2009-11-07
> **HousieMousie2 said:**
> REISUB, thank you.  I had wondered at that, from my uneducated point of view, it seemed backwards to ask it to perform an action like that when the troublesome program was still 'active'.



To be clear... that is SysRq + k on the keyboard?  Or are you signifying something else with a capitalized k?

SysRq + k, no capital K. And of course you also need to press the Alt unless you have a separate SysRq key. :) Same as with the REISUB thing.

---

### Post by HousieMousie2 on 2009-11-07
> **mcduck said:**
> SysRq + k, no capital K. And of course you also need to press the Alt unless you have a separate SysRq key. :) Same as with the REISUB thing.

lol Thank you.  I HAD to ask, just in case it meant something else... or if there was supposed to be a Shift key in there.

Yep, Alt is a must for me, SysRq is combined with PrtScn... although... hmmm, I wonder...

On my keyboard, SysRq is under PrtScn, not over it.  Wouldn't that imply that Print Screen is the one that needs the Alt and not SysRq?  Like % needs the Shift key, but 5 doesn't...?

---

