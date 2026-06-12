---
title: "HP touch buttons not working under Ubuntu 9.10 H)@RHIOFHONHKJF"
date: 2009-09-12
forum: General Help
---

### Post by Berishman on 2009-09-12
Kind of slammed the keyboard to get you in here.

I have an HP Pavillion Dv7 Entertainment PC.

That means that I have the wonderful touch sensitive buttons above the keyboard that allow me to do things such as adjust the volume, skip tracks, go back, fast forward, pause/play, TURN WIRELESS ADAPTER ON/OFF... etc.

Conveniently these buttons do not work in Ubuntu.

I do not blame Ubuntu.
I love Ubuntu.

What I need to know is, first, if any one has had this same issue, and resolved it, and if not:

HELP.

I think that when you touch one of the buttons, there is software that works (on vista) to tell the computer to do whatever, so say I push the volume control button, then a piece of software in vista sees it, and adjusts the volume...... obviously.

I just need to get the wireless switch to work.
I don't care if the rest of the buttons work.
So if there is a way to simply have your wireless adapter on ALL THE TIME in ubuntu, I would like to hear it.
I don't think there is an option within ubuntu to turn the adapter on/off is there?


Maybe finding out which piece of software senses that i have touched a button would be a good place to start?

It's not possible that software could run under Wine is it?

Oh, and finally, sorry this is so sporadically written, but needless to say me + laptop - ubuntu = bad.

---

### Post by jerrrys on 2009-09-13
here's my guess since we have a hp dv6000 with touch buttons...

i wiped vista from this laptop and replaced it with 8.04, but there was one partition on the HDD that was marked HP something something.  i left this one partition on the hdd thinking it was needed; did you?

---

### Post by Blakefreak on 2009-09-13
My wife's dv9910's buttons worked fine with Ubuntu... before she made me put Win 7 on it.  What kernel are you using?

---

### Post by Berishman on 2009-09-13
> **jerrrys said:**
> here's my guess since we have a hp dv6000 with touch buttons...

i wiped vista from this laptop and replaced it with 8.04, but there was one partition on the HDD that was marked HP something something.  i left this one partition on the hdd thinking it was needed; did you?

Yes, I left it, I should mention I still have Vista on here as well.
The HP partition you saw is probably the recovery partition.



As for which kernel I have... well.
I don't recall.

I have 9.10 though.

Should I go back to 8.04 or 9.04 maybe?

---

### Post by jerrrys on 2009-09-13
wellll so much for my guesswork; have you been here?

[http://www.google.com/search?q=hp+touch+buttons+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=hp+touch+buttons+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Berishman on 2009-09-14
> **jerrrys said:**
> wellll so much for my guesswork; have you been here?

[http://www.google.com/search?q=hp+touch+buttons+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=hp+touch+buttons+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Haha, yep.

In fact, upon clicking that link I was bombarded with purple.
(clicked links) haha

---

### Post by Ayuthia on 2009-09-14
If I recall correctly, xev is installed with Ubuntu.  You can go into the Terminal and run:
```
xev
```It should pop up a little window that has a black square in it.  You can either close that little window when you are done testing or press control-c.  As soon as you touch a key on the keyboard, it should respond.  Try pressing one of the touch buttons (like the volume button) and see if it spits something back.  If it does, then Ubuntu sees it.  If it produces something like:
```
KeyRelease event, serial 34, synthetic NO, window 0x4000001,
    root 0x9f, subw 0x0, time 36439311, (398,767), root:(399,789),
    state 0x0, keycode 123 (keysym 0x1008ff13, XF86AudioRaiseVolume), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

```
In the code box above, you will notice the XF86AudioRaiseVolume is displayed.  That shows that Ubuntu has mapped it to the volume button.  If it doesn't then it is not been linked to the correct key.

If xev does not respond to the button press, you should check dmesg.  It might have a message that contains something about mapping a key using setkeycodes.  If it does, it means that Ubuntu knows that it is there, but it has not assigned the key to anything yet.

If you get nothing at all, that means that Ubuntu does not see it.

---

### Post by Soley on 2009-09-14
@Ayuthia Wow. What a nice thing to know. I've never run into that problem but thank you for explaining so much of what xev does.

---

### Post by Berishman on 2009-09-19
> **Ayuthia said:**
> If I recall correctly, xev is installed with Ubuntu.  You can go into the Terminal and run:
```
xev
```It should pop up a little window that has a black square in it.  You can either close that little window when you are done testing or press control-c.  As soon as you touch a key on the keyboard, it should respond.  Try pressing one of the touch buttons (like the volume button) and see if it spits something back.  If it does, then Ubuntu sees it.  If it produces something like:
```
KeyRelease event, serial 34, synthetic NO, window 0x4000001,
    root 0x9f, subw 0x0, time 36439311, (398,767), root:(399,789),
    state 0x0, keycode 123 (keysym 0x1008ff13, XF86AudioRaiseVolume), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

```
In the code box above, you will notice the XF86AudioRaiseVolume is displayed.  That shows that Ubuntu has mapped it to the volume button.  If it doesn't then it is not been linked to the correct key.

If xev does not respond to the button press, you should check dmesg.  It might have a message that contains something about mapping a key using setkeycodes.  If it does, it means that Ubuntu knows that it is there, but it has not assigned the key to anything yet.

If you get nothing at all, that means that Ubuntu does not see it.

Strangely enough, ubuntu detects the volume adjust buttons, but not any of the others.

Is there a command you can use under ubuntu to turn the wireless card on or whatever?

because then i could just create a keyboard shortcut that would run that command couldnt I?

Thanks for all your help

---

### Post by harmannanda on 2010-05-27
I was using 9.10 until a few days ago but never had such problems. However, ever since I updated to 10.04, I have had similar problems. I have a dv6000. The volume controls work fine initially, but after a couple of hours they stop responding altogether. If I restart, they start working again, but only till the said time limit again. Any ideas to correcting it? I'd appreciate the help.

---

### Post by coldraven on 2010-05-27
No problem with 9.10 on Compaq 6715b.
I did read somewhere to make sure that you switch the wi-fi ON with the hardware button while you still have Windows installed and then install Ubuntu afterwards.

---

### Post by geoffsn on 2010-08-06
I sort of had/have the same issue.  I have an HP dv7 with the same touch buttons.  My boot-up time was lagging and I tried setting acpi=off on boot-up.  This made the process MUCH faster, but the touch buttons no longer worked.  Whenever I leave the acpi on at boot up, the touch buttons are recognized and work.  I don't know if this helps at all.

---

