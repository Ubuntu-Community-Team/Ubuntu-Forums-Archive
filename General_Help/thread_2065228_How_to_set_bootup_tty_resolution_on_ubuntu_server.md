---
title: "How to set bootup tty resolution on ubuntu server"
date: 2012-10-01
forum: General Help
---

### Post by Brockley John on 2012-10-01
Apologies if this is a common newbie question; I've found many similar questions asked & answered but none seemed to apply sufficiently closely.

I have ubuntu 12.0.4 installed as a terminal-based server only (no x-windows stuff) as it's on a creaky old celeron desktop.

It works fine and initially the resolution of the tty1 text interface that comes up after booting was reasonable. At some point since, it has somehow become configured to a massively high resolution that works but needs a magnifying glass to read (through no deliberate actions on my part!).

I'd like to force the text to something more comfortable, especially as I'm going to need to put a more basic monitor onto it that won't handle the resolution it's currently displaying.

I've tried editing /etc/default/grub with no effect. In fact, few of the configuration files that were referred to in answers to other people's questions seem to exist at all, and the few that I have found do not seem to set the graphics resolution.

Some basic pointers would be greatly appreciated.

thanks in advance

---

### Post by lechien73 on 2012-10-01
Hi and welcome to the forums,

I actually just saw your question as I was setting up an Ubuntu console-only server, so your timing was perfect :)

To change the resolution to 800x600, you would use the following command:

```
sudo nano /etc/default/grub
```

Then add the following lines - or uncomment and modify them if they already exist:

```
GRUB_GFXMODE=800x600
GRUB_CMDLINE_LINUX_DEFAULT="915.modeset=0 nomodeset"

```

Finally:

```
sudo update-grub
reboot
```

I successfully adjusted the resolution on my server with this method.

---

### Post by Brockley John on 2012-10-01
Thanks, that sorted it. It was the line that sets the command line default which was missing from other answers I found.

Thanks for your help.

---

### Post by lechien73 on 2012-10-01
You're welcome, glad to help. If you get chance, please could you use the **Thread Tools** menu above and mark the issue as [SOLVED]?

Thanks

---

