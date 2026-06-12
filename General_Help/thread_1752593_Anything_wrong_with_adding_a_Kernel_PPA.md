---
title: "Anything wrong with adding a Kernel PPA?"
date: 2011-05-08
forum: General Help
---

### Post by polardude1983 on 2011-05-08
So I'm currently using Ubuntu 10.04.2 and the current Kernel I have is 2.6.32-32-generic. Anyways I am wanting to upgrade my kernel just for the sake of upgrading it.

Are there any cons to adding a kernel PPA? anybody have any thoughts against it? good, bad?

PPA is 

ppa:kernel-ppa/ppa

---

### Post by winchendonsprings on 2011-05-08
I was wondering too. I read this - [http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0](http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0) - this morning.

I'm having display issues on both my machines. I can't track down the problem and thought a newer kernel might help, yeah?

---

### Post by polardude1983 on 2011-05-08
Yeah unfortunately I didn't read that until i Uninstalled 11.04 and downgraded back to 10.04.2

Does upgrading your Kernel like the same as upgrading your bios? meaning only upgrade when you have a problem?

I know you shouldn't upgrade your bios because it could cause serious problem and you shouldn't update it unless you have a problem. Because it could break your system. Never update your bios just to update it. But my question is does the same go for kernel upgrades?

---

### Post by VanR on 2011-05-08
Well I'm running 2.6.39 on 10.10 and it seems really fast and stable.

---

### Post by lykwydchykyn on 2011-05-08
the worst that could happen is that the new kernel doesn't boot or something doesn't work under the new kernel.  In which case, you reset your machine, choose your old kernel in the GRUB menu, and happily boot as you were (and of course remove the broken kernel).

Unlike BIOSes, you can keep as many kernels on your system as you want and choose which one you want at boot time.  So feel free to tinker.

---

### Post by cwwilson721 on 2011-05-08
> **lykwydchykyn said:**
> the worst that could happen is that the new kernel doesn't boot or something doesn't work under the new kernel.  In which case, you reset your machine, choose your old kernel in the GRUB menu, and happily boot as you were (and of course remove the broken kernel).

Unlike BIOSes, you can keep as many kernels on your system as you want and choose which one you want at boot time.  So feel free to tinker.

To expand just a little on this:

The [COLOR="Blue"]BIOS[/COLOR] (Basic Input Ouput System) is a flash chip (usually), and part of your motherboard's hardware. Don't bother updating this until you have a real good reason to, and use the BIOS's provided by your motherboard maker.

The [COLOR="Red"]kernel[/COLOR], on the other hand, is the "brains and backbone" of your OS (Operating System). Yes, Windows has a kernel too. But you cannot only update Windows kernels like you can Linux. You can update your kernel as you see fit, however and whenever you wish. You can either use the PPA like you want, or compile and install your own. But, as the quote above states, if it doesn't work, just use the 'last known good' kernel during boot (If you 'roll your own' kernel, make sure to package it first, so you can use a previous version. Google the procedure if you want).

As far as actually using a PPA to install newer kernels, I'd think about it. How much does 'bleeding edge' kernel builds matter to you, as compared to stability and completeness? If you are an 'average user', you'd be best off waiting for the kernels to get built and pushed through Update Manager. If you absolutely need the latest one right now, go to the PPA or 'roll your own'.

The other side of the coin is do you 'trust' this PPA to be safe, and free from malicious code? (Of course, you should ALWAYS think of this anytime you add ANY PPA)

Either way, it is your system. Do as you feel fit. What I would do, or not, depends on me. You know what you want. It is your system. 

This ain't Windows or Mac. You have a choice.

---

### Post by winchendonsprings on 2011-05-08
@cwwilson721 Can you tell us what nvidia driver you are using? I have a similar video card and things are NOT going smoothly since 11.04.

---

### Post by cwwilson721 on 2011-05-08
270.41.06

That's from nvidia-settings.

According to the 'Additional Drivers' app, it is "Activated but not currently in use" (current). It IS in use, just says it's not.

---

### Post by winchendonsprings on 2011-05-08
> **cwwilson721 said:**
> 270.41.06

That's from nvidia-settings.

According to the 'Additional Drivers' app, it is "Activated but not currently in use" (current). It IS in use, just says it's not.

@cwwilson721 I have the same driver and same problem saying it isn't in use. But I'm having lots of glitches, artifact, compiz failing, having to drop to console to restart gdm...

 Although I can use  System>Preferences>Monitors I can also use the  System>Administration>Nvidia X Server Settings. About once every  15 minutes there is a major screen flicker moving all windows to current  workspace, and about once every 90 minutes Compiz or an unknown fails  completely leaving the keyboard useless. I then have to drop to the  console(alt=+ctrl+f1) and restart gdm.

Anyway, lot's of issues

---

