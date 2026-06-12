---
title: "Undoing updates"
date: 2010-03-07
forum: General Help
---

### Post by VimesCarrot on 2010-03-07
Completely new to Ubuntu, basically never used anything but Windows before, hadn't even had a chance to properly test out Ubuntu before I broke it. So, sorry if this question is very easy...or if I'm posting it in the wrong place...

Anyway, I cleverly installed the most recent drivers for my graphics card, and it killed Ubuntu - it won't start now. This happens on Windows, too, but Windows will System Restore for me. How might I fix this in Ubuntu?

I can choose Ubuntu from the grub menu, but then the screen goes blank, the fan on my computer goes into overdrive, and nothing happens.

Am currently running my Karmic Koala from LiveCD...

---

### Post by Barriehie on 2010-03-07
> **VimesCarrot said:**
> Completely new to Ubuntu, basically never used anything but Windows before, hadn't even had a chance to properly test out Ubuntu before I broke it. So, sorry if this question is very easy...or if I'm posting it in the wrong place...

Anyway, I cleverly installed the most recent drivers for my graphics card, and it killed Ubuntu - it won't start now. This happens on Windows, too, but Windows will System Restore for me. How might I fix this in Ubuntu?

I can choose Ubuntu from the grub menu, but then the screen goes blank, the fan on my computer goes into overdrive, and nothing happens.

Am currently running my Karmic Koala from LiveCD...

Boot to single-user mode, terminal, and see if running dexconf as root will fix it.  It -should- rebuild the Xorg.conf file.

---

### Post by VimesCarrot on 2010-03-08
Thank you, but I think you underestimate how unfamiliar I am with Ubuntu. I don't know how to do any of that...

---

### Post by Barriehie on 2010-03-08
> **VimesCarrot said:**
> Thank you, but I think you underestimate how unfamiliar I am with Ubuntu. I don't know how to do any of that...

k, :), when you have the grub menu you should have at least 2 choices; the first one will look something like this: (except for Ubuntu)
```

Debian GNU/Linux, kernel 2.6.26-2-amd64
```

and the second one something like this: (note the single-user mode)
```

Debian GNU/Linux, kernel 2.6.26-2-amd64 **(single-user mode)**
```

Select the one that says single-user-mode.  This will put you at a black screen with white letters and say something like **'Enter root password for maintenance or enter Ctrl-D to continue'**  Here you'll enter the root password and you'll get to a prompt, logged in as root.  The prompt should have '**#**' at the end of it.  At this point you'll enter:
```

dexconf
``` and hit enter.  It will do it's thing and then you type exit.  The machine will then restart back to grub.  Choose the option without the single-user-mode, should be the first one, and we'll see if the Xorg.conf file is generated correctly.  What make/model of video card do you have???

HTH,
Barrie

---

### Post by VimesCarrot on 2010-03-08
Thanks, I'll go try that now and report back.  The graphics card: GeForce 9500 GT. I've resigned myself to using drivers from years ago (from the disc that came with the card) on Windows for the rest of my life. No idea what to try on Ubuntu, since the disc presumably won't work (not that I've tried it yet).

---

### Post by dcstar on 2010-03-08
> **VimesCarrot said:**
> Thanks, I'll go try that now and report back.  The graphics card: GeForce 9500 GT. I've resigned myself to using drivers from years ago (from the disc that came with the card) on Windows for the rest of my life. No idea what to try on Ubuntu, since the disc presumably won't work (not that I've tried it yet).

Support for old Nvidia cards was dropped around 8.04, if the Ubuntu system offered you a driver then your card is supported, if you just decided to install a driver in another way then you broke your system.

---

### Post by VimesCarrot on 2010-03-08
Well, that was amusing. It didn't have single-user mode, but it had recovery mode. I thought I'd give it a go.  Shortly after entering it (before getting chance to do anything) I was greeted with some kind of error screen. It had a cancel option, which I took. I wrote down some of the details of that, if you need it, but it didn't seem to have any effect on anything, really.

Once I got a prompt I logged in. The following is what I ended up with when I tried dexconf:

  aaron@aaron-desktop:~$ dexconf
 debconf: DbDriver "passwords" warning: could not open /var/cache/passwords.dat: Permission denied

Sounds to me like recovery mode isn't single-user mode.

