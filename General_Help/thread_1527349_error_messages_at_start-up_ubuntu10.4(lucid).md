---
title: "error messages at start-up ubuntu10.4(lucid)"
date: 2010-07-09
forum: General Help
---

### Post by joe iwannou on 2010-07-09
hy everybody
im from greece and im not write well english
my problem is  ubuntu run slower now(after 2 months ago i install ubuntu)
and at begin it was much faster than win.
at start up after choose grub (dual boot ubuntu - xp)
displayed the error messages below and i don know what to do 
to repair.
laptop toshiba l-10 1gb ram 
[IMG]http://img30.imageshack.us/img30/8139/screenshotscl.png[/IMG]
[IMG]http://img267.imageshack.us/img267/8259/screenshot1od.png[/IMG]
[IMG]http://img51.imageshack.us/img51/6694/screenshot5ok.png[/IMG]
i write in greek ubuntu forum but no one answer
if anyone can help is welcome
thank you

---

### Post by Rubi1200 on 2010-07-09
Hi,
could you please provide us with some more details?

Specifically, we need to know the following:

What graphics card do you have?

Are you still able to get into Ubuntu, meaning do you get to the Desktop?

Do you have an installation CD for Ubuntu or can you get one?

I will try and help you understand what is going on.

The "drm:i915_handle_error" suggests a graphics issue. i915 is for Intel chipsets, but we need to know which series (see question above)

The error about /dev failed could be a kernel issue. Have you updated your installation recently?

See this link:

[http://ubuntuforums.org/showthread.php?t=1435968](http://ubuntuforums.org/showthread.php?t=1435968) especially post #4

The other messages you see are related to an Ubuntu security feature known as AppArmor which is loaded at boot. Not sure why you are seeing those messages.

---

### Post by joe iwannou on 2010-07-10
> **Rubi1200 said:**
> Hi,
could you please provide us with some more details?

Specifically, we need to know the following:

What graphics card do you have?

Are you still able to get into Ubuntu, meaning do you get to the Desktop?

Do you have an installation CD for Ubuntu or can you get one?

I will try and help you understand what is going on.

The "drm:i915_handle_error" suggests a graphics issue. i915 is for Intel chipsets, but we need to know which series (see question above)

The error about /dev failed could be a kernel issue. Have you updated your installation recently?

See this link:

[http://ubuntuforums.org/showthread.php?t=1435968](http://ubuntuforums.org/showthread.php?t=1435968) especially post #4

The other messages you see are related to an Ubuntu security feature known as AppArmor which is loaded at boot. Not sure why you are seeing those messages.

1 my graphic card is 82852/855GM 
2 yes i go to desktop and all work good but litle slower than at begin
3 i dont have cd install but i can make one
4 my chipset i think is on the photo bellow
[IMG]http://img59.imageshack.us/img59/5115/screenshot2hu.png[/IMG]
thank you

---

