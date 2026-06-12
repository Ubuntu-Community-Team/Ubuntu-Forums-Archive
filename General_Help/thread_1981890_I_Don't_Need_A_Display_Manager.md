---
title: "I Don't Need A Display Manager?"
date: 2012-05-17
forum: General Help
---

### Post by ohnonot on 2012-05-17
Hello,
i read that it is possible to start X straight into your favorite window manager without using a display manager.
Unfortunately it was a howto for arch linux...
How could i do that in ubuntu?
i don't want to recompile the whole bootprocess, i'm too dumb for that anyway, i just want to go one step down from the destop environment and try out what's possible.
also i don't see why i need a display manager - i have only one display anyway, which is on auto login, and i can help myself if sth crashes.

any ideas? thanx in advance.
:popcorn:
ps: this is xubuntu but i'd think it's the same for all *buntu?!

---

### Post by CatKiller on 2012-05-17
TBH, you'd probably find it easier starting with something like the Server image and installing your window manager of choice rather than installing the Desktop image and stopping stuff. Either way will work OK, though.

Tutorials for one distro will largely work for other distros OK; they aren't that dissimilar. It might be a different file you edit, or the same file in a slightly different place, but you'll probably manage.

---

### Post by ohnonot on 2012-05-18
i have xubuntu installed already and am using it. i should have a partition for playing around, but i don't. so, no server image at this point though it sounds like a good idea.

i was refering to [this article]("https://wiki.archlinux.org/index.php/Start_X_at_boot") - neither bash_profile nor inittab are present on my system and creating them with the appropriate lines had no effect.

it seems that ubuntu is using a [different bootup method called upstart]("http://upstart.ubuntu.com/") which is far too complex for me.

so would anybody know where to put the crowbar to wrench out the display manager (and boot straight into X with my custom setup)?

---

### Post by Cheesemill on 2012-05-18
Instead of getting rid of the display manager just enable automatic logon, it will have exactly the same effect.

---

### Post by ohnonot on 2012-05-18
> **Cheesemill said:**
> Instead of getting rid of the display manager just enable automatic logon, it will have exactly the same effect.i am using that already.
just want to go one step further towards a minimalized & customized system.

---

### Post by lolpenguin on 2012-05-18
You can go as far as deleting the lines referring to display managers in xorg.conf and start X using startx or xinit, but...

---

### Post by zombifier25 on 2012-05-18
> **ohnonot said:**
> i have xubuntu installed already and am using it. i should have a partition for playing around, but i don't. so, no server image at this point though it sounds like a good idea.

i was refering to [this article]("https://wiki.archlinux.org/index.php/Start_X_at_boot") - neither bash_profile nor inittab are present on my system and creating them with the appropriate lines had no effect.

it seems that ubuntu is using a [different bootup method called upstart]("http://upstart.ubuntu.com/") which is far too complex for me.

so would anybody know where to put the crowbar to wrench out the display manager (and boot straight into X with my custom setup)?

Ubuntu does not use .bash_profile, it uses .profile instead.

---

