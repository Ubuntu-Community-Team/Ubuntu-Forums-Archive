---
title: "I can't log in. Blank screen."
date: 2010-07-17
forum: General Help
---

### Post by marphi2 on 2010-07-17
My problem is that I can't log in to Ubuntu, as you've already seen in the title. Here's what's happening:

I turn on the computer.
I see the GRUB.
I press Enter.
I see a blinking underscore (_) as if i was in a terminal.
The underscore disappears and I can see my cursor, but nothing else. I can move the cursor, but that's all I can do.

I've seen some similar problem here on the forums, but he could log in, he just couldn't see the screen.
I can't log in, so don't confuse these two problems.
Thank God for Splashtop, which enables me to post this!

Thanks in advance to whoever solves this problem!

---

### Post by Rubi1200 on 2010-07-17
Questions:

1. Is this a fresh install of Lucid?

2. What type of graphics card do you have?

---

### Post by marphi2 on 2010-07-17
> **Rubi1200 said:**
> Questions:

1. Is this a fresh install of Lucid?

2. What type of graphics card do you have?

1. No, it's not a fresh install, I've had it since it came out.

2. It's an ''on board'' graphics card. (I use an Asus EEE Box)

---

### Post by Rubi1200 on 2010-07-17
Ok, you could try this and see if it helps:

When it boots press Shift to get to the GRUB menu (you may need to play around with this e.g. hitting Shift a few times to get it right).

When you see the entry for the kernel (says something like Linux image x.xx.xx etc)
press e

Move the cursor with the arrow keys until you get to the line which ends with this:

```
ro quiet splash
```

Remove quiet splash and type xforcevesa instead (don't add anything else including extra spaces)

Then Ctrl + x to boot.

Let us know what happens.

---

### Post by marphi2 on 2010-07-17
> **Rubi1200 said:**
> Ok, you could try this and see if it helps:

When it boots press Shift to get to the GRUB menu (you may need to play around with this e.g. hitting Shift a few times to get it right).

When you see the entry for the kernel (says something like Linux image x.xx.xx etc)
press e

Move the cursor with the arrow keys until you get to the line which ends with this:

```
ro quiet splash
```Remove quiet splash and type xforcevesa instead (don't add anything else including extra spaces)

Then Ctrl + x to boot.

Let us know what happens.

When I did that, this happened:

After the underscore, text started scrolling on the screen. It was checking my mouse, keyboard, printer and whatnot.
I heard the log in screen's sound and saw my cursor again, but this time, there were text in the top left of the screen. It said this:


fsck from util-linux-ng 2.17.2
/dev/sda10: clean, 231762/526240 files, 1401468/2104832 blocks

* Starting AppArmor profiles          Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                              [OK]
* Setting sensors limit           [OK]
[COLOR=Red]* [COLOR=Black]Speech-dispatcher configured for user sessions
* Starting Winbind daemon winbind          [OK]
* Starting Common Unix Printing System: cupsd          [OK]
[COLOR=Red]* [COLOR=Black]PulseAudio configured for per-user sessions
* Enabling additional executable binary formats binfmt-support          [OK]
* Checking battery state          [OK]
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by Rubi1200 on 2010-07-17
Ok, that is all normal. Did you let it continue? What happened next?

---

### Post by marphi2 on 2010-07-17
> **Rubi1200 said:**
> Ok, that is all normal. Did you let it continue? What happened next?
Nothing happens. I can't do anything except move my mouse.

---

