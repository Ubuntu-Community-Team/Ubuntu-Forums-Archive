---
title: "Reinstall Ubuntu; no keyboard, now no boot."
date: 2012-09-25
forum: General Help
---

### Post by cowpig on 2012-09-25
I have a 2-month old Sony Vaio S, and am dual-booting windows 7/ubuntu on it.

Ubuntu was crashing a lot and acting strange, so I decided to reinstall it. Upon reinstalling, I was asked to restart, and instead of going to the ubuntu login screen, or grub, I got an all-black terminal screen. I typed 'exit', and there was a message saying something about 'panic,' and it seemed to be frozen, so I just ignored it (as you do), and force-restarted my computer.

Well, upon restarting, my computer didn't detect any keyboard input, only my USB mouse. I didn't test the trackpad. It won't detect the keyboard in grub either, and now there seems to be no timer, so I'm permanently stuck in GNU GRUB. I don't like it here.

I don't have a PS/2 port on my laptop, and don't own a USB keyboard, so I can't try that. Also, I can't even get to the Sony Vaio boot menu, which is extra bonus wtf.

Help!!

---

### Post by cowpig on 2012-09-25
OK so it seems my USB device which I used to install ubuntu boots ubuntu off itsself as default, so now I'm in Ubuntu with no keyboard. Trackpad isn't working either, but my external mouse does.

oh, edit: I'm on my old laptop, on Ubuntu. So if there's something I could do by sshing into my laptop somehow (if that's possible) then that might work?

edit edit: Upon the discovery of ubuntu's Universal Access feature, I can now type things in by clicking keys on an on-screen keyboard (albeit very slowly). Someone please tell me how to figure out wtf is going on!!

---

### Post by irv on 2012-09-25
Why don't you just start over with a reinstall. Boot with the DVD/CD or USB whatever you were booting with and start the install over again. You should have a keyboard and mouse again with the install.

---

### Post by cowpig on 2012-09-25
Just reinstalled, and keyboard/touchpad still not working, even in GRUB/USB boot menu

---

### Post by irv on 2012-09-25
> **cowpig said:**
> Just reinstalled, and keyboard/touchpad still not working, even in GRUB/USB boot menu

When you are first booting you PC, before the grub. When your first screen comes up does your keyboard work to hit the hot keys to get into your CMOS? If that doesn't work you have a hardware problem. On my Dell laptop it is the F2 key, it might be different on your.
Can you boot with the install media? And run the live OS? And does the keyboard work with the live OS?

---

### Post by cowpig on 2012-09-25
> **irv said:**
> When you are first booting you PC, before the grub. When your first screen comes up does your keyboard work to hit the hot keys to get into your CMOS? If that doesn't work you have a hardware problem. On my Dell laptop it is the F2 key, it might be different on your.

I can't get into the CMOS.

I just have trouble believing that my computer ran into a hardware problem precisely as I reinstalled ubuntu, but maybe!!?

> **irv said:**
> 
Can you boot with the install media? And run the live OS? And does the keyboard work with the live OS?

Yes, I can, that's the only operating system I can get to right now, and no, the keyboard still doesn't work.

---

### Post by irv on 2012-09-25
> **cowpig said:**
> I can't get into the CMOS.

I just have trouble believing that my computer ran into a hardware problem precisely as I reinstalled ubuntu, but maybe!!?



Yes, I can, that's the only operating system I can get to right now, and no, the keyboard still doesn't work.

If you can't get into your CMOS it can't be anything else but your keyboard.
Let me get this straight, are you saying that you can't get in because of the keyboard not responding or you don't know how to get in? (you don't know what the hot keys are)?

---

