---
title: "Random lock-ups on Ubuntu 10.10 - which logs to check?"
date: 2011-03-08
forum: General Help
---

### Post by LeXxPT on 2011-03-08
Hi,

I've been experiencing lock-ups on my Ubuntu 10.10, which cause me to lose the ability to switch or launch new applications using my mouse (I can still move the pointer around, but clicking doesn't do anything). I can switch applications via Alt+Tab, but for some reason it seems really clumsy when I do.

The way I have been using to get out of this is by pressing Ctrl+Alt+F1, and then on the shell running the command sudo killall -9 Xorg.
This obviously causes me to lose my opened windows, which is really annoying.

However, this hasn't only happened to me in 10.10. I remember it also happening on 9.10, and the only thing that I seem to be doing in common is using Eclipse, the terminal, and having the graphics settings set to normal (so that I can have a transparent terminal). I don't remember having this issue when I had it the graphics settings on "off" (or something like it, sorry but I'm not on Ubuntu right now and I don't remember the exact setting).

Having the setting on "normal", also means that I am using the proprietary Nvidia drivers (I have an Nvidia 8600m GT card).

So my question is, which logs should I check after the crash in order to get some idea of what might be causing this?

Thanks.

---

### Post by wojox on 2011-03-08
I'd check in /var/log/Xorg.0.log first. To weed out the problems run these two commands sereratly:

```
cat /var/log/Xorg.0.log | grep '(WW)'
cat /var/log/Xorg.0.log | grep '(EE)'
```

---

### Post by LeXxPT on 2011-03-09
Thanks for the reply.

I've got this when running the commands:

$ cat /var/log/Xorg.0.log | grep '(WW)'
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.258] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.258] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    26.258] (WW) Disabling Keyboard0
[    26.258] (WW) Disabling Mouse0

$ cat /var/log/Xorg.0.log | grep '(EE)'
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.


I guess the font isn't the problem here.
I'm going to do some digging to see what the line below it (AllowEmptyInput is on) is about.

Edit: So I just added 'Option "AllowEmptyInput" "false"' to my Xorg.conf. Let's hope that this fixes the problem.

---

### Post by LeXxPT on 2011-03-11
So that did not fix the problem, as I just experienced it.

Here's what I found in syslog:

Mar 11 19:29:18 alex-laptop acpid: client 1295[0:0] has disconnected
Mar 11 19:29:18 alex-laptop acpid: client 1295[0:0] has disconnected
Mar 11 19:29:18 alex-laptop acpid: client connected from 1295[0:0]
Mar 11 19:29:18 alex-laptop acpid: 1 client rule loaded
Mar 11 19:29:19 alex-laptop acpid: client connected from 1295[0:0]
Mar 11 19:29:19 alex-laptop acpid: 1 client rule loaded
Mar 11 19:30:27 alex-laptop kernel: [26681.000278] usb 5-1: USB disconnect, address 2
Mar 11 19:30:29 alex-laptop kernel: [26682.728215] usb 5-1: new low speed USB device using uhci_hcd and address 3
Mar 11 19:30:29 alex-laptop kernel: [26682.933719] input: Microsoft  Compact Optical Mouse 500 as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input10
Mar 11 19:30:29 alex-laptop kernel: [26682.933826] generic-usb 0003:045E:0737.0003: input,hidraw0: USB HID v1.11 Mouse [Microsoft  Compact Optical Mouse 500] on usb-0000:00:1d.0-1/input0

And on Xorg.log I get the following warnings and errors:

[ 26808.157] (WW) Warning, couldn't open module kbd
[ 26810.375] (WW) Warning, couldn't open module kbd


[ 26808.157] (EE) Failed to load module "kbd" (module does not exist, 0)
[ 26810.375] (EE) Failed to load module "kbd" (module does not exist, 0)
[ 26810.375] (EE) No input driver matching `kbd'

Any ideas?

---