### Post by ohnonot on 2012-05-18
> **lolpenguin said:**
> You can go as far as deleting the lines referring to display managers in xorg.conf and start X using startx or xinit, but...the "but..." is understood. but there's no xorg.conf?!```
$ locate xorg.conf
/usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
/usr/share/X11/xorg.conf.d/11-evdev-trackpoint.conf
/usr/share/X11/xorg.conf.d/50-synaptics.conf
/usr/share/X11/xorg.conf.d/50-vmmouse.conf
/usr/share/X11/xorg.conf.d/50-wacom.conf
/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
/usr/share/man/man5/xorg.conf.5.gz
```
- and thanks to zombifier - the file exists, but did not help here either.

---

### Post by apmcd47 on 2012-05-18
Ideally you would turn off the X display manager but I can't find out how to do that on Ubuntu right now. So how about this? 
[LIST=1]
[*]Before logging on press the key combination Ctrl-Alt-F1
[*]Log in at the login prompt
[*]type ```
xinit -- :1
```
[/LIST]
This will start a second X session on your computer. It is not ideal but at least you can try things out until you find out how to stop the display manager.

Although by the sound of it you really want to change your environment so that you use a different desktop environment. If that is the case I think this is not the correct route for you at all. 

Andrew

---

### Post by JKyleOKC on 2012-05-18
> **ohnonot said:**
> i read that it is possible to start X straight into your favorite window manager without using a display manager.
Unfortunately it was a howto for arch linux...
How could i do that in ubuntu?For a couple of years now, Ubuntu and all of its variants have used UpStart as their boot sequence, replacing the older SysV system that was pretty much the standard from the beginning. One of the most obvious differences between the two is that the "inittab" file is no longer present, and won't have much if any effect if you create it. The main, not-so-obvious, difference between the two systems is that UpStart attempts to do everything at once, while SysV does things in strict sequence.

What this means, with respect to your question, is that you really would have to make major changes to the UpStart files to prevent the display manager from being used.

Actually, the name "display manager" is somewhat misleading. It also controls the login process, and is what makes it possible for you to log in automatically. And the "display" doesn't refer to your actual monitor, but rather to the window manager you are using. If you use only the XFCE WM that's in Xubuntu, you won't see a "chooser" dialog on the login screen, but if you want to experiment with straight GNOME, KDE, or any of the others, it'll be the display manager that lets you choose which to load at login time.

You can experiment quite a bit by using the alternate terminals via CTRL-ALT-F1 through F6; log out from your normal GUI, which should take you back to the login screen. There, use CTRL-ALT-F2 to bring up TTY2 as your console, and login through its text-mode prompts. When you type in your password, don't expect to see any response at all; just keep typing it and hit Enter.

When you get a prompt that ends with "$" you can type "sudo service gdm stop" to stop the gdm display manager. You may need to replace "gdm" with "lightgdm" depending on the version of your system. This will stop the display manager. You can then type "startx" to launch the window manager itself.

Some 10 years ago or so, the recommended procedure was to boot into text mode, with no display manager loaded at all, then type "startx" to launch a GUI session. I suspect that's what you're thinking of doing -- but it now means some serious modification of the boot files, and will prevent automatic login.

Have fun experimenting, nevertheless. Even when you crash things, it's a learning process.

---

### Post by ohnonot on 2012-05-21
d*** it, my answer to this got lost-....
anyhow, thanks a bunch to JKyleOKC, whose answer was helpful.

for a guy like me, there's no way of getting into upstart and starting to change things there.
so i guess my best bet will be to replace lightdm with sth more minimalistic/lightweight.

i tried **qingy** but didn't get anywhere with it. if someone has experience with qingy and *buntu, please tell!

**slim** works but there doesn't seem to be an easy way of getting a complete list of my sessions. not useful for me, i'm experimenting so much at the moment.

**cdm** (the console display manager) looks interesting but there's just no way of installing it other than 100% manual. again, if someone knows if this can work under *buntu and if there's a howto, i'm interested.

**nodm** surprisingly works! it's in the repos. it does require some fiddling with conf-files but they're commented properly. it just logs you in automatically, no more. surprisingly login seems to be slightly slower than lightdm; but that's not my only concern.
unfortunately the gnome-keyring doesn't work. (edit: and it just won't work even if i start manually and change some files (pam.d) according to [this.]("https://wiki.archlinux.org/index.php/SLiM#SLiM_and_Gnome_Keyring")

---

### Post by markbl on 2012-05-21
> **zombifier25 said:**
> Ubuntu does not use .bash_profile, it uses .profile instead.
Incorrect. Ubuntu bash is the same as every other distro bash. Read the bash man page.

---

### Post by ohnonot on 2012-05-25
anybody anything to say about my previous post (#12)?

---

### Post by Haneef Mubarak on 2012-05-25
Something I'd just like to point out, it seems like Arch Linux would be better for you, because it's basically designed to be tailored to fit by you. I've heard a lot about it, so if you'd like to try, read this: [Lifehacker: Build a Killer Customized Arch Linux Installation (and Learn All About Linux in the Process)]("Build a Killer Customized Arch Linux Installation (and Learn All About Linux in the Process)")

You probably wouldn't replace Ubuntu with Arch, judging by what you've said, but it might be something that would provide insight to you.

Happy hunting!

---

### Post by Rodney9 on 2012-05-25
Or maybe [Ubuntu Minimal]("https://help.ubuntu.com/community/Installation/MinimalCD")

[http://maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24](http://maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24)


Rodney

---

### Post by ohnonot on 2012-05-30
yes i've been thinking about arch linux a lot...
i guess i'll give it a try when there's plenty of time... mayb in winter.
ubuntu minimal sounds similar. i wonder if there's any reason to even call it ubuntu anymore, if it's that minimal, isn't it just linux?
well i guess one would have to try out to find out.

have a nice summer (if you're on the northern hemisphere - otherwise, have a nice winter)!

---

