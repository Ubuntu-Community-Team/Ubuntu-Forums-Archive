---
title: "Help!!! 12.04 install going directly to blank screen"
date: 2012-05-03
forum: General Help
---

### Post by airspoon on 2012-05-03
Hello, 
 So I'm trying to install Ubuntu 12.04 onto a brand new SSD and just after I get to the little text menu that asks whether you want to run Ubuntu from the USB stick or install it, the screen goes blank after picking any of the options.
 
I'm assuming (though I have no idea) based on quick research through threads, that I need to use NOMODESET, however I have no idea how to do that. I literally don't have ay options to do anything other than choosing one of four menu items at the text screen before everything goes blank.
 
For whatever it's worth, I'm using an Nvidia GTX 560 ti. Thanks.
 
Any and all help would be greatly appreciated.

---

### Post by airspoon on 2012-05-03
Is there anyway that I can download an earlier release, like 11.10 and try that? I can't find a download for any other release besides 12.04.

---

### Post by airspoon on 2012-05-03
Okay, I found an old(er) version of 11.10 and tried installing. I got the same problem where the screen just goes blank after I choose to either 'install onto Hard drive' or 'run from USB stick'. This is weird because I had it installed on this computer before I decided to try Win 8 Consumer Preview, and I didn't run into this problem at all.

Does anyone have any suggestions? Thanks.

---

### Post by plucky on 2012-05-03
> **airspoon said:**
> Is there anyway that I can download an earlier release, like 11.10 and try that? I can't find a download for any other release besides 12.04.

[Releases Ubuntu.Com](http://releases.ubuntu.com/) for all the current releases.


> I'm assuming (though I have no idea) based on quick research through threads, that I need to use NOMODESET, however I have no idea how to do that. I literally don't have ay options to do anything other than choosing one of four menu items at the text screen before everything goes blank.


On the Live CD/USB I think if you tap on the F6 key you should be able to select "nomodeset".

Good Luck

---

### Post by airspoon on 2012-05-03
Thanks for the reply. The same thing happens when I try to install 11.10 as well. I tried 'F6' but nothing really happens. I'm able to get to the grub screen however, as soon as I click on an option, the screen goes blank (like that same second) so I don't know if I'm not pressing F6 fast enough, or if it just isn't the reason. 

I guess I'm not understanding this, considering that I had Ubuntu installed only a couple of weeks ago on this same, brand new computer. Now all of the sudden, installs aren't working. The only difference this time however, is that I have an Nvidia graphics card installed, when I was using the on-die graphics from intel before. 

Realizing this, I tried to plug my monitor's cable back into the built-in DVI connection on the Mobo to see if I could get the install going that way. However, when I do this, it just boots straight into windows (within like 2 seconds) and doesn't even give me the BIOS (UEFI) startup screen which would allow me to boot from my USB stick.

I would suspect my computer, however windows seems to be working perfectly fine, which is weird considering that I have always been pained by Windows while Ubuntu has worked, not the other way around.

Any suggestions on what I should do? Would completely wiping off windows help? Could this be an issue with Windows (I don't see how, but I'm becoming desperate). 

Again, thanks.

---

### Post by 2ta8gdfte on 2012-05-03
Here is the nomodeset link that is good to have saved.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by airspoon on 2012-05-03
Thanks for the link, it looks really helpful and seems to detail my problem, however I don't have the same options available in grub on install USB stick. For instance, there is no 'F6' option (or anything else. It does however tell me to press 'c' in order to get to a command prompt to 'change the commands'. I'm not sure if that would even work but I could try it if there is a specific command. Is there a specific command? Thanks.

---

### Post by airspoon on 2012-05-03
Okay, I have so far learned that my only two options (that do anything besides giving me a blank screen) once inside grub are to press 'e' (I believe this allows me to set boot options through a command line type interface) and to press 'c', which brings me to a command prompt. Is there anything that I can do with either of these two options in order to set 'nomodeset' or install Ubuntu? The above link detailing nomodeset, only tells me how to do it through options that I don't have, such as pressing 'F6'. So, is there a command that I can give or code that I can put into the boot options?
 
I don't think that I have ever hard-booted a computer so many times in my life. Does Ubuntu no longer work on Nvidia now? I specifically bought an Nvidia card (at a higher price/performance ratio) because I have heard that ATI doesn't play well with Ubuntu (at least Gnome Shell). 
 
I'm now utterly confused.
 
There has to be another way to disable the video drivers in the kernel besides pressing a non-existent 'f6' option in grub, right?

---

### Post by 2ta8gdfte on 2012-05-03
Carefully read the link, it can be confusing for sure. It is hit e for edit at the grub menu then use the arrow key to move the cursor to almost the end of the kernel where you might see splash or no splash insert nomodeset there with a space before and after then boot in.

---

### Post by airspoon on 2012-05-03
Cool, it actually worked! I was skipping over that part because it said for already installed OS, as opposed to the Live CD. However, it worked. I was able to install 11.10 and then I immediately upgraded to 12.04 from the popup in 11.10. I thought that I have read before that upgrading Ubuntu without a clean install isn't that wise as its often prone to problems. However, I figured that since 11.10 was a clean install, it might be okay. I'll be crossing my fingers.

Anyway, when I changed the boot options, did that change them permanently? Should I change it again now that I have the Nvidia drivers installed, or is there no need since I have the nvidia drivers installed?

Again, thanks! I was pulling my hair with frustration all day trying to tackle this issue.

---

### Post by 2ta8gdfte on 2012-05-03
> **airspoon said:**
> Cool, it actually worked! I was skipping over that part because it said for already installed OS, as opposed to the Live CD. However, it worked. I was able to install 11.10 and then I immediately upgraded to 12.04 from the popup in 11.10. I thought that I have read before that upgrading Ubuntu without a clean install isn't that wise as its often prone to problems. However, I figured that since 11.10 was a clean install, it might be okay. I'll be crossing my fingers.

Anyway, when I changed the boot options, did that change them permanently? Should I change it again now that I have the Nvidia drivers installed, or is there no need since I have the nvidia drivers installed?

Again, thanks! I was pulling my hair with frustration all day trying to tackle this issue.

 That is a temporary command you would have to insert it in the grub setup to make it always run. Glad your up and running. :)

