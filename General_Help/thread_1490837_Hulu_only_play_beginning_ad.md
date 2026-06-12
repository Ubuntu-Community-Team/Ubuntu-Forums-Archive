---
title: "Hulu only play beginning ad"
date: 2010-05-22
forum: General Help
---

### Post by Metalclay on 2010-05-22
Hello,

Youtube's working fine for me, so is Vimeo and Hulu will also play the beginning ad. However, after that it just stays black. I mean, I can lower lights, turn up/down volume, pop out, even the preview scroll bar feature where you can quickly load up to the scene where the pointer is, works. The video of the actual thing I want to watch though, just doesn't go. 

I've tried on chrome and firefox and have tried other videos on hulu, nothing works. It's not even trying to transfer anything, it just says "done" at the bottom left in chrome. When I move the pointer for the preview thumbnail on the scroll bar though, it does start reading: "transferring ib.huluim.com..."

I'm on Lucid x64.

Thanks.

---

### Post by -humanaut- on 2010-05-22
Try deleting flash and reinstalling that will normally fix flash related problems atleast from my experience.

---

### Post by Metalclay on 2010-05-22
Nope didn't work.

I actually had to go into my .mozilla/plugin folder  and delete the .so file because the software manager couldn't uninstall it.

Anyway, still at a loss. I reinstalled and I still get the same outcome, everything works fine, event he ad, but the actual programming won't play.

---

### Post by OpSecShellshock on 2010-05-22
I usually get an error telling me it's having a problem with 64-bit flash, but I don't even get ad content when that happens. I've just kind of written off the site on my 64 bit desktop and use my 32 bit device instead.

---

### Post by efflandt on 2010-05-22
What flash plugin are you using?  Did you use Synaptic to install flashplugin-installer (or ubuntu-restricted-extras which includes that), or something else.  That is actually 32-bit flash with nswrapper, but should work.

If you installed real 64-bit flash instead, that no longer works with Hulu from a browser (Hulu broke that some time ago).  I hear that real 64-bit flash works with 64-bit Hulu Desktop.  But I cannot test that because my older Athlon64 lacks the lahf_lm instruction, and while someone did come up with a flashplugin-lahf-fix that works in browsers, Hulu Desktop does not pick up on that.

So I have been using 64-bit Hulu Desktop with flashplugin-installer, and that flash also works in 64-bit Firefox.

Did you try disabling all Visual Effects on your desktop.  I always do that because I have an older computer.  Another possibility is to try **nomodeset** as a kernel boot parameter in case your video has an issue with the new kernel mode setting (KMS).

---

### Post by Metalclay on 2010-05-22
Yup, that's it.

Checked the software manager and I have the 64 bit alpha flash installed. I downloaded Hulu Desktop and it worked. I still find it odd that the ad would play on the site, but the content did not. 

Out of curiosity, I uninstalled the 64 bit flash, and installed the x86 version using the app found here: 

[Adobe Tools]("http://dolphinaura.com/programming/adobe-tools/adobe-flash-plugin-installer-uninstaller-linux")

Went back to hulu via chrome, and it's now working with the x86.

Thanks!

---

### Post by bcg30506 on 2010-07-30
I have just the opposite problem.  My Hulu works fine in Firefox but Hulu Desktop only plays the ad at the start then a black screen.  It did play earlier however it froze every few seconds.  I changed the buffer size to try and fix that and that is when it playing videos.

I have a 32-bit system with a fresh mythbuntu 10.04 install and the 10.1 deb file for Flash from Adobe's site.

---

