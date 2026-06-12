---
title: "Black screen during boot but GUI comes up properly"
date: 2012-09-26
forum: General Help
---

### Post by JKyleOKC on 2012-09-26
I have a strange one on 12.04.1 Precise 64-bit installed in a VM under vbox 4.1.20. When first installed it worked normally, with the Plymouth screen and moving bar while it was booting, then the switch to the XFCE desktop. I really wanted to see the scrolling text during boot, so edited /etc/default/grub to remove "quiet splash" then ran update-grub and rebooted.

The screen remained totally dark during the boot, then came up with the lightdm login display. No scrolling text, no nothing to indicate that anything was happening.

I then put the "quiet splash" options back in place, updated grub again, and expected to be back where I began.

I wasn't. It's still not showing anything at all during the boot process, but working normally once it gets to the login screen and lets me log in.

What else do I need to do to put it back to letting me know that SOMETHING is happening during the boot process?

---

### Post by bogan on 2012-09-27
Hi!**, JkyleOKC,**

Try editing the Grub Menu script, [ Press 'e' with Ubuntu highlighted], remove 'quiet' and add "--verbose text" [ no quotes ] and press 'Crtl+x" to boot.

That should give you the scrolling text.

Chao!, **bogan**.

---

### Post by JKyleOKC on 2012-09-27
Tried it, no change at all. Also tried adding "nomodeset" in case it was a driver issue, again with no effect.

I've verified now that it happens exactly the same way with all three of my Xubuntu 12.04.1 VMs. One is 64-bit running on a 64-bit 12.04.1 host, another is the same 64-bit version but running on a 32-bit 10.04.4 host, and the last is a 32-bit version running on that same 10.04.4 host.

I'm suspecting that it has something to do with the hidden "vt-handoff=7" option that was introduced last year. The 32-bit VM does show some of the boot text very briefly at the end of the boot process, followed by a quick flash of the plymouth animation screen before launching the XFCE desktop via automatic login. The 64-bit VMs may be doing similar things but they go by so rapidly that I can't be sure they are even there.

I'll try editing the grub.d files to change the handoff option, on one of the throwaway VMs, and see whether that makes any difference...

Thanks for the suggestion! I was beginning to wonder if I'm the only one seeing this behavior. All three VMs are on vbox; it's 4.1.20 on the 64-bit host but 3.2.12 on the 32-bit host, and it's possible that the vbox video driver isn't playing nice with the 12.04 boot process. The 64-bit guest on the 32-bit host cannot install Guest Additions, but they are installed and working on the 32-bit guest, so there are different vboxvideo drivers involved yet both behave the same way...

---

### Post by Linux_junkie on 2012-09-27
I have the same thing happening but I have Xubuntu 11.10 installed.  Switch computer on, screen goes black then when its ready it displays the login screen and everything works fine after that.

Only for me this is not an issue.   As long as there is no problems booting the computer or in running Xubuntu

---

### Post by JKyleOKC on 2012-09-27
Finally solved it: the /etc/default/grub file has these two lines:```
# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"
```I removed the "#" from the second line to disable the graphical terminal, and immediately got the result I wanted. It also seems to load a bit faster, which is an added bonus. The lines now look like this:```
# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL="console"
```

EDIT: You can also do this from the grub-customizer program, by clicking the "Advanced" button on the "General" tab, locating the line that contains the word "console" and clicking the checkbox for that line. This avoids the hassle of launching an editor in super-user mode and makes it much simpler.

---

### Post by bogan on 2012-09-28
Hi!, **JKyleOKC**,

I tried uncommenting the "GRUB_TERMINAL" line and ran 'update-grub', booted with "quiet splash $vc_handoff" still in place,  just to see what would happen with 12.04.1 [32bit pae]; it is a long time since I last used it.

I am running a straight Ubuntu desktop with Grub Customizer, but no ' VM, vbox or XFCE'.

It shut out the GC set-up, giving the default Grub Menu, text & background, white on black, booted to a black screen with a message: "Booting to a command list" and a flashing cursor, then gave a brief Plymouth splash screen with some lines of text, too briefly to read, and the Lightdm login screen without the background I had set, just the 'Aubergine Flare' background.

SO whatever it does for you is quite different from with my 'standard' set-up.

Chao!, **bogan.**

---

### Post by JKyleOKC on 2012-09-28
I think that, had you edited out the "quiet splash" options via grub-customizer, you would have seen pretty much the same thing I see here. The update-grub scripts insert the vthandoff option if they find "splash" as one of the options present, and that's what gives you the black screen followed by a flash of the plymouth screen. The vthandoff option is already there by the time you get to the "e" edit.

I'm pretty much convinced, now, that the cause of the totally black screen is that the current /etc/grub.d/05_debian_theme script switches to a frame buffer that's not actually present in the current kernel, but I've not found a reliable way to change that action and it will probably be different in the next release anyway!

---

### Post by bogan on 2012-09-28
Hi!. **JKyleOK**C,

Yeah, you were right, I had to delete the 'splash' as well as the 'quiet' to get more text than the "Booting to a command list" message.

Even then I only got the last five or so lines, until I deleted the "$vt_handoff' as well, then i got the whole screed, without adding '--verbose text'.

I think it is update-grub that puts "$vt-handoff" in /boot/grub/grub.cfg from 10_linux_proxy [ when GC is in use ], and hence in the grub menu script.

Chao!,** bogan.**

---

