---
title: "Cable Gateway + HP Printer killed by dapper"
date: 2006-06-07
forum: General Help
---

### Post by cached on 2006-06-07
I was using Linksys BEFCMUH4 as my cable modem+router (in one) and it worked very well with 5.10 but one I upgraded to 6.06, the top choice in the GRUB menu wont work with it (so I boot from the bottom one).

From both choices, my printer (HP Deskjet 5940) doesn't work anymore... it doesnt seem to allow me to install any drivers.

What should I do? ](*,)

---

### Post by Casey on 2006-06-07
None of us will know what the entries are in your grub list without you telling us.

The easy way to do that is:
open a terminal, type:
```
cat /boot/grub/menu.lst
```

Copy the portion that looks like this:
```
## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-23-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-686 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-686 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-686 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-23-686
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Here so that we can see it (Basically copy the Automagic Kernels List).

Edit: Also it will help if you use CODE blocks to post (Click the # sign on the post window and paste the contents of the file between the two code tags).  Also Ctrl-C will not work for copying from a terminal.  Select the text, right click, select copy.  Then you can paste it into this window.

---

### Post by cached on 2006-06-07
```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, kernel 2.6.12-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by Casey on 2006-06-07
Of these, which one is working:
```

Dapper  ->  Ubuntu, kernel 2.6.15-23-386
Dapper  ->  Ubuntu, kernel 2.6.15-23-386 (recovery mode)
Breezy  ->  Ubuntu, kernel 2.6.12-10-386
Breezy  ->  Ubuntu, kernel 2.6.12-10-386 (recovery mode)
Breezy  ->  Ubuntu, kernel 2.6.12-9-386
Breezy  ->  Ubuntu, kernel 2.6.12-9-386 (recovery mode)

```

The last 4 entries are from your Breezy installation (so when you use one of those, your printer still works).  The first 2 are from Dapper.  It's possible that support for the devices was working in .12 (Breezy) but not .15 (Dapper).  In this case, you should be able to file a bug at launchpad.  Perhaps someone else can also provide more insight.

I suspect that
Ubuntu, kernel 2.6.12-10-386
and 
Ubuntu, kernel 2.6.12-9-386
would both work but
Ubuntu, kernel 2.6.15-23-386
doesn't.

---

### Post by cached on 2006-06-07
This is what appears in printer properties:
> Printing: open device failed; will retry in 30 seconds...

Also, sound doesn't work with anything EXCEPT the Dapper install (was working fine before).  Here is what it says when I double click on the icon:
> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

What now?](*,)

---

### Post by Casey on 2006-06-07
Unfortunately I don't have an HP Printer to test with or that cable modem.  I think that right now the forums are swamped with questions from newer users, so it might be more difficult to get a good response than normal.

That said, I think your best chance for help with these issues would be in IRC.  There are a list of possible channels available from the ubuntu community website:
[http://www.ubuntu.com/community/irc]("http://www.ubuntu.com/community/irc")
The IRC Server is irc.freenode.net and the channel is #ubuntu

I think that they will probably be able to help you with the printer issues (as I would imagine HP printers are fairly common) but I'm not as sure about the cable modem issue.

I hope that this is of some assistance to you.

If you need more help with how to use IRC, I should be able to help you with that.  Unfortunately I don't know how to solve your problems though (But giving people this link should get them started).

---

### Post by cached on 2006-06-10
Well I went into the IRC channel and got no help (not even a reply). I did find that on startup alsa gives an error "no soundcard found", which probably means that some drivers were added/removed in the upgrade process. Is there any way to revert to the old drivers that I had with 5.10?

---

### Post by cached on 2006-06-13
Sorry for double post, but I really need this to work :-({|=

---

