---
title: "tty1 to tty6 shows small screen"
date: 2010-03-30
forum: General Help
---

### Post by baha'a on 2010-03-30
hi guys

I really like command line (I get there by pressing Ctrl+Alt+(F1..F6)) but the screen isn't full it's just a rectangle in the middle (like wide screen movies) I don't know what's the problem, can you help me please?
thanks in advance:)

---

### Post by vzomik on 2010-03-31
you should change how the kernel options in grub.cfg

---

### Post by baha'a on 2010-03-31
> **vzomik said:**
> you should change how the kernel options in grub.cfg

thanks a lot for replying:)

I found these stuff online
[QUOTE=http://www.mail-archive.com/linux-newbie@vger.kernel.org/msg05492.html]
James Miller wrote:
> I'm having some display problems on a couple of laptops: one has Gentoo,
> the other Debian Sid.  The difference in the nature of the problem between
> the two laptops is that one has an Xwindows display that looks fine
> (Gentoo), while I'm still working on getting X going (hoping to set up
> Xfbdev) on the other.  But the aspect of the problem the two share
> concerns when the computers are in console mode - like when they're
> booting.  Until the Gentoo machine gets to the login window for X, the
> console part of the screen where text is showing as boot messages scroll
> by occupies only a small portion that the center of the screen, rather
> than taking up the whole screen.  It's not as though anything is cut off:
> I see all the text there that I think I should be seeing.  But it's as
> though the console has been shrunken down to occupy a small portion at the
> center of the screen, with just blank black surrounding it.  This display
> is meant to function at 1024x768, btw.  The other laptop does the exact
> same thing: there is a console in the center of the screen with just blank
> black surrounding it.  As I said, I haven't got any sort of X going on
> this machine yet, so I'm forced to use this small portion of the screen as
> a console when I'm trying to do things at the command line or using mc or
> whatever other console apps I run.  This laptop's screen does 800x600,
> btw.
>
> Can anyone onlist inform me as to the nature of the problem I'm
> confronting?  Just as well, can anyone offer suggestions about how I might
> make the console take up the entire screen, rather than just a portion of
> it?
>
> Thanks, James

This is a fairly common problem with laptops (and is not actually
related to Linux, btw), and with desktop systems with LCD monitors.  It
is caused by the way LCDs handle non-native resolutions (ie: 640x480 on
your LCD laptop capable of 1024x768).  LCDs are actually incapable of
running at any resolution other that their native resolution, and so
they can either do what you are seeing, where only the central 640x480
of the total 1024x768 is used, or it can stretch the image so it is
displayed fullscreen.  They have this because the method used to stretch
the display sometimes does a poor job, especially with text fonts.  How
to change your laptops to display fullscreen depends on what type of
laptop you have, usually either in the BIOS setup, or using a special
function key.  On my Dell Latitude CPi, it has a 'Font' function key
[Fn+F7] that toggles this.  If you still have trouble finding how to
switch to fullscreen,  I would recommend checking your laptop
manufacturers support.

Hope this helps,
Conway S. Smith
[/QUOTE]

I pretty much have the same problem

and there is this guy:
[QUOTE=http://whacked.net/ldl/faq/]
3.5. My screen is small, and there's a black border around it!
        Hit Fn-F7, or whatever your 'Font' function key is.  Basically,
        an LCD is set to run at a fixed pixel resolution, so when you 
        run at a resolution smaller than that (i.e.: if you have a 
        UXGA screen but want to run 1024x768), then it will either fix 
        1024x768 and fill in the remaining of the 1600x1200 with black, 
        or it will scale it to fill the whole screen.
8)
[/QUOTE]

---

### Post by baha'a on 2010-03-31
> **vzomik said:**
> you should change how the kernel options in grub.cfg

I found a value in that file
640*480

I made it 1024*768 (my screen config in Xmode);

I'll reboot and see what happens
;)

---

### Post by baha'a on 2010-03-31
well it didn't work :(

and neither changing preferences from Bios setup.

does any body have an idea

please!

---

### Post by baha'a on 2010-03-31
I read once about posting in forums for asking for help

and the writer said that one shouldn't pimp his thread so often

but the problem that I really like this forum and like you guys and most of all I like linux (or ubuntu because I never lived any other distru)

but it really annoys me that I noticed that when the member is a newbie and has just came on board every body helps him even when the problem is complicated but when I asked for help with this problem which I noticed when I started sailing ubuntu 

the help was very little and there are many posts that has reply such like 0 or 1

I like you're voluntary work and for sure I'll help whenever I can but I really like to get some help

even it was like books I can read or sites I can search

sorry for the language and thanks for every thing

---

### Post by dcstar on 2010-03-31
> **baha'a said:**
> I found a value in that file
640*480

I made it 1024*768 (my screen config in Xmode);

I'll reboot and see what happens
;)

Rebooting will do nothing unless you run the following command after changing /etc/default/grub:

```
sudo update-grub
```

---

### Post by baha'a on 2010-04-01
thanks a lot for replaying

I modified the /etc/default/grub but there are comment should I delete the one in the beginning of the line that contains the values:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1024x768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

I ran 
```
update-grub
```

and then rebooted but nothing happend

but I noticed that - my computer is a Compaq- when it gives me in the beginning of the boot sequence the logo of Compaq and in the bottom the direction to enter setup "press ESC to enter setup" they are in a small square in the middle to.

and I remember that in the days of windows it did the same thing but I didn't care because I didn't use a console in Windows

so I think as a guy said it's a laptop LCD problem but could there be a solution in (great Linux :D)

thanks guys!

---

### Post by dcstar on 2010-04-02
> **baha'a said:**
> thanks a lot for replaying

I modified the /etc/default/grub but there are comment should I delete the one in the beginning of the line that contains the values:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
**#GRUB_GFXMODE=1024x768**

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

I ran 
```
update-grub
```

and then rebooted but nothing happend
........

Well, it isn't going to change anything if you leave the line commented out, it is?

---

### Post by baha'a on 2010-04-03
thanks for replying
but it didn't work out!

I believe it's a hardware problem

does any body have Compaq presario 2100

can you tell me if you have the same problem????

---

### Post by baha'a on 2010-04-07
hey guys I solved it
a guy called "maginot" in ubuntu support channel on IRC helped me.
Thanks maginot:D

any way after all changes listed apove I edited
```

/etc/default/grub

```
I recommented this line:
```

GRUB_GFXMODE=1024x768

```
and put (vga=791) in the commas in this line:
```

GRUB_CMDLINE_LINUX="vga=791"

```

note: this configuration is for 1024x768 resolution.

---

### Post by dcstar on 2010-04-07
> **baha'a said:**
> 
........
and put (vga=791) in the commas in this line:
```

GRUB_CMDLINE_LINUX="vga=791"

```

note: this configuration is for 1024x768 resolution.

As long as you don't mind the "deprecated" message that pops up on boot, that will work ok.

---

### Post by baha'a on 2010-04-11
> **dcstar said:**
> As long as you don't mind the "deprecated" message that pops up on boot, that will work ok.

the message you are talking about is like heaven versus the hell of the small screen
when it worked and I saw the full screen text I was going to jump from happyness

but I don't mind if you have a solution for it :D

thanks for replying any way :)

---