About the graphics card: I used the Update Manager to get the drivers. The problem is identical on Windows, when downloading them from the Nvidia website; any online update results in system death.

---

### Post by Barriehie on 2010-03-08
> **VimesCarrot said:**
> Well, that was amusing. It didn't have single-user mode, but it had recovery mode. I thought I'd give it a go.  Shortly after entering it (before getting chance to do anything) I was greeted with some kind of error screen. It had a cancel option, which I took. I wrote down some of the details of that, if you need it, but it didn't seem to have any effect on anything, really.

Once I got a prompt I logged in. The following is what I ended up with when I tried dexconf:

  aaron@aaron-desktop:~$ dexconf
 debconf: DbDriver "passwords" warning: could not open /var/cache/passwords.dat: Permission denied

Sounds to me like recovery mode isn't single-user mode.

About the graphics card: I used the Update Manager to get the drivers. The problem is identical on Windows, when downloading them from the Nvidia website; any online update results in system death.

Do it again except at the prompt enter:
```

sudo dexconf
```
You have to be root user to run it.  When you are root user your prompt will change and end with a '#'.

Barrie

Edit: Yes on the errors, the more we know the less we beat around the bushes!

---

### Post by Barriehie on 2010-03-08
Googling is yielding some results, the majority say it won't work and you could install Ubuntu 8.04 or uninstall all the nvidia drivers and install envy-ng.  Another post says when you get to the prompt, ```
sudo nvidia-xconfig
``` I would try this last one.

This might help, I'm going to link it here so I don't have to bookmark it.
[http://ubuntuforums.org/archive/index.php/t-1090146.html](http://ubuntuforums.org/archive/index.php/t-1090146.html)

---

### Post by VimesCarrot on 2010-03-08
Entirely unrelated problem: I don't have the password it's asking me for.

In my Little Book of Passwords, I only have one password for Ubuntu (the one I have to put in to access recovery mode), and that doesn't work.

I can only assume I've never created the password, since I'm certain I would have written it down. Is there likely to be a default password? I'll try out a few (leaving it blank and trying "password" occurs to me now) although it only actually asked the first time I tried it - when I repeated my command, it didn't ask for the password any more, it just does nothing.

---

### Post by Barriehie on 2010-03-08
Try yours.

---

### Post by VimesCarrot on 2010-03-08
Sorry about the password thing, misinterpretation from my end. dexconfig did nothing, so I assumed the password didn't work, but it did.

nvidia-xconfig gave me this.

```

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/x11.conf'

```

I've never read command prompt/terminal stuff before, but this looks to me like it did what it was supposed to.

Nothing has changed.

I'll browse that link you gave me now.

---

### Post by Barriehie on 2010-03-08
> **VimesCarrot said:**
> ...muted...

I'll browse that link you gave me now.

Good, because I'm running out of ideas! :)

---

### Post by VimesCarrot on 2010-03-09
Thanks for trying to help.

I figure it'd be easier to just reinstall Ubuntu! So that's what I'm going to do.

I'll mark this thread as Resolved now :)

---

### Post by JigglyWiggly_ on 2010-03-09
Delete the xorg.conf file, and reboot... should generate a new one. It did for me when I had graphics problems.

---

### Post by Barriehie on 2010-03-09
After you install you can go into Synaptic, System > Administration > Synaptic Package Manager and after you find your video driver you can 'pin' the package so it won't update.

---

### Post by VimesCarrot on 2010-03-09
Thanks, should come in useful to avoid some accidental suicides ;)

Jiggly - won't let me delete the file from a LiveCD boot, and don't know how to in the terminal.

---

### Post by Barriehie on 2010-03-09
> **VimesCarrot said:**
> Thanks, should come in useful to avoid some accidental suicides ;)

Jiggly - won't let me delete the file from a LiveCD boot, and don't know how to in the terminal.

What file?

---

### Post by VimesCarrot on 2010-03-09
The one Jiggly was talking about, xorg.conf. Don't worry, the reinstall worked fine, so no need anyway. ;)

---

### Post by Barriehie on 2010-03-09
> **VimesCarrot said:**
> The one Jiggly was talking about, xorg.conf. Don't worry, the reinstall worked fine, so no need anyway. ;)

Cool!  Now I'ld make a backup...

---

