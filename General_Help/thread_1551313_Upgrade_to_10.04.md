---
title: "Upgrade to 10.04"
date: 2010-08-12
forum: General Help
---

### Post by shad0w_crash on 2010-08-12
I installed the upgrade to ubuntu 10.04 (from 9.10). After rebooting it showed the ubuntu screen for loading, but when the loading is finished the screen turns black (not even a mousepointer or textpointer).
The first thing I tryed was booting it in recovery mode with console only. That worked. Then I checked the etc/X11/xorg.conf file. But that doesn´t seem different from the file it used to be (had a .backup because an earlier update did mess up my whole config so when I got it all working again i backupped the file )

Do someone know what the problem is, and how it can be fixed?

---

### Post by realzippy on 2010-08-12
What graphics-card driver do you use?

```
lspci | grep VGA
```

---

### Post by dino99 on 2010-08-12
your issue is not unique, it fullfilled this forum since the beginning of plymouth, remove "splash" on the boot line (/etc/default/grub) then update-grub again

check that your graphic driver is activated (system admin hardware driver)

---

### Post by shad0w_crash on 2010-08-12
@realzippy,
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
@dino99,
It did remove the splashscreen but didn't bring me the loginscreen.

Tnx for the advice so far, but it didn't work yet:( Any other clues?

---

### Post by tryst0 on 2010-08-12
I am having similar kind of problem. first I tried to upgrade(from 9.10)  by update manager but it failed at setting new channel.then I upgraded from terminal "sudo apt-get upgrade".it worked ...up-gradation done successfully.But after restart, it shows grub then first it showed ubuntu logo then a black login screen(terminal kind) rather than GUI login.
black screen says:
ubuntu 10.04.1 LTS loadb1.tm.local tty1
loadb1.tm.local login:

here i am able to login by my 9.10 user name 
that shows 
tryst0@loadb1 rather than tryst0@tryst0 
still i can see my file which or on desktop
mean its working like terminal
i tried lot of suggestion from here and there
and a lot of time it showed:gksudo:3037:Gtk-Warning**:cannot open display 

any help will be appreciated.
now i have installed new 9.10. keeping the problematic lucid to correct it

---

### Post by tryst0 on 2010-08-12
i just tried "startx"
it opens the GUI but my keypad is not working in it though mouse(only touch pad but not USB ) is working.
also every time i have to login on same terminal like window and then "startx"....
even on shutdown, it do not shutdown but return to same terminal like window ....
what is going on ...any help and suggestion please....

---

### Post by shad0w_crash on 2010-08-12
Logging in by the terminal and executing startx doesn't work here either!

---

### Post by dino99 on 2010-08-12
maybe you need to test booting with nomodeset on the boot line

---

### Post by shad0w_crash on 2010-08-12
@dino99
well I'd like to try, but I don't think it's a boot problem. Because the system does boot (to terminal for example) and login in works fine (via terminal). 

The problem occurs when I execute startx then the whole screen turns black without a mouse pointer or any other sign of activity. 
But in terminal everything works fine, I want my gui back:P!

---

### Post by shad0w_crash on 2010-08-12
I've collected some more information. The problems seems to be in GDM:

/var/log/gdm/:0-greeter.log
Windowmanager waarschuwing: currentTime used to choose focus window; focus window may not be correct.
windowmanager waarschuwing: Got a request to focus the no_focus_window with a timestamp of 0. This shouldn't happen!
Windowmanager waarschuwing: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1400027(Aanmeldven)

(waarschuwing is a dutch word for warning)

I already tryed dpkg-reconfigure gtm

---

### Post by shad0w_crash on 2010-08-13
Anyone got a clue what is happening here and/or how to fix it?

---

