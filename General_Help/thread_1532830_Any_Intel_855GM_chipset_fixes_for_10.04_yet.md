---
title: "Any Intel 855GM chipset fixes for 10.04 yet?"
date: 2010-07-17
forum: General Help
---

### Post by not1 on 2010-07-17
Do you guys remember the inability for lucid to boot with some intel graphics cards?
[http://ubuntuforums.org/showthread.php?t=1466337](http://ubuntuforums.org/showthread.php?t=1466337)
[http://ubuntuforums.org/showthread.php?t=1472282](http://ubuntuforums.org/showthread.php?t=1472282)

Anyway I used a workaround to get it working on my Toshiba Portege laptop. However from it stemmed slower graphics, no splash, et cetera. That didn't worry me too much. However, I am now at the stage where I am getting arrays of different issues (that don't necessarily relate) and I would like to just have a *nice* clean install. I have been upgrading since 8.something and I long for freshness. My files are allready off.

Has anyone patched the kernel or anything? I'm purely a newbish end user and have not been following launchpad or anything. I did the workaround the week of the release...

any fixes floating around? If not, I'll go back to 9.10.

Thanks in advance.

---

### Post by prshah on 2010-07-17
> **not1 said:**
> Do you guys remember the inability for lucid to boot with some intel graphics cards?

```
Sat Jul 17 @12:36:43:~$ lspci|grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

Remember? I'm living with the damn thing.

There's no fixes yet. I can only boot with the i915.modeset=1 kernel option, and that kills video playback with any program, including totem and the ever reliable VLC. (in-browser flash playback works fine though).

---

### Post by Rubi1200 on 2010-07-17
There **is** a fix

> -UPDATE- Glasen's PPA appears to fix these issues completely for everyone affected using 855gm chips. If the Potential Solution does not work for you (or you are not using an 855gm chip), please try the temporary workarounds below it.

It worked for me on my test environment but I cannot guarantee that it will work for everyone:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Please read the instructions carefully and let the commands do their thing; it can take quite some time so be patient.

As I said, this worked for me on a clean install of 10.04. 

If you have made any changes such as previously suggested workarounds, you may need to either undo them or go for a clean start following the above.

Remember to always backup first!

---

### Post by not1 on 2010-07-17
Thanks guys

> **Rubi1200 said:**
> There **is** a fix

If you have made any changes such as previously suggested workarounds, you may need to either undo them or go for a clean start following the above.

Remember to always backup first!

Now this confuses me. Is it asking the people with the bug to get Lucid installed and running with a workaround, installing fixed drivers and then removing the workaround - effectively fixing everything?

If that's the case and *I want a clean install* do I have to go and edit my bootline code again?

I'm confused (and an amateur end user)

---

### Post by Rubi1200 on 2010-07-17
> **not1 said:**
> Thanks guys



Now this confuses me. Is it asking the people with the bug to get Lucid installed and running with a workaround, installing fixed drivers and then removing the workaround - effectively fixing everything?

If that's the case and *I want a clean install* do I have to go and edit my bootline code again?

I'm confused (and an amateur end user)

Here is how I did it:

1. Booted the LiveCD using the i915.modeset=1 parameter on the bootline.

2. Installed Lucid not making any other changes.

3. Rebooted as required and edited GRUB when it comes up with the  i915.modeset=1 parameter, not making any other changes.

4. Followed the instructions on the link.
a) 
```
sudo add-apt-repository ppa:glasen/intel-driver 
sudo apt-get update && sudo apt-get upgrade
```b) Reboot

c) ```
sudo add-apt-repository ppa:glasen/855gm-fix
sudo apt-get update && sudo apt-get install dkms 855gm-fix-exp-dkms
```5. Reboot and everything should be normal

If you have all your important stuff saved, this would be my recommendation.

If something is unclear, let me know.

---

### Post by not1 on 2010-07-17
So there's no step 6 where I edit the GRUB bootline back to "quiet splash"?

*edit* sorry i'm pretty terrible at this...

---

### Post by Rubi1200 on 2010-07-17
> **not1 said:**
> So there's no step 6 where I edit the GRUB bootline back to "quiet splash"?

*edit* sorry i'm pretty terrible at this...

No, there is no need to edit the GRUB menu after installation if you followed the above steps.

As I said, this worked for me and I have the same Intel chipset.

Good luck and let us know if this works.

Just to be clear, you only use the i915 parameter to boot the CD and then again at the GRUB prompt _after the first reboot_. Don't edit the GRUB menu anywhere else.

---

### Post by not1 on 2010-07-17
Sorry sorry :/

When I have installed and rebooted for the first time, how do I edit GRUB? Is there a function key I press during the boot sequence?

I haven't started yet I just don't want to screw things up, even though everything is backed up.

---

### Post by Rubi1200 on 2010-07-17
> **not1 said:**
> Sorry sorry :/

When I have installed and rebooted for the first time, how do I edit GRUB? Is there a function key I press during the boot sequence?

I haven't started yet I just don't want to screw things up, even though everything is backed up.

Yes, when the computer boots as it gets to the GRUB prompt press Shift (you may have to do this a few times to get it right e.g. pressing a few times).

You should then see the entry for the Linux image; press e to edit and use the arrow keys to move the cursor to the kernel boot line. It is the one that ends with```
 ro quiet splash
```

Remove quiet splash and add the i915.modeset=1 parameter.

Then Ctrl + x to boot.

---

### Post by not1 on 2010-07-17
\\:D/	\\:D/

Hahaha! You absolute legend. Everything looks good from here. Thanks for your clear and concise instructions, bravo kind sir!

---

### Post by Rubi1200 on 2010-07-17
You are more than welcome!

Keep your system updated and don't forget to drop by even if you don't have a question. I have learned a huge amount just by reading what other people have posted here on the forums.

Enjoy!!!!

:D

---

### Post by polomint77 on 2010-07-30
> **Rubi1200 said:**
> Here is how I did it:

1. Booted the LiveCD using the i915.modeset=1 parameter on the bootline.

2. Installed Lucid not making any other changes.

3. Rebooted as required and edited GRUB when it comes up with the  i915.modeset=1 parameter, not making any other changes.

4. Followed the instructions on the link.
a) 
```
sudo add-apt-repository ppa:glasen/intel-driver 
sudo apt-get update && sudo apt-get upgrade
```b) Reboot

c) ```
sudo add-apt-repository ppa:glasen/855gm-fix
sudo apt-get update && sudo apt-get install dkms 855gm-fix-exp-dkms
```5. Reboot and everything should be normal

If you have all your important stuff saved, this would be my recommendation.

If something is unclear, let me know.


YOU ARE A STAR !!!, :D  I almost went back to using Windows because any video I played caused Ubuntu to crash....  Now I can stay here, yayyyyy....

TY AGAIN. :)

---

### Post by Cyberbyte on 2010-11-07
Great stuff! This solved the same issue on my Dell D400 with a clean install of Ubuntu 10.10!  I just did the steps:

a) 
 	Code:
 	sudo add-apt-repository ppa:glasen/intel-driver 
sudo apt-get update && sudo apt-get upgrade 
b) Reboot

c)  	Code:
 	sudo add-apt-repository ppa:glasen/855gm-fix
sudo apt-get update && sudo apt-get install dkms 855gm-fix-exp-dkms 
5. Reboot and everything should be normal

but got a message regarding 855gm-fix-exp-dkms was now replaced with 855gm-fix-dkms so repeated last step simply using: 

sudo apt-get update && sudo apt-get install dkms 855gm-fix-dkms

Thanks all!!!!:)

---

