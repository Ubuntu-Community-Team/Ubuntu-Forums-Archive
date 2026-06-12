---
title: "A couple terminal questions."
date: 2009-10-16
forum: General Help
---

### Post by rob86 on 2009-10-16
I have a couple questions. 

Is it possible to make the terminal have more lines before stuff starts getting erased? When doing commands with long output, the top always gets cut off. I know there are ways around it like > file or the more command or something, but it'd be nice if the terminal just had more lines.

Another question, is there any way to change the resolution of the tty's so the font is smaller and more information fits on the screen?

---

### Post by beastrace91 on 2009-10-16
Did a quick Google search and found this as the first link:

[https://lists.ubuntu.com/archives/ubuntu-users/2007-June/117497.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-June/117497.html)

> It's not very difficult to change the resolution.  First, 
install hwinfo, if it isn't already installed:
sudo apt-get install hwinfo

Then run:
sudo hwinfo --framebuffer

You'll see something like this:

  Mode 0x0317: 1024x768 (+2048), 16 bits
   Mode 0x0318: 1024x768 (+4096), 24 bits
   Mode 0x031a: 1280x1024 (+2560), 16 bits
   Mode 0x031b: 1280x1024 (+5120), 24 bits
   Mode 0x0330: 320x200 (+320), 8 bits
   Mode 0x0331: 320x400 (+320), 8 bits
   Mode 0x0332: 320x400 (+640), 16 bits

Find the resolution you want and the hexadecimal equivalent of 
the resolution.

For example, my choice of video resolution is 1280x1024 24 bit 
so the relevant hexadecimal I need is "0x031b".

Then edit your /boot/grub/menu.lst and change your kernel 
entry from this:

kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro 
quiet splash

to this:

kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro 
quiet vga=0x031b splash

Then when you enter tty mode (ctl-alt-f1 etc) you will have 
high resolution tty.


Hope this helps,
~Jeff

---

### Post by zer0x on 2009-10-16
Hi,

Pipe your command through the 'less' command (man 1 less) :D

e.g.
```

dmesg | less
```

Or you could use GNU Screen (man 1 screen), which allows you to configure its scrollback buffer. Check /etc/screenrc (defscrollback).

[http://www.gnu.org/software/screen/manual/screen.html]("http://www.gnu.org/software/screen/manual/screen.html")

It has a lot of very useful features, such as the ability to keep an application running in screen when you logout, and allow you to re-attach to that same screen on your next login :D

I just found this:
[URL="http://www.educ.umu.se/~bjorn/linux/linux-faq/Linux-FAQ-7.html"]
http://www.educ.umu.se/~bjorn/linux/linux-faq/Linux-FAQ-7.html[/URL]

> You can't increase the amount of scrollback, because it is implemented using the video memory to store the scrollback text. You may be able to get more scrollback in each virtual console by reducing the total number of VC's. See linux/tty.h.

And this on soft scrollback:

[http://forums.gentoo.org/viewtopic-t-557095-start-0.html]("http://forums.gentoo.org/viewtopic-t-557095-start-0.html")

> That "software scrollback" option is only for the VGA console, ie the "real" text mode console, not for framebuffers.

I would just stick with screen and a high resolution console.

HTH

zer0x

---

### Post by scorp123 on 2009-10-16
> **rob86 said:**
> change the resolution of the tty's
[http://ubuntuforums.org/showpost.php?p=6281148&postcount=73](http://ubuntuforums.org/showpost.php?p=6281148&postcount=73)

[http://ubuntuforums.org/showpost.php?p=7957561&postcount=91](http://ubuntuforums.org/showpost.php?p=7957561&postcount=91)

---

### Post by falconindy on 2009-10-16
Isn't the vga= style declaration deprecated (or obsolete)? Or is that only true of grub2?

---

### Post by benj1 on 2009-10-16
> **zer0x said:**
> Hi,

Or you could use GNU Screen (man 1 screen), which allows you to configure its scrollback buffer. Check /etc/screenrc (defscrollback).


dont need screen, you can define the scroll back buffer in all good terminals *tm*

@op shift-pgup/pgdown can scroll up and down also

---

### Post by StuartN on 2009-10-16
> **rob86 said:**
> Is it possible to make the terminal have more lines before stuff starts getting erased?

In Terminal, select Edit->Profiles... and edit your profile (Default if you haven't set one up). On the Scrolling tab, change the Scrollback setting from "512 lines (about 326.0 KB)".

---

### Post by zer0x on 2009-10-16
> **benj1 said:**
> dont need screen, you can define the scroll back buffer in all good terminals *tm*

Due to the OP's question about changing the resolution of the virtual consoles I assume the scrollback question was about them, not an X terminal? :confused:

---

### Post by Giblet5 on 2009-10-16
> **rob86 said:**
> Another question, is there any way to change the resolution of the tty's so the font is smaller and more information fits on the screen?

+ 100 on the Edit/Profiles... font suggestion.

Another way is to resize the window.

There's also the Wall-Of-Monitors approach. I like that one.

---

### Post by scorp123 on 2009-10-16
> **falconindy said:**
> Isn't the vga= style declaration deprecated (or obsolete)? 

It's disabled per default ... deeper explanation here:

[http://ubuntuforums.org/showpost.php?p=7182310&postcount=89](http://ubuntuforums.org/showpost.php?p=7182310&postcount=89)

---

