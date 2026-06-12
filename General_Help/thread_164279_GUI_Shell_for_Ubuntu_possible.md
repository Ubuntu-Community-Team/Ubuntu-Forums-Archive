---
title: "GUI Shell for Ubuntu possible?"
date: 2006-04-22
forum: General Help
---

### Post by uzi09 on 2006-04-22
hey all!

i was surfing [www.gnome-look.org](www.gnome-look.org) for some themes and came across this (actually, it was under the splashscreens section for some reason):
[http://www.gnome-look.org/content/show.php?content=22329&PHPSESSID=0b1ddb4123db7609c537ab3778a346e7](http://www.gnome-look.org/content/show.php?content=22329&PHPSESSID=0b1ddb4123db7609c537ab3778a346e7)

for the longest time i wanted to be able to log into a shell, but (surprisingly) failed to find much on the net on exactly how to do that. the only thing i could find was to change run levels (for some reason ctrl+alt+F1 or ctrl+alt+F7 refused to work for me again after the first try)

also, i had big chunky fonts when i did get into it, and as much as i liked feeling cool by using a cui 8) - i kinda found it a lil bland =\

when i came across this, it was perfect for what i wanted. booting into a shell environment yet still having it look pretty nice.

i asked the author about how to achieve this, but he couldn't provide me with much info besides:

> This theme is not a Gnome splash, but thing called 'fbsplash'. fbsplash
is a kernel patch that allows you to set up some kind of picture with
progress bar, animated icons, etc etc, which will show up during the
boot process instead of plain text informations. It has two modes -
silent and verbose. Silent is a mode similar to WindowsXP startup
screen (image with a progressbar), while verbose is similar to classic
Linux startup process (showing textual infos, but with
the custom background).

when i searched the web for this 'fbsplash' it seemed to point to Gentoo every time.

i was hoping somebody with more experience than me (pretty much anyone else) can advise me on whether this is possible or not to accomplish on Ubuntu and how

thanks in advance,
uzi

---

### Post by jazzmuzik on 2006-04-22
You don't need to boot into a shell to have a shell. Just try Applications, Accessories, Terminal. The terminal is the shell. And in the terminal's menus you can set a background images, (but why?) and fonts.

---

### Post by uzi09 on 2006-04-22
well, that would make it a terminal.

i would like to be booted into a SHELL where i can login/logout right from the cui (cuz it loads faster) - not wait for gnome/kde/(any other window manager) to load (i'm aware some of the small window managers like FB or BB are quick to load - but i really don't want to use those).

---

### Post by jazzmuzik on 2006-04-22
OIC.

You need to edit /etc/inittab

Look for the line:

id:2:initdefault:

And change the 2 to a 3. The number refers to the runlevel and I THINK that 3 is the runlevel for text mode. 2 is obviously for gui. Please verify before trying as I've never tried it in Ubuntu, only Fedora. But I did read this somewhere on this forum.

---

### Post by frenkel on 2006-04-22
Ignore this... (How can i delete a message :S)

---

### Post by uzi09 on 2006-04-22
[QUOTE=jazzmuzik]OIC.

You need to edit /etc/inittab

Look for the line:

id:2:initdefault:

And change the 2 to a 3. The number refers to the runlevel and I THINK that 3 is the runlevel for text mode. 2 is obviously for gui. Please verify before trying as I've never tried it in Ubuntu, only Fedora. But I did read this somewhere on this forum.[/QUOTE]

yes that would do it, but i'm trying to have it setup like the link i provided above. is there a way to do it that way?

