---
title: "Unable to install ATI driver for 5850"
date: 2010-04-16
forum: General Help
---

### Post by pain1986 on 2010-04-16
I am using ubuntu 10.04 and I am trying to install drivers through the hardware drivers in system > administration but I keep getting "SystemError: installArchives() failed" error.

I also tried installing the latest drivers from the ati website but nothing worked.

When I go to synaptic package manager it says "fglrx-amdcccle" broken. I tried to remove it but when I reboot, it says its still broken.

Any help would be greatly appreciated as I hate using a low resolution on my desktop.

---

### Post by pain1986 on 2010-04-16
Anyone able to help?

---

### Post by e4uforums on 2010-04-16
I have a 4870x2 and I recently tried to update to 10.04.  Everything went well until I got to the video drivers and then I had a ton of trouble.  Eventually some folks on the forum told me that AMD hasn't released proper drivers to work with Lucid yet.  As I understand, this is pretty typical.

I reverted back to Karmic and the same 10.3 catalyst drivers installed without issue.

If anyone has information to the contrary, I would be very interested.  :)

---

### Post by pain1986 on 2010-04-16
Hi.

I donwloaded this driver - ati-driver-installer-10-3-x86.x86_64.run

How did you install this driver? I installed it but it gave me errors.

---

### Post by e4uforums on 2010-04-16
I installed it by following the guide on the ATI site.  I can't tell you exactly off hand, but I did follow the instructions to the "T".

---

### Post by pain1986 on 2010-04-16
I get this error when trying to remove the broken package.

> E: /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu2_i386.deb: subprocess new pre-installation script returned error exit status 1

---

### Post by elrasho on 2010-06-05
I'm new to Ubuntu and I'm trying to install the 10.4 ATI drivers. I get upto the part that says "Enter the command sh ./ati-driver-installer-10-5-x86.x86_64.run to launch the ATI
Proprietary Linux driver installer", but then it says I can only install the drivers as a SuperUser.

How do I do this? I've googled and apparently I just need to add "sudo" at the beginning but that doesn't work, says "cannot open file". Ive put the driver file (.run) on the Desktop aswell.

An help would be greatly appreciated, this is a fresh installation of 10.04 too.

---

### Post by davidmohammed on 2010-06-05
have you tried

sudo sh ./ati-driver-installer-10-5-x86.x86_64.run

?

---

### Post by bcooperb on 2010-06-21
@elrasho

Like davidmohammed posted:
[B]
sudo sh./FileToInstall.run[/B]

**sudo** means SuperUser Do.....
in this case run a Bourne-Again SHell (Bash) Script also known as a SHell Script.

Hope that helps you understand that a little more....

As far as the ATI issue! I am in the same boat, with the same errors! And I haven't found a solution for this yet. I can't uninstall and I can't reinstall.

---

### Post by khelben1979 on 2010-06-21
Have you tried with the latest driver which is available now?

---

