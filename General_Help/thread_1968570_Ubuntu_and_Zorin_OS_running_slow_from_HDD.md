---
title: "Ubuntu and Zorin OS running slow from HDD"
date: 2012-04-29
forum: General Help
---

### Post by H4wkBlaster on 2012-04-29
Hi , I had installed Ubuntu 11.10 on my HDD successfully but it started freezing , I tried opening up mozilla but nothing happened , same with other applications and then the whole system crashed. I then tried to install Zorin OS , succesfull installation again but same freezing instead that this time some applications would actually open up but freeze very fast.

It's weird because both Ubuntu and Zorin OS run just fine from my USB , I am typing from Zorin OS live cd just now .
Also if I load Zorin OS in failsafex it freezes less and there is a pop up menu that always appear "Your graphic device was not recognized , you will have to configure this yourself" something like that , but that message only appears when I load Zorin OS failsafex mode.

Computer specs 
Intel 82495g
Intel e1200 Dual core 1.6Ghz
250 GB HDD
3Gb Ram 
Zorin OS 5.2


Before Ubuntu I had Vista installed and that was freezing aswel , I thought it was freezing just because it was Vista.
I don't know if it's the lack of drivers that made the system freeze , any help would be appreciated.

Thanks in advance.

---

### Post by H4wkBlaster on 2012-04-30
Bump..

---

### Post by H4wkBlaster on 2012-05-01
Anyone?

---

### Post by H4wkBlaster on 2012-05-02
> **H4wkBlaster said:**
> Bump..

](*,)](*,)](*,)

---

### Post by ezsit on 2012-05-02
Three different OS installs and freezing occurring in all three? Sounds like hardware to me. I'd suspect the hard drive first, and go from there.

---

### Post by H4wkBlaster on 2012-05-02
> **ezsit said:**
> Three different OS installs and freezing occurring in all three? Sounds like hardware to me. I'd suspect the hard drive first, and go from there.

Yes but what do I do? I tried checking HDD with Gparted and got "An error occurred while applying the operations" 

e2fsck attempt to read block from filesystem resulted in a short read while trying to open /dev/sda1

From USB the systems run fine though..

---

### Post by jerome1232 on 2012-05-02
First thing I would do is pop open the case, reseat all cables on the HDD, reseat the sata/pata connection to the Mobo.

If that didn't fix it, I would try other sata ports (if it's sata).

If that didn't fix it, I would check the smart status of the drive to see if it has excessive errors. (SMART status can be found in "disk utility" under Ubuntu)

---

### Post by H4wkBlaster on 2012-05-02
> **jerome1232 said:**
> First thing I would do is pop open the case, reseat all cables on the HDD, reseat the sata/pata connection to the Mobo.

If that didn't fix it, I would try other sata ports (if it's sata).

If that didn't fix it, I would check the smart status of the drive to see if it has excessive errors. (SMART status can be found in "disk utility" under Ubuntu)

It shows up as Smart status Not supported 

NOTE I am using a different keyboard configuration so I am sorry that I can't use most of the correct pounctuation.

Will try to reseat cables as soon as I read some more suggestions

---

### Post by holycow131415 on 2012-05-02
Check your bios to see if there is a hard drive test. Run a memory test too. Sounds to me to be a hdd beginning to fail. Disconnect your hdd and if you run the livecd, does ubuntu freeze then? If not, then its a hdd problem.

---

### Post by jerome1232 on 2012-05-02
> **holycow131415 said:**
> Check your bios to see if there is a hard drive test. Run a memory test too. Sounds to me to be a hdd beginning to fail. Disconnect your hdd and if you run the livecd, does ubuntu freeze then? If not, then its a hdd problem.

Please read the thread. The op has already stated that it runs fine from a usb device.

Although the HDD is likely beginning to fail, it's possible the motherboard (HDD ports) is failing, the cables for the HDD are failing, or the power supply is failing. Any one of those could lead to the symptoms described.

---

### Post by |{urse on 2012-05-02
Go nab an iso off your favorite torrent site for Hiren's boot disk, burn iso to cd and boot to it, run hdd-regenerator (from the 'hard disk tools' section in the main menu).

Takes a while but this is the **very best** tool for that job imho.

---

### Post by holycow131415 on 2012-05-02
> **jerome1232 said:**
> Please read the thread. The op has already stated that it runs fine from a usb device.

Although the HDD is likely beginning to fail, it's possible the motherboard (HDD ports) is failing, the cables for the HDD are failing, or the power supply is failing. Any one of those could lead to the symptoms described.

Thanks for telling me to read the thread. However, I obiviously did in order to list the suggestions for the OP to deduce that the hdd may be the cause. Even though he said what he said, OP may not have known otherwise. Thanks for feeling like you need to be the internet police.

---

### Post by H4wkBlaster on 2012-05-03
> **jerome1232 said:**
> First thing I would do is pop open the case, reseat all cables on the HDD, reseat the sata/pata connection to the Mobo.