(please see this pic: [http://www.gnome-look.org/content/preview.php?preview=1&id=22329&file1=22329-1.png&file2=22329-2.jpg&file3=22329-3.jpg&name=Genpowered&PHPSESSID=0b1ddb4123db7609c537ab3778a346e7](http://www.gnome-look.org/content/preview.php?preview=1&id=22329&file1=22329-1.png&file2=22329-2.jpg&file3=22329-3.jpg&name=Genpowered&PHPSESSID=0b1ddb4123db7609c537ab3778a346e7))

ps: frenkel: lol - not sure ;)

---

### Post by jazzmuzik on 2006-04-22
I didn't study that site very much so I don't know exactly what you are trying to do, but the image looks like a hybrid between gui and text. I believe it is called framebuffer mode. Sorry, I don't know much about it, it's been a long time since I tried booting up in that mode.

---

### Post by uzi09 on 2006-04-22
atleast we're on the same page now,

thanks tho

if anybody else has any input - please post - i'm dying to have a setup like that :D

thxx

---

### Post by Kevinator on 2006-04-22
[QUOTE=jazzmuzik]OIC.

You need to edit /etc/inittab

Look for the line:

id:2:initdefault:

And change the 2 to a 3. The number refers to the runlevel and I THINK that 3 is the runlevel for text mode. 2 is obviously for gui. Please verify before trying as I've never tried it in Ubuntu, only Fedora. But I did read this somewhere on this forum.[/QUOTE]
I think you are mistaken. There doesn't seem to be any difference between runlevel 2 and 3 by default. Unlike some other distributions, Ubuntu (and Debian) don't define a multi-user text mode level. Ubuntu essentially has 2 usable levels - 1 and 2. 1 is the single user mode and 2 is multi-user. 3, 4, and 5 are the same as 2. 6 is reboot and 0 is halt.

---

### Post by Dr Gonzo on 2006-04-22
For a dirty hack, you can just make it so that the OS doesn't load GDM on startup: ```
sudo chmod -x /etc/init.d/gdm
```Ubuntu will complain about the script not being writable, but it's not a big deal.

You can then, if you wish, start X by doing ```
startx
```as your normal user.

To choose a WM, like e.g. Gnome, you'll need a file in your home directory called .xinitrc containing something like ```
exec gnome-session
```  You can sub in "startkde" or "fluxbox" or whatever else you want for your WM.

Note that, even when X has started, you can always get back to a different console by doing [ctrl][alt][F$], where $={1,2,3,4,5,6}

---

### Post by Computeruser on 2006-04-22
Hmmm,  too bad. I prefer to start Linux without starting the GUI and starting it separately. I prefer installing the VMware Tools without the GUI running (it used to be necessary a while back). I may try the dirty hack method, but I would prefer a nicer method if possible. Thanks for the info.

---

### Post by Dr Gonzo on 2006-04-22
Okay, then I've got a better one for you.  :) (just found it myself.)

Go to System->Administration->Services.  Deselect "Graphical Login Manager."  Reboot.  Enjoy.

---

### Post by Computeruser on 2006-04-22
Thank you.

---

### Post by jazzmuzik on 2006-04-22
I'm having a hard time finding an answer. In another thread people were also admiring Gentoo's text (framebuffer?) mode. At any rate you can control how many lines and rows text mode uses though. You need to add 'vga=xxx' to /boot/grub/menu.lst like this:

kernel          /vmlinuz-2.6.12-10-386 root=/dev/hdb6 ro quiet splash vga=792

Here's more:
[http://ubuntuforums.org/showthread.php?t=41709&highlight=vga%3D792](http://ubuntuforums.org/showthread.php?t=41709&highlight=vga%3D792)

---

### Post by uzi09 on 2006-04-22
hey thank you guys (esp. Dr Gonzo),

this stuff is great. i had been looking for this information for some time now!

i'm going to go and give this a try right now, unfortunately this does only answer half the questions though :S. next step would be to try to get a nice gui thingy setup (or more technically 'framebuffer').

also, in the mean time to spruce up the looks as best as possible, is it possible to configure the font size -- or would we have to just change the resolution. changing the resolution may be a problem for me though because of the type of computer i have (dell inspiron 6400). it has had problems running gnome, but a fix was finally created (915 resolution or something) which Dapper Drake carries with it. Although gnome is finally working on it now, we (me as well as a few other ppl using this comp) are still unable to get it to use its default resolution of 1280x800 (i'm not 100% on the numbers, but i know it's 1280 something).

thx again!
uzi

---

### Post by croak77 on 2006-04-22
uzi9, Do you not want to use X? Or do you just want a background image for the login shell?

---

### Post by uzi09 on 2006-04-22
[QUOTE=croak77]uzi9, Do you not want to use X? Or do you just want a background image for the login shell?[/QUOTE]

i'd like to:
1) boot into a shell (ie: X not running)
2) when i please, i'd like to use "startx" to start up a window manager

(more on 1) - when it boots into a shell, i'd like to have it looking nice - not just the ol' black&white screen. something like this pic would be perfect:
[http://www.gnome-look.org/content/preview.php?preview=1&id=22329&file1=22329-1.png&file2=22329-2.jpg&file3=22329-3.jpg&name=Genpowered&PHPSESSID=0b1ddb4123db7609c537ab3778a346e7](http://www.gnome-look.org/content/preview.php?preview=1&id=22329&file1=22329-1.png&file2=22329-2.jpg&file3=22329-3.jpg&name=Genpowered&PHPSESSID=0b1ddb4123db7609c537ab3778a346e7)

thx,
uzi

---

### Post by croak77 on 2006-04-22
I'm not sure how you would do this in Ubuntu.

[http://dev.gentoo.org/~spock/projects/gensplash/]("http://dev.gentoo.org/~spock/projects/gensplash/") 

You need fbsplash for console backgrounds. Not sure if the Ubuntu kernel are patched with fbsplash or not.

---

### Post by uzi09 on 2006-04-22
hmm, well, i guess i'll have to research this some more to figure out if it is possible or how to force it if it isn't :D.

one thing though, when they say 'system console' do they mean a TERMINAL or a SHELL or something else??

> <...> display a background picture on the system consoles.

uzi

---

### Post by jazzmuzik on 2006-04-22
Ubuntu uses usplash. There's some info here:

[http://lists.debian.org/debian-desktop/2006/03/msg00014.html](http://lists.debian.org/debian-desktop/2006/03/msg00014.html)

'system console' TERMINAL or a SHELL all mean the same thing to me.

---

### Post by z_diver on 2006-04-23
[QUOTE=uzi09]hmm, well, i guess i'll have to research this some more to figure out if it is possible or how to force it if it isn't :D.

one thing though, when they say 'system console' do they mean a TERMINAL or a SHELL or something else??



uzi[/QUOTE]
I think the terminology is rather confusing.  Maybe the way to look at it is a shell is an environment that uses syntax to run command line programs.  For instance, bash is a shell, zsh is another shell, sh another...  

A terminal is a program that allows you to run "shells" in a graphical environment.  And a console is the pure command line, which also runs "shells" but with no gui started.

I've seen lots of live cds that do what you want.  Come to think of it they may all be gentoo based too.  i'll post back with some links.

Edit: Here is a link: [http://www.sysresccd.org/Screenshots](http://www.sysresccd.org/Screenshots)
Towards the bottom of that page are some screenshots of what the live cd looks like.  I have seen others, with more complex graphical layouts, kororaa comes to mind, but it's also gentoo based.

---

### Post by Computeruser on 2006-04-23
The method of stopping the gdm service (Dr. Gonzo's post) works on a one-time basis. That is, stop the service, restart, and come up without the GUI starting. GUI starts with 'startx'. When I shut down, the gdm service then restarts on its own and the GUI starts on its own. This is all workable for me. If I need to be in a shell without a GUI, I can do it. Most times, the GUI starting is no problem for me.

---

### Post by uzi09 on 2006-04-23
[QUOTE=z_diver]I think the terminology is rather confusing.  Maybe the way to look at it is a shell is an environment that uses syntax to run command line programs.  For instance, bash is a shell, zsh is another shell, sh another...  

A terminal is a program that allows you to run "shells" in a graphical environment.  And a console is the pure command line, which also runs "shells" but with no gui started.

I've seen lots of live cds that do what you want.  Come to think of it they may all be gentoo based too.  i'll post back with some links.

Edit: Here is a link: [http://www.sysresccd.org/Screenshots](http://www.sysresccd.org/Screenshots)
Towards the bottom of that page are some screenshots of what the live cd looks like.  I have seen others, with more complex graphical layouts, kororaa comes to mind, but it's also gentoo based.[/QUOTE]
i know about the different types of shells that they have and i know that a terminal emulates a shell -- but isn't one -- and a console, i hadn't really heard of. i think i just mixed up the shell and console into one :S. thanks for clearing it up for me though.

also, as far as they sysresccd -- aka System Rescue CD -- i actually have that already burnt and used it to resize my NTFS HDD when I was putting Dapper Drake on my computer. I did realize it was Gentoo and I kinda liked the look of it as well, but didn't know that it could have been made to look as nice as the pic i've linked to multiple times within this thread. Last night, I was thinking about downloading Gentoo on a live CD and giving it a try, but I guess I'll hold off on that for now -- atleast until my exams are over =S


[QUOTE=Computeruser]The method of stopping the gdm service (Dr. Gonzo's post) works on a one-time basis. That is, stop the service, restart, and come up without the GUI starting. GUI starts with 'startx'. When I shut down, the gdm service then restarts on its own and the GUI starts on its own. This is all workable for me. If I need to be in a shell without a GUI, I can do it. Most times, the GUI starting is no problem for me.[/QUOTE]
Yeah, I noticed that! I didn't really care much a bout it though - the changing of permissions worked like a charm, so if I really wanted, I could just do it that way.

In the mean time, I'll look into Gentoo, but in all honesty, I researched the distro a bit on Distro Watch and it looks like it's still fairly new and doesn't have as many people behind it as Ubuntu (then again what does :mrgreen:) and in all honesty - I like Ubuntu for its philosophy as well as the people. I'm sure if I was to post a thread like this in any other place, I woulda been flamed like crazy for the first lil while and then had some sort of a crappy response or two and then the thread would prolly have become history ](*,) 

thanks all
uzi

---

### Post by Computeruser on 2006-04-23
I tried to run Gentoo 2004 and was unsucessful. It is not a supported guest for VMware, and I could get a text system running but no GUI. Further, it was way too complex just for an OS. Red Hat, SuSE and Ubuntu are all easier (done them all) and Ubuntu is the easiest. A bit off-topic for this thread and hopefully no one will mind.

---

### Post by black_rob on 2006-04-30
Hi, this thread seems to have died ( a week since the last post ), but I've done exactly what the original post asked about, so I thought I might be able to help.

First problem: you don't want X to start up automatically when you boot into the computer.  When linux first starts, it looks for the file /etc/inittab.  Among other things, this file tells linux which runlevel to start in -- the simplest description of runlevels I know of is here: [http://www.linuxfromscratch.org/lfs/view/stable/chapter07/usage.html]("http://www.linuxfromscratch.org/lfs/view/stable/chapter07/usage.html").  Every distro does runlevels a little different, and Ubuntu being Debian-based, it's  runlevels should be about the same as Debian's.  Am not positive, because I never used Debian much, and am new to Ubuntu, but you should be able to just remove the call to the gdm script in runlevel 2 (the default runlevel, according to my /etc/inittab ).

So, let's try this out in a terminal:
     ls /etc/rc2.d/

For my this produces 
S05vbesave          S19cupsys         S20powernowd       S98usplash
S10acpid            S19hplip          S20rsync           S99acpi-support
S10powernowd.early  S20apmd           S25bluez-utils     S99rc.local
S10sysklogd         S20festival       S25mdadm           S99rmnologin
S11klogd            S20hotkey-setup   S89anacron         S99stop-readahead
S12dbus             S20laptop-mode    S89atd             S99timidity
S13gdm              S20makedev        S89cron
S14ppp              S20nvidia-kernel  S90binfmt-support

Now, if you do 
     ls -l /etc/rc2.d/S13gdm
you get this
     lrwxrwxrwx 1 root root 13 2006-04-04 13:17 /etc/rc2.d/S13gdm -> /etc/init.d/gdm

This means that S13gdm is just a simlink to the real script in /etc/init.d.  So what I would do is just rename S13gdm to something else --anything that doesn't start with a capital S and a two digit number.  If it doesn't work, just change it back, no harm done. 

 sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/blockedS13gdm

I'm gonna do it to mine right now just to make sure it works, then I'll post again to tell you how to get the gentoo-style framebuffer background.

---

### Post by cskeide on 2006-04-30
A more "clean" way of doing this is:
```
sudo update-rc.d -f gdm remove
```

If you want to change it back, run:
```
sudo update-rc.d gdm defaults
```

---

### Post by egon spengler on 2006-05-01
You should be able to change your console font from /etc/console-tools/config. I'm not running ubuntu at the moment so I can't test it but if you install the console-terminus font then a line like **SCREEN_FONT_vc1=ter-114n.psf.gz** *should* work. Of course you can also just substitute the reference to ter-114pn with a font of your choice although I believe that the console can only display fonts specifically created as console fonts

---

### Post by uzi09 on 2006-05-04
wow thanks guys. yea the thread did kind of die down and i pretty much just gave up assuming that it could only be done with Gentoo. I looked into how Gentoo is as a distro and didn't seem to like it as much as Ubuntu, so I decided on forgetting about it altogether.

I think I'll go try these things out.

One thing though - black_rob, you mentioned that doing what you did will enable frame buffer for Ubuntu. I don't have enough technical expertise to know what frame buffer really does. All I understand from it is that it looks nice ;D. Once frame buffer is up though, do you know how I could setup graphics? Or is there a link that anyone can provide that'll let me adjust the looks as I'd like em (pretty much like the first pic I posted).

Thanks again all,
uzi

---

### Post by z_diver on 2006-05-04
If and when we do get this figured out on Ubuntu, what I'd like to do is setup some unused runlevel, maybe 3, to boot in framebuffer mode. Then I'll make a new entry in grub like "Graphical Console mode" calling init 3 and it should boot to the nice graphical console.  

[COLOR=DarkRed]Does anyone see a problem with this approach?[/COLOR]

---

### Post by BungaMan on 2006-05-04
I can't help out much as I haven't tried it myself but first off it seems to be gentoo specific.  The gen in gensplash stands for gentoo i guess :)

Here are a few links that can help you out:
Instructions on how to do it on debian [http://jdurand.home.cern.ch/jdurand/fbsplash.html](http://jdurand.home.cern.ch/jdurand/fbsplash.html)
The Wiki HOWTO to install gensplash on gentoo. At the bottom is info for other distro's [http://gentoo-wiki.com/HOWTO_fbsplash](http://gentoo-wiki.com/HOWTO_fbsplash)

Seems like every distro is creating its own splash implementation.  Good luck!

---

### Post by uzi09 on 2006-05-05
[QUOTE=BungaMan]I can't help out much as I haven't tried it myself but first off it seems to be gentoo specific.  The gen in gensplash stands for gentoo i guess :)

Here are a few links that can help you out:
Instructions on how to do it on debian [http://jdurand.home.cern.ch/jdurand/fbsplash.html](http://jdurand.home.cern.ch/jdurand/fbsplash.html)
The Wiki HOWTO to install gensplash on gentoo. At the bottom is info for other distro's [http://gentoo-wiki.com/HOWTO_fbsplash](http://gentoo-wiki.com/HOWTO_fbsplash)

Seems like every distro is creating its own splash implementation.  Good luck![/QUOTE]


Thank you - this is a great link - i'll be sure to try it out!

---

### Post by black_rob on 2006-05-05
Sorry I haven't posted back with info on how to get gensplash running right.  It's turning out to be a pain to get the utilities to compile.  Search the forums for "gensplash" and you'll see within the last three weeks two threads talking about how to get it working, no one has succeeded.  A little background information (which has mostly already been mentioned in other posts, but just to pull it all together).

- Gensplash was written by a Gentoo developer "spock" ( on a side note, if you want to feel dumb, check out the guy's bio: he's like only 18 or 19 ); googling for "gensplash"  brings up his site first. Read it!

- It requires of an appropriately patched kernel.  There are two patches in particular I looked for, fbsplah and vesafb-tng.  I'm not sure if either of them are completely necessary --fbsplash is needed for a fancy splash screen on boot (check out spock's screenshots section), but I don't know if it's necessary for a framebuffer background, and vesafb-tng is "the next generation" of the kernel vesafb driver.  I use them because Spock wrote them along with the splashutils utilities, so I figure they all work well together.  (Plus vesafb-tng plays nice with the Nvidia binary drivers, something that apparently the unpatched vesafb doesn't.)  However, in the README that comes with the splashutils sources, it seems to imply that some of the utilites it provides will work on any kernel with a framebuffer driver.  So maybe the patches aren't necessary but it's more likely to work right and trouble free with them, so use them.

- The easiest way to get both of these patches in an up to date kernel is to either download a prepatched kernel source (I wonder if we could get one put in the multiverse?), or download a fresh kernel from kernel.org and patch it with [this patchset]("http://iphitus.loudas.com/archck.php") (use the 2.6.16-beyond3 patch and a stock 2.6.16 kernel and follow any of the excellent guides for compiling a kernel from these forums)

- Be sure to compile in support for some things (vesafb-tng, console framebuffer, the appropriate resolution, etc) directly into the kernel, not as modules (follow [this guide]("http://gentoo-wiki.com/HOWTO_fbsplash")).  Also don't forget to correct your kernel options in grub's menu.lst ( vesafb-tng needs things written in a certain way).

The above will get you a nice framebuffer console, with a plain black background.

After that, you have to install Spock's splashutils package.  Right now, that's a sticking point for me --it won't compile.  Maybe the version of something on Dapper Drake is wrong, maybe it's because Dapper uses gcc-4.0, I don't know.  On Spock's site there is a section of links to how-tos by people using gensplash with distros other than gentoo [ here ]("http://dev.gentoo.org/~spock/projects/gensplash/archive/contrib/").  One has a pretty good writeup on getting it to work in debian, including some debs of splashutils, but if I recall correctly the version he used was pretty old (i.e. probably won't work on Ubuntu).

Okay, having said that, here's my two cents on the topic.  Bootsplashes are lame.  Thye're weak.  I like seeing the kernel messages scroll by, I learned a lot about linux by reading them and then looking up things I didn't understand, and they give me clues as to what's going wrong when I've screwed things up.  I do like seeing them scroll by in a nice hi-res framebuffer, but I never put any background on it.  What I do do is put some commands in my .bash_profile so that when I log in at the console, it will load my background, borders and fonts.  Makes me feel special ($0.02).

Having said that, I also like the idea of having a line in my grub menu that will boot me into a different runlevel (one that doesn't start X).  It's probably pretty simple, but I've never looked into it.

---

### Post by ed_agamemnon on 2006-05-08
I use these scripts to disable/re-enable/kick-start booting the GDM:

disable:

```
sudo update-rc.d -f gdm remove

```

re-enable:

```
sudo update-rc.d gdm start 20 2 3 4 5 .

```

kick-start:

```
sudo /etc/init.d/gdm start
```

---

