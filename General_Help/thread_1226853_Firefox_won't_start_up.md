---
title: "Firefox won't start up"
date: 2009-07-30
forum: General Help
---

### Post by slymi2005 on 2009-07-30
I can't launch firefox (from awn, panel, menu, terminal) but it shows up in system monitor and it says running. I can run it in safemode but how do I go about fixing it so that I can run it again in normal mode.

solved

---

### Post by slymi2005 on 2009-07-30
It ran when I disabled all addons in safemode.

Update: I'm checking each add on one at a time.

---

### Post by QIII on 2009-07-30
So are you saying that after you ran it in safe mode and disabled the plugins, you are now able to launch it normally?

---

### Post by slymi2005 on 2009-07-30
I got this from the terminal:

```
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
The program 'firefox-3.5' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 820 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by QIII on 2009-07-30
> **slymi2005 said:**
> 
Update: I'm checking each add on one at a time.

Thanks.  That's what I was going to ask.

Let us know when you get to the one that is causing your problem.  It'll be something someone else can refer to by searching the forum some day.

---

### Post by slymi2005 on 2009-07-30
Yes. with all addons and plugins disabled it ran fine. Then I tried it with plugins enabled and it ran, then I enabled adblock and it ran but then I enabled download status bar and i got the error above.

---

### Post by QIII on 2009-07-30
Saw a few LaunchPad reports with regard to canberra.

For now, don't enable the last, and it might be worth a look through LaunchPad to see if you are experiencing the same as others and add a confirm.

Otherwise, if you can't find a resolution here (I don't have any advice), then consider making a bug report.

---

### Post by slymi2005 on 2009-07-30
Thanks I'll head on over there, its strange because firefox 3.0 popped up all of a sudden with all addons enabled and then I got out of it and tried firefox 3.5 with download status bar enabled and it worked but then it stopped with the next addon so its not status bar. Thanks though.

---

### Post by slymi2005 on 2009-07-30
I ended up having to run this command:

sudo chown -R username:username ~/.mozilla (where username is my username)


and everything works fine, yay!

---

### Post by lovinglinux on 2009-07-30
> **slymi2005 said:**
> I ended up having to run this command:

sudo chown -R username:username ~/.mozilla (where username is my username)


and everything works fine, yay!

For future reference...

See **Solution** [*[COLOR="Red"]**FOT001**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT001).

I have been experiencing similar problems with Firefox 3.5, even with the correct ~/.mozilla permissions. If you find yourself on the same situation in the future, try running Firefox with this command:

```
firefox -P "**[COLOR="DarkRed"]Default[/COLOR]**"
```

Where **[COLOR="DarkRed"]Default[/COLOR]** is the profile name. Most of the time when I have this issue, Firefox launches correctly when using this command.

---

