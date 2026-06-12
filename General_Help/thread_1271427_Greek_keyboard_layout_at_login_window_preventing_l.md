---
title: "Greek keyboard layout at login window preventing login"
date: 2009-09-20
forum: General Help
---

### Post by Witepa on 2009-09-20
I added the Greek keyboard layout using GNOME's System > Preferences > Keyboard, and on reboot it has set the Greek keyboard as the layout for the gdm login window. Now, I cannot login, and even when I try to boot into recovery mode, the keyboard layout is Greek, so I cannot run any commands.

I have tried to edit both /etc/default/console-setup and /etc/X11/xorg.conf (using a LiveCD), but both were already set to the keyboard layout "us", with no mention of Greek whatsoever. I then used dpkg-reconfigure xserver-xorg and dpkg-reconfigure console-setup, but neither has fixed the problem. When I try to change the language in gdm, there is no affect on the keyboard layout.

I have read through and done everything in the following threads, to no success:
[[SOLVED]cannot change login keyboard layout (gdm)]("http://ubuntuforums.org/showthread.php?t=1153459")
[Wrong keyboard layout at login screen]("http://ubuntuforums.org/showthread.php?t=1151141")
[[SOLVED] My Keyboard Layout changed to Arabic => Can't login...]("http://ubuntuforums.org/showthread.php?p=6967917")

I cannot login at all and I can't use my machine :(. I need help ASAP!

---

### Post by Peacefulpieofdeath on 2009-09-20
Are there no little keyboard figure on your login screen that will let you change your keyboard layout.

---

### Post by Witepa on 2009-09-20
> **Peacefulpieofdeath said:**
> Are there no little keyboard figure on your login screen that will let you change your keyboard layout.
No, although I read somewhere that it was a feature for Karmic Koala's gdm.

---

### Post by calman on 2009-09-20
bump

---

### Post by Witepa on 2009-09-21
Still no solution found... this is a seemingly basic problem that is crippling me from using my computer at all. Help please!

---

### Post by StuartN on 2009-09-22
> **Witepa said:**
> Still no solution found... this is a seemingly basic problem that is crippling me from using my computer at all. Help please!

Do you not have a little "Gre" after the right hand end of your login box? If so, then clicking on it should cycle through your installed keyboards.

---

### Post by Witepa on 2009-09-22
> **StuartN said:**
> Do you not have a little "Gre" after the right hand end of your login box? If so, then clicking on it should cycle through your installed keyboards.
I do not. I was under the impression that this was not a feature in Jaunty, but it's possible that the standard US QWERTY keyboard was removed from my list of layouts, leaving me with only the Greek layout, thus disabling the menu.

If this is the case, then I just need to figure out how I can add the US QWERTY keyboard layout to the list by altering the file system by using a Live CD, because I cannot login via gdm or recovery mode. Any ideas?

---

### Post by StuartN on 2009-09-22
Well I do have a language layout option at first login, but I am still using 8.10.

Is it possible to edit your /etc/X11/xorg.conf to reset this section, where I assume your startup keyboard layout is configured?

```
#Section "InputDevice"
#	Option		"XkbLayout"	"ie"
```

---

### Post by Witepa on 2009-09-27
Still no success, I had already tried that solution though. I had /etc/X11/xorg.conf "XkbLayout" set to "us", but "ie" doesn't work either. The language layout you are talking about is there for me too, but it is just a language selector and not a keyboard layout selector. My language is still in English, it's just my keyboard that is stuck in Greek.

Does anyone know what files the gnome-keyboard-preferences changes? This problem started for me immediately after I edited those settings, and I may have deleted the US QWERTY layout from the list.

Also, where can I find a file that show's me my keyboard shortcuts as defined by GNOME? If I figure out what the layout changer shortcut is, I may be able to change it back without any trouble.

---

### Post by StuartN on 2009-09-27
> **Witepa said:**
> Does anyone know what files the gnome-keyboard-preferences changes?

~/.gconf/desktop/gnome/peripherals/keyboard/kbd

> **Witepa said:**
> Also, where can I find a file that show's me my keyboard shortcuts as defined by GNOME?

~/.gconf/apps/metacity/global_keybindings

(both are in %gconf.xml files, and the .gconf directory exactly mirrors the Configuration Editor).

Is there any chance you can log in using Unicode? For instance, pressing ctrl-shift-u 057 gives a capital W. So ctrl-shift-u each in the sequence 057 069 074 065 070 061 would give Witepa on any keyboard. Then you could just click the selector...

---

### Post by Witepa on 2009-09-27
> **StuartN said:**
> Is there any chance you can log in using Unicode? For instance, pressing ctrl-shift-u 057 gives a capital W. So ctrl-shift-u each in the sequence 057 069 074 065 070 061 would give Witepa on any keyboard. Then you could just click the selector...

Unfortunately, in the Greek keyboard layout, I cannot even access the 'u' key.

---

### Post by StuartN on 2009-09-28
> **Witepa said:**
> Unfortunately, in the Greek keyboard layout, I cannot even access the 'u' key.

I did not think of that! What is the equivalent of ctrl-shift-u on a Greek keyboard? None of the Unicode information I have says anything useful.

But if you can access and edit your ~/.gconf/desktop/gnome/peripherals/keyboard/kbd/~%gconf.xml then you will find an entry:

```
<li type="string">
<stringvalue>grp	grp:alts_toggle</stringvalue>
</li>
```

This defines "Both Alt keys" as the layout switcher and, due to a bug [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/251443](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/251443) (aren't you just the luckiest with this problem?) it does not function. If you add the following item then you will have "Both Shift keys" as an additional switcher:

```
<li type="string">
<stringvalue>grp	grp:shifts_toggle</stringvalue>
</li>
```

---

### Post by Witepa on 2009-09-28
Well, that didn't solve it... I think the us keyboard layout has possibly been removed from the list, thus leaving nothing to toggle to/from.

How would I just copy the keymap? I tried copying /etc/console-setup/boottime.kmap.gz from the LiveCD to the affected filesystem, but to no success, again :(. Is this the appropriate way to do it?

If you're curious, [here]("http://paste.ubuntu.com/280079/") is the previous boottime.kmap.gz file.

---

### Post by StuartN on 2009-09-28
Did you try altering the boot options to set a UK or US keyboard with **bootkbd=uk**, see [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Witepa on 2009-09-28
> **StuartN said:**
> Did you try altering the boot options to set a UK or US keyboard with **bootkbd=uk**, see [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I just tried that... followed the instructions to the key. I tried it both with the recovery mode and the normal, my boot line in recovery mode was the hash followed by ro single bootkbd=us (I tried it with uk too). It had no effect, it still booted up with a Greek layout. This is getting really frustrating...

---

### Post by StuartN on 2009-09-28
> **Witepa said:**
> This is getting really frustrating...

I feel your pain - so many solutions to just one problem, and none work! I hate to say it, but at this stage I would back up my ~/home and re-install.

---

### Post by alimooghashang on 2009-09-29
i have the same problem
who know what to do?
the both alt key doesn't work in changing the layout :((

---

### Post by Witepa on 2009-09-29
Well,  I think I'm gonna install on a second partition and copy over my home folder and just reconfigure everything :(. Maybe I'll fix it once I'm on the second partition though, we'll see.

> **alimooghashang said:**
> i have the same problem
who know what to do?
the both alt key doesn't work in changing the layout :((

Out of curiosity, what did you do to change the keyboard layout? Did you use the GNOME Keyboard Preferences or did you do it some other way? Did you actually remove the US keyboard layout from the list or did you just change the default layout, but leaving both on the list?

Here's what I would try if I were you:

If you can't access the recovery mode or login via gdm or tty1 (press ctrl+alt+f1 at the login screen) due to the wrong keyboard layout, login via a LiveCD and mount your Ubuntu partition (you can do this by going to places and selecting the appropriate media).

[LIST=1]
[*]Look at /etc/X11/xorg.conf (it will be something like /media/disk/etc/X11/xorg.conf from the LiveCD), and see if you find this:
```
Section "InputDevice"
	Option		"XkbLayout"	"us"
```
If it is not "us", then you should change it to it and that should hopefully fix the problem.


[*]Look at /etc/default/console-setup (again, it will be like /media/disk/etc/default/console-setup). See if it says this:
```
XKBLAYOUT="us"
```
If not, then try changing it to "us" and hopefully *that* will fix it.


[*]chroot to /media/disk (or whatever your mount point is) and try dpkg-reconfigure xserver-xorg and console setup. This will lead you through a series of prompts that will hopefully be able to reset your keyboard layout. The commands will look like the following:
```
sudo mount --bind /dev /media/disk/dev   # This is necessary to make dpkg to work properly
sudo chroot /media/disk
dpkg-reconfigure xserver-xorg
dpkg-reconfigure console-setup
```
If 1 and 2 don't work, then it wouldn't surprise me if this doesn't either. This basically automates the process of that and you might want to try this before those anyway.


[*]Try switching the keyboard shortcut for previous keyboard layout to both shift keys rather than both alts. As StuartN pointed out, using both alts at the login screen is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/251443"). Do this by editing ~/.gconf/desktop/gnome/peripherals/keyboard/kbd/~%gconf.xml to:
```
<li type="string">
<stringvalue>grp	grp:shifts_toggle</stringvalue>
</li>
```
Then try pressing both shifts at the login screen.


[*]If you can access the 'u' character in your keyboard layout, press ctrl+shift+u and then the [appropriate unicode code]("http://www.utf8-chartable.de/") for each character in your username/password to login at gdm.
[/LIST]


Good luck with this, I hope this consolidates some of the solutions that have been suggested to me in a more concise manner. While it seems like some of these solutions have worked for others, none worked for me :(. Let me know (in this thread) if it works, and if so, what did it?

Much thanks to StuartN, abrotman, Jordan_U, badiane, and catsup for their efforts (both in forums and in IRC).

---

### Post by alimooghashang on 2009-09-29
thanks
it worked
and my problem is solved

---

### Post by Witepa on 2009-09-29
> **alimooghashang said:**
> thanks
it worked
and my problem is solved

Wow, I solved your similar problem but I can't solve mine...

What exactly did it for you? (Also, what keyboard layout were you in?)

---

### Post by alimooghashang on 2009-09-29
> **Witepa said:**
> Wow, I solved your similar problem but I can't solve mine...

What exactly did it for you? (Also, what keyboard layout were you in?)
it was in "ir"
i changed it to "us"
and now it worked...
thanks

---

### Post by StuartN on 2009-09-30
I just saw this tip in a completely different problem - use a numeric password if you are multilingual. Then you can log in using any keyboard layout.

Witepa, if you can log in as root, then can you reset the password to a numeric?

---

### Post by Witepa on 2009-10-05
> **StuartN said:**
> I just saw this tip in a completely different problem - use a numeric password if you are multilingual. Then you can log in using any keyboard layout.

Witepa, if you can log in as root, then can you reset the password to a numeric?
I can't login as root, but can I change the password with chroot on a liveCD?

---

### Post by StuartN on 2009-10-05
> **Witepa said:**
> I can't login as root, but can I change the password with chroot on a liveCD?

It LOOKS simple [http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/](http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/)

---

### Post by Witepa on 2009-10-05
> **StuartN said:**
> It LOOKS simple [http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/](http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/)
Cool, that does look simple. The only issue is that my username is not numeric... and with my current gdm configuration I have to type that in as well rather than choosing from a drop down list.

---

### Post by StuartN on 2009-10-05
> **Witepa said:**
> Cool, that does look simple. The only issue is that my username is not numeric... and with my current gdm configuration I have to type that in as well rather than choosing from a drop down list.

Surely it is booting off the LiveCD, so nothing in your existing installation will have any effect? Then you just (!) chroot and reset your password.

---

### Post by Witepa on 2009-10-05
> **StuartN said:**
> Surely it is booting off the LiveCD, so nothing in your existing installation will have any effect? Then you just (!) chroot and reset your password.

Yeah, I can reset my password, but that doesn't fix the issue that I can't type in my username to gdm when I boot off my harddrive.

---

### Post by maltareef on 2009-10-17
I have the same problem but I am unable to make the changes to the xorg.conf file or any other file once the Live CD System has logged me in. What is the sequence of commands to provide me with a root or Admin user shell from within the Live CD login-session???

---

### Post by cholericfun on 2009-10-17
in the liveCd you just sudo as well, only that your passwrd is empty
( if i remember correctly)


just out of curiosity:
is there a way to work with a greek layout in the commandline?

say i wanted to "ls"
typing "&#955;&#963;" just says "command not found"
how do people who use greek kbrd use the command line??

---

### Post by @ntonius on 2009-10-17
> **cholericfun said:**
> in the liveCd you just sudo as well, only that your passwrd is empty
( if i remember correctly)


just out of curiosity:
is there a way to work with a greek layout in the commandline?

say i wanted to "ls"
typing "&#955;&#963;" just says "command not found"
how do people who use greek kbrd use the command line??

Command line is always in English. All greek users use english layout when working in terminal (keyboards have both english and greek letters on them).


> **Witepa said:**
> Yeah, I can reset my password, but that doesn't fix the issue that I can't type in my username to gdm when I boot off my harddrive.

Have you asked for help in the greek forum? [http://forum.ubuntu-gr.org](http://forum.ubuntu-gr.org)

---

### Post by maltareef on 2009-10-18
Thanks ... I used "sudo -i"   and it worked.

---

### Post by babltiga on 2010-04-16
Had same problem, boot from live cd, created new user with username "1" and password "1", loged in as "1" and added English Layout. Only question how does English layout removed from the pc :) ......

---

### Post by Witepa on 2010-04-16
> **babltiga said:**
> Had same problem, boot from live cd, created new user with username "1" and password "1", loged in as "1" and added English Layout. Only question how does English layout removed from the pc :) ......

I'm a bit confused as to what you are trying to accomplish.

Are you looking to remove the English keyboard layout completely?
Are you stuck in a non-roman keyboard layout and are unable to log in like the previous users in this thread?

---