If that didn't fix it, I would try other sata ports (if it's sata).

If that didn't fix it, I would check the smart status of the drive to see if it has excessive errors. (SMART status can be found in "disk utility" under Ubuntu)


Changed all possible SATA cables still the same problem , I am guessing the HDD isn't broken because as in Vista and Linux they both run fine from Safety mode and failsafex low graphic mode , so I am betting in either drivers needing update or HDD bad sectors , what do you think?

---

### Post by H4wkBlaster on 2012-05-03
> **|{urse said:**
> Go nab an iso off your favorite torrent site for Hiren's boot disk, burn iso to cd and boot to it, run hdd-regenerator (from the 'hard disk tools' section in the main menu).

Takes a while but this is the **very best** tool for that job imho.

Will do that thanks.

---

### Post by H4wkBlaster on 2012-05-04
Ran HDD tests from Hiren's boot HDAT2 , samsung HDD utility , and both pointed out no errors , 
samsung HDD utility said that if my computer was failing the most probable cause would be my mother board ports ( already mentioned here ) or the cables , I don't think it's neither though... I changed my CD sata cable with my HDD sata cable and it runs fine 
, changed HDD sata port into another port and still freezing problem , I don't think it's my psu because Ubuntu and Zorin OS Both run fine from usb and in failsafex mode from HDD as well... 

So how can I manually check for drivers? What are all the drivers that I need? 

Already mentioned pc specs in first post but will include here again :
 intel 82945g
 e1200 1.6 Ghz , CPU
 Zorin OS 5.2 Core ,
 Ata Samsung 250GB hj 
Motherboard : 945GCT-M2

And also if there really is no other solution is there anyway I can start low graphic mode as default? I rather have a non freezing computer than fancy graphics .

Thanks again

---

### Post by jerome1232 on 2012-05-04
The only reason I mentioned psu, is they gradually produce less and less power, sometimes when they are producing *just enough* power to get things going, weird things start happening, usually with high power demand components like HDD's, graphics cards, and the cpu.

I suppose it *could* be your graphics card? Perhaps when you run from the HDD your psu just can't supply the graphics card with enough juice and you freeze?

As far as drivers most of them are built into the kernel. lshw shows what drivers your devices are using. You didn't mention what your graphics card is. I just have a  hard time making the leap to a driver problem due the fact your were having issue across three OS's. Leads me to suspect hardware immediately.

To get the full list
```
sudo lshw
```

For specific components you use the -C tag and the class of component.

```
sudo lshw -C video
sudo lshw -C network

```

---

### Post by H4wkBlaster on 2012-05-05
> **jerome1232 said:**
> The only reason I mentioned psu, is they gradually produce less and less power, sometimes when they are producing *just enough* power to get things going, weird things start happening, usually with high power demand components like HDD's, graphics cards, and the cpu.

I suppose it *could* be your graphics card? Perhaps when you run from the HDD your psu just can't supply the graphics card with enough juice and you freeze?

As far as drivers most of them are built into the kernel. lshw shows what drivers your devices are using. You didn't mention what your graphics card is. I just have a  hard time making the leap to a driver problem due the fact your were having issue across three OS's. Leads me to suspect hardware immediately.

To get the full list
```
sudo lshw
```

For specific components you use the -C tag and the class of component.

```
sudo lshw -C video
sudo lshw -C network

```

Sorry wrote my gpu name wrong it's intel express chipset 82945g, sorry about that ,it's an onboard gpu.

---

### Post by H4wkBlaster on 2012-05-10
Bump

---

### Post by H4wkBlaster on 2012-05-11
Bump..

---

### Post by H4wkBlaster on 2012-05-12
It's almost for sure the intel gpu , did a test , installed Starcraft and ran it on normal mode it was fullscreen and smooth but freezing 1 in 1 minute until the whole system crashed , then booted in failsafex mode , ran starcraft it occupied 25% of the screen the rest was black and it was super laggy but didn't freeze at all.

---

### Post by jerome1232 on 2012-05-12
Could be overheating too, this is a laptop? You still have a warranty on it?

---

### Post by H4wkBlaster on 2012-05-12
> **jerome1232 said:**
> Could be overheating too, this is a laptop? You still have a warranty on it?

It's a desktop with an onboard gpu.

---

### Post by jerome1232 on 2012-05-12
Have you monitored the temps while trying to recreate a freeze? Is the desktop still under warranty?

---

### Post by H4wkBlaster on 2012-05-12
> **jerome1232 said:**
> Have you monitored the temps while trying to recreate a freeze? Is the desktop still under warranty?

Both no , what utility can I use to monitor temps?

Thanks for helping btw

---

### Post by bobnutfield on 2012-05-12
I cannot be sure about your GPU, but I can tell you that the Intel 82845G, which was called the Brookdale chip, has not run well on any linux kernel since 2.6.35 without adding a modeset line to the boot options.  This is a very old graphics chip but was used in many, many onboard desktops and laptops.  Intel no longer supports this chip with any linux driver and there are many threads on various forums about it.  It is not possible to use desktop effects even when you do get it working with modesetting.

Something to consider, though you listed yours as the 82945G, so it might be a different chip.  I would be surprised if your much newer equipment used this chip.  In any event, you check what module is driving your graphics with lsmod.  I am betting that it is the i915 module.

---

### Post by H4wkBlaster on 2012-05-12
> **bobnutfield said:**
> I cannot be sure about your GPU, but I can tell you that the Intel 82845G, which was called the Brookdale chip, has not run well on any linux kernel since 2.6.35 without adding a modeset line to the boot options.  This is a very old graphics chip but was used in many, many onboard desktops and laptops.  Intel no longer supports this chip with any linux driver and there are many threads on various forums about it.  It is not possible to use desktop effects even when you do get it working with modesetting.

Something to consider, though you listed yours as the 82945G, so it might be a different chip.  I would be surprised if your much newer equipment used this chip.  In any event, you check what module is driving your graphics with lsmod.  I am betting that it is the i915 module.

It is i915 , is there any turnaround for this? The weird thing is that, from live usb all the fancy effects run fine, also runs fine in failsafex mode from HDD and just now played 2 full hours of Starcraft 1 in generic mode BUT from a previous Linux version and the game ran fine with merely 2 freezes in the whole 2 hours , but when I go to test the computer , bam whole computer freezes and I am forced to restart in failsafex mode.


It's  probably what you said, a problem with the intel chip causing instability.

Sorry for the late reply and thanks for helping.

So is there any solution?

---

### Post by jerome1232 on 2012-05-13
Firstly lets see if your using the driver mentioned

Post the output of the commmand below wrapped in code tags. Go to advanced mode, highlight all output, click the # symbol on toolbar.
```
sudo lshw -C Video
```

---

### Post by H4wkBlaster on 2012-05-13
> **jerome1232 said:**
> Firstly lets see if your using the driver mentioned

Post the output of the commmand below wrapped in code tags. Go to advanced mode, highlight all output, click the # symbol on toolbar.
```
sudo lshw -C Video
```

 description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:fea80000-feafffff ioport:dc00(size=8) memory:d0000000-dfffffff memory:fea40000-fea7ffff

Sorry for not replying earlier , we live in different time zones.

---

### Post by bobnutfield on 2012-05-14
When you get the grub boot screen, hit "e" to enter the edit mode.  On the kernel line, right after "ro". Type the following:

> i915.modeset=0

This turns off kernel mode setting which seems to be the problem with the Intel chipset.  I don't completely understand kernel modeset ting, but it does give me a usable desktop on an old laptop using the 82845G chipset.  I don't know if graphics intensive stuff will be available using this, but you should get a stable desktop.  If this works well enough for you, you can make the append to the kernel line permenant by adding this line to the /etc/default/grub "quiet splash" line (put it just before that) and run sudo update-grub, then reboot.

Hope that helps

---

### Post by H4wkBlaster on 2012-05-18
> **bobnutfield said:**
> When you get the grub boot screen, hit "e" to enter the edit mode.  On the kernel line, right after "ro". Type the following:



This turns off kernel mode setting which seems to be the problem with the Intel chipset.  I don't completely understand kernel modeset ting, but it does give me a usable desktop on an old laptop using the 82845G chipset.  I don't know if graphics intensive stuff will be available using this, but you should get a stable desktop.  If this works well enough for you, you can make the append to the kernel line permenant by adding this line to the /etc/default/grub "quiet splash" line (put it just before that) and run sudo update-grub, then reboot.

Hope that helps

OMG , I am writing this on generic mode with NO CRASHES OR FREEZES dude thank you soooooooooo much , but how do I make this permanent? I don't see the line you are talking about , I ran sudo gedit /etc/default/grub , where do I put the "quiet splash" line?? 

There's already a similar line
 "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Thanks again :KS

---

### Post by bobnutfield on 2012-05-19
> **H4wkBlaster said:**
> OMG , I am writing this on generic mode with NO CRASHES OR FREEZES dude thank you soooooooooo much , but how do I make this permanent? I don't see the line you are talking about , I ran sudo gedit /etc/default/grub , where do I put the "quiet splash" line?? 

There's already a similar line
 "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Thanks again :KS

Put the line just before "quiet splash" in this line that you have identified.

GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=0 quiet splash"

Save the changes.

Then run 

Sudo update-grub.  That will do it.

---

### Post by H4wkBlaster on 2012-07-02
Sorry for the very late reply , wasn't around , anyways thank you so much for your help and for fixing this problem for me , you have no idea how much I needed this fixed ,
and thanks to everyone that helped , you guys rock :guitar::KS:KS:KS:KS:KS

---

