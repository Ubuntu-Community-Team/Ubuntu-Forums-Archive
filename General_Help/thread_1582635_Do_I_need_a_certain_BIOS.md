---
title: "Do I need a certain BIOS?"
date: 2010-09-26
forum: General Help
---

### Post by NathanDTaylor on 2010-09-26
Do I need a certain BIOS for my computer to run Ubuntu? I have a Toshiba Satellite L505. Someone said if I update my bios, it might work. When I try to update my bios, I get an error says something like "The current BIOS settings could not be found" so I called toshiba and they said that Ubuntu might require a certain BIOS. Can anyone help me? I reaaaallllyyy want Ubuntu.

---

### Post by Sub101 on 2010-09-26
I havent heard of such a case myself.

You do generally need to change your BIOS settings to ensure your device is booting from CD/DVD or perhaps USB depending on your installation medium. As for having to update the BIOS, I would be surprised.

---

### Post by NathanDTaylor on 2010-09-26
> **Sub101 said:**
> I havent heard of such a case myself.

You do generally need to change your BIOS settings to ensure your device is booting from CD/DVD or perhaps USB depending on your installation medium. As for having to update the BIOS, I would be surprised.

I can successfully boot from CD/Flash Drive but when the purple screen goes away, it comes up to a CMD prompt type window and it says something like "[0.6#######] thread_starter" or something like that. I could take a pic if that would help.

---

### Post by Sub101 on 2010-09-26
Not something I know of... Do you have any more information about the error message?

---

### Post by NathanDTaylor on 2010-09-26
> **Sub101 said:**
> Not something I know of... Do you have any more information about the error message?

I'll take a pic of it

---

### Post by NathanDTaylor on 2010-09-26
> **Sub101 said:**
> Not something I know of... Do you have any more information about the error message?

Actually I recorded a video. It is uploading to youtube. ETA: 15 mins

---

### Post by NathanDTaylor on 2010-09-26
> **Sub101 said:**
> Not something I know of... Do you have any more information about the error message?

Here is a video of me trying it
[http://www.youtube.com/watch?v=1CKspxjiMwI](http://www.youtube.com/watch?v=1CKspxjiMwI)

---

### Post by Sub101 on 2010-09-26
Thanks for taking the time.

I would suggest this is your problem;

[http://newyork.ubuntuforums.org/showthread.php?t=1467548](http://newyork.ubuntuforums.org/showthread.php?t=1467548)

Essentially, press F6 when the livecd is loading and switch off ACPI.

Its not something I have done myself, but looks like it COULD fix it.

---

### Post by NathanDTaylor on 2010-09-26
> **Sub101 said:**
> Thanks for taking the time.

I would suggest this is your problem;

[http://newyork.ubuntuforums.org/showthread.php?t=1467548](http://newyork.ubuntuforums.org/showthread.php?t=1467548)

Essentially, press F6 when the livecd is loading and switch off ACPI.

Its not something I have done myself, but looks like it COULD fix it.

Thanks, Ill try it

---

### Post by mick222 on 2010-09-26
Had problems on a my sons toshiba trying to run live cd but seemed to work fineif booting from memory card.Download unetbootin and try with a flash drive or sd card.

---

### Post by NathanDTaylor on 2010-09-26
> **Sub101 said:**
> Thanks for taking the time.

I would suggest this is your problem;

[http://newyork.ubuntuforums.org/showthread.php?t=1467548](http://newyork.ubuntuforums.org/showthread.php?t=1467548)

Essentially, press F6 when the livecd is loading and switch off ACPI.

Its not something I have done myself, but looks like it COULD fix it.

This allowed me to install it. Once installed it asked me to restart, which I did. Then it gives me the list of OS's. I hit Ubuntu and it comes up with the same thing as b4.

---

### Post by NathanDTaylor on 2010-09-26
Bumppp

---

### Post by gandaran on 2010-09-26
> **NathanDTaylor said:**
> Do I need a certain BIOS for my computer to run Ubuntu? I have a Toshiba Satellite L505. Someone said if I update my bios, it might work. When I try to update my bios, I get an error says something like "The current BIOS settings could not be found" so I called toshiba and they said that Ubuntu might require a certain BIOS. Can anyone help me? I reaaaallllyyy want Ubuntu.
I have a Toshiba NB100 netbook and I did have to update the bios to run Ubuntu 10.04, before updating the bios only old versions of Ubuntu up to 8.10 worked, all the recent versions just froze the netbook, so you could also try an old Ubuntu version and if it works then surely the problem is the bios.

---

### Post by srs5694 on 2010-09-27
> **NathanDTaylor said:**
> Do I need a certain BIOS for my computer to run Ubuntu? I have a Toshiba Satellite L505. Someone said if I update my bios, it might work. When I try to update my bios, I get an error says something like "The current BIOS settings could not be found" so I called toshiba and they said that Ubuntu might require a certain BIOS. Can anyone help me? I reaaaallllyyy want Ubuntu.

What is your *precise* model number? Toshiba's got about a bazillion of them, and the first four characters only narrow it down to about a million models.

I've got a Toshiba L505-ES5018. I've never installed Ubuntu on it, but I've had no problems with the basic installation of OpenSUSE or Funtoo (a minor Gentoo variant), both in 64-bit form. I also tried an Arch Linux installation. I had problems with that, but they were related to my LVM configuration, so nothing to do with the hardware. The WiFi doesn't work out of the box; I had to download a driver from Realtek.

---

### Post by Sub101 on 2010-09-27
> **NathanDTaylor said:**
> This allowed me to install it. Once installed it asked me to restart, which I did. Then it gives me the list of OS's. I hit Ubuntu and it comes up with the same thing as b4.

I think you will need to turn ACPI off again, as when booting the live cd.

If you read this [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2). And edit the /etc/default/grub file where it says about ACPI off, it will make the change permanent.

---

### Post by NathanDTaylor on 2010-09-27
> **Sub101 said:**
> I think you will need to turn ACPI off again, as when booting the live cd.

If you read this [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2). And edit the /etc/default/grub file where it says about ACPI off, it will make the change permanent.

It appears that you have to be loged into Ubuntu to do this and I cannot log into Ubuntu.

---

### Post by NathanDTaylor on 2010-09-27
Bumppp

---

### Post by Sub101 on 2010-09-27
> **NathanDTaylor said:**
> It appears that you have to be loged into Ubuntu to do this and I cannot log into Ubuntu.

I assume you get past grub loading before the lock up.

If this is the case then when Grub appears press either "e" or "Tab" (It should say at the bottom of the list options for editing parameters) and next to where it says "quiet splash" add "acpi=off".

This is not permanent so you would then, upon booting, need to edit grub as the previous instruction.

Hope that helps.

EDIT: It is "e" you need to press to edit grub option. And the line you need to change ends "quiet splash" so just add "acpi=off"

---

### Post by NathanDTaylor on 2010-09-27
I am on Ubuntu right now but I can't download the StartupManager

---

### Post by Sub101 on 2010-09-27
> **NathanDTaylor said:**
> I am on Ubuntu right now but I can't download the StartupManager

Why do you need that? I mean is it related to the booting problem or a new one?

---

### Post by NathanDTaylor on 2010-09-27
that link u sent me says to dl StartupManager to edit that.. i think. That is what I get out of it. But StartupManager won't download

---

### Post by Sub101 on 2010-09-27
Sorry, but the part I meant was about editing Grub2.

I am assuming you still need to add the ACPI=off option?

If yes then run

```
gksudo gedit /etc/default/grub
```

and change the line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
```

to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off" 
```

---

