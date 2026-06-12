---
title: "boot hangs"
date: 2009-11-16
forum: General Help
---

### Post by Ron_ on 2009-11-16
Please help.  I am a newbie in serious trouble.

A few weeks ago, I successfully installed 9.10 for dual-boot with Windows7.  I installed /, /home, /usr, /var and swap in encrpted partitions.  Since LVM2 prompts me for a password, I set Ubuntu to log me on automatically as the single user.  I  launch Firestarter at Startup, so it prompts me immediately for my password for sudo.  All was well until today, when I made a series of changes and errors.

1) I installed the cube and various ComPizConfig add-ons and changed a few key bindings.  No apparent problems so far.
2) I repositioned my bottom panel to the left, with auto-hide.  This is where my problems began.  It would not un-hide.
3) I added new panels on the bottom, right and a second panel at the top with auto-hide.  Now my main top panel, which does display, does not work.
4) I looked around the Forums for ideas, and I came upon the suggestion to use Alt-Ctrl-F1 to get a terminal.  I did this and got a black screen with a login prompt.  Repeated login attempts failed. In exasperation, I hit Alt-Ctrl-Del.
5) Ubuntu hung on the brown screen at boot.  I powered down and up again.
6) Ubuntu hung again in the same place.  I used Alt-Ctrl-F1 successfully to get a good $ prompt, but I didn't know what to do next.  I hit Alt-Ctrl-Del.
7) I tried booting Ubuntu in recovery mode, but when I selected Resume Normal Boot, I encountered all the same problems.

Please help!

---

### Post by Giblet5 on 2009-11-16
Flip to the text console via Ctrl+Alt+F1

At the login: prompt, enter your username and hit enter.
At the Password: prompt, enter your password (nothing will echo) and hit Enter.

You should be at a shell prompt "/home/blahblah/: $ ".

Enter these commands:
```
mkdir config-wrong
mv .gconf* .config config-wrong
sudo /etc/init.d/gdm restart ; exit
```

That last command will prompt you for your password, just like above. Provide it and hit Enter.

You'll automatically flip back to the login screen. Log in.

Everything should be back to the way it was when you installed.

---

### Post by Ron_ on 2009-11-16
Thank you, giblet5.  It was pretty upsetting to loose the hole GUI based on what seemed to be a fairly small cosmetic change to the desktop.  I have been really enjoying my new Ubuntu system, but I was unprepared for its apparent fragility.

Your fix brought me back to a pristine desktop, reflecting none of my customizations.  Is there any fairly safe way to salvage some of the information in config-wrong, or should I just try to repeat my moves.  (A full backup of /home was scheduled but did not yet happen.)  The .config directory seems not to have been modified since yesterday.

---

### Post by Ron_ on 2009-11-16
Thanks so much, again.  Damage was not too bad, so I was able to retrace my steps.

---

