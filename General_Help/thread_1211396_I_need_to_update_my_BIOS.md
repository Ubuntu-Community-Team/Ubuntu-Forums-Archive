---
title: "I need to update my BIOS"
date: 2009-07-12
forum: General Help
---

### Post by darkknight85 on 2009-07-12
Well I need to update my bios and was wondering if I install wine how do I use it to update my bios.

---

### Post by philinux on 2009-07-12
I guess you searched the web for "linux updating bios".

Throws up a lot of links.

This one looks good.
[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

[http://www.google.co.uk/search?q=linux+updating+bios&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.co.uk/search?q=linux+updating+bios&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by darkknight85 on 2009-07-14
Well those seemed to be helpful. I was wondering if you knew if I could use something like windows xp live boot cd to do it or not.

---

### Post by fballem on 2009-07-14
> **darkknight85 said:**
> Well those seemed to be helpful. I was wondering if you knew if I could use something like windows xp live boot cd to do it or not.

I used a bootable USB key that I made in Windows using the HP USB boot tool and instructions found here: [http://www.vistax64.com/tutorials/191416-dos-usb-boot-drive.html](http://www.vistax64.com/tutorials/191416-dos-usb-boot-drive.html)

My USB key is 4 Gigabytes.

Once I had the bootable USB, I unzipped the bios flash utility into a subdirectory on the USB key. To boot, I had to go into BIOS and change the boot order so that the system would boot off of the USB key first.

A full shut down, then reboot with the USB key, and I was good to go.

When I was done, I shut down, and then changed the boot order back to CD Drive first, HDD second. The new bios worked well. I have set the USB key aside for safe keeping in case I have to do something similar in the future.

Hope this helps,

---

### Post by Lampi on 2009-07-14
It depends on the mainboard manufacturer:

- some offer live update inside bios
- some still offer dos tools with a binary file to flash bios
- some offer windows update tools

darkknight85 ... you gotta be more specific and visit the hp of your mainboard manufacturer first.

---

### Post by darkknight85 on 2009-07-24
Well my main board was made my a subsidiary of Intel. the bios is done by phoenix and they are currently doing a lot of work with MobLin which I understand to be Mobile Linux for smart phones. I contacted phoenix and asked them if they could help me out or direct me to a web page that could. I could probable do a openfirmware BIOS upgrade but I am not confident enough to want to try. Incase I fluck it up and turn my laptop into a paperweight. I am running Ubuntu 9.04 and the only really anoyence is when i tell my system to sleep it restarts. I have tried several differnt suggestions to fix the issue. Always makeing note of what I have done so I can fix it without reinstalling, with no real succses. I guess i can continue to logout then shutdown and wait for the reboot to press my power button.
No biggy....

---

### Post by kdetech on 2009-07-24
New computers can update directly form bios utility by accessing a FAT partition. It's called Asus EZ2 flash on my PC.

---

### Post by Bondy on 2009-07-24
You should NEVER attempt to update your Bios from within any operating system you will kill your motherboard

Phillinux's post has the required instructions how to do it though

---

### Post by dcstar on 2009-07-24
> **Bondy said:**
> You should NEVER attempt to update your Bios from within any operating system you **will** kill your motherboard


You "will" not do anything of the sort.

I have updated the BIOS on many (many) machines from within an OS (with the provided tools) without any problems at all.

There ***may*** be a risk of something going wrong in any BIOS update, but misleading statements do no one any service at all.

---

### Post by dcstar on 2009-07-24
> **darkknight85 said:**
> Well my main board was made my a subsidiary of Intel. the bios is done by phoenix and they are currently doing a lot of work with MobLin which I understand to be Mobile Linux for smart phones. I contacted phoenix and asked them if they could help me out or direct me to a web page that could. I could probable do a openfirmware BIOS upgrade but I am not confident enough to want to try. Incase I fluck it up and turn my laptop into a paperweight. I am running Ubuntu 9.04 and the only really anoyence is when i tell my system to sleep it restarts. I have tried several differnt suggestions to fix the issue. Always makeing note of what I have done so I can fix it without reinstalling, with no real succses. I guess i can continue to logout then shutdown and wait for the reboot to press my power button.
No biggy....

The **flashrom** package might be able to be used if you can get an actual image of the BIOS, install it and see if it can read your existing BIOS.

---

### Post by Bondy on 2009-07-24
> **dcstar said:**
> You "will" not do anything of the sort.

I have updated the BIOS on many (many) machines from within an OS (with the provided tools) without any problems at all.

There ***may*** be a risk of something going wrong in any BIOS update, but misleading statements do no one any service at all.

Well your certainly increasing your chances of it going wrong surely?

I have always been told to never do it from the OS personally and have never done so

---

### Post by Cheesemill on 2009-07-24
> **Bondy said:**
> Well your certainly increasing your chances of it going wrong surely?

I have always been told to never do it from the OS personally and have never done so

It depends on the motherboard manufacturer. Some of them provide a Windows program for flashing BIOS, I use the HP program on all of our machines at work and have never had any issues. You may run into problems if you try using an app that's been designed to run from a DOS boot disc in Windows though.

Basically just follow the instructions on the manufacturers website and you should be fine, just don't try running any of the Windows apps through Wine, you could very well brick your motherboard.

If you can only get hold of a Windows app then you should use a Windows Live CD such as BartPE to perform the update.

---

### Post by darkknight85 on 2009-07-28
Well my computer is a Gateway M305CRV its MFD is 07/07/06 not very old as I had originally suspected. When I tried Gateway and said I was using Linux they ended the conversation. I have also heard that both Intel and Phoenix are starting to develop more things in Linux. I have contacted both in  hopes of getting some kinda help. 
Additionally:
Will you please read my thread about my PSP question and see if you could answer it 
Thank you all.

---

### Post by wandalalakers on 2010-02-21
Darkknight,
I know this is an old thread but I just updated a Gateway M305CRV bios to 38.01.07 by Pheonix.  I had to reinstall windows in order to do this because you have to run a program called winplash or something like that from windows.  This newest bios fixed my Kubuntu 8.04 shutdown problem.

---