---

### Post by twipley on 2012-05-03
Indeed. And to recapitulate, tap F6 on Live-CD boot to avoid black screen with blinking underscore cursor, select NOMODESET from there, and go on with the install. If ever, once after having installed, you encounter a frozen purple screen upon booting, reboot tapping shift to access GRUB, and then from there select the "recovery" option, which has the NOMODESET boot option set as a default. Such commands are only temporary, of course, and at our great pleasure.

Next time, do as I will be doing next time and favor open-source-driver devices. More open source for the better... ;)

---

### Post by airspoon on 2012-05-04
> **twipley said:**
> Indeed. And to recapitulate, tap F6 on Live-CD boot to avoid black screen with blinking underscore cursor, select NOMODESET from there, and go on with the install. If ever, once after having installed, you encounter a frozen purple screen upon booting, reboot tapping shift to access GRUB, and then from there select the "recovery" option, which has the NOMODESET boot option set as a default. Such commands are only temporary, of course, and at our great pleasure.

Next time, do as I will be doing next time and favor open-source-driver devices. More open source for the better... ;)

Thanks twipley, however 'F6' wasn't an option for me, as I suspect it won't be for others as well. Instead, you have to change the boot command by pressing 'e' @ grub and then typing 'nomodeset' at the end of the line that has the 'splash ****' (might be 'splash quiet', as it was for mine). Then, you can press 'F10' to continue with the nomodeset boot option. After installing the proprietary Nvidia drivers, -should no longer be an issue.

As far as open-source driver devices, that sounds like a great idea. However, I didn't have much of an option due to needing a med-high end graphics card and didn;t have the money for a quadro. I did however shell out a little more price/performance wise for nvidia due to ATI (AMD now?) driver difficulties with Linux. However, I'll keep that in mind for the next time I add anything to my machine.

---

