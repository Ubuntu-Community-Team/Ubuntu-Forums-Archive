---
title: "Configuring MCE Remote in Oneiric"
date: 2011-10-24
forum: General Help
---

### Post by a0peter on 2011-10-24
I just installed Oneiric 11.10 on my Asus EB1501 and to my satisfaction the remote works out of the box without installing lirc. But I would like to edit the actions the different buttons have. How do I do that?

The MCE button for example launches Banshee, and I would like for it to launch XBMC.

---

### Post by mutant_matt on 2011-11-30
Does the play button work for you?  I have Mythbuntu 11.10 installed and am using the Microsoft Vista/Windows 7 MCE remote (the one with the built-in mouse pad), and the kernel loads it's main-tree driver out of the box, and works, only with some buttons (up/down/left/right/OK (enter), number buttons).  It doesn't work with others, but I am struggling to figure it out/find fixes on the web.

Sorry to hijack your post! :)

Cheers,

Matt.

---

### Post by aquarius18 on 2011-12-25
> **a0peter said:**
> I just installed Oneiric 11.10 on my Asus EB1501 and to my satisfaction the remote works out of the box without installing lirc. But I would like to edit the actions the different buttons have. How do I do that?

The MCE button for example launches Banshee, and I would like for it to launch XBMC.

The**[ XBMC Wiki]("http://wiki.xbmc.org/index.php?title=Main_Page")** discusses a stack of different remotes that work with Linux - along with their relevant configurations, ups and downs etc.

---

### Post by mutant_matt on 2011-12-26
To remap buttons, you either remap them directly (which IMO is a bad idea, because then you're remapping the keys that it is pretending to be as a keyboard HID device, and if you plug in an HID/USB keyboard, that will have the same remappings).

The other way, is to use LIRC to do it, in which case, if you've got the same remote as me ("Windows 7/Vista" MCE remote with the added "mousepad" circular thing), then you'll need to "chain" two LIRCDs together (as some of the keys come via the "keyboard" part of the remote, and some as the "mouse" part (two event devices)).

I can post my hacked /etc/init.d/lirc if need be, if you find yourself in that position.

Cheers,

Matt.

---

