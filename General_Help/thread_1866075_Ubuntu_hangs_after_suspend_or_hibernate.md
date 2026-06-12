---
title: "Ubuntu hangs after suspend or hibernate"
date: 2011-10-20
forum: General Help
---

### Post by SyncMr on 2011-10-20
Hi,
After doing suspend or hibernate in Ubuntu 10.10, I am unable to resume. The system hangs and have to restart it by holding the power button. On googling I found similar cases. But is there any solution for this.

---

### Post by tredsyn on 2011-10-21
i have the same problem, i use 10.04 though. really annoying especially if you have 2 browsers open(with 5 tabs each) and you didn't bookmarked :(

---

### Post by SyncMr on 2011-10-21
yeah.. anyone knows how to solve it.? its really annoying.

---

### Post by kid1000002000 on 2011-10-21
same problem in 11.10

---

### Post by SyncMr on 2011-10-22
This problem seem to be present in most versions. Even then isn't there any permanent solution for this.? Senior member of ubuntu please help.

---

### Post by cozumel on 2011-10-22
I read somewhere about it being an issue with USB3 causing the hang @ suspend or hibernate.  They wrote a short script to resolve.  Going to see if I can find the link for you

---

### Post by cozumel on 2011-10-22
Found it!  It was for 11.10 with XPS L702X.  Maybe this helps you guys or maybe not.  But I post anyhow.

> The issue with the shutdown, hibernation and suspension is an issue with the USB3 driver. To work around it, insert a file into /etc/pm/config.d (I called mine 'XPS17-custom') with the following content:

SUSPEND_MODULES="$SUSPEND_MODULES xhci-hcd"

[http://www.cmdematos.com/2011/10/ubuntu-1110-oneric-on-dell-xps17-l702x.html]("http://www.cmdematos.com/2011/10/ubuntu-1110-oneric-on-dell-xps17-l702x.html")

Edit: Just noticed that there was an edit to the bottom of blog to which I linked, where it gave another script in the case when wireless card is causing the issue.

---

### Post by SyncMr on 2011-10-22
I tried adding the command to config.d, but it didnot work. :( Still the same problem.

---

### Post by tredsyn on 2011-10-24
> **SyncMr said:**
> I tried adding the command to config.d, but it didnot work. :( Still the same problem.

hey SyncMR, were you able to do steps 1 & 2? I just read the other thread and most of them got the issue fixed. I'm still unable to get through step 1, i'm getting confused of the commands you need to type in the termianl. but i'd try this again later (need to sleep) :)

---

### Post by tredsyn on 2011-10-25
Alright I was able to do steps #7 & #8 from [[COLOR="Blue"]_this_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1444822") forum. "Hibernate" is NOW working but "suspend" just turns the harddisk, fan, & the usb mouse on; screen is just blank, PC doesnt turn on completely. Important thing is Hibernate is now working :)

1. create "/etc/pm/sleep.d/20_custom-ehci_hcd" from the terminal
```
sudo touch /etc/pm/sleep.d/20_custom-ehci_hcd
```

2. edit the file
```
sudo gedit /etc/pm/sleep.d/20_custom-ehci_hcd
```
this will open gedit

3. follow post #7 from the link above. save file

4. make the file executable (as intructed from post #8 from the link above)
```
sudo chmod +x /etc/pm/sleep.d/20_custom-ehci_hcd
```

hibernate should now work :)

---

### Post by mpjanet on 2011-10-25
Was it really "hang"? try "Caps Lock" or "num lock" to see if KB light changes. If you are using ATI video card, it will always "hang". coz video card can not recover. try to append "vga=0" option to line begin with GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub. It work for my old thinkpad. sleep & hibernate worked like a charm.

---

