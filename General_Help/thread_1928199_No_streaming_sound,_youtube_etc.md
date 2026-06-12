---
title: "No streaming sound, youtube etc"
date: 2012-02-19
forum: General Help
---

### Post by oxf on 2012-02-19
IBM ThinkPad
Pentium 2, 512Mb RAM
Lubuntu 11:10

I've successfully installed Lubuntu 11:10 on this aging laptop.

I'm getting no sound out from youtube or other streaming sources(Firefox and Chromium).
I have checked and Flash plugin installer and Lubuntu Restricted Extras are both installed.

I assume the principles here are much the same as full Ubuntu.

Any ideas? I'll provide further info if needed
Thanks!
Katya

```
radegonde@radegond-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1251A
00:02.1 CardBus bridge: Texas Instruments PCI1251A
00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
radegonde@radegond-laptop:~$ 


```

---

### Post by oxf on 2012-02-19
What maybe related to the above problem is this. I added the ALSA  GUI and that also fails to launch with the error msg "unable to find mixer"

I assume this means I'm missing something critical?

---

### Post by mardybear on 2012-02-20
> **oxf said:**
> What maybe related to the above problem is this. I added the ALSA  GUI and that also fails to launch with the error msg "unable to find mixer"

I assume this means I'm missing something critical?
Howdy...

Just some preliminary things to try. I've had my share of linux sound problems over the years with fresh installs but always managed to get things working.

Seems simple but first ensure your laptop sound is enabled (not muted, sound turned up). Every laptop has different function keys. For sound testing, try playing a music CD or an .mp3 file, rather than a youtube video which may be a Flash problem not a sound issue.

If still no sound then open a terminal (eg. gnome terminal) and run 'alsamixer'. If alsamixer is not installed then install or re-install it via synaptic package manager. I believe the software is called 'alsa-utils'. Check/adjust your volume settings in alsamixer (left/right and up/down arrow keys). Also use the F6 key to check what sound cards/chips Ubuntu recognizes. If it lists more than one sound card, then select the other options and recheck for sound.

Hopefully your sound problem can be fixed with one of these simple solutions. If not repost and someone with more experience should be able to help. As mentioned, i've had sound issues on most of my previous Ubuntu installs but always managed to get it running. Don't let a temporary sound problem deter you from using Ubuntu/Linux.

mardybear

---

### Post by oxf on 2012-02-20
Thanks Mardybear for those sugestions. Yes it appears there is no sound at all, from CD/MP3 etc. 

It seems I have a problem with ALSA Mixer. I re-installed it in Synaptic but when I try to run it in terminal  it returns "no such file or directory" So if anyone can tell me where to go next?

Thanks
Katya

---

### Post by mardybear on 2012-02-20
Hi Katya...

Sorry you still got problems.

I rechecked synaptic, the software you'll need is 'alsa-base' and 'alsa-utils'. Ensure these are both installed and then run 'alsamixer' from terminal.

If still no luck, then open syaptic package manager and right-click/mark both of these packages (alsa-base and alsa-utils) for 'reinstallation', click 'apply' to reinstall the software. Try running 'alsamixer' again from terminal.

Success ?

mardybear

---

### Post by mardybear on 2012-02-20
Hi again...

Sorry i misread...you already tried to reinstall.

You are typing 'alsamixer' (type exactly, no spaces or caps) into terminal. Can't see why it wouldn't work.

Repost if still problems. This is beyond me but someone else can probably help.

Good luck,

mardybear

---

### Post by oxf on 2012-02-21
> **mardybear said:**
> Hi again...

Sorry i misread...you already tried to reinstall.

You are typing 'alsamixer' (type exactly, no spaces or caps) into terminal. Can't see why it wouldn't work.

Repost if still problems. This is beyond me but someone else can probably help.

Good luck,

mardybear

Yes this is a strange one! I have both Alsa-base and -utils installed so can't understand it.
I am trying to get this running on an older laptop for a friend using Lubuntu. I did a comparisom with my laptop which has full blown Ubuntu on it and that works fine, Alsa launches from the command line just fine. I also checked synaptic and compared packages so I am perplexed why it wont run on the older IBM Thinkpad.

Thanks for your ideas anyway

Katya

---

### Post by mardybear on 2012-02-21
Hi Katya.

I'm currently using an older Ubuntu version. My alsa-utils also requires the 'udev' package but i think you should have been prompted for any additional required packages during the reinstallation attempt. Wouldn't hurt to check for udev or any other required packages via synaptic package manager.

Just another thought...open up the Ubuntu control centre and select 'services'.  Ensure 'audio settings management (alsa-utils)' is checked/enabled. If not then enable it, reboot the system and retry alsamixer.

mardybear

---

### Post by claracc on 2012-02-22
Have you tried to install pulseaudio?. You can do it through synaptic.

---

### Post by oxf on 2012-02-22
> **claracc said:**
> Have you tried to install pulseaudio?. You can do it through synaptic.

Is Pulse essential to Alsa? I thought it was different.

But anyways I just did a comparisom between my Laptop with full Ubuntu and the problem one with Lubuntu, specifically the Alsa and udev packages and can't see anything I'm missing. I also just reinstalled Alsa-base and Alsa-Utils in case that was a problem. Still no luck.

I'm seriously beginning to wonder if because this is an older machine it's just not fully Linux compatible?

One final note. The system sounds, i.e volume up/down for beeps etc do work on the PC but I assume this is set on the bios anyway

---

### Post by claracc on 2012-02-23
Certainly pulseaudio is not essential to lubuntu but it can help. In my lubuntu 11.04 pentium III laptop, pulseaudio fixed audio problems.

Also, you can try the tips and solutions given in this link: [http://askubuntu.com/questions/106224/no-sound-after-lubuntu-installation](http://askubuntu.com/questions/106224/no-sound-after-lubuntu-installation)

---

