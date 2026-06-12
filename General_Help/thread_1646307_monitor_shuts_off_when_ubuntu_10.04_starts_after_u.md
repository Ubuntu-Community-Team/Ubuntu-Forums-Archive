---
title: "monitor shuts off when ubuntu 10.04 starts after upgrade"
date: 2010-12-15
forum: General Help
---

### Post by revto on 2010-12-15
I know that this is a know issue with nvidia cards and that is (of course) what I have. I have tried many of the fixes that I found on these forums. Some of them seemed to work but the problem has still remained (maybe its because i'm still too new)

I have been tempted to go back to windows but I cannot let this problem drive me away from ubuntu so any help is greatly appreciated.

Thomas

---

### Post by revto on 2010-12-16
I know the first post was very vague but I was in a hurry yesterday but need this problem resolved because I have been trying to deal with it since July and needed to pressure myself to ask for help.

in a nut shell, I have had 8.04 for a few years with no windows partition and upgraded from 8.04 to 10.04 and everything went smooth with no error messages until I rebooted. thats when the screen went black and the monitor shut off. I did some searching and found that it is likely the cause of my Nvidia onboard video drivers. Most of the posts were pointing to the correct drivers being in the 8.04 partition and for some reason 10.04 doesn't use them. After trying with no success, sometimes half of the "fix" worked and sometimes I didn't even know where to start. 

After many frustrating nights of trying and reading up as much as I can on Linux and Ubuntu, I got the bright idea that 10.04 should be fine after I wipe the drive and repartition my drive with only a 10.04 partition. That didn't work either as I couldn't even install it because the same black screen would appear then turn off the monitor.

I found some posts about this problem and found it is a common problem and all I needed to do was on the setup screen press f6 and select "nomodeset" and then correct the "quiet splash" line in the kernal. finally figured out how to do this and all was great until I tried to end the line command by hitting tab or one post said ctrl-x to reboot, which for my comp did nothing and when I hit tab I got an error 11. 

Since then I tried wiping out the hard drive again and this time installing 8.04, not installing and drivers and then upgrading, this gave me the same result of the black screen. 
Then I tried to wipe it clean and install 8.04, update the drivers except any Nvidia drivers and then upgrade, with the same result of a black screen.

As you can see I am much better at wiping a drive clean and doing a fresh install than I am at fixing a problem but that was always the best thing for windows that I found, which is why I like ubuntu there are a lot of people that can fix it and I want to be more hands on with my computer which I thank you ahead of time for reading this and for any help you can give. below are some of the posts and links I found that I was talking about.

thanks again,
Thomas
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)
[http://ubuntuforums.org/showthread.php?t=1604104&page=4](http://ubuntuforums.org/showthread.php?t=1604104&page=4)

---

### Post by gordintoronto on 2010-12-16
It might help if you said what nVidia card you have. Also, have you tried 10.10?

You said nomodeset worked, or did you? I can't figure out what you said.

---

### Post by revto on 2010-12-16
Nvidia GeForce 6150 LE is what it says on my computer and it is onboard video. When I try "lspci | grep VGA" i get the error "/bin/sh: lspci : not found" but I think this is because I am in a BusyBox shell. I am told I need a live cd to correct this. I have a 8.04 and a copy of 10.04 and 10.10 but do not know if this is what I need to use or how to use them. sorry still new. I have also been getting answers to this thread at another thread [http://ubuntuforums.org/showthread.php?t=1646786](http://ubuntuforums.org/showthread.php?t=1646786)
If that makes it any easier to connect the dots.
Thanks for the help
Thomas

---

### Post by revto on 2010-12-16
Sorry, nomodeset worked for me when I was trying a fresh install of 10.04 and I selected it by pressing f6 at the install window and I guess it installed it but I was in a command prompt. There I didn't know what to do but after a reset it took me to black screen after grub started. After that I installed 8.04 again and then upgraded again and that is where I have been stuck.

---

### Post by Crusty Old Fart on 2010-12-16
> **revto said:**
> Sorry, nomodeset worked for me when I was trying a fresh install of 10.04 and I selected it by pressing f6 at the install window and I guess it installed it but I was in a command prompt. There I didn't know what to do but after a reset it took me to black screen after grub started. After that I installed 8.04 again and then upgraded again and that is where I have been stuck.

Thomas:

I had been having similar problems for MONTHS...like about six months! I finally got things working. So, I have some experience with what you're going through. In fact, my system still fails to boot at times followed by my monitors going to sleep and everything being locked up so tight that I have to perform a hard reboot followed by some magic tricks in grub to kick life into it.

Fixing this problem may require a fair amount of learning on your part. If you're up for it, then the first thing we need to do is determine whether or not you can boot from a Live CD and run Ubuntu in tryout mode.

Can you do that?

---

### Post by revto on 2010-12-16
I can try the live cd approach but I lack the info to do so. If you can explain it to me I can do it.

---

### Post by Crusty Old Fart on 2010-12-16
> **revto said:**
> I can try the live cd approach but I lack the info to do so. If you can explain it to me I can do it.

Sure...no problem...it's really easy.

There are two types of CD's used to install Ubuntu. One is usually called a Live CD, and the other is called an Alternate CD.

Both will boot your system. However, the easiest way to know which CD you have is that the Alternate CD does not provide a graphical interface. It's text only. Whereas the Live CD uses a graphical interface for installation. So, which one do you have for version 10.04?

---

### Post by revto on 2010-12-16
I just have the cd that I downloaded from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) . I also have an original version of 8.04 if that helps.

---

### Post by Crusty Old Fart on 2010-12-16
> **revto said:**
> I just have the cd that I downloaded from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) . I also have an original version of 8.04 if that helps.

Okay...but that download is for the Live CD for version 10.10

Still, we can use it for a test. When you boot from it, do you get a picture for version 10.10 that looks similar to this one for version 10.04?

[IMG]https://help.ubuntu.com/community/LiveCDBootOptions?action=AttachFile&do=get&target=Boot-Welcome.png[/IMG]

---

### Post by revto on 2010-12-16
The same link can download 10.04 and 10.10 of which I have both. But both of them produce the same results, whether you choose "try Ubuntu 10.04" or "try Ubuntu 10.10", it goes to a black screen with a blinking cursor in the top left. except my screen looks different from yours. mine has a big language menu over the main menu that makes you choose first before any other option. I would send you a screen shot but I am on another computer because I cannot get my main machine to do anything and I cannot figure out how to interface the two using linux language.

---

### Post by revto on 2010-12-16
Also mine had no window, just a menu screen after the language select menu with the 10.04 purple background. Then it goes black then the monitor turns off. hope this info helps some

---

### Post by Crusty Old Fart on 2010-12-16
Okay...after you select a language do you see something like this?

[img]https://help.ubuntu.com/community/LiveCDBootOptions?action=AttachFile&do=get&target=Boot-Options.png[/img]

---

### Post by revto on 2010-12-16
Yes, exactly. the language menu is over it and I select english and that is what I see.

---

### Post by revto on 2010-12-16
I just tried booting to the 10.10 disk and hitting f6 and selecting "nomodeset". and it booted to a ubuntu 10.10 loading screen with the 4 flashing dots. it brings me to a command prompt that has ubuntu@ubuntu:~$. not sure what this means

---

### Post by Crusty Old Fart on 2010-12-16
Okay...good.

Have you ever tried the option at the top: "Try Ubuntu without installing"

---

### Post by revto on 2010-12-16
That is how I got to the command prompt that said ubuntu@ubuntu:~$. But I don't know where to go from there. The install command gives me the black screen

---

### Post by Crusty Old Fart on 2010-12-16
> **revto said:**
> I just tried booting to the 10.10 disk and hitting f6 and selecting "nomodeset". and it booted to a ubuntu 10.10 loading screen with the 4 flashing dots. it brings me to a command prompt that has ubuntu@ubuntu:~$. not sure what this means

That means you have successfully booted the operating system running from the CD. This is what we mean when we say: run from the Live CD.

You are probably in a tty1 virtual shell. What do you get for output if you issue this command:
```

lspci | grep VGA

```

---

### Post by revto on 2010-12-16
Thank you so much for helping!

I got 
00:05.0 VGA compatible controller: nVidia Corporation  c51 [GeForce 6150 LE] (rev a2)

---

### Post by Crusty Old Fart on 2010-12-16
At this point, I'd like you to try an experiment:

[LIST]
[*]Reboot from the Live CD.
[*]Select English when you get to the language menu.
[*]When you get to the next menu that has "Try Ubuntu without installing" highlighted at the top, just press your enter key and let me know what happens. (Don't change any kernel boot options with the F6 key, or anything with any of the other F# keys -- I need to find out if you can boot all the way to the gnome desktop with the Live CD without doing anything special.)
[/LIST]

---

### Post by revto on 2010-12-16
It goes to a black screen with the cursor blinking at the top left then the monitor shuts off

---

### Post by Crusty Old Fart on 2010-12-16
> **revto said:**
> It goes to a black screen with the cursor blinking at the top left then the monitor shuts off

Okay. That means that the default Nvidia driver (probably the nouveau driver) doesn't work with your graphics card. So, in order for you to boot the OS, you need to disable Kernel Mode Setting (KMS) by using the nomodeset boot option as you have been doing.

Please answer the following two questions:

Is it okay with you if from this point forward, we don't use version 10.10. I can help you through this a little better if we use version 10.04.

Also, is the current installation on your hard drive a fresh 10.04 installation, or is it an "upgraded" version of 8.04?

---

### Post by revto on 2010-12-16
Version 10.04 is the version that I would like to run so, yes. 
And the version I am running is an upgrade from 8.04 but I can do a fresh install of 10.04 if if would be easier.

---

### Post by Crusty Old Fart on 2010-12-17
> **revto said:**
> Version 10.04 is the version that I would like to run so, yes. 
And the version I am running is an upgrade from 8.04 but I can do a fresh install of 10.04 if if would be easier.

Yes...Upgrades are very often problematic. Please do a fresh install of 10.04. Understand that it still won't boot all the way to gnome until we get a good driver installed. We'll do that from a tty virtual shell.

---

### Post by revto on 2010-12-17
I have a 10.04 disk but when I try to install I have to use the f6 "nomodeset" trick and it brings me to a ubuntu@ubuntu:~$ prompt

Am I doing it wrong or do I need to do a different trick

---

### Post by Crusty Old Fart on 2010-12-17
> **revto said:**
> I have a 10.04 disk but when I try to install I have to use the f6 "nomodeset" trick and it brings me to a ubuntu@ubuntu:~$ prompt

Am I doing it wrong or do I need to do a different trick

We need a different trick. We may not be able to install with a Live CD. Have you ever done an install using an Alternate CD?

---

### Post by revto on 2010-12-17
What is an alternative cd? Where do I get it and what is the basis behind this kind of disk? I love learning and I appreciate you helping me. Thanks

---

### Post by Crusty Old Fart on 2010-12-17
> **revto said:**
> What is an alternative cd? Where do I get it and what is the basis behind this kind of disk? I love learning and I appreciate you helping me. Thanks

First...and most importantly...You're mighty welcome. Thank you for the thanks.

Secondly...it's called an Alternate (not Alternative) CD. 

The Alternate CD is used for computers unable to run the graphical desktop based  installation, either because the computer does not meet the minimum  requirements for the live cd or because the computer requires  configuration after the installation is complete in order to use the  desktop.

You can download the ISO for the 10.04 LTS Alternate CD from the following link:
[http://mirror.hmc.edu/ubuntu-releases//lucid/ubuntu-10.04.1-alternate-i386.iso](http://mirror.hmc.edu/ubuntu-releases//lucid/ubuntu-10.04.1-alternate-i386.iso)

The MD5 SUM for it is:
1c77abb717e7c1ad28611fd81510c758

---

### Post by revto on 2010-12-17
Thats funny! I kept telling myself "alternate" and somehow I managed to put in the "iv". 
Once I have it in disc form is it like a normal install from disc or is there some steps that I need to pay attention to or steps to avoid?

---

### Post by Crusty Old Fart on 2010-12-17
> **revto said:**
> Thats funny! I kept telling myself "alternate" and somehow I managed to put in the "iv". 
Once I have it in disc form is it like a normal install from disc or is there some steps that I need to pay attention to or steps to avoid?

It's pretty simple. You'll get asked for language, then you'll get a menu with different options. Just pick the one that says install Ubuntu. Don't bother with anything special from the F# keys.

The trickiest part is partitioning. But, there is an option to have the OS use all the available space as one partition for everything. If you want to set up a custom partitioning scheme and have multiple drives and OS's, you'll have the freedom to do it. Fortunately, in this part of the setup there are warnings given before any changes will be permanently written to disk and you have a chance to cancel the disk write and make changes if you want.

After the partitioning is done, you'll have some simple questions to answer, select a machine name, a user name, an admin password, set the clock, choose a location...that sort of stuff. A lot of files will be installed from CD and others will be pulled in through your Internet connection. At the very end, it will install grub and tell you to remove the CD and reboot.

If you get to a place where you aren't sure of what to do, just write it down so you can post it here, and then just make your best guess and continue. If things get jacked, you can always reinstall it. I must have reinstalled it over seventy times. It installs in about 45 minutes on my system (an old 2.4GHz P4 with 2GB RAM).

---

### Post by revto on 2010-12-17
Sorry for blanking out last night it was 1:30 here but I got the 10.04 alternate disk downloaded and burned to disc. When it goes to grub I get a black screen with a blinking cursor in the top left. I would think this is a downloading error but I downloaded it to two different computers and burned. 

The biggest kick in the pants is that the one not working is one of my newest and this one that I am on is a decade old and wouldn't handle win7 but ubuntu 10.04 runs like a champ and it has a nvidia video card. Go figure

---

### Post by revto on 2010-12-17
Sorry, it goes to a black screen with a cursor blinking in the top left hand and the monitor doesn't shut off and that is immediately after bios

---

### Post by Crusty Old Fart on 2010-12-17
> **revto said:**
> The biggest kick in the pants is that the one not working is one of my  newest and this one that I am on is a decade old and wouldn't handle  win7 but ubuntu 10.04 runs like a champ and it has a nvidia video card.  Go figure
Yup. That's because the default video driver, that is included as part of the installation, runs the Nvidia card in your old machine without any problem. That's good to know. It give us the option of pulling the Nvidia card from your old machine and running it in your new machine. We may do that later, but not yet.

It would help to know a few things about your new machine:

[LIST]
[*]Is the architecture 32 bit or 64 bit? (I should have asked this a long time ago)
[*]What is the make and model?...or...if you built it yourself, what is the make and model of the main board?
[*]How old is it?
[/LIST]
> **revto said:**
> Sorry, it goes to a black screen with a cursor blinking in the top left hand and the monitor doesn't shut off and that is immediately after bios
No problem. We didn't expect it to boot all the way to gnome yet. However, at least we have the OS installed (I think) that we can configure.

Please perform the following steps and tell me what happens:

[LIST]
[*]Reboot the installed OS.
[*]When the grub screen displays, use your down arrow to select the recovery kernel.
[*][s][COLOR=Red]Press Ctrl-e to edit it.[/COLOR][/s] [COLOR=Blue]Press e to edit it.[/COLOR]
[*][s][COLOR=Red]Find the line containing the kernel boot options and remove quiet and splash if they exist. Then add the following option: reboot=b[/COLOR][/s][COLOR=Blue] Find the line containing the kernel boot option: single and add the kernel option: reboot=b so the kernel options on this line should be: single reboot=b[/COLOR]
[*]Press Crtl-x to continue booting
[/LIST]
Hopefully, you'll get to a screen that contains a list of recovery options. Let me know if you can get that far.

---

### Post by revto on 2010-12-17
I would love to switch video cards but I have 3 machines with 3 different types of video cards in them. 

I have a HP Pavilion m750n with an AMD Athalon 64 x2, 2 gig of ram, and the notorious Nvidia Geforce 6150LE. I have left this one alone as stock except I have removed the tv card and wiped the hard drive clean from the original vista os. 

I believe I am trying for the 32 version. I don't remember it ever asking me. 

Trying to delete "quiet splash" works until I get done typing "reboot=b" ctrl-x does nothing for me and if I press tab it says "Error 11: Unrecognized Device String" . And if I continue on with the boot I get the black screen. Weird thing is I thought the ctrl button wasn't working so I tried a new keyboard and when I got into the kernal instead of "quiet splash" it said "single". ctrl still did not work but when I switched keyboards back the "quiet splash" was back

---

### Post by revto on 2010-12-17
Also I found this as well. In the menu for ubuntu, i have 2 generic ones and 2 recovery ones and a memtest.

the 2.6.32-26 generic and the 2.6.24.-28 generic ones say "quiet splash" in the kernal 
the 2.6.32-26 recovery and 2.6.24-28 recovery ones say "single" at the end of the kernal where "quiet splash" was. I didn't notice if this was like this earlier because I thought pressing e was a menu option in general not for each one.

---

### Post by Crusty Old Fart on 2010-12-17
> **revto said:**
> I would love to switch video cards but I have 3 machines with 3 different types of video cards in them.
Now I'm confused. I thought you said the video card in your HP Pavilion m750n was an onboard card. I read that to mean: Integrated. So, is the Nvidia Geforce 6150LE card plugged into a PCI slot, or is it integrated into the main board (a.k.a.: mother board)?

What are the video cards in your other machines that we could swap?

> **revto said:**
> I have a HP Pavilion m750n with an AMD Athalon 64 x2, 2 gig of ram, and the notorious Nvidia Geforce 6150LE. I have left this one alone as stock except I have removed the tv card and wiped the hard drive clean from the original vista os.

Are you sure it's an HP Pavilion m750n and not an HP Pavilion m7750n. Details are important here. [**[COLOR=Red]Is THIS your computer?[/COLOR]**]("http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&cc=us&product=3339301&dlc=en&")

I'd still like you to tell me how old this machine is.

> **revto said:**
> I believe I am trying for the 32 version. I don't remember it ever asking me.
I've been guessing it's 32 bit. But, I won't know for sure until I'm sure what your computer is.

> **revto said:**
> Trying to delete "quiet splash" works until I get done typing "reboot=b" ctrl-x does nothing for me and if I press tab it says "Error 11: Unrecognized Device String" . And if I continue on with the boot I get the black screen. Weird thing is I thought the ctrl button wasn't working so I tried a new keyboard and when I got into the kernal instead of "quiet splash" it said "single". ctrl still did not work but when I switched keyboards back the "quiet splash" was back
[LIST]
[*]Please don't press tab anymore unless I ask you to. Thanks.
[/LIST]
> **revto said:**
> Also I found this as well. In the menu for ubuntu, i have 2 generic ones and 2 recovery ones and a memtest.

the 2.6.32-26 generic and the 2.6.24.-28 generic ones say "quiet splash" in the kernal
the 2.6.32-26 recovery and 2.6.24-28 recovery ones say "single" at the end of the kernal where "quiet splash" was. I didn't notice if this was like this earlier because I thought pressing e was a menu option in general not for each one.
Okay...I think you're getting a better idea of how to navigate the grub bootloader options now. So in addition to answering my questions above, it would help to try to boot from the recovery kernel again. Please do the following and let me know what happens:
[LIST]
[*]Reboot the installed OS.
[*]Keep your paws away from the tab button.
[*]When the grub screen displays, use your down arrow to highlight the recovery kernel. It should be the second one from the top.
[*]Press e to edit it.
[*]Find the line that ends with the kernel option: single, and add the following kernel options at the end of it: reboot=b nomodeset. The end of the line should contain all three kernel options, separated by at least one space, like this: single reboot=b nomodeset
[*]Press the Ctrl key and the x key simultaneously (Ctrl-x) to continue booting
[*]Post back here and tell me what happened.
[/LIST]

---

### Post by revto on 2010-12-17
The video is onboard and yes that is my computer a pavilion m7750n. Sorry
This one has a pci express slot and I don't have any of that kind .

As far as age, I am not sure. Older than 2 years and less than 5 years old.

I will stay away from the tab key, but I still cannot continue to boot by pressing ctrl-x. For some reason it won't work. I tried both ctrl buttons individually and even replaced the keyboard with another one but get the same result. ctrl alt delete will work so I know that it works but won't in grub. Is there any other way to continue to boot?

---

### Post by Crusty Old Fart on 2010-12-17
> **revto said:**
> The video is onboard and yes that is my computer a pavilion m7750n. Sorry
This one has a pci express slot and I don't have any of that kind .

As far as age, I am not sure. Older than 2 years and less than 5 years old.

I will stay away from the tab key, but I still cannot continue to boot by pressing ctrl-x. For some reason it won't work. I tried both ctrl buttons individually and even replaced the keyboard with another one but get the same result. ctrl alt delete will work so I know that it works but won't in grub. Is there any other way to continue to boot?

We need a different installation CD. Download the ISO using the following link:
[http://releases.ubuntu.com//lucid/ubuntu-10.04.1-alternate-amd64.iso](http://releases.ubuntu.com//lucid/ubuntu-10.04.1-alternate-amd64.iso)

MD5 SUM = f3da7da6931e3160738b3067d79e346a

Burn it to a CD and install it.

---

### Post by Crusty Old Fart on 2010-12-17
**_[SIZE=1]Reference Info:[/SIZE]_**  
[LIST]
[*]Computer: [HP Pavilion Media Center TV m7750n Desktop PC]("http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&cc=us&product=3339301&dlc=en&")
[LIST]
[*]Manufacturer's Specification: [HP Pavilion Media Center TV m7750n Desktop PC Product Specifications]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00821657&tmp_track_link=ot_faqs/top_issues/en_us/c00821657/loc:2&lc=en&dlc=en&cc=us&product=3339301")
[*]Release Date: 03-Jan-2007
[/LIST]
[br]1[/br]
[*]Processor: [AMD Athlon 64 X2]("http://www.amd.com/us/products/desktop/processors/athlon-x2/Pages/amd-athlon-x2-dual-core-processors-desktop.aspx")
[LIST]
[*]Architecture: 64-bit
[/LIST]
[br]1[/br]
[*]Integrated graphics adapter: [Chipset: GeForce 6150 LE]("http://www.nvidia.com/object/mcp_amd_page.html")
[LIST]
[*]Driver Info:
[LIST]
[*]Default nouveau driver for NVIDIA: compatible with GeForce 6XXX (Ref.: man nouveau)
[*][s][color=red]But apparently not compatible with the integrated GeForce 6150 LE  graphics chipset.[/color][/s] [color=blue]Nope. The nouveau driver works fine with the 6150 LE chipset, as long as the OS is installed with the monitor connected directly to the computer rather than being connected through the KVM splitter (see posts [post=10274048]#362[/post] through [post=10274356]#377[/post])[/color].
[/LIST]
 
[/LIST]
[br]1[/br]
[*]Monitor: Dell E176FPb
[br]1[/br]
[*]Splitter: KVM 2 port switch MT-270S
[br]1[/br]
[*]Ubuntu ISO's:
[LIST]
[*]10.04.1 LTS AMD 64 bit Alternate ISO: [http://releases.ubuntu.com//lucid/ubuntu-10.04.1-alternate-amd64.iso](http://releases.ubuntu.com//lucid/ubuntu-10.04.1-alternate-amd64.iso)
[LIST]
[*]MD5 SUM = f3da7da6931e3160738b3067d79e346a
[/LIST]
[br]1[/br]
[*]10.04.1 LTS AMD 64 bit Desktop ISO (Live CD): [http://releases.ubuntu.com//lucid/ubuntu-10.04.1-desktop-amd64.iso](http://releases.ubuntu.com//lucid/ubuntu-10.04.1-desktop-amd64.iso)
[LIST]
[*]MD5 SUM = b4faa186c2419dc26e522e5f82e268a1
[/LIST]
 
[/LIST]
[br]1[/br]
[*]Errors:
[LIST]
[*]nforce2__smbus 000:00:0a:1: Error probing SMB1
[LIST]
[*]Ref.: [post=10255020]Post #91[/post]
[*]Ref.: [thread=1607657]Thread 10.04 LTS live cd goes blank after boot[/thread]
[/LIST]
 
[/LIST]
[br]1[/br]
[*]Command outputs:
[LIST]
[*][COLOR=Red]**Before Nvidia binary driver installation:**[/COLOR]
[LIST]
[*]cat ~/farts/xorg.conf_original: [post=10262212]Post #201[/post]
[*]lshw: [post=10262279]Post #204[/post]
[*]lsmod: [post=10262294]Post #206[/post]
[*]lspci -tvv: [post=10262329]Post #209[/post]
[*]xrandr -q --verbose: [post=10262502]Post #227[/post]
[/LIST]
[br]1[/br]
[*][COLOR=Green]**After Nvidia binary driver installation:**[/COLOR]
[LIST]
[*]sudo cat /etc/X11/xorg.conf: [post=10272574]Post #290[/post]
[*]xrandr -q --verbose: [post=10272563]Post #288[/post]
[/LIST]
 
[/LIST]
[br]1[/br]
[*]Research:
[LIST]
[*][X/KernelModeSetting - Ubuntu Wiki]("https://wiki.ubuntu.com/X/KernelModeSetting")
[*][Install Nvidia graphical driver in Ubuntu Lucid (10.04)]("http://ubuntuguide.net/install-nvidia-graphical-driver-in-ubuntu-lucid-10-04")
[*][Thoughts on Technology: Installing nVidia Driver in Ubuntu 10.04]("http://jeffhoogland.blogspot.com/2010/04/installing-nvidia-driver-in-ubuntu-1004.html")
> Ref.: [Kevin (Whizard72)]("http://jeffhoogland.blogspot.com/2010/04/installing-nvidia-driver-in-ubuntu-1004.html?showComment=1273032878227#c8073070906417695077")
Upon upgrade, the nouveau driver does not work at all with 6150LE  graphics chipset at all, results in scrambled video with no ability to  get to a virtual terminal, seems like machine locks up tight
[*][X/Config/Resolution - Ubuntu Wiki]("https://wiki.ubuntu.com/X/Config/Resolution#Output%20port%20names")
[*][X.Org Wiki - FAQVideoModes]("http://www.x.org/wiki/FAQVideoModes#head-82230a582646cbf28ac41dec2139732ee868e0d2")
[/LIST]
[br]1[/br]
[*]Nvidia Binary Driver Installation:
[LIST]
[*][NVIDIA DRIVERS 256.35 Certified]("http://www.nvidia.com/object/linux-display-ia32-256.35-driver.html")
[LIST]
[*]Supported products:
> 
**GeForce 6 series:**
6600 GT, 6200 A-LE, 6800 XT, 6250, 6150, 6200, 6200 LE, 6100, 6150SE nForce 430, 6200 TurboCache, **[COLOR=Red]6150 LE[/COLOR]**, 6200SE TurboCache, 6100 nForce 405, 6700 XL, 6150LE / Quadro NVS 210S, 6600 LE, 6800 GS/XT, 6600, 6600 VE, 6800 GT, 6800 LE, 6500, 6100 nForce 420, 6800, 6100 nForce 400, 6610 XL, 6800 Ultra, 6800 XE, 6800 GS

[/LIST]
 
[*][BinaryDriverHowto/Nvidia - Community Ubuntu Documentation]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")
[LIST]
[*]Removing old xorg.conf files:
```

sudo rm /etc/X11/xorg.conf
sudo rm /etc/X11/xorg.conf_original

```
[*]Removing the Nouveau driver:
```

sudo apt-get --purge remove xserver-xorg-video-nouveau

```
[/LIST]
 
[*][How To Install nVidia 256.35 Display Drivers In Ubuntu (From A PPA Repository) ~ Web Upd8: Ubuntu / Linux blog]("http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html")
[br]1[/br]
[LIST=1]
[*]**Add the PPA**
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```
[*]**Install the nVidia display drivers**
```
sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
```Then go to System > Administration > Hardware Drivers and make sure "Nvidia current" is activated.
[br]1[/br]
[*]**Reboot.**
[br]1[/br]
[/LIST]
 
[*]If driver installation goes badly and some of what was done needs to be reversed, the following link may help: [Remove PPA Repositories Via Command Line [Quick Ubuntu Tip] ~ Web Upd8: Ubuntu / Linux blog]("http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html")
[/LIST]
 
[/LIST]

---

### Post by revto on 2010-12-17
So does this mean that I have been trying to install a 32 bit os when I should have been trying to install a 64 bit system?

---

### Post by Crusty Old Fart on 2010-12-17
> **revto said:**
> So does this mean that I have been trying to install a 32 bit os when I should have been trying to install a 64 bit system?
Yup. Sure seems like it.

---

### Post by Crusty Old Fart on 2010-12-17
An interesting test at this point would be to burn a 64-bit Live CD and see if it would take you all the way into gnome in tryout mode.

There's a link to the Live CD on the red reference post in my signature.

It may seem like we're back to square one, but I would argue that we've learned a lot so far about what we're dealing with and have a much better chance of success than we had in the beginning, especially since between HP, AMD, and Nvidia, your graphics hardware is knitted together pretty tightly on your motherboard. At least, that's the conclusion I came to after visiting the links included on the reference post and studying the content of what I found at the different websites.

---

### Post by revto on 2010-12-17
I'll be ready for that test in a minute, just got done downloading the live disc and started burning

good news is that the alt disc let me install it which all of the other 10.04 would not let me get that far even if it did blackscreen after reboot

---

### Post by revto on 2010-12-17
Within seconds of "try ubuntu without installing" I get the black screen and the monitor turns off

---

### Post by revto on 2010-12-17
I can get the live cd to work using "nomodeset" which brings me to a "ubuntu@ubuntu" prompt.

---

### Post by Crusty Old Fart on 2010-12-17
> **revto said:**
> I can get the live cd to work using "nomodeset" which brings me to a "ubuntu@ubuntu" prompt.
That's not good news. Same thing as before with the other Live CD.

> **revto said:**
> ...good news is that the alt disc let me install it which all of the other  10.04 would not let me get that far even if it did blackscreen after  reboot
Am I right to read this meaning that you now have a 64-bit OS installed on your hard drive from the Alternate CD?

[s][COLOR="Red"]And if so, have you tried to boot from it?[/COLOR][/s] [COLOR="Blue"]Oh...never mind. It blackscreened.[/COLOR]

---

### Post by revto on 2010-12-17
Yes its the same but the alt 64 disc actually let me install it which all other 10.04 discs would not including the live disc 10.04 64 bit. 

I booted into the system after install and like before after bios, it would have a blinking cursor in the top left and then blackscreen and the monitor shuts off

---

### Post by Crusty Old Fart on 2010-12-17
Did it display the grub menu?

If it did, what did you do there?

---

### Post by revto on 2010-12-17
It didn't show a grub menu, just from bios to a black screen with a blinking cursor in the top left then no cursor and the monitor turns off

---

### Post by Crusty Old Fart on 2010-12-17
> **revto said:**
> It didn't show a grub menu, just from bios to a black screen with a blinking cursor in the top left then no cursor and the monitor turns off
This is even worse than before.
What makes you believe the 64 bit OS got installed?
At the end of the installation process, did it tell you that it was ready to install grub on /dev/sda1?

---

### Post by revto on 2010-12-17
It installed with a lot of install windows and the last one was the grub install which took like 5-10 minutes. It asked me if I wanted to write it to the "master boot sector on the partition"?? I should have wrote it down. I said yes because it was recommended for single operating systems using ubuntu. I can reinstall any version again because that is usually how I fix computer problems especially with windows. Putting computers together and installing operating systems is my strong point, though that is still weak in the computer field.

---

### Post by Crusty Old Fart on 2010-12-17
> **revto said:**
> It installed with a lot of install windows and the last one was the grub install which took like 5-10 minutes. It asked me if I wanted to write it to the "master boot sector on the partition"?? I should have wrote it down. I said yes because it was recommended for single operating systems using ubuntu. I can reinstall any version again because that is usually how I fix computer problems especially with windows. Putting computers together and installing operating systems is my strong point, though that is still weak in the computer field.
You did the right thing. But, grub should have installed much faster than it did. Still...when you tell me that this is the first time you have gotten the install to complete, it makes me wonder what grub we've been playing with if the 32 bit Alternate CD never installed. But, I guess that's water under the bridge at this point.

Some people have success by pressing the Enter button when they get the black screen with the blinking cursor at the top-left. Please try a reboot and press the Enter key before the monitor goes to sleep and tell me what happens.

---

### Post by Crusty Old Fart on 2010-12-17
Does your motherboard look like this?

[IMG]http://h10025.www1.hp.com/ewfrf-JAVA/Doc/images/c02261467.jpg[/IMG]

---

### Post by revto on 2010-12-17
When the blinking cursor appears pressing enter makes the cursor disappear but it comes back a few seconds later and after the text at the top appears it go to a black screen and the monitor turns off. if you press the enter button after the cursor reappears the cursor drops down 2 lines but the same end results. If you press and hold the enter button the cursor disappears then returns and then drops down 2 then 4 then 6 lines and the same end results again.

---

### Post by Crusty Old Fart on 2010-12-17
> **revto said:**
> When the blinking cursor appears pressing enter makes the cursor disappear but it comes back a few seconds later and after the text at the top appears it go to a black screen and the monitor turns off. if you press the enter button after the cursor reappears the cursor drops down 2 lines but the same end results. If you press and hold the enter button the cursor disappears then returns and then drops down 2 then 4 then 6 lines and the same end results again.
Can you tell me what the text at the top of the screen says before it goes black?

---

### Post by revto on 2010-12-17
That looks just like it. The IDE ports, power ports, processor port, pci express and pci ports all look the same

The ram ports as well

---

### Post by revto on 2010-12-17
I believe it is the info text that says "debian" something something. It goes so quick that I cannot see it but ill try to record it

---

### Post by revto on 2010-12-17
Good thing I recorded it. It says:

[          9.367005] nForce2_smbus 0000:00:0a.1: Error probing SMB1.

---

### Post by Crusty Old Fart on 2010-12-17
It really bugs me that grub doesn't work. It also bugs me that for most of time we'd been using the old grub, you say the OS never got installed. I wish I had known that. I must be missing something big, because I can't understand that it would make any sense to you to try to boot an OS from grub that you knew didn't get installed. Any light you can shed on any of this would help me understand what's been going on. Just something for you to think about and comment on if you want to. However, in the future, if we try to install an OS, and you know it failed, please let me know as soon as you can. There's no point in playing with the grub bootloader when there's no OS for it to load.

I'd like to try the following:

[LIST=1]
[*]Mount the hard drive.
[*]Zero out the boot sector.
[*]Format the HDD.
[*]Install the 64 bit OS from the Aternate CD
[/LIST]
Steps 1 and 2 will require us to use the Live CD to open a virtual shell from which we can issue commands.

Step 3 can be done early in the installation process of Step 4. You have the option to erase all data before you partition, then set up the new partition and flag it for formatting. At least I think it's something similar to that.

So, if you're up for this, then boot from the 64 bit Live CD, use the nomodeset boot option and let me know when you get to the ubuntu@ubuntu prompt.

---

### Post by revto on 2010-12-17
I'm there and ready.

---

### Post by Crusty Old Fart on 2010-12-17
Shucks...I can't remember off the top of my head how to do what I wanted to do from the Live CD.

---

### Post by revto on 2010-12-17
It says:

mount: cannot find /dev/sda in /etc/ftab or /etc/mtab

---

### Post by Crusty Old Fart on 2010-12-17
I need to take some time to study up on a few things and test them on my system so I don't waste your time with a bunch of crap commands that won't work.

When I'm ready, I'll post back here. By that time, you will have gone to bed.

Sleep well.

See you tomorrow.

---

### Post by revto on 2010-12-17
Thank you so much for your help.
Even if we don't make progress, I am learning, which is the best part of the process and I appreciate that.
Thomas

---

### Post by Crusty Old Fart on 2010-12-17
You're mighty welcome, Thomas.

I'm also going to take some more time to see if I can discover what causes the nForce error you get before your screen goes black.

Later,

Crusty

---

### Post by Crusty Old Fart on 2010-12-17
That didn't take as long as I thought it would.

I'm back in the saddle and ready to ride!

---

### Post by revto on 2010-12-18
Just let me know what to try and I will try it as soon as I get home from work tomorrow or if I have time before work and post the results asap.

---

### Post by Crusty Old Fart on 2010-12-18
Okay...
After you boot using the 64-bit Live CD with the nomodeset kernel option, enter the following command at the ubuntu@ubuntu prompt:
```

sudo fdisk -l

```Then, post every line from the output that begins with: /dev/
There may be only one of them.

After I see what you posted, I'll give you the next instruction.

---

### Post by revto on 2010-12-18
I get a /dev/sda1 with an * next to it and a /dev/sda2 and a /dev/sda5.

Does this mean that I didn't wipe it clean when I reformatted?

---

### Post by Crusty Old Fart on 2010-12-18
> **revto said:**
> I get a /dev/sda1 with an * next to it and a /dev/sda2 and a /dev/sda5.

Does this mean that I didn't wipe it clean when I reformatted?
No...it's fine.

Now we're going to make a mount point for the boot partition.
Enter the following command:
```

sudo mkdir /media/bootpart

```If you don't get any output, then it should have worked.
You can make sure by cd into the mount point:
```

cd /media/bootpart

```Let me know if that worked.

---

### Post by revto on 2010-12-18
"sudo mkdir /media/bootpart"  returns me to a ubuntu@ubuntu prompt (like you said) and when I type cd /media/bootpart it takes me to a "ubuntu@ubuntu:/media/bootpart$" prompt

---

### Post by Crusty Old Fart on 2010-12-18
> **revto said:**
> "sudo mkdir /media/bootpart"  returns me to a ubuntu@ubuntu prompt (like you said) and when I type cd /media/bootpart it takes me to a "ubuntu@ubuntu:/media/bootpart$" prompt
Perfect.

Now were going to mount the boot partition with the following command:
```

sudo mount /dev/sda1 /media/bootpart

```

Let me know if it gives you any errors.

---

### Post by revto on 2010-12-18
If there is no space between /dev/sda1 and /media/bootpart then I get:

mount can't find /dev/sda1/media/bootpart  in /etc/fstab or /etc/mtab

when there is a space between them it returns me to the "ubuntu@ubuntu:media/bootpart$" prompt.
couldn't tell if there was a space or not

---

### Post by Crusty Old Fart on 2010-12-18
> **revto said:**
> If there is no space between /dev/sda1 and /media/bootpart then I get:

mount can't find /dev/sda1/media/bootpart  in /etc/fstab or /etc/mtab

when there is a space between them it returns me to the "ubuntu@ubuntu:media/bootpart$" prompt.
couldn't tell if there was a space or not
There's supposed to be a space between them. You're in good shape.

Now we're going to zero write the entire master boot record, including the disk signature and partition table, with the following command:
```

[SIZE=5]sudo dd if=/dev/zero of=/dev/sda bs=512 count=1[/SIZE]

```I made it bigger so you can see where the spaces are. This command has to be entered perfectly. So, make sure you have it exactly right before you press your enter key.

---

### Post by revto on 2010-12-18
After triple checking it then pressing enter it gave me a bunch of SQUASHFS error codes.
Most say something like this:

[47142. (changing numbers)] SQUASHFS error: unable to read page, block efb5893, size 3581
[47142. (changing number)] SQUASHFS error: unable to read fragment cache entry [2fb58931]

The second part of the [47142. (changing number)] changed on every line but the rest stayed constant. The last 2 different lines look like this and is repeated again with only the changing number changing:

47142.(changing number)] SQUASHFS error: unable to read page, block 2fd13fc size 5fb8
47142.(changing number)] SQUASHFS error: unable to read fragment cache entry [2fd13fc]

---

### Post by Crusty Old Fart on 2010-12-18
> **revto said:**
> After triple checking it then pressing enter it gave me a bunch of SQUASHFS error codes.
Most say something like this:

[47142. (changing numbers)] SQUASHFS error: unable to read page, block efb5893, size 3581
[47142. (changing number)] SQUASHFS error: unable to read fragment cache entry [2fb58931]

The second part of the [47142. (changing number)] changed on every line but the rest stayed constant. The last 2 different lines look like this and is repeated again with only the changing number changing:

47142.(changing number)] SQUASHFS error: unable to read page, block 2fd13fc size 5fb8
47142.(changing number)] SQUASHFS error: unable to read fragment cache entry [2fd13fc]

It looks to me like the system may have been rebooted between Post #73 and Post #74. So, is that right? Did you reboot the computer before you entered the command in Post #74?

---

### Post by revto on 2010-12-18
I haven't rebooted since at or before post 60. I could see all of the previous commands before the [47142.xxxxx] codes took over the screen

---

### Post by Crusty Old Fart on 2010-12-18
> **revto said:**
> I haven't rebooted since at or before post 60. I could see all of the previous commands before the [47142.xxxxx] codes took over the screen
Allright...well that kind of blows my suspicion. However, you may not have been in good as shape as I assumed after you experimented with and without the space in Post #73.

Would you like to try this again?

---

### Post by revto on 2010-12-18
I am always ready to go!!

---

### Post by Crusty Old Fart on 2010-12-18
> **revto said:**
> I am always ready to go!!
Great!

The process described below needs to be completed in a single session. In other words, it cannot be interrupted by a system reboot.
If for some reason, a reboot must be performed, then this process will need to be attempted again beginning at the first step.

Please perform the steps below. If you get any errors, please stop working and post a description of the error and the number of the step in the process you are trying to complete.

[LIST=1]
[*]Boot from the 64 bit Live CD using the nomodeset boot option to get to a tty1 virtual shell with the ubuntu@ubuntu:~$ command prompt.
[br]1[/br][s][COLOR=red][/COLOR][COLOR=red]
[*]Create a mount point by entering the following command:
```

[SIZE=4]sudo mkdir /media/bootpart[/SIZE] 

```If it worked, you won't get any output and will be returned to the command prompt.

Check to make sure the mount point was created by changing to its directory with the following command.
```

[SIZE=4]cd /media/bootpart[/SIZE]

```If everything has worked, you won't get any output and your command prompt will have changed to: ubuntu@ubuntu:/media/bootpart$
[br]1[/br]
[*]Mount the boot partition with the following command:
```

[SIZE=4]sudo mount /dev/sda1 /media/bootpart[/SIZE]

```If it worked, you won't get any output and will be returned to the command prompt.
[/COLOR][/s][br]1[/br]
[B][COLOR=Blue]EDIT: The disk should _NOT_ be mounted when performing the zero MBR write below.
[br]1[/br]
[/COLOR][/B]
[*]Zero write the the entire master boot record, including the disk signature and partition table, with the following command (take special care to enter the command **_exactly_** as shown):
```

[SIZE=4]sudo dd if=/dev/zero of=/dev/sda bs=512 count=1[/SIZE]

```If this write worked, you may or may not get any output. I don't remember. However, if it fails, you will most likely get error output
[/LIST]
Please let me know if you were successful before you attempt to reinstall an OS.

---

### Post by revto on 2010-12-18
I get an error after step three that says:

mount: special device /dev/sda1 does not exist

also I rebooted the computer before I tried again as to start fresh

---

### Post by Crusty Old Fart on 2010-12-18
Yup...I think I may have screwed up by mounting the hard drive before trying to zero write the MBR.

Sorry about that.

One thing is certain, the drive isn't mounted now, so go ahead and enter this command again:
```

[SIZE=4]sudo dd if=/dev/zero of=/dev/sda bs=512 count=1[/SIZE]
```

---

### Post by revto on 2010-12-18
I don't know if this is good but it looked better than the error messages. It said:

1=0 records in
1=0 records out
512 bytes (512 B) copied, 0.00110864 s, 462 kB/s
ubuntu@ubuntu:/media/bootpart$ (prompt)

---

### Post by revto on 2010-12-18
sorry it was:

1+0 records in 
1+0 records out

not an = sign, sorry

---

### Post by Crusty Old Fart on 2010-12-18
> **revto said:**
> ...512 bytes (512 B) copied, 0.00110864 s, 462 kB/s
ubuntu@ubuntu:/media/bootpart$ (prompt)

Paydirt! 512 bytes written with zeros. Now we have a clean master boot record, disk signature and partition table.

So, now we can install the OS using the 64-bit Alternate CD. My main interest is that GRUB gets successfully installed. When it asks you for permission to install it into the Master Boot Record of your first hard drive, allow it, like you did before. Hopefully we'll get a good installation of GRUB this time. If the system thinks so, it should tell you to remove your CD and reboot (or something like that) after it finishes installing grub.

I'm REALLY curious to know what happens at the end of the install.

Good Luck.

I'll be waiting for your next post.

---

### Post by revto on 2010-12-18
Should I repartition? I want it to be the only partition but I don't want to mess up what we have accomplished. Usually I choose the "guided, use whole disk" option. should I choose something else?

---

### Post by revto on 2010-12-18
actually there is:

guided use entire disk
guided use entire disk with setup LVM
guided use entire disk with encrypted LVM

---

### Post by Crusty Old Fart on 2010-12-18
> **revto said:**
> actually there is:

guided use entire disk
guided use entire disk with setup LVM
guided use entire disk with encrypted LVM

Use this one --> [SIZE=1][COLOR=Blue]**guided use entire disk**[/COLOR][/SIZE][COLOR=Blue]
[/COLOR]
It will use the entire disk and set up the partitions you need:
/dev/sda1 <-- The boot partition (primary)
/dev/sda2 <-- The system partition (primary)
/dev/sda5 <-- The swap area partition (extended/logical)

But you probably won't even notice.

Go for it.

---

### Post by revto on 2010-12-18
When this is done is there any instruction before the reboot or are we awaiting the results of the reboot?

---

### Post by Crusty Old Fart on 2010-12-18
The last step is the installation of the GRUB bootloader. It will ask you for permission to install it. Let it.

Following that, it should tell you to remove your CD and boot into your new OS. Do it.

That's all the instructions it will give you.

I don't expect it to boot all the way into gnome. However, I'm hoping for a good GRUB where we can specify kernel options and have Ctrl-x continue the boot process with them -- we've never been able to do that yet.

We'll need to be able to get into a virtual shell to make configuration changes to get the desktop to load. We've never been able to to that either. All we've gotten has been the black screen with the upper-left blinking cursor followed by the monitor napping on us.

If we get UNBELIEVABLY, FEALLY, RUCKING LUCKY -- gnome will be served to us. But I wouldn't get my hopes up about that yet.

---

### Post by revto on 2010-12-18
Blackscreen on startup with the nvidia error at the top saying:

[      6.437190] nforce2__smbus 000:00:0a:1: Error probing SMB1

---

### Post by Crusty Old Fart on 2010-12-18
> **revto said:**
> Blackscreen on startup with the nvidia error at the top saying:

[      6.437190] nforce2__smbus 000:00:0a:1: Error probing SMB1

Did you ever see the grub menu?

---

### Post by revto on 2010-12-19
No. Just a blinking cursor that disappears then back and then the error code. 

I caught it in the right spot by pressing shift and got a grub menu with:

ubuntu, with linux 2.6.32-24-generic and a recovery version and now 2 memtests

You want me to try to edit the kernal or try something else?

---

### Post by Crusty Old Fart on 2010-12-19
Yeah...highlight the recovery kernel.
Press e to edit it.
Add nomodeset to the line ending with the kernel option: single
Press Ctrl-x

Let me know what happens.

---

### Post by revto on 2010-12-19
If this is the way I was supposed to edit the kernal, I see why you said to not press tab. In the other kernal It made it out like that was the way you ***pleted a ***mand. 

I changed it and ctrl-x worked and now I am at a prompt that says:

ubuntu2 login: and I sign in
password 

now I am at a thomas@ubuntu2:~$ prompt

obviously thomas is my login and ubuntu2 is the name of the ***puter

---

### Post by revto on 2010-12-19
scratch that last reply..I am the recovery menu. please proceed

---

### Post by Crusty Old Fart on 2010-12-19
I think the first option is the one you want.
Something like continue with normal login or something.

That should take you back to the shell where you were and I wanted you to be, I hope.

Also, the ubuntuforms.org domain seems to be having a problem with the letter group: c o m

When they are together without spaces between them, they display as ***
Just sayin'.

---

### Post by revto on 2010-12-19
Ok I am in the prompt mentioned in post 95. 

In the future I will try to separate the c o m's

---

### Post by Crusty Old Fart on 2010-12-19
testing testing testing
c
c o
co
co m
***
co mmand
***mand

Wow...this sucks...I'm not even going to try to give you co_mmands other than this one:
```

sudo shutdown now

```Let's call it a night and hope that the forum staffs gets this c o m bug fixed by tomorrow.

We made some really good progress tonight. I really don't want to screw it up with a bad
co mmunication problem.

G'night, Mate

---

### Post by revto on 2010-12-19
OK. Let me know the next steps as you can. 

And thank you for your help. I appreciate you sticking with me and using your valuable time to help me. That is the true spirit of ubuntu and linux that keeps me trying instead of reverting to windows to over***e "simple" fixes that I must use use my brain or to have the courage to ask for help with. You are good Ubuntu people! Thank you.  
Thomas

---

### Post by Crusty Old Fart on 2010-12-19
Soon, it may help for me to see what is on your monitor.
Do you have a digital camera, or a cell phone...anything that you could use to take a picture of it and upload it to this forum?

By the way, it looks like the com censoring problem has been fixed here, at least for new posts.

---

### Post by revto on 2010-12-19
Just walked in the door, have a digital camera ready and I am itchin to mark this thread solved. 

Please proceed whenever you are ready

---

### Post by Crusty Old Fart on 2010-12-19
Okay...let's get to work.

Have you booted and are in a tty1 virtual shell with the thomas@ubuntu2:~$ command prompt?

---

### Post by revto on 2010-12-19
I am there and ready

---

### Post by Crusty Old Fart on 2010-12-19
Good. The first thing we need to do is update the system.

Enter the following command:
```

[SIZE=4]sudo apt-get update && apt-get -y upgrade[/SIZE]

```

---

### Post by revto on 2010-12-19
Also when I log in it tells me that I have 183 packages can be updated and 90 updates are security updates.

Didn't think we needed to do anything with this yet but I thought I would let you know. Didn't notice it the last few times I logged in.

---

### Post by revto on 2010-12-19
It read the packages, then says:

reading package lists ... done
E: Could not open lock file /var/lib/dpkg/lock - open (13: permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg), are you root?
thomas@ubuntu2:~$

---

### Post by Crusty Old Fart on 2010-12-19
Looks like we'll have to do them one at a time.
Enter the following commands:
```

[SIZE=4]sudo apt-get update
sudo apt-get -y upgrade[/SIZE]

```

---

### Post by revto on 2010-12-19
Wow, that was probably the most amount of code to race by my eyes.

Everything seemed to download and install correctly. no errors or error messages

---

### Post by Crusty Old Fart on 2010-12-19
Good. Now we'll do a bit of housekeeping.

In the code box below, there are four commands I'd like you to run.
If you get any errors, stop working and post them.
Wait for each command to finish before entering the one after it.
You will get output from the first three. I don't need to you to post it unless you get errors.
You may or may not get any output from the last command.
```

sudo dpkg --configure -a
sudo update-initramfs -k all -u
sudo update-grub
sudo apt-get clean

```Please let me know when you're finished and we'll move on to the next step.

---

### Post by revto on 2010-12-19
Yet another bank of commands that appear to have been done correctly

---

### Post by Crusty Old Fart on 2010-12-19
> **revto said:**
> Yet another bank of commands that appear to have been done correctly
Right...that's just another reason why I get paid the BIG BUCK$!

Now it's time to show off your expert photographic prowess.
Enter the following commands:
```

clear
cat /etc/default/grub

```Take a picture of your monitor and post it.
Hopefully, I'll be able to read the text.

---

### Post by revto on 2010-12-19
```

```[IMG]http://ubuntuforums.org/thomas/100_1376.jpg[/IMG]

---

### Post by revto on 2010-12-19
hopefully this is the pic

---

### Post by Crusty Old Fart on 2010-12-19
> **revto said:**
> hopefully this is the pic
That's perfect. Thank you.

We are going to modify your grub configuration.
Before we do that, we are going to make a copy of your grub configuration so we can revert back to it if we screw things up.
Enter the following command to make the copy:
```

[SIZE=4]sudo cp /etc/default/grub /etc/default/grub_original[/SIZE]

```Let's make sure the copy was made successfully.
Enter the following command:
```

[SIZE=4]ls -l /etc/default | grep grub[/SIZE]

```Do you at least see a file named: grub, and another one named: grub_original?

---

### Post by revto on 2010-12-19
That is exactly what I see, one grub one grub_original

---

### Post by Crusty Old Fart on 2010-12-19
Okay...now we are going to edit the file.
Which editor (i.e. vi, nano) are you familiar with?

---

### Post by revto on 2010-12-19
I guess that I am familiar to none of them, but I love crash courses!! Except with planes

---

### Post by Crusty Old Fart on 2010-12-19
> **revto said:**
> I guess that I am familiar to none of them, but I love crash courses!! Except with planes
Uhhh...as tempting as it is, now is NOT the time for crash courses in modifying the grub configuration. We'll do it later.

I did some more research on the error you were getting after BIOS boot:
[ 6.437190] nforce2__smbus 000:00:0a:1: Error probing SMB1

As it turns out, it's a bug. The update we did should have fixed it.

So...let's see what happens if we let the system use its default kernel (not spelled kernal) options.

Enter the following command:
```

sudo reboot now

```Hopefully, you won't see the Error probing SMB1.

And if we're ridiculously lucky, and I mean ridiculous, gnome might actually come up.

Good Luck!

---

### Post by revto on 2010-12-19
Got another error probing SMB1

---

### Post by revto on 2010-12-19
Also I know that I seem like a wild card but I am pretty decent at working
on windows, and can take direction easily and will ask upon any point that doesn't go perfectly if you want to go ahead with grub edit.

---

### Post by Crusty Old Fart on 2010-12-19
> **revto said:**
> Got another error probing SMB1
Nutz! They lied. They must be taking lessons from Microsuck.

Still...it's a benign error. Does pressing the enter key get you beyond it?

---

### Post by revto on 2010-12-19
No, when the error probing SMB1 message shows it goes to a black screen then the monitor shuts off.

---

### Post by Crusty Old Fart on 2010-12-19
> **revto said:**
> Also I know that I seem like a wild card but I am pretty decent at working
on windows, and can take direction easily and will ask upon any point  that doesn't go perfectly if you want to go ahead with grub  edit.
I'll give you a crash course later. We'll create a junk file to practice on before mucking around with the grub file.

[s]Where are we now?[/s] Never mind.

---

### Post by Crusty Old Fart on 2010-12-19
Please reboot.

Get to the GRUB menu, highlight the first recovery kernel, and press the enter key to boot.

I want to know what happens when we try the recovery kernel without modifying the kernel boot options. So, let me know what happens.

---

### Post by revto on 2010-12-19
I am at the grub menu and I noticed that the generic still says "quiet splash" and the recovery still says "single". 

I can log into a shell if you have more sudo commands to try

---

### Post by Crusty Old Fart on 2010-12-19
Can you log in to a shell WITHOUT adding the nomodeset boot option to the recovery kernel?

---

### Post by revto on 2010-12-19
No, I have to alter the nomodeset option to access a shell

---

### Post by Crusty Old Fart on 2010-12-19
> **revto said:**
> No, I have to alter the nomodeset option to access a shell
Okay go ahead and do that.

Tell me what happens when you try this command:
```

sudo service gdm start

```
Probably an error.

---

### Post by revto on 2010-12-19
The screen kinda freaked out and flashed a few times then it said:

gdm start/running, process 1356
thomas@ubuntu2:~$

---

### Post by Crusty Old Fart on 2010-12-19
> **revto said:**
> The screen kinda freaked out and flashed a few times then it said:

gdm start/running, process 1356
thomas@ubuntu2:~$

What happens when you press Ctrl-Alt-F7

---

### Post by revto on 2010-12-19
I go here with a flashing prompt by itself no command prompt

---

### Post by Crusty Old Fart on 2010-12-19
Okay...thanks.

Reboot again, and get back into a shell.

At your thomas@ubuntu2:~$ prompt, enter the following commands:
```

[SIZE=4]sudo X -configure
sudo cp ~/xorg.conf.new /etc/X11/xorg.conf[/SIZE]

```After that, reboot again, only this time try using the recovery kernel WITHOUT the nomodeset boot option.

Let me know how that goes.

---

### Post by revto on 2010-12-19
The last code gives me the error:

cp: cannot create regular file '/etc/x11/xorg.conf': no such file or directory

---

### Post by Crusty Old Fart on 2010-12-19
Does this give you ANY output:
```

[SIZE=4]ls -l /etc | grep X[/SIZE]

```

---

### Post by revto on 2010-12-19
I get:

drwxr-xr-x 10 root        root          4096 2010-12-19 00:14 X11

and the last X is in red

---

### Post by Crusty Old Fart on 2010-12-19
Okay...what do you get for output from this command:
```

[SIZE=4]ls -l ~/ | grep xorg[/SIZE]

```

---

### Post by revto on 2010-12-19
I get:

-rw-r--r-- 1 root    root    2699 2010-12-19 21:01 xorg.conf .new

and "xorg" is in red

---

### Post by revto on 2010-12-19
there is more spaces between root and root; as well as between root and 2699

don't know why it didn't show, I put them in there

---

### Post by Crusty Old Fart on 2010-12-19
> **revto said:**
> I get:

-rw-r--r-- 1 root    root    2699 2010-12-19 21:01 xorg.conf .new

and "xorg" is in red

Aha...I see the problem.
There's not supposed to be a whitespace between conf and .new.
The file name is xorg.conf.new (no spaces in it)
Enter the following command:
```

[SIZE=4]sudo cp ~/xorg.conf.new /etc/X11/xorg.conf[/SIZE]
```

Then reboot and try using the recovery kernel WITHOUT the nomodeset boot option.

---

### Post by revto on 2010-12-19
I get:

cp: cannot create regular file '/etc/x11/xorg.conf': no such file or directory

---

### Post by Crusty Old Fart on 2010-12-19
> **revto said:**
> there is more spaces between root and root; as well as between root and 2699

don't know why it didn't show, I put them in there
The forum formatter has a mind of its own when it comes to extra spaces and extra lines.

---

### Post by Crusty Old Fart on 2010-12-19
> **revto said:**
> I get:

cp: cannot create regular file '/etc/x11/xorg.conf': no such file or directory
This makes no sense.
Type the command to me, exactly like you've been typing it into the other computer.

---

### Post by revto on 2010-12-19
sudo cp ~/xorg.conf.new /etc/x11/xorg.conf

---

### Post by Crusty Old Fart on 2010-12-19
> **revto said:**
> sudo cp ~/xorg.conf.new /etc/x11/xorg.conf
[SIZE=4]
[/SIZE] [SIZE=4]sudo cp ~/xorg.conf.new /etc/x11/xorg.conf

No no no...it's upper case X in X11, always has been:

[/SIZE][SIZE=4]sudo cp ~/xorg.conf.new /etc/[COLOR=Red]X11[/COLOR]/xorg.conf[/SIZE]
[SIZE=5]
[/SIZE]

---

### Post by revto on 2010-12-19
Should I try the:

[SIZE=4]sudo X -configure
sudo cp ~/xorg.conf.new /etc/X11/xorg.conf[/SIZE]
commands again the correct way?

sorry about that, I have been trying to pay attention to every detail

---

### Post by Crusty Old Fart on 2010-12-19
I think you just got even with me for all the crap I put you through when I mistakenly had you mount /dev/sda1 before trying to zero write the sda MBR. Touche, Thomas!

---

### Post by revto on 2010-12-19
I love not vengeance, just adventure!

---

### Post by Crusty Old Fart on 2010-12-19
> **revto said:**
> Should I try the:

[SIZE=4]sudo X -configure
sudo cp ~/xorg.conf.new /etc/X11/xorg.conf[/SIZE]
commands again the correct way?

sorry about that, I have been trying to pay attention to every detail

No. Just enter the second command:
```

[SIZE=4]sudo cp ~/xorg.conf.new /etc/X11/xorg.conf[/SIZE]

```Then reboot using the recovery kernel and see if you can get to a shell WITHOUT using the nomodeset boot option.

---

### Post by Crusty Old Fart on 2010-12-19
> **revto said:**
> I love not vengeance, just adventure!
Looks to me like you got both ](*,)

---

### Post by revto on 2010-12-19
I came back to my famous black screen once again

---

### Post by Crusty Old Fart on 2010-12-19
> **revto said:**
> I came back to my famous black screen once again
Well...ain't that just ducky!

Okay then, reboot again using the recovery kernel and the nomodeset option and when you get to a shell, enter this command:
```

[SIZE=4]sudo service gdm start[/SIZE]

```

Let's see if it works this time.

---

### Post by revto on 2010-12-19
For some reason I just deleted "quiet splash" on the generic kernal and inserted "nomodeset" thinking I would load a shell and I just loaded the login and then the "real" 10.04 homescreen

---

### Post by Crusty Old Fart on 2010-12-19
> **revto said:**
> For some reason I just deleted "quiet splash" on the generic kernal and inserted "nomodeset" thinking I would load a shell and I just loaded the login and then the "real" 10.04 homescreen

How does it look? Good resolution? Can you run Firefux?

---

### Post by revto on 2010-12-19
Firefox works but there is no internet connection.  Ubuntu says networking disabled in the menu bar. video resolution is 800 x 600

---

### Post by Crusty Old Fart on 2010-12-19
Would you like to configure grub now?

---

### Post by revto on 2010-12-19
Heck yeah!

---

### Post by Crusty Old Fart on 2010-12-19
Okay...open a shell from your Applications menu (upper left of screen)
Applications > Accessories > Terminal

That will open a shell window.

Enter the following command:
```

sudo gedit /etc/default/grub

```

A new gedit window will open your grub file.

Find the line that says:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Change it to:
GRUB_CMDLINE_LINUX_DEFAULT=""

DON'T MAKE ANY OTHER CHANGES.

Save the file and close the gedit window.

Now...back in your shell window, enter the following command:
```

sudo update-grub

```

Then reboot without adding nomodeset and see if it works.

We've made so many changes that all of them may not take effect until we've gone through a few more reboots.

So, if the first reboot doesn't work, just try it a couple more times.

---

### Post by revto on 2010-12-19
everything seemed good until reboot where I got the error probing SMB1 code and then a black screen

---

### Post by Crusty Old Fart on 2010-12-19
Okay...reboot using the generic kernel but add the nomodeset to it.

Evenutally, we may need to abandon nomodeset,

Let's try for an Internet connection. As soon as we can get an Internet connection, this job will be a lot easier when you can post to the forum from that machine. Then you'll be able to upload code into posts and I can modify it and post it back to you and you can download it.

---

### Post by revto on 2010-12-19
The error came during script that runs when I actually get in, towards the end. 

also I rebooted 4 times. I figured that would show a patern

---

### Post by revto on 2010-12-19
Im ready as usual, lead the way

---

### Post by Crusty Old Fart on 2010-12-20
Okay...are you signed into a gnome desktop?

---

### Post by revto on 2010-12-20
I'm in 10.04 gnome desktop

---

### Post by Crusty Old Fart on 2010-12-20
Good...Let's pickup any updates that may be updates to the updates that we loaded before.

This time we'll do it using the gnome update manager from the System menu:

System > Administration > Update Manager

I'll assume that you know how to take it from there.

---

### Post by Crusty Old Fart on 2010-12-20
Ooops...hope the Internet connection comes alive for that.

---

### Post by revto on 2010-12-20
I got "failed to fetch" errors but I think that is because I have no internet according to this machine

---

### Post by Crusty Old Fart on 2010-12-20
Can you activate it using the button in the upper right hand corner of the display?

---

### Post by revto on 2010-12-20
uh oh!! I am starting to be able to use ubuntu!

the world may never be the same again!

anyways, back to reality: I got the web working and I am downloading the updates

---

### Post by Crusty Old Fart on 2010-12-20
You ROCK!, buddy.

---

### Post by revto on 2010-12-20
I noticed that "quiet splash" was deleted from the kernal and all I had to do was add "nomodeset" and it logged me right in. is there a way to set up "nomodeset" in its place so it will boot right in or do we have to change other options to get to that point?

---

### Post by Crusty Old Fart on 2010-12-20
You know the drill with the Update Manager, right? You run it over and over until it doesn't find anymore.

After you've done that try rebooting again without using nomodeset and see if the SMB1 error goes away.

Hopefully, at some point, you'll get much better screen resolution automatically. But it won't happen as long as you are forced to use nomodeset to boot.

---

### Post by Crusty Old Fart on 2010-12-20
> **revto said:**
> I noticed that "quiet splash" was deleted from the kernal and all I had to do was add "nomodeset" and it logged me right in. is there a way to set up "nomodeset" in its place so it will boot right in or do we have to change other options to get to that point?
The answer is yes. But we don't want to do that. Nomodeset disables Kernel Mode Setting (KMS). RandR works hand in hand with KMS to configure your displays. However, if a good xorg.conf file exists, it overrides KMS automatically. Eventually we will be taking a close look at your xorg.conf file. But we're not at that point yet. We need to try to get beyond this stinking SMB1 probe problem first if we can.

---

### Post by revto on 2010-12-20
Update manager must have got all the updates the first time, it keeps telling me "system up-to-date"

---

### Post by revto on 2010-12-20
And I still need "nomodeset" to get a desktop

---

### Post by Crusty Old Fart on 2010-12-20
Okay...can you log into this forum now from that machine?

---

### Post by lucid_dream on 2010-12-20
Good evening , I have just finished reading your thread and am having the same issue with essentially the same setup. I kind of lost track about 5 or 10 pages ago and was not really able to follow everything you were doing. 

Dont know what its worth but i can fully boot my PSLinuxOS LiveCD but get the black screen too with ubuntu

---

### Post by revto on 2010-12-20
For the first time this machine greets the forum.

Thank you sir crusty!

---

### Post by Crusty Old Fart on 2010-12-20
To lucid_dream: Stay tuned, if we keep kicking this turd, eventually we'll knock all the corn out of it.

To Thomas:
Now is a good place to stop. There's a temptation to experiment at this point. Please don't. A lot of what we've done is just the beginning of what I need to do to complete the heavy lifting. Now that you can access the forum with that machine, we'll be able to look at a lot more stuff, a lot easier.

I need to say Good Night and get some things done around here. My fire went out, the house is getting cold, I need a shower, and I need to head out for some groceries.

Sleep well, my friend.

See you tomorrow.

Crusty

---

### Post by revto on 2010-12-20
Again I must thank you for all of your hard work. Get the house warm and snug and enjoy the winter! it kicks in tomorrow for me and in 2 hours and a tomorrow for you (if i did my math correct)

---

### Post by Crusty Old Fart on 2010-12-20
Before we got all caught up in the joy over your successful boot into gnome, there was a test that I wanted to have done using the recovery kernel.

So, please do the following and let me know what happens.

Reboot using the recovery kernel and the nomodeset option.
When you get to the shell, enter this command:
```

[SIZE=4]sudo service gdm start[/SIZE] 

```Hopefully, this will take you to the gnome login screen.

---

### Post by revto on 2010-12-20
I tried the:

sudo service gdm start

and like you said it brought me to the gnome login, enter my password and I am in

---

### Post by revto on 2010-12-20
Also I now have 2 generic and 2 generic recovery options in the grub menu where I used to only have one each.

---

### Post by Crusty Old Fart on 2010-12-20
> **revto said:**
> I tried the:

sudo service gdm start

and like you said it brought me to the gnome login, enter my password and I am in
That's good news. You kinda stole my thunder, but that's okay.

> **revto said:**
> 
Also I now have 2 generic and 2 generic recovery options in the grub menu where I used to only have one each.

Yup...that's because your kernel got upgraded from version 2.6.32-24   to version 2.6.32-25. Grub keeps your old kernels around just in case you need them if you have a problem with the new one. Apparently, the new one is working just fine.

Allrighty...are you coming at this forum from your new installation?

---

### Post by revto on 2010-12-20
Yes I now posting from the comp that needs the help

---

### Post by Crusty Old Fart on 2010-12-20
> **revto said:**
> Yes I now posting from the comp that needs the help
Good. From now on, I'd like you to use this machine all the time. From this point forward, I will assume that you are using this machine unless you tell me otherwise...Okay?

Also, we need to understand the difference between a **[COLOR=SeaGreen]shell window[/COLOR]** (I'll just call it a **[COLOR=SeaGreen]shell[/COLOR]** in the future) and a **[COLOR=Blue]tty virtual shell[/COLOR]** (I'll just call that one a **[COLOR=Blue]virtual shell[/COLOR]** in the future).

A **[COLOR=SeaGreen]shell[/COLOR]** is what you get when you open a window from your Applications menu by following the click sequence: Applications > Accessories > Terminal

A **[COLOR=Blue]virtual shell[/COLOR]** is what you've been used to using after booting from the recovery mode. There are other ways to get to it that I'll show you soon.

Please open a shell. Click and drag your mouse over your command prompt, right click and select Copy. Then, paste it into your next post. Just want you to see that you can cut and paste from the shell.

Now here's a command that you can copy with your mouse from the code box below and paste it at the command prompt in your shell. After you paste it in, press enter and it will list the contents of your home directory and give you another command prompt:
```

ls -al

```See?

From now on, whenever I give you commands in a code box to enter, I want you to paste them into your shell instead of typing them. That will save us a lot of time and it will keep the typos to a minimum.

I'll wait for your comments before I post again.

---

### Post by revto on 2010-12-20
Copy/paste is so much better than writing it down and retyping. And I already get the difference. terminal=shell or terminal shell which reminds me of turtle shell.

---

### Post by Crusty Old Fart on 2010-12-20
Now we are going to make a directory on your machine for me. We'll name it: farts
Please run this command in your shell (cut and paste, please)
```

mkdir ~/farts

```

Do you know how to make a code box in a post?

---

### Post by revto on 2010-12-20
```
Is this how to add code?
```

---

### Post by revto on 2010-12-20
Sweet!

---

### Post by revto on 2010-12-20
Also I tried 

```
ls
```

for list and I can see the "farts" folder

---

### Post by Crusty Old Fart on 2010-12-20
Okay. Run the following commands, one at a time. DO NOT PASTE ANYMORE THAN ONE LINE INTO YOUR SHELL AT A TIME.
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_original
sudo cp /etc/X11/xorg.conf_original ~/farts

```

---

### Post by Syed75 on 2010-12-20
I had this problem before. I reinstalled Ubuntu and it works like a charm now. I'm not sure whats going with you....

---

### Post by revto on 2010-12-20
Ok got that. 

So we copied X11/xorg to _original then copied _original to the farts folder

---

### Post by Crusty Old Fart on 2010-12-20
To Syed75;

> **Syed75 said:**
> I had this problem before. I reinstalled Ubuntu  and it works like a charm now. I'm not sure whats going with  you....
You can satisfy your curiosity by reading this thread from the  beginning. The solution hasn't been as easy for us as it was for you.

---

### Post by Crusty Old Fart on 2010-12-20
> **revto said:**
> Ok got that. 

So we copied X11/xorg to _original then copied _original to the farts folder
Yup

---

### Post by revto on 2010-12-20
I'm catchin on a little.

Now I can say that I am qualified to use ubuntu.

Someday I may qualify to fix ubuntu

---

### Post by Crusty Old Fart on 2010-12-20
Okay, now run these commands:
```

clear
cat ~/farts/xorg.conf_original

```Then, copy the entire output of the cat command into a code box in your next post.
You may have to scroll your shell window.

---

### Post by revto on 2010-12-20
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dri2"
    Load  "dbe"
    Load  "record"
    Load  "extmod"
    Load  "dri"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "FlatPanel"              # [<bool>]
        #Option     "FPDither"               # [<bool>]
        #Option     "CrtcNumber"             # <i>
        #Option     "FPScale"                # [<bool>]
        #Option     "FPTweak"                # <i>
        #Option     "DualHead"               # [<bool>]
    Identifier  "Card0"
    Driver      "nv"
    VendorName  "nVidia Corporation"
    BoardName   "C51 [GeForce 6150 LE]"
    BusID       "PCI:0:5:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

### Post by Crusty Old Fart on 2010-12-20
Please edit your last post and put all that into a code box.

---

### Post by revto on 2010-12-20
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dri2"
    Load  "dbe"
    Load  "record"
    Load  "extmod"
    Load  "dri"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "FlatPanel"              # [<bool>]
        #Option     "FPDither"               # [<bool>]
        #Option     "CrtcNumber"             # <i>
        #Option     "FPScale"                # [<bool>]
        #Option     "FPTweak"                # <i>
        #Option     "DualHead"               # [<bool>]
    Identifier  "Card0"
    Driver      "nv"
    VendorName  "nVidia Corporation"
    BoardName   "C51 [GeForce 6150 LE]"
    BusID       "PCI:0:5:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

---

### Post by Crusty Old Fart on 2010-12-20
Well...that's the idea. But I had wanted you to edit your previous post, not make a new one. Too late now.

Next:
Please run these commands and copy the entire output into a _**code box**_ in your next post:
```

clear
lshw

```

---

### Post by revto on 2010-12-20
```
thomas@ubuntu2:~$ lshw
WARNING: you should run this program as super-user.
ubuntu2                   
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 1
          size: 1880MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          size: 2600MHz
          capacity: 2600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24 ioport:b000(size=4096) memory:fde00000-fdefffff ioport:fdb00000(size=1048576)
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25 ioport:9000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
     *-display UNCLAIMED
          description: VGA compatible controller
          product: C51 [GeForce 6150 LE]
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: latency=0
          resources: memory:fc000000-fcffffff memory:e0000000-efffffff(prefetchable) memory:fb000000-fbffffff memory:80000000-8001ffff(prefetchable)
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:11 ioport:4c00(size=64) ioport:4c40(size=64)
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: a.2
          bus info: pci@0000:00:0a.2
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fe02e000-fe02e0ff
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f400(size=16)
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:e000(size=16) memory:fe02d000-fe02dfff
     *-ide:2
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:22 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:cc00(size=16) memory:fe02c000-fe02cfff
     *-pci:2
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master cap_list
          resources: ioport:a000(size=4096) memory:fdd00000-fddfffff memory:fdc00000-fdcfffff(prefetchable)
        *-firewire
             description: FireWire (IEEE 1394)
             product: FW322/323
             vendor: Agere Systems
             physical id: 5
             bus info: pci@0000:03:05.0
             version: 70
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=24 mingnt=12
             resources: irq:19 memory:fddff000-fddfffff
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k Data/Fax Modem
             vendor: Conexant Systems, Inc.
             physical id: a
             bus info: pci@0000:03:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=32
             resources: memory:fdde0000-fddeffff ioport:ac00(size=8)
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:fe024000-fe027fff
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: 00:1a:92:40:c3:f8
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.1.101 latency=0 maxlatency=20 mingnt=1 multicast=yes
          resources: irq:23 memory:fe02b000-fe02bfff ioport:c800(size=8)
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
```

---

### Post by revto on 2010-12-20
Sorry, output would be:

```
WARNING: you should run this program as super-user.
ubuntu2                   
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 1
          size: 1880MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          size: 2600MHz
          capacity: 2600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24 ioport:b000(size=4096) memory:fde00000-fdefffff ioport:fdb00000(size=1048576)
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25 ioport:9000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
     *-display UNCLAIMED
          description: VGA compatible controller
          product: C51 [GeForce 6150 LE]
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: latency=0
          resources: memory:fc000000-fcffffff memory:e0000000-efffffff(prefetchable) memory:fb000000-fbffffff memory:80000000-8001ffff(prefetchable)
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:11 ioport:4c00(size=64) ioport:4c40(size=64)
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: a.2
          bus info: pci@0000:00:0a.2
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fe02e000-fe02e0ff
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f400(size=16)
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:e000(size=16) memory:fe02d000-fe02dfff
     *-ide:2
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:22 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:cc00(size=16) memory:fe02c000-fe02cfff
     *-pci:2
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master cap_list
          resources: ioport:a000(size=4096) memory:fdd00000-fddfffff memory:fdc00000-fdcfffff(prefetchable)
        *-firewire
             description: FireWire (IEEE 1394)
             product: FW322/323
             vendor: Agere Systems
             physical id: 5
             bus info: pci@0000:03:05.0
             version: 70
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=24 mingnt=12
             resources: irq:19 memory:fddff000-fddfffff
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k Data/Fax Modem
             vendor: Conexant Systems, Inc.
             physical id: a
             bus info: pci@0000:03:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=32
             resources: memory:fdde0000-fddeffff ioport:ac00(size=8)
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:fe024000-fe027fff
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: 00:1a:92:40:c3:f8
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.1.101 latency=0 maxlatency=20 mingnt=1 multicast=yes
          resources: irq:23 memory:fe02b000-fe02bfff ioport:c800(size=8)
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
```

---

### Post by Crusty Old Fart on 2010-12-20
Very good.

Now:
Please run the following commands and copy the entire output into a _**code box**_ in your next post:
```

clear
lsmod

```

---

### Post by revto on 2010-12-20
```
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_realtek   279008  1 
snd_hda_intel          25741  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
snd_seq_oss            31191  0 
softcursor              1565  1 bitblit
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
vga16fb                12757  1 
vgastate                9857  1 vga16fb
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
nouveau               515227  0 
ttm                    60847  1 nouveau
drm_kms_helper         30742  1 nouveau
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lp                      9336  0 
drm                   198948  3 nouveau,ttm,drm_kms_helper
snd_timer              23649  2 snd_pcm,snd_seq
psmouse                64576  0 
parport                37160  2 ppdev,lp
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               4918  0 
i2c_nforce2             6099  0 
i2c_algo_bit            6024  1 nouveau
edac_core              45423  0 
k8temp                  4040  0 
edac_mce_amd            9278  0 
snd                    71251  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
ohci1394               30260  0 
usb_storage            49961  0 
ieee1394               94771  1 ohci1394
forcedeth              55624  0 
pata_amd               11962  0 
sata_nv                23714  2 
```

---

### Post by Crusty Old Fart on 2010-12-20
Good.

And finally...
Please run the following commands and copy the entire output into a _**code box**_ in your next post:
```

clear
lspci -tvv

```

---

### Post by revto on 2010-12-20
```
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_realtek   279008  1 
snd_hda_intel          25741  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
snd_seq_oss            31191  0 
softcursor              1565  1 bitblit
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
vga16fb                12757  1 
vgastate                9857  1 vga16fb
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
nouveau               515227  0 
ttm                    60847  1 nouveau
drm_kms_helper         30742  1 nouveau
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lp                      9336  0 
drm                   198948  3 nouveau,ttm,drm_kms_helper
snd_timer              23649  2 snd_pcm,snd_seq
psmouse                64576  0 
parport                37160  2 ppdev,lp
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               4918  0 
i2c_nforce2             6099  0 
i2c_algo_bit            6024  1 nouveau
edac_core              45423  0 
k8temp                  4040  0 
edac_mce_amd            9278  0 
snd                    71251  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
ohci1394               30260  0 
usb_storage            49961  0 
ieee1394               94771  1 ohci1394
forcedeth              55624  0 
pata_amd               11962  0 
sata_nv                23714  2 
thomas@ubuntu2:~$ clear

thomas@ubuntu2:~$ lspci -tvv
-[0000:00]-+-00.0  nVidia Corporation C51 Host Bridge
           +-00.1  nVidia Corporation C51 Memory Controller 0
           +-00.2  nVidia Corporation C51 Memory Controller 1
           +-00.3  nVidia Corporation C51 Memory Controller 5
           +-00.4  nVidia Corporation C51 Memory Controller 4
           +-00.5  nVidia Corporation C51 Host Bridge
           +-00.6  nVidia Corporation C51 Memory Controller 3
           +-00.7  nVidia Corporation C51 Memory Controller 2
           +-02.0-[0000:01]--
           +-04.0-[0000:02]--
           +-05.0  nVidia Corporation C51 [GeForce 6150 LE]
           +-09.0  nVidia Corporation MCP51 Host Bridge
           +-0a.0  nVidia Corporation MCP51 LPC Bridge
           +-0a.1  nVidia Corporation MCP51 SMBus
           +-0a.2  nVidia Corporation MCP51 Memory Controller 0
           +-0b.0  nVidia Corporation MCP51 USB Controller
           +-0b.1  nVidia Corporation MCP51 USB Controller
           +-0d.0  nVidia Corporation MCP51 IDE
           +-0e.0  nVidia Corporation MCP51 Serial ATA Controller
           +-0f.0  nVidia Corporation MCP51 Serial ATA Controller
           +-10.0-[0000:03]--+-05.0  Agere Systems FW322/323
           |                 \-0a.0  Conexant Systems, Inc. HSF 56k Data/Fax Modem
           +-10.1  nVidia Corporation MCP51 High Definition Audio
           +-14.0  nVidia Corporation MCP51 Ethernet Controller
           +-18.0  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
           +-18.1  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
           +-18.2  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
           \-18.3  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
```

---

### Post by revto on 2010-12-20
Sorry,

```
-[0000:00]-+-00.0  nVidia Corporation C51 Host Bridge
           +-00.1  nVidia Corporation C51 Memory Controller 0
           +-00.2  nVidia Corporation C51 Memory Controller 1
           +-00.3  nVidia Corporation C51 Memory Controller 5
           +-00.4  nVidia Corporation C51 Memory Controller 4
           +-00.5  nVidia Corporation C51 Host Bridge
           +-00.6  nVidia Corporation C51 Memory Controller 3
           +-00.7  nVidia Corporation C51 Memory Controller 2
           +-02.0-[0000:01]--
           +-04.0-[0000:02]--
           +-05.0  nVidia Corporation C51 [GeForce 6150 LE]
           +-09.0  nVidia Corporation MCP51 Host Bridge
           +-0a.0  nVidia Corporation MCP51 LPC Bridge
           +-0a.1  nVidia Corporation MCP51 SMBus
           +-0a.2  nVidia Corporation MCP51 Memory Controller 0
           +-0b.0  nVidia Corporation MCP51 USB Controller
           +-0b.1  nVidia Corporation MCP51 USB Controller
           +-0d.0  nVidia Corporation MCP51 IDE
           +-0e.0  nVidia Corporation MCP51 Serial ATA Controller
           +-0f.0  nVidia Corporation MCP51 Serial ATA Controller
           +-10.0-[0000:03]--+-05.0  Agere Systems FW322/323
           |                 \-0a.0  Conexant Systems, Inc. HSF 56k Data/Fax Modem
           +-10.1  nVidia Corporation MCP51 High Definition Audio
           +-14.0  nVidia Corporation MCP51 Ethernet Controller
           +-18.0  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
           +-18.1  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
           +-18.2  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
           \-18.3  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
```

---

### Post by Crusty Old Fart on 2010-12-20
That's it...But, it would have been better for you to make the correction to your previous post by editing it. There's an edit button at the lower right hand corner for you on every one of your posts. Did you know that?

---

### Post by Crusty Old Fart on 2010-12-20
Now we need to make a folder in which we can do some experimentation.

Please run this command:
```

mkdir ~/playpen

```

---

### Post by revto on 2010-12-20
Yeah, I couldn't get it to edit a phrase into a code line (now I can do it manually) and I am used to making a paper trail for work and I go back and look at the posts and it helps me remember where and how I made mistakes so I can not do that in the future. I am trying to teach myself ubuntu and with your help I am starting to get it

---

### Post by revto on 2010-12-20
playpen engaged

---

### Post by Crusty Old Fart on 2010-12-20
Yah...going back and editing them now wouldn't be good. My comments wouldn't make sense.

Please run the following commands:
```

cd playpen
touch homework.txt

```

---

### Post by revto on 2010-12-20
I'm back at the "thomas@ubuntu2:~/playpen$" menu

---

### Post by Crusty Old Fart on 2010-12-20
Good.

Run the following command to close your shell:
```

exit

```Now, we're going to open homework.txt in a gedit window from your Places on the left side of your upper desktop panel with the following click sequence:

Places > Home Folder > {Double Click} playpen > {Double Click} homework.txt

Let me know when you have the empty file: homework.txt opened in a gedit window.

---

### Post by revto on 2010-12-20
open and ready

---

### Post by Crusty Old Fart on 2010-12-20
Now we're going to put some text in it for you to play with later.

Copy everything in the following code box and paste it into your homework.txt file:
```

Learning vi or vim is not easy. But it doesn't have to be that difficult, either. It is, in any case, faster,     more powerful, and more productive than editing with any other editor, so you would do very well in investing the     time and effort to learn it.
           Being a vi lover myself, I came up with the idea of providing a graphical cheat sheet for those learning vi or vim,     and I also found out it was a very good way to structure a tutorial. Here are the results for your learning enjoyment     (or your colleagues').
           By the way, I recently published the definitive article explaining why vi/vim editing is so much better     than regular editing.

```Then, save and close the homework.txt file. And open a shell.

---

### Post by revto on 2010-12-20
done, done, and done

---

### Post by Crusty Old Fart on 2010-12-20
Get into your playpen with the following command:
```

cd playpen

```

Open the homework.txt file for editing with the following command:
```

vi h*

```

Close the editor by issuing the following command inside the editor. Don't copy it from the code box. Type it in. The command will appear at the bottom of the window:
```

:q

```

---

### Post by revto on 2010-12-20
k, ready to go

---

### Post by Crusty Old Fart on 2010-12-20
I need a little more information:

Please run the following commands and post the entire output in a code box in your next post:
```

clear
xrandr -q --verbose

```

---

### Post by revto on 2010-12-20
[QUOTE=Crusty Old Fart;10262382]Yah...going back and editing them now wouldn't be good. My comments wouldn't make sense.[QUOTE]

I won't enter any commands, just looking at how we made it to here and what the commands were by looking at them but more importantly figuring out what the commands are and why they were used in that order. I have a passion to find out how things work and why, which is what I do for a living, and not being able to figure things out for myself makes me want to know more. Ubuntu is one of these things

---

### Post by revto on 2010-12-20
I should be at a "thomas@ubuntu2:$" prompt and not at the "thomas@ubuntu2:~/playpen$", correct?

---

### Post by Crusty Old Fart on 2010-12-20
You can learn a lot from the manpages that you can access from the shell.
To see a manpage for any command, you just type: man command
You know about the list (ls) command. You can read its manpage from the shell like this:
```

man ls

```

---

### Post by Crusty Old Fart on 2010-12-20
> **revto said:**
> I should be at a "thomas@ubuntu2:$" prompt and not at the "thomas@ubuntu2:~/playpen$", correct?
It doesn't matter.

---

### Post by revto on 2010-12-20
```
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 (0x128) normal (normal) 0mm x 0mm
    Identifier: 0x127
    Timestamp:  260300
    Subpixel:   unknown
    Clones:    
    CRTC:       0
    CRTCs:      0
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
  800x600 (0x128)   28.8MHz *current
        h: width   800 start    0 end    0 total  800 skew    0 clock   36.0KHz
        v: height  600 start    0 end    0 total  600           clock   60.0Hz
  800x600 (0x129)   26.9MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   33.6KHz
        v: height  600 start    0 end    0 total  600           clock   56.0Hz
  640x480 (0x12a)   18.4MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   28.8KHz
        v: height  480 start    0 end    0 total  480           clock   60.0Hz
  400x300 (0x12b)    7.2MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   18.0KHz
        v: height  300 start    0 end    0 total  300           clock   60.0Hz
  400x300 (0x12c)    6.7MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   16.8KHz
        v: height  300 start    0 end    0 total  300           clock   56.0Hz
  320x240 (0x12d)    4.6MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   14.4KHz
        v: height  240 start    0 end    0 total  240           clock   60.0Hz
```

---

### Post by Crusty Old Fart on 2010-12-20
Thank you very much, Thomas.

My homework assignment is to study the information we collected tonight and figure out how to configure your graphics card.

Your homework assignment is to: **[[COLOR=Blue]Learn the VI editor[/COLOR]]("http://www.rightrepublic.com/loader.php?tnv=main&lnv=vied&do=off&clr=sage&bclr=sea&tclr=sea&gclr=sea&fclr=sage&frm=off&bdr=3&pg=vimchtsht&cki=")**

You have a file: homework.txt that you can experiment on in your ~/playpen.

Here's the **[[COLOR=Blue]Cheat Sheet[/COLOR]]("http://www.viemu.com/a_vi_vim_graphical_cheat_sheet_tutorial.html")**

Study hard, you'll love it!

I have to go now. It's been a pleasure as always,

Fartagus Magnus

---

### Post by Crusty Old Fart on 2010-12-21
Thomas:

I've changed the links in the previous post, and in my signature, to provide more resources for learning VI. That should make your homework a little easier. The external links in the left navigation menu at the website for **[[COLOR=Blue]Learn the VI editor[/COLOR]]("http://www.rightrepublic.com/loader.php?tnv=main&lnv=vied&do=off&clr=sage&bclr=sea&tclr=sea&gclr=sea&fclr=sage&frm=off&bdr=3&pg=vimchtsht&cki=")** are all very good and range from help for beginners all the way up to experts. In fact, they are some of the best VI Editor links I've ever seen. However, the website is a little weird. I've played around with it and still can't figure out what those guys over there are all about. But, their computer section is helpful.

Also, I've gone back and studied this thread from the very beginning and now suspect that I may have discovered how to get your integrated graphics card working properly. So, after I get some much needed sleep, I'd like to run a few tests to find out if my suspicions have any merit to them.

May the farts be with you, especially considering all the beans you've been awarded,

Fart Fader

---

### Post by revto on 2010-12-21
I am ready to run the tests if you want, I'm still reading about vi and vim

---

### Post by Crusty Old Fart on 2010-12-21
Okay...but for the testing I want to do, I need to wait until both of us are online at the same time. So, hopefully you'll see this come into your email and show up here.

---

### Post by revto on 2010-12-21
Just let me know when you are ready, I should be here still reading

---

### Post by Crusty Old Fart on 2010-12-21
Okay...There's a chance that what I'm about to do may break your system. So, I need to have you signed into this forum with **_both_** of your computers.

Please run the following command in a shell on the computer we're trying to fix and post the output from it.
```

ls -l ~/farts

```

---

### Post by revto on 2010-12-21
```
total 4
-rw-r--r-- 1 root root 2699 2010-12-20 19:09 xorg.conf_original
```

---

### Post by Crusty Old Fart on 2010-12-21
Thanks.

Now run the following commands and post the output from the second one:
```

sudo rm /etc/X11/xorg.conf
ls -l /etc/X11/xorg.*

```

---

### Post by revto on 2010-12-21
```
-rw-r--r-- 1 root root  269 2010-12-19 21:00 /etc/X11/xorg.conf.failsafe
-rw-r--r-- 1 root root 2699 2010-12-20 19:07 /etc/X11/xorg.conf_original

```

---

### Post by Crusty Old Fart on 2010-12-21
Please perform a normal reboot using the default generic kernal. DO NOT add nomodeset or any other kernel options.

Watch for the SMB1 probe error. I'm hoping it won't show up.

Please let me know what happens. (you may need to post using your other computer).

---

### Post by revto on 2010-12-21
I get the "error probing SMB1" code again in the same place on startup

---

### Post by Crusty Old Fart on 2010-12-21
> **revto said:**
> I get the "error probing SMB1" code again in the same place on startup
...and a black screen with no way to get beyond it without rebooting?

---

### Post by revto on 2010-12-21
Correct. And I have been trying to get in using nomodeset and I only go to a virtual shell.

---

### Post by Crusty Old Fart on 2010-12-21
> **revto said:**
> Correct. And I have been trying to get in using nomodeset and I only go to a virtual shell.
Rod Rammit! That sucks. I think my theory just got blown.

Please type the following command into your virtual shell:
```

[SIZE=4]sudo cp /etc/X11/xorg.conf_original /etc/X11/xorg.conf[/SIZE]

```Remember that upper case X in X11.

---

### Post by revto on 2010-12-21
Back at my thomas@ubuntu2:~$ prompt, with no errors and I will never forget the capitol X in X11 again

---

### Post by Crusty Old Fart on 2010-12-21
Okay, good.

Now reboot with the default kernel but ADD the nomodeset option, log in to the gnome desktop and post back when you get there.

---

### Post by revto on 2010-12-21
I tried (with my fingers crossed) doing nothing but got the SMB1 code, when I edited the kernal , I also got a SMB1 code but the screen flashed a few times and the login poped up. I am back on the pavilion comp that needs all the help, I am just gonna call it the ubuntu2 comp since thats what I named it

---

### Post by Crusty Old Fart on 2010-12-21
Good.

The rest of my posts tonight will be my Christmas present to you.

Stay on ubuntu2 unless I tell you differently.

Run the following command in a shell:
```

sudo gedit /etc/default/grub

```Then, in the gedit window that pops up, find the line that says:
```

GRUB_CMDLINE_LINUX_DEFAULT=""

```and paste the following line in its place.
```

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

```Save the file and close the gedit window.
Run the following command in your shell:
```

sudo update-grub

```Lastly, run the following commands in your shell and post the output:
```

clear
cat /etc/default/grub

```

---

### Post by revto on 2010-12-21
After the last command I get
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by Crusty Old Fart on 2010-12-21
Looks like you did everything perfectly.

Now, when you reboot, you should NOT have to touch the machine until it serves up a gnome desktop login screen.

Try it out.

---

### Post by revto on 2010-12-21
I got another SMB1 message but it loaded to the login window and I am in gnome without touching the comp upon restart! Thats making progress!

---

### Post by Crusty Old Fart on 2010-12-21
Please answer the following questions:

[LIST=1]
[*]Your screen resolution is 800 x 600. Is your monitor capable of a higher resolution?
[*]Is your monitor a flat screen display or is it a CRT?
[/LIST]

---

### Post by revto on 2010-12-21
I have a dell flatscreen monitor and it does 1024 x 768 on the other 10,04 rig but I thought it went higher than that. It definitely is not high def though. 

I looked it up and it says it can only go to 1280 x 1024

---

### Post by Crusty Old Fart on 2010-12-21
> **revto said:**
> I have a dell flatscreen monitor and it does 1024 x  768 on the other 10,04 rig but I thought it went higher than that. It  definitely is not high def though. 

I looked it up and it says it can only go to 1280 x 1024Okay. Thank you.

We definitely need to drive that monitor much better than we are with the NV driver that the system is presently using. The default nouveau driver is SO MUCH BETTER than the NV driver. But, I think the SMB1 probe crash is preventing the system from using it, which may also be the reason why you can't install from the Live CD. I have to study up on a few more things before finishing up my next plan of attack.

Several posts back, when we first got gnome running, I asked you to resist the temptation to experiment because we had finally gotten the system functional enough for the heavy lifting that I was getting it ready for. We did most of that heavy lifting by having you post output from all those commands the other day.

So, now I'm going to lift the experimentation warning a bit and encourage you to play with ubuntu2 as much as you want. If you brick the OS so badly that we have to zero write the entire master boot record, reinstall, and update the packages again...no big fat problem. We know how to do all that now and it sure as hell won't take 250 posts to get it done.

The VI editor works in your shell. The safest way to play with it is to stay in your playpen when you're experimenting. In other words, your command prompt should be **[COLOR=Blue]thomas@ubuntu2:~/playpen$[/COLOR]**

The homework.txt file is in there for you to practice with the VI editor. It's just a bunch of text that we threw in there from a website. If you completely destroy it, it's okay.

I showed you how to get into your playpen and open the homework.txt file with the VI editor back in [B][[COLOR=Red]Post #220[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10262458&postcount=220")
[/B]
For the rest of this year, I won't have as much time to spend on this forum as I have been spending recently. I'll pop in every once in a while, but my availability is going to be limited during the holidays.

That's all I have for tonight.

Merry Christmas to you and all your loved ones.
Have fun learning.

Crusty

---

### Post by revto on 2010-12-21
Thank you for all of your help, it has been a hell of an adventure with more to pursue, I should be around somewhere, so when you find time to post, go for it.

Merry Christmas to you and all of yours,

Thomas

---

### Post by Crusty Old Fart on 2010-12-22
We're ready to install a driver for your onboard graphics chipset now.

---

### Post by revto on 2010-12-22
Lead the way!

---

### Post by Crusty Old Fart on 2010-12-23
Before we get started, we need to do a few things that will allow us to reverse any changes we make so we can get the system back to where it is now if things go wrong.

So, please download the file from this link:
[https://launchpad.net/%7Exorg-edgers/+archive/ppa/+files/ppa-purge_0.2.6%7Ekarmic_all.deb](https://launchpad.net/%7Exorg-edgers/+archive/ppa/+files/ppa-purge_0.2.6%7Ekarmic_all.deb)
and save it in the ~/farts directory.

After you've done that, please post the output from this command:
```

ls -l ~/farts

```

---

### Post by revto on 2010-12-23
Ok, I am feeling pretty dumb right now. I have downloaded it and cannot transfer the file to farts, cannot download it to farts, cannot copy and paste or drag and drop. Do I transfer it in a shell?

---

### Post by Crusty Old Fart on 2010-12-23
Run the following command in a shell:
```

ls -l ~/Downloads

```
If you get any output, please post it.

---

### Post by Crusty Old Fart on 2010-12-23
For what we're doing tonight, you need to be posting from ubuntu2.

---

### Post by revto on 2010-12-23
```
total 4
-rw-r--r-- 1 thomas thomas 3432 2010-12-23 01:22 ppa-purge_0.2.6~karmic_all.deb
```

---

### Post by Crusty Old Fart on 2010-12-23
Okay...is that output from your ubuntu2 computer?

---

### Post by revto on 2010-12-23
Yes

---

### Post by Crusty Old Fart on 2010-12-23
Good. Thanks.

We'll just leave the file where it is in the Downloads directory for now.

The rest of what we need to do tonight won't take very long and hopefully, everything will go well.

Now we need to remove the configuration files that we made that use the NV driver.
Please run the following commands from your shell and post the output from the last one:
```

sudo rm /etc/X11/xorg.conf
sudo rm /etc/X11/xorg.conf_original
ls -l /etc/X11

```

---

### Post by revto on 2010-12-23
```
total 76
drwxr-xr-x 2 root root  4096 2010-12-18 23:43 app-defaults
drwxr-xr-x 2 root root  4096 2010-12-18 23:43 cursors
-rw-r--r-- 1 root root    14 2010-12-18 23:44 default-display-manager
drwxr-xr-x 6 root root  4096 2010-12-18 23:37 fonts
-rw-r--r-- 1 root root 17394 2009-12-03 05:56 rgb.txt
lrwxrwxrwx 1 root root    13 2010-12-18 23:19 X -> /usr/bin/Xorg
drwxr-xr-x 3 root root  4096 2010-12-18 23:42 xinit
drwxr-xr-x 2 root root  4096 2010-04-15 08:12 xkb
-rw-r--r-- 1 root root   269 2010-12-21 20:30 xorg.conf.failsafe
-rwxr-xr-x 1 root root   709 2010-04-01 07:19 Xreset
drwxr-xr-x 2 root root  4096 2010-12-18 23:18 Xreset.d
drwxr-xr-x 2 root root  4096 2010-12-18 23:18 Xresources
-rwxr-xr-x 1 root root  3730 2010-04-01 07:07 Xsession
drwxr-xr-x 2 root root  4096 2010-12-19 19:00 Xsession.d
-rw-r--r-- 1 root root   265 2008-07-01 13:41 Xsession.options
-rw------- 1 root root   601 2010-12-18 23:18 Xwrapper.config
```

---

### Post by Crusty Old Fart on 2010-12-23
Good.

Next, we need to remove the nouveau driver.
Please run the following command and let me know when you're done.
```

sudo apt-get --purge remove xserver-xorg-video-nouveau

```

---

### Post by revto on 2010-12-23
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-24-generic linux-headers-2.6.32-24
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xserver-xorg-video-all* xserver-xorg-video-nouveau*
0 upgraded, 0 newly installed, 2 to remove and 7 not upgraded.
After this operation, 328kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 148436 files and directories currently installed.)
Removing xserver-xorg-video-all ...
Removing xserver-xorg-video-nouveau ...
Processing triggers for man-db ...
```

ready

---

### Post by Crusty Old Fart on 2010-12-23
Okay...now we need to add the PPA.
Please run the following command and let me know when you're done.
```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

```

---

### Post by revto on 2010-12-23
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: public key "Launchpad PPA for Ubuntu-X" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

```

ready

---

### Post by Crusty Old Fart on 2010-12-23
Great.

Now we'll install the Nvidia driver.
Please run the following command and let me know when you're done. Make sure to copy this entire command before you hit the enter key after you paste it.
```

sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

```

---

### Post by revto on 2010-12-23
All done and no errors. I can post the results if you want.

---

### Post by Crusty Old Fart on 2010-12-23
Excellent.

Now, from the System menu on the left side of your desktop's upper panel, go to System > Administration > Hardware Drivers and make sure "Nvidia current" is activated.

Let me know how this goes.

---

### Post by revto on 2010-12-23
When I go there I have 3 choices, NVIDIA accelerated graphics driver version 173, 96 and version current [recommended]. the version current [recommended] is the one selected

---

### Post by Crusty Old Fart on 2010-12-23
That's perfect.

Now for the moment we've been waiting for...THE SMOKE TEST!

Reboot with your default settings just the way they are and watch the show. Hopefully, after you initiate the reboot process, you won't have to touch the computer until the gnome login screen shows up and you won't see any reports of there being an SMB1 probing error.

Post back here and let me know if you're monitor comes up with a higher resolution.

---

### Post by revto on 2010-12-23
When I logged back in I checked out system> preferences > monitors

and I got 

It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by revto on 2010-12-23
also I got the SMB1 error again but it came up without any action from me

---

### Post by Crusty Old Fart on 2010-12-23
Did you get a higher resolution?

---

### Post by Crusty Old Fart on 2010-12-23
> **revto said:**
> When I logged back in I checked out system> preferences > monitors

and I got 

It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
We can deal with this in a little while.
Right now, I just want to know if your monitor gave you a higher resolution all by itself when you rebooted. Please answer that question.

---

### Post by revto on 2010-12-23
When I choose system> preferences> monitors I get the error:

It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

if I choose 'yes' I get:

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

Post 276 question: no higher resolution still 800 x 600 max

---

### Post by Crusty Old Fart on 2010-12-23
Please don't play around with: system> preferences> monitors yet.

I was asking about the resolution on boot to determine if we need to reboot WITHOUT the nomodeset option.

It would help if you don't get ahead of me while we're working through this stuff.

Please reboot the computer. Get into the GRUB menu, edit the first kernel in the list by pressing "e" and then remove the nomodeset option and press Ctrl-x to continue booting.

Post back and tell me one thing: Did your monitor boot with a higher resolution all by itself this time.

---

### Post by revto on 2010-12-23
I am back after a reset and the "nomodeset" deleted, all seemed fine on startup. Same video resolution

---

### Post by Crusty Old Fart on 2010-12-23
Very good...this is the first time we've ever gotten to the desktop WITHOUT the nomodeset option.

Now take a look at system> preferences> monitors

Does it still give you the same error?

---

### Post by revto on 2010-12-23
yes I still get both of the errors

---

### Post by Crusty Old Fart on 2010-12-23
Thanks.

Run the following command from a shell:
```

sudo nvidia-xconfig

```

I'll tell you how to restart X in my next post

---

### Post by revto on 2010-12-23
```
WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'
```

---

### Post by Crusty Old Fart on 2010-12-23
Good...Now we need to restart X

From the System menu on the left side of your upper desktop panel, go to:
System > Preferences > Keyboard
Click on the Layouts tab.
Click on the Options button at the lower left of the window.
Click on the plus sign (+) to the left of the list item: Key sequence to kill the X server
Put a check in the box to the left of: Control + Alt + Backspace
Click the Close button at the lower right corner of this window
Click the Close button at the lower right corner of the remaining window

From now on, you'll be able to use the key combination: Ctrl-Alt-Backspace to restart X.
So, go ahead and press Ctrl-Alt-Backspace.

---

### Post by Crusty Old Fart on 2010-12-23
Now...see if you can use:  system> preferences> monitors 
to change your resolution.

You may need to reboot for the changes to take effect.

I recommend rebooting WITHOUT the nomodeset option for the time being.

---

### Post by revto on 2010-12-23
Post 284 went by fine with no errors. When I rebooted I now have 640 x 480 resolution max.
When I press  system> preferences> monitors, I get an error:
It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead? 
with a yes and no. if I press no it takes me to the monitor window with only 2 resolutions, 640 x 480 and 320 x 240
if yes I go to a Nvidia X Server settings: of which I just tried to close out of which is tricky. the screen is too big for my resolution but shows part of the window. any time I click on the window or buttons it moves around and makes it difficult to just click on the quit button to escape. (when I hit the quit button, it moved the window and the quit button is off the screen, then I move the window to show the quit button and press it and the window moves again. eventually the quit button is barely exposed at the bottom and I can quit it)

---

### Post by Crusty Old Fart on 2010-12-23
Can you open a shell and post the output from the following command:
```

xrandr -q --verbose

```

---

### Post by revto on 2010-12-23
```
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 (0x1b4) normal (normal) 0mm x 0mm
    Identifier: 0x1b3
    Timestamp:  2089818
    Subpixel:   unknown
    Clones:    
    CRTC:       0
    CRTCs:      0
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
  640x480 (0x1b4)   15.4MHz *current
        h: width   640 start    0 end    0 total  640 skew    0 clock   24.0KHz
        v: height  480 start    0 end    0 total  480           clock   50.0Hz
  320x240 (0x1b5)    3.9MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   12.2KHz
        v: height  240 start    0 end    0 total  240           clock   51.0Hz

```

---

### Post by Crusty Old Fart on 2010-12-23
Thank you.

Please post the output from the following command:
```

sudo cat /etc/X11/xorg.conf

```

---

### Post by revto on 2010-12-23
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.29  (buildmeister@swio-display-x86-rhel47-04.nvidia.com)  Wed Dec  8 12:27:39 PST 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Crusty Old Fart on 2010-12-23
Thank you.

Hang tough while I study that information for a few minutes. I'll be back shortly. We are getting very close to marking this thread as [SOLVED].

---

### Post by Crusty Old Fart on 2010-12-23
> **Bananas1234 said:**
> nerds :D
Oh man...you have no idea...Geekus Maximus

Thomas:

Please enter the following command and post the output:
```
cvt 1280 1024
```

---

### Post by ImDougy on 2010-12-23
my girlfriend called us nerds :grin: u scared a guy away on another thread :P keep it up laury

---

### Post by Crusty Old Fart on 2010-12-23
> **ImDougy said:**
> my girlfriend called us nerds :grin: u scared a guy away on another thread :P keep it up laury
Wo!...A nerd with a girlfriend??? I didn't know that was even possible. I wonder if I might get one of those for Christmas. Just for the day, you know? I don't think I'd know what to do with her for the night.:cool:

---

### Post by revto on 2010-12-23
```
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```

---

### Post by owise1 on 2010-12-23
Hi Revto and Crusty old Fart - have been enjoying reading this long and twisted tail of nvidia woe!

Revto - from one of your earlier posts you appears to have a problem with the nvidia configuration tool - too big for that crap resolution that you have at the moment?  To see all the window you can hold down the alt key while clicking on the window (when not maximised and anywhere within) and then drag the window around so that you can see the other options available.  This will let you push the window outside the desktop viewable area.

Cheers

Dave

---

### Post by Crusty Old Fart on 2010-12-23
Thanks. Let's do one more:
Please post the output from this command:
```

cvt 1024 768

```

---

### Post by revto on 2010-12-23
```
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
```

---

### Post by Crusty Old Fart on 2010-12-23
> **owise1 said:**
> Hi Revto and Crusty old Fart - have been enjoying reading this long and twisted tail of nvidia woe!

Revto - from one of your earlier posts you appears to have a problem with the nvidia configuration tool - too big for that crap resolution that you have at the moment?  To see all the window you can hold down the alt key while clicking on the window (when not maximised and anywhere within) and then drag the window around so that you can see the other options available.  This will let you push the window outside the desktop viewable area.

Cheers

Dave
Thank you, Dave. I never knew. :cool:

---

### Post by Crusty Old Fart on 2010-12-23
> **revto said:**
> ```
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
```
Thanks Thomas.

Here's the deal. In order to configure your settings, I will be building you a new configuration file so that once we get it configured, the configuration will persist.

Before I do that, we can try to make your life a little easier by reconfiguring your resolution for this session. Would you like to try that, and if so, would you prefer a resolution of 1280 x 1024, or 1024 x768?

---

### Post by revto on 2010-12-23
Heck yeah I wanna try, this 640 is horrible. I would love to have 1024. That would be great

---

### Post by Crusty Old Fart on 2010-12-23
> **revto said:**
> Heck yeah I wanna try, this 640 is horrible. I would love to have 1024. That would be great
I'm assuming you mean 1024 x 768 instead of 1280 x 1024 -- See, there's a 1024 in both of them. Which one?

---

### Post by revto on 2010-12-23
Woops. 1024 x 768 would be great.

---

### Post by Crusty Old Fart on 2010-12-23
> **revto said:**
> Woops. 1024 x 768 would be great.
Okay, I need some more information.
Please run the following command and post the output:
```

ls -l /var/log | grep X

```

---

### Post by revto on 2010-12-23
```
-rw-r--r-- 1 root              root   13678 2010-12-23 18:23 Xorg.0.log
-rw-r--r-- 1 root              root   12855 2010-12-23 13:45 Xorg.0.log.old
-rw-r--r-- 1 root              root   39375 2010-12-21 20:30 Xorg.1.log
-rw-r--r-- 1 root              root   39375 2010-12-21 20:25 Xorg.1.log.old
-rw-r--r-- 1 root              root   39375 2010-12-21 20:30 Xorg.2.log
-rw-r--r-- 1 root              root   39375 2010-12-21 20:25 Xorg.2.log.old
-rw-r--r-- 1 root              root   39375 2010-12-21 20:30 Xorg.3.log
-rw-r--r-- 1 root              root   39375 2010-12-21 20:25 Xorg.3.log.old
-rw-r--r-- 1 root              root   39375 2010-12-21 20:30 Xorg.4.log
-rw-r--r-- 1 root              root   39375 2010-12-21 20:25 Xorg.4.log.old
-rw-r--r-- 1 root              root   39375 2010-12-21 20:30 Xorg.5.log
-rw-r--r-- 1 root              root   39375 2010-12-21 20:25 Xorg.5.log.old
-rw-r--r-- 1 root              root   36973 2010-12-21 20:30 Xorg.failsafe.log
-rw-r--r-- 1 root              root   36973 2010-12-21 20:25 Xorg.failsafe.log.old
```

---

### Post by Crusty Old Fart on 2010-12-23
Perfect. Now I need you to run this next command and post the output. There will be a LOT of output, so make sure you get it all:
```

sudo cat /var/log/Xorg.0.log

```

---

### Post by revto on 2010-12-23
```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux ubuntu2 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-26-generic root=UUID=c2f29bda-9e2a-4a77-8406-b9c1048dfda8 ro nomodeset
Build Date: 10 November 2010  11:25:53AM
xorg-server 2:1.7.6-2ubuntu7.4 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 23 13:45:56 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:0:5:0) 10de:0241:103c:2a34 nVidia Corporation C51 [GeForce 6150 LE] rev 162, Mem @ 0xfc000000/16777216, 0xe0000000/268435456, 0xfb000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  260.19.29  Wed Dec  8 12:24:30 PST 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  260.19.29  Wed Dec  8 12:10:14 PST 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00@00:05:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) Dec 23 13:45:57 NVIDIA(0): Enabling RENDER acceleration
(II) Dec 23 13:45:57 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Dec 23 13:45:57 NVIDIA(0):     enabled.
(WW) Dec 23 13:45:57 NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) Dec 23 13:45:57 NVIDIA(0): NVIDIA GPU GeForce 6150 LE (C51) at PCI:0:5:0 (GPU-0)
(--) Dec 23 13:45:57 NVIDIA(0): Memory: 524288 kBytes
(--) Dec 23 13:45:57 NVIDIA(0): VideoBIOS: 05.51.28.50.38
(--) Dec 23 13:45:57 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Dec 23 13:45:57 NVIDIA(0): Connected display device(s) on GeForce 6150 LE at PCI:0:5:0
(--) Dec 23 13:45:57 NVIDIA(0):     CRT-0
(--) Dec 23 13:45:57 NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(II) Dec 23 13:45:57 NVIDIA(0): Assigned Display Device: CRT-0
(==) Dec 23 13:45:57 NVIDIA(0): 
(==) Dec 23 13:45:57 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Dec 23 13:45:57 NVIDIA(0):     will be used as the requested mode.
(==) Dec 23 13:45:57 NVIDIA(0): 
(II) Dec 23 13:45:57 NVIDIA(0): Validated modes:
(II) Dec 23 13:45:57 NVIDIA(0):     "nvidia-auto-select"
(II) Dec 23 13:45:57 NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) Dec 23 13:45:57 NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) Dec 23 13:45:57 NVIDIA(0):     from CRT-0's EDID.
(==) Dec 23 13:45:57 NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) Dec 23 13:45:57 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Dec 23 13:45:57 NVIDIA(0): Initialized GPU GART.
(II) Dec 23 13:45:57 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Dec 23 13:45:57 NVIDIA(0): Built-in logo is bigger than the screen.
(II) Loading extension NV-GLX
(II) Dec 23 13:45:57 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Dec 23 13:45:57 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) XKB: reuse xkmfile /var/lib/xkb/server-0C76CA335E924C2441A31FBFED02D59A89874CA6.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/event4)
(**) ImPS/2 Logitech Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Logitech Wheel Mouse: always reports core events
(**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event4"
(II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Logitech Wheel Mouse: Found relative axes
(II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
(**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Logitech Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: removing device ImPS/2 Logitech Wheel Mouse
(II) ImPS/2 Logitech Wheel Mouse: Close
(II) UnloadModule: "evdev"
(II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/event4)
(**) ImPS/2 Logitech Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Logitech Wheel Mouse: always reports core events
(**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event4"
(II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Logitech Wheel Mouse: Found relative axes
(II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
(**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Logitech Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
```

---

### Post by Crusty Old Fart on 2010-12-23
Sorry for the delay. It took me a little while to find what I needed.

Please run these three commands, one at a time, in the order shown. The first one is pretty wide. Make sure you get all of it. Unless you get some sort of errors, I don't need any output. Your screen resolution should change when you finish:
```

xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode CRT-0 1024x768
xrandr --output CRT-0 --mode 1024x768 --rate 60

```

---

### Post by revto on 2010-12-23
```
xrandr: cannot find output "CRT-0"
```

after I put in

xrandr --addmode CRT-0 1024x768

---

### Post by Crusty Old Fart on 2010-12-23
I was afraid of that. I think the first command went in. So, we only need to change the last two. Try this:
```

xrandr --addmode default 1024x768
xrandr --output default --mode 1024x768 --rate 60

```

---

### Post by revto on 2010-12-23
```
xrandr: cannot find mode "1024x768"
```

---

### Post by Crusty Old Fart on 2010-12-23
I was afraid of that too.
Try this:
```

xrandr --addmode 1024x768
xrandr --output --mode 1024x768 --rate 60

```

---

### Post by revto on 2010-12-23
```
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
```

---

### Post by Crusty Old Fart on 2010-12-23
Aaaaaaa...Nutdust!

I was afraid of that too.
Let's try this:
```

xrandr --addmode DPMS 1024x768
xrandr --output DPMS --mode 1024x768 --rate 60

```

---

### Post by revto on 2010-12-23
```
xrandr: cannot find output "DPMS"
```

---

### Post by Crusty Old Fart on 2010-12-23
Here's the damned stinkin' problem:
Your integrated graphics chipset is not finding a name for your monitor.
The log has the following errors in it:

(WW) Dec 23 13:45:57 NVIDIA(GPU-0): Unable to read EDID for display device CRT-0

(WW) Dec 23 13:45:57 NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) Dec 23 13:45:57 NVIDIA(0):     from CRT-0's EDID.


Did you use the nomodeset option when you booted the computer for this session?

---

### Post by revto on 2010-12-23
No, I thought we fixed that last night so I wouldn't have to enter it anymore. The last time I restarted I just hit restart and had no problem so I haven't used it

---

### Post by owise1 on 2010-12-23
Try  xrandr --prop to see if brings back the EDID

I had a laptop with a monitor that had a dud EDID - I was able to find a correct version after much googling and reference to the nvidia forums.  If you can find one then there is a line you can add - customEDID - to your config.

Nvidia-settings should also allow you to suck out the EDID from the monitor - you could also try the nvidia-settings tool to set the right resolution

have a look here - [http://analogbit.com/fix_nvidia_edid](http://analogbit.com/fix_nvidia_edid)

---

### Post by Crusty Old Fart on 2010-12-23
Nope...we didn't fix it. We just removed it from the grub kernel selection for ONE boot.
Let's see what happens if you do this:

Reboot
Get into the GRUB menu, the default kernel at the top should be highlighted. Press "e" to edit the kernel options, remove the nomodeset option, press Ctrl-x to continue booting.

If it doesn't boot you to gnome, you'll have to reboot again with the nomodeset option left in there.

Please let me know what happens.

---

### Post by revto on 2010-12-23
I'm back with no "nomodeset" in the kernal. I think crossing my fingers did it. (like I haven't been crossing them every time I restart)

---

### Post by Crusty Old Fart on 2010-12-23
Please post the latest  Xorg log:
```

sudo cat /var/log/Xorg.0.log

```

---

### Post by revto on 2010-12-23
```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux ubuntu2 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-26-generic root=UUID=c2f29bda-9e2a-4a77-8406-b9c1048dfda8 ro
Build Date: 10 November 2010  11:25:53AM
xorg-server 2:1.7.6-2ubuntu7.4 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 23 20:47:38 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:5:0) 10de:0241:103c:2a34 nVidia Corporation C51 [GeForce 6150 LE] rev 162, Mem @ 0xfc000000/16777216, 0xe0000000/268435456, 0xfb000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  260.19.29  Wed Dec  8 12:24:30 PST 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  260.19.29  Wed Dec  8 12:10:14 PST 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00@00:05:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) Dec 23 20:47:39 NVIDIA(0): Enabling RENDER acceleration
(II) Dec 23 20:47:39 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Dec 23 20:47:39 NVIDIA(0):     enabled.
(WW) Dec 23 20:47:39 NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) Dec 23 20:47:39 NVIDIA(0): NVIDIA GPU GeForce 6150 LE (C51) at PCI:0:5:0 (GPU-0)
(--) Dec 23 20:47:39 NVIDIA(0): Memory: 524288 kBytes
(--) Dec 23 20:47:39 NVIDIA(0): VideoBIOS: 05.51.28.50.38
(--) Dec 23 20:47:39 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Dec 23 20:47:39 NVIDIA(0): Connected display device(s) on GeForce 6150 LE at PCI:0:5:0
(--) Dec 23 20:47:39 NVIDIA(0):     CRT-0
(--) Dec 23 20:47:39 NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(II) Dec 23 20:47:39 NVIDIA(0): Assigned Display Device: CRT-0
(==) Dec 23 20:47:39 NVIDIA(0): 
(==) Dec 23 20:47:39 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Dec 23 20:47:39 NVIDIA(0):     will be used as the requested mode.
(==) Dec 23 20:47:39 NVIDIA(0): 
(II) Dec 23 20:47:39 NVIDIA(0): Validated modes:
(II) Dec 23 20:47:39 NVIDIA(0):     "nvidia-auto-select"
(II) Dec 23 20:47:39 NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) Dec 23 20:47:39 NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) Dec 23 20:47:39 NVIDIA(0):     from CRT-0's EDID.
(==) Dec 23 20:47:39 NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) Dec 23 20:47:39 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Dec 23 20:47:39 NVIDIA(0): Initialized GPU GART.
(II) Dec 23 20:47:39 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Dec 23 20:47:39 NVIDIA(0): Built-in logo is bigger than the screen.
(II) Loading extension NV-GLX
(II) Dec 23 20:47:39 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Dec 23 20:47:39 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) XKB: reuse xkmfile /var/lib/xkb/server-0C76CA335E924C2441A31FBFED02D59A89874CA6.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/event4)
(**) ImPS/2 Logitech Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Logitech Wheel Mouse: always reports core events
(**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event4"
(II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Logitech Wheel Mouse: Found relative axes
(II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
(**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Logitech Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
```

---

### Post by Crusty Old Fart on 2010-12-23
> **owise1 said:**
> Try  xrandr --prop to see if brings back the EDID

I had a laptop with a monitor that had a dud EDID - I was able to find a correct version after much googling and reference to the nvidia forums.  If you can find one then there is a line you can add - customEDID - to your config.

Nvidia-settings should also allow you to suck out the EDID from the monitor - you could also try the nvidia-settings tool to set the right resolution

have a look here - [http://analogbit.com/fix_nvidia_edid](http://analogbit.com/fix_nvidia_edid)
Thank you, Dave. I appreciate that very much.
We'll give xrandr --prop a go. And I'll check out the link. I can't build a happy xorg.conf file without getting this problem fixed.

---

### Post by revto on 2010-12-23
> **owise1 said:**
> Try  xrandr --prop to see if brings back the EDID

I had a laptop with a monitor that had a dud EDID - I was able to find a correct version after much googling and reference to the nvidia forums.  If you can find one then there is a line you can add - customEDID - to your config.

Nvidia-settings should also allow you to suck out the EDID from the monitor - you could also try the nvidia-settings tool to set the right resolution

have a look here - [http://analogbit.com/fix_nvidia_edid](http://analogbit.com/fix_nvidia_edid)

Thanks for your help. I am checking it out right now

---

### Post by Crusty Old Fart on 2010-12-23
Well, Thomas, the same errors are in that log as well.
When we ran the command: xrandr -q --verbose, it also enabled the --prop option that Dave suggested. However, there's no harm done at this point to follow his suggestion anyway.

Please post the output of this command:
```

xrandr --prop

```

---

### Post by revto on 2010-12-23
```
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0 
```

---

### Post by Crusty Old Fart on 2010-12-23
That's still no good. The graphics chipset is using "default" for the name of the monitor and feeding it the lame resolution you're getting.

Dave:
How do we do this:
 You can use nvidia-settings to get your EDID info. **[COLOR=Red]Run nvidia-settings, click on DFP-0, then click "Acquire EDID..."[/COLOR]**

---

### Post by owise1 on 2010-12-23
mine produces

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280
VGA connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x301mm
        EDID_DATA:
                00ffffffffffff0034a17019b8e00000
                330f010368261e782a6ac6a1594b9923
                174f59bfef0081800101010101010101
                010101010101302a009851002a403070
                1300782d1100001e000000ff00333335
                35434a41303537353238000000fd0037
                4b1e530e000a202020202020000000fc
                0044563139372f53420a202020200076
   1280x1024      60.0*+   75.0     59.9
   1024x768       75.1     70.1     60.0
   832x624        74.6
   800x600        72.2     75.0     60.3     56.2
   640x480        75.0     72.8     66.7     60.0
   720x400        70.1

---

### Post by owise1 on 2010-12-23
what is the make / model of the monitor?

---

### Post by Crusty Old Fart on 2010-12-23
Thomas:

Let's fix your bootloader now that you don't need nomodeset anymore.
Run this command in a shell:
```

sudo gedit /etc/default/grub

```

In the gedit window that pops up change the following line:
From this:
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

To this:
GRUB_CMDLINE_LINUX_DEFAULT=""

Save the file and close the gedit window.

Then run the following command in your shell:
```

sudo update-grub

```

---

### Post by revto on 2010-12-23
It is a Dell E176FPb

---

### Post by revto on 2010-12-23
Everything looked like it went good. I got:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

---

### Post by Crusty Old Fart on 2010-12-23
> **owise1 said:**
> what is the make / model of the monitor?
Good question. We haven't gathered that piece of information yet.

When Thomas comes back with an answer I'll add it to the red link in my signature. I've been keeping a lot of stuff in there for reference so I don't have to read this thread from the beginning so much.

---

### Post by owise1 on 2010-12-23
can you swap out the monitor??

also have you tried the nvidia config tool?

---

### Post by Crusty Old Fart on 2010-12-23
> **revto said:**
> Everything looked like it went good. I got:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

The best way to check it is to reboot, and press "e" in the GRUB menu to edit the default kernel. If you did everything right, The nomodeset option will be gone and you can press Ctrl-x to continue booting without changing anything. If it's still in there, then we have to repeat the process.

Also, when it reboots without nomodeset, do you still get the SMB1 probing error?

And finally, we're hoping you can provide the make and model number of your monitor. I remember you saying Dell, but I don't recall ever asking for the model number.

I can hardly believe this schidt. We run into a frappin' brick wall ](*,) at every turn!

---

### Post by Crusty Old Fart on 2010-12-23
> **owise1 said:**
> can you swap out the monitor??

also have you tried the nvidia config tool?
Would the nvidia config tool give us any more resolution options than are in [COLOR=Red][S]xorg.conf (Ref.: [post=10272574]Post #290[/post] or what is reported in[/S][/COLOR] our most recent Xorg.0.log file? We only have two really low resolutions in there.

Any chance you could tell us how we can  **[COLOR=Red]Run nvidia-settings, click on DFP-0, then click "Acquire EDID..."?[/COLOR]**

---

### Post by Crusty Old Fart on 2010-12-23
> **revto said:**
> It is a Dell E176FPb
Thanks...sorry I missed that. -- Added to [post=10249945]**[COLOR=Red]revto Reverence post #39[/COLOR]**[/post]

---

### Post by owise1 on 2010-12-23
My current PC has an intel video card - the older laptop with nvidia has gone to heaven and sorely missed (1600X1400 resolution)!!  The GUI tool should be under preferences>nvidia-config (will have the nvidia icon next to it) if the non-free driver is installed.  I think that Revto had trouble using it because it was larger than his visible screen hence my suggestion to use the "alt"+ click and drag suggestion.  If the EDID in the monitor is crap however I do not think that he will have much luck as that is used by the driver to get screen parameters for setting the various resolutions possible.  That is why I suggested that he swap out the monitor.

By the way I think that your (COF) ongoing support for Levto is wonderful and a great example of this community's camaraderie.

---

### Post by revto on 2010-12-23
Get ready to hate me, crusty. I totally forgot about this until tonite. I am running a KVM 2 port switch MT-270S spliter for the two computers cause I have only one monitor (flatscreen). I disconnected it and just plugged in the ubuntu2 comp and the resolution was higher than 1280 x 1024 and after login it wouldn't set the resolution and told me it was maxed out. Thats the good part. The bad (not really) is that every time we have something to try I have to shut down and hook up the other computer or plug back into this switch which brings me back to 640 x 480. Sorry I never thought of this.

---

### Post by Crusty Old Fart on 2010-12-23
> **owise1 said:**
> My current PC has an intel video card - the older laptop with nvidia has gone to heaven and sorely missed (1600X1400 resolution)!!  The GUI tool should be under preferences>nvidia-config (will have the nvidia icon next to it) if the non-free driver is installed.  I think that Revto had trouble using it because it was larger than his visible screen hence my suggestion to use the "alt"+ click and drag suggestion.  If the EDID in the monitor is crap however I do not think that he will have much luck as that is used by the driver to get screen parameters for setting the various resolutions possible.  That is why I suggested that he swap out the monitor.

By the way I think that your (COF) ongoing support for Levto is wonderful and a great example of this community's camaraderie.

Thanks, Dave. I appreciate that.

---

### Post by revto on 2010-12-23
> **owise1 said:**
> By the way I think that your (COF) ongoing support for Levto is wonderful and a great example of this community's camaraderie.

I really appreciate it too crusty, most would have long since been gone. This is the reason I keep trying with ubuntu instead of switching back to windows (that and my hatred of windows). I appreciate all of your help too, Dave. Thanks

---

### Post by Crusty Old Fart on 2010-12-23
> **revto said:**
> Get ready to hate me, crusty. I totally forgot about this until tonite. I am running a KVM 2 port switch MT-270S spliter for the two computers cause I have only one monitor (flatscreen). I disconnected it and just plugged in the ubuntu2 comp and the resolution was higher than 1280 x 1024 and after login it wouldn't set the resolution and told me it was maxed out. Thats the good part. The bad (not really) is that every time we have something to try I have to shut down and hook up the other computer or plug back into this switch which brings me back to 640 x 480. Sorry I never thought of this.

Oh ho ho...I can feeeeeeeeel the LUV!!! Can you? I gotta read that again and let it sink in!

Okay, tell you what, we have to redo a lot of stuff. the logs suck, xorg.conf sucks and God only knows what else sucks. I need to go back through this thread and gather up all the schidt that needs to be redone and put a new plan together. I'm not going to rush that job.

How about we call it a night for now so I can study up on this jazz and get back to you later?

---

### Post by Crusty Old Fart on 2010-12-23
Before I go...Did you check to see if nomodeset was really gone from the default kernel in your GRUB menu when you rebooted...AND...Did you get the SMB1 probing error (I wonder if the splitter may have had something to do with that?)

---

### Post by owise1 on 2010-12-23
lunch time for me!  Again if you can use the resolution that is provided when the monitor is plugged in directly to the PC in question then I suggest that you use the nvidia GIU tool to set up.

I guess that this follows the rule that when things go wrong that you should get the system setup in a minimal configuration first!

Just an aside - is the other PC connected to that KVM switch running a linux flavor??  If so what does its xorg look like??

bye for now

---

### Post by revto on 2010-12-23
"nomodeset" is gone from the kernal and every time for the last week I have got the SMB1 error upon restart no matter what I change, but somehow you got it to continue after that. 

I also get an error window when I log in that says something like "xorg cannot support this resolution" or something like that it is quick, I'll take a picture. It is when I log in using the spliter

---

### Post by Crusty Old Fart on 2010-12-23
> **revto said:**
> "nomodeset" is gone from the kernal and every time for the last week I have got the SMB1 error upon restart no matter what I change, but somehow you got it to continue after that. 

I also get an error window when I log in that says something like "xorg cannot support this resolution" or something like that it is quick, I'll take a picture. It is when I log in using the spliter

Maybe things aren't as mucked up as I feared they are. Can you post from ubuntu2 WITHOUT it being on the splitter?

---

### Post by revto on 2010-12-23
> **owise1 said:**
> Just an aside - is the other PC connected to that KVM switch running a linux flavor??  If so what does its xorg look like??

The other computer is my old one that I have pieced back together many times and also only runs ubuntu, I'll have to check the specs. I believe it is a 2.53g pentium 4 processor, (older than the board) Nvidia video card.
It downloaded ubuntu 8.04 and upgraded to 10.04 using the spliter with no problems at all.

---

### Post by revto on 2010-12-23
> **Crusty Old Fart said:**
> Can you post from ubuntu2 WITHOUT it being on the splitter?

No, the resolution must be set too high, the monitor says it can only handle 1280 x 1024 with that error that you see if you set it out of the monitors bounds

---

### Post by Crusty Old Fart on 2010-12-23
> **revto said:**
> The other computer is my old one that I have pieced back together many times and also only runs ubuntu, I'll have to check the specs. I believe it is a 2.53g pentium 4 processor, (older than the board) Nvidia video card.
It downloaded ubuntu 8.04 and upgraded to 10.04 using the spliter with no problems at all.
But it was probably configured BEFORE it was put on the splitter. THAT'S what we need to do to ubuntu2. Most of what I need to do now MUST be done WITHOUT ubuntu2 connected to the splitter. That's why I need to know if you can post from it when it's connected directly to the monitor.

---

### Post by revto on 2010-12-23
> **Crusty Old Fart said:**
> But it was probably configured BEFORE it was put on the splitter. THAT'S what we need to do to ubuntu2. Most of what I need to do now MUST be done WITHOUT ubuntu2 connected to the splitter. That's why I need to know if you can post from it when it's connected directly to the monitor.

No, I have used the twin computer on the splitter for years now and have installed ubuntu and windows using it on at least 5 computers and some computers had multiple installs of both (remember when I said I can wipe a drive but not fix? gives a little insight doesn't it) because I can switch to the other when something goes wrong to google a reason why. 
This is also why I didn't think of it, never had a problem until ubuntu2

---

### Post by Crusty Old Fart on 2010-12-23
> **revto said:**
> No, the resolution must be set too high, the monitor says it can only handle 1280 x 1024 with that error that you see if you set it out of the monitors bounds
We're going to need to reverse some of what we've done. We can't do it from the Live CD, but we may be able to do it while we're connected to the splitter. The nouveau driver has been removed, but maybe the NV driver is still installed. We have the original NV xorg.conf file in a couple of folders outside of /etc/X11 so maybe we can get it running again without having to go all the way back to running without being able to boot to the gnome desktop. The more I think about this, the more I begin to wonder if the simplest thing would be to start with a fresh install. It might just save us a whole lot of time. What do you think about that?

---

### Post by revto on 2010-12-23
That is very easily done. Just will take time and we may be back to the "pen and paper route".

---

### Post by owise1 on 2010-12-23
revto - with regard to the old PC with the old nvidia card - dont upgrade to 10.10 just yet as it will cream your PC.  If it is using the legacy nvidia driver then that is buggered with the new xorg 1.9.  It is being fixed but not in the main repository yet.

---

### Post by revto on 2010-12-23
> **owise1 said:**
> revto - with regard to the old PC with the old nvidia card - dont upgrade to 10.10 just yet as it will cream your PC.  If it is using the legacy nvidia driver then that is buggered with the new xorg 1.9.  It is being fixed but not in the main repository yet.

Thanks, I appreciate the info. I don't need another project until a while after I fix this one.

---

### Post by Crusty Old Fart on 2010-12-23
> **revto said:**
> That is very easily done. Just will take time and we may be back to the "pen and paper route".
Yeah...but those commands were much shorter than a lot of the more recent ones have been. Plus, we won't have to futz around nearly as much as we had been because we know exactly how to get that machine to gnome now. And...for all we know the nouveau driver might work while we're not on the splitter. My vote is for a fresh install. After that, the thing we need to be MOST careful about is keeping track of when we're on the splitter and when we aren't.

How about this:
We agree on two terms: 
**ubuntu2direct** (meaning connected directly to the monitor)
**ubuntu2split** (meaning connected to the splitter)

If you're happy with that phraseology, then whenever you're ready, go ahead an perform a fresh install using the Alternate 64-bit CD on ubuntu2direct. I'll get you back into gnome as quickly as I can.

---

### Post by revto on 2010-12-23
Do you think after we get ubuntu2 working correctly that I will be able to plug back in to the splitter and have it work correctly?

---

### Post by Crusty Old Fart on 2010-12-23
I have absolutely no idea. But was wondering the same thing. I wish you had another monitor that you could connect to your other machine and just leave the Dell monitor always connected directly to ubuntu2.

---

### Post by matt_symes on 2010-12-23
Hi

Sorry to jump on this thread, but i thought this might be pertinent and explain KVM and install problems for other readers of this thread.

KVM's and install problems. From Beginning Ubuntu Linux (at the bottom of the page)....

[http://books.google.co.uk/books?id=Tl3lxVNHRG8C&pg=PA76&lpg=PA76&dq=i'm+using+a+kvm+and+the+screen+looks+all+wrong&source=bl&ots=Rn7RJV5Zzo&sig=1zNbbu5_xujyvvBkquM_dCitiu8&hl=en&ei=fBkUTe2tA8eIhQf3zJi3Dg&sa=X&oi=book_result&ct=result&resnum=4&sqi=2&ved=0CCsQ6AEwAw#v=onepage&q=i'm%20using%20a%20kvm%20and%20the%20screen%20looks%20all%20wrong&f=false](http://books.google.co.uk/books?id=Tl3lxVNHRG8C&pg=PA76&lpg=PA76&dq=i'm+using+a+kvm+and+the+screen+looks+all+wrong&source=bl&ots=Rn7RJV5Zzo&sig=1zNbbu5_xujyvvBkquM_dCitiu8&hl=en&ei=fBkUTe2tA8eIhQf3zJi3Dg&sa=X&oi=book_result&ct=result&resnum=4&sqi=2&ved=0CCsQ6AEwAw#v=onepage&q=i'm%20using%20a%20kvm%20and%20the%20screen%20looks%20all%20wrong&f=false)

Great thread. It's like a novel.

Kind regards

---

### Post by revto on 2010-12-23
> **matt_symes said:**
> Hi

Sorry to jump on this thread, but i thought this might be pertinent and explain KVM and install problems for other readers of this thread.

KVM's and install problems. From Beginning Ubuntu Linux (at the bottom of the page)....

[http://books.google.co.uk/books?id=Tl3lxVNHRG8C&pg=PA76&lpg=PA76&dq=i'm+using+a+kvm+and+the+screen+looks+all+wrong&source=bl&ots=Rn7RJV5Zzo&sig=1zNbbu5_xujyvvBkquM_dCitiu8&hl=en&ei=fBkUTe2tA8eIhQf3zJi3Dg&sa=X&oi=book_result&ct=result&resnum=4&sqi=2&ved=0CCsQ6AEwAw#v=onepage&q=i'm%20using%20a%20kvm%20and%20the%20screen%20looks%20all%20wrong&f=false]("http://books.google.co.uk/books?id=Tl3lxVNHRG8C&pg=PA76&lpg=PA76&dq=i%27m+using+a+kvm+and+the+screen+looks+all+wrong&source=bl&ots=Rn7RJV5Zzo&sig=1zNbbu5_xujyvvBkquM_dCitiu8&hl=en&ei=fBkUTe2tA8eIhQf3zJi3Dg&sa=X&oi=book_result&ct=result&resnum=4&sqi=2&ved=0CCsQ6AEwAw#v=onepage&q=i%27m%20using%20a%20kvm%20and%20the%20screen%20looks%20all%20wrong&f=false")

Great thread. It's like a novel.

Kind regards

I'm going to have to leave that one with you crusty, I can only see the top of it and I cannot scroll down to see a thread

---

### Post by Crusty Old Fart on 2010-12-23
> **matt_symes said:**
> Hi...

Great thread. It's like a novel.

Kind regards
Welcome to the revto and Crusty horror story. Becoming more a tome than a novel with every passing post.

---

### Post by Crusty Old Fart on 2010-12-23
> **revto said:**
> I'm going to have to leave that one with you crusty, I can only see the top of it and I cannot scroll down to see a thread
It's hosed for me too. But I have most of the google domain blocked.

---

### Post by revto on 2010-12-23
So what are you thinking? Go ahead with the reinstall? Or should I wait a few?

---

### Post by Crusty Old Fart on 2010-12-23
I'm ready whenever you are. It's up to you. Just make damned sure that you're running ubuntu2direct when you do it.

---

### Post by revto on 2010-12-23
Alright I gonna start the install and in the mean time look for another way to communicate

---

### Post by Crusty Old Fart on 2010-12-23
Hey wait a minute...remember all the problems we had with GRUB. How about we zero write the master boot record before you start the install?

---

### Post by revto on 2010-12-23
Sounds good to me

---

### Post by Crusty Old Fart on 2010-12-23
It's so easy...Boot using the 64-bit Live CD.

Use the nomodeset option and get into a virtual shell in tryout mode.

At the virtual shell, enter this command exactly as shown:
```

[SIZE=5]sudo dd if=/dev/zero of=/dev/sda bs=512 count=1[/SIZE]
```

---

### Post by revto on 2010-12-23
> **Crusty Old Fart said:**
> It's so easy...Boot using the 64-bit Live CD.

Use the nomodeset option and get into a virtual shell in tryout mode.

At the virtual shell, enter this command exactly as shown:
```

[SIZE=5]sudo dd if=/dev/zero of=/dev/sda bs=512 count=1[/SIZE]
```

Then start the install?

---

### Post by Crusty Old Fart on 2010-12-23
> **revto said:**
> Then start the install?
Only if you get output that looks like this:
```

1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.00110864 s, 462 kB/s

```Don't forget to**[COLOR=Red] install using the Alternate 64-bit CD[/COLOR]** instead of the Live CD that you will use to zero write the MBR.

---

### Post by Crusty Old Fart on 2010-12-23
Wouldn't it be the cat's asss if Lucid installs and boots into gnome using the nouveau driver without ubuntu2 being connected to the monitor through the splitter. I'll be ROTFFLMFAO. (hope the moderators don't punt me for that little zinger)

---

### Post by revto on 2010-12-24
I am back after the new install. I couldn't get to a virtual shell no matter what I did as it would just load me into the login and then gnome at 1280 x 1024, but I did need to use the nomodeset option to get anywhere. I have a fresh install minus a clean masterboot record but I have a max resolution of 1280 x 1024 and I have since put it back to 1024 x 768 so it is easier on the eyes with a 17" monitor.

---

### Post by revto on 2010-12-24
Getting in after the install, I needed to delete "quiet splash" and add "nomodeset" though

---

### Post by matt_symes on 2010-12-24
That is the funniest thing i have read for ages. You have made my night.

Good work though Crusty.

Not sure why you cant see that link. I found it after googled for something separate and was browsing through the book.

Moral of the story. Don't use a KVM while installing

---

### Post by Crusty Old Fart on 2010-12-24
I think we're almost done.

Did you ever see an SMB1 probing error?

Are you happy enough with the default nouveau driver that is driving your graphics to keep it?
(I would if I were you.)

Would you like to configure grub now?

---

### Post by revto on 2010-12-24
> **matt_symes said:**
> Moral of the story. Don't use a KVM while installing

I won't be anymore. Glad I kept you laughing, if there is any good to this story it is:

I learned a lot and crusty is one swell guy to still be helping.

---

### Post by Crusty Old Fart on 2010-12-24
> **matt_symes said:**
> That is the funniest thing i have read for ages. You have made my night.

Good work though Crusty.

Not sure why you cant see that link. I found it after googled for something separate and was browsing through the book.

Moral of the story. Don't use a KVM while installing

Can you believe this? I think we just had our Jesus moment!

---

### Post by revto on 2010-12-24
> **Crusty Old Fart said:**
> Did you ever see an SMB1 probing error?

Are you happy enough with the default nouveau driver that is driving your graphics to keep it?
(I would if I were you.)

Would you like to configure grub now?


Everything seems to be fine looking, didn't see a SMB1 error, and I'm ready for anything!

---

### Post by Crusty Old Fart on 2010-12-24
> **revto said:**
> Everything seems to be fine looking, didn't see a SMB1 error, and I'm ready for anything!
Okay let's configure GRUB:
First we make a copy of the original file:
```

sudo cp /etc/default/grub /etc/default/grub_original
ls -l /etc/default | grep grub

```Please post your output.

---

### Post by revto on 2010-12-24
```
-rw-r--r-- 1 root root  865 2010-12-24 00:40 grub
-rw-r--r-- 1 root root  865 2010-12-24 01:14 grub_original
```

---

### Post by Crusty Old Fart on 2010-12-24
Please post the output from this command:
```

sudo cat /etc/default/grub

```

---

### Post by revto on 2010-12-24
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by Crusty Old Fart on 2010-12-24
Open grub in a gedit window with the following command:
```

sudo gedit /etc/default/grub

```Make the following changes in the gedit window (you can copy and paste):
```

***[COLOR=Red]~~~ Change this line: ~~~[/COLOR]***
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

***[COLOR=Green]~~~ to this: ~~~[/COLOR]***
GRUB_CMDLINE_LINUX_DEFAULT=""

[br]2[/br]
***[COLOR=Red]~~~ Change this line: ~~~[/COLOR]***
GRUB_CMDLINE_LINUX=""

***[COLOR=Green]~~~ to this: ~~~[/COLOR]***
[COLOR=Red][s][COLOR=Black]GRUB_CMDLINE_LINUX="nomodeset"[/COLOR][/s][/COLOR] ***[COLOR=Blue](Edit: Use the line below instead. It will produce the correct output shown in [/COLOR]***[Post #385]("http://ubuntuforums.org/showthread.php?p=10274451#post10274451")***[COLOR=Blue])[/COLOR]***
[COLOR=Blue]GRUB_CMDLINE_LINUX="nouveau.modeset=0"[/COLOR]

```Then save and close the gedit window

Now, back in your shell, run these commands and post your output:
```

sudo update-grub
sudo cat /etc/default/grub

```

---

### Post by revto on 2010-12-24
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

on the first one and: 

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="nomodeset"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

on the second command

---

### Post by Crusty Old Fart on 2010-12-24
[B][COLOR=Blue]Edit: Disregard this post and Post #383 and see the corrected [post=10274406]Post #382[/post] above Post #383.[/COLOR]
[/B]
[s]I'm sorry Thomas. I told you wrong. For the default, nouveau driver, KMS is supposed to be disabled with: nouveau.modeset=0

Open grub in a gedit window with the following command:[/s]
```
[s]
sudo gedit /etc/default/grub
[/s]
```[s]Make the following changes in the gedit window (you can copy and paste):[/s]
```
[s]
***[COLOR=Red]~~~ Change this line: ~~~[/COLOR]***
GRUB_CMDLINE_LINUX="nomodeset"

***[COLOR=Green]~~~ to this: ~~~[/COLOR]***
GRUB_CMDLINE_LINUX="nouveau.modeset=0"
[/s]
```[s]Then save and close the gedit window

Now, back in your shell, run these commands and post your output:[/s]
```
[s]
sudo update-grub
sudo cat /etc/default/grub
[/s]
```[s]Sorry.
[/s]

---

### Post by revto on 2010-12-24
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="nouveau.modeset=0"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by Crusty Old Fart on 2010-12-24
That looks fine.

But...Did you remember to run:
```

sudo update-grub

```
after you made the change/

---

### Post by revto on 2010-12-24
yes I got

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

---

### Post by revto on 2010-12-24
I did that before I gave you the results in post 385

---

### Post by Crusty Old Fart on 2010-12-24
> **revto said:**
> I did that before I gave you the results in post 385
Okay...just wanted to make sure. EVERY TIME the grub file is changed, it MUST be updated with the sudo update-grub command.

Let's try a reboot.

You shouldn't have to touch a thing until the gnome login screen comes up.

---

### Post by revto on 2010-12-24
Everything worked great but I did notice that the pesky SMB1 error is back.

---

### Post by Crusty Old Fart on 2010-12-24
> **revto said:**
> Everything worked great but I did notice that the pesky SMB1 error is back.
I think he likes you.

Do you feel lucky?
Lucky enough to see what happens if you shut down, then connect to the splitter, and boot into it?

---

### Post by revto on 2010-12-24
Sure thing. Be right back

---

### Post by revto on 2010-12-24
When I do that, everything goes exactly the same but when I get the SMB1 error I drop into a virtual shell login instead of going to gnome login.

---

### Post by Crusty Old Fart on 2010-12-24
> **revto said:**
> When I do that, everything goes exactly the same but when I get the SMB1 error I drop into a virtual shell login instead of going to gnome login.
Did you get back to gnome with this?:
```

sudo service gdm start

```

One thing about that damned KVM...It might be a good idea NOT to be connected to it when you download and install any updates...just sayin'.

---

### Post by Crusty Old Fart on 2010-12-24
Since I promised you this a long time ago:

There are six tty Virtual Shell processes running in the background all the time. 
You can get to any one of them from gnome at any time by pressing Ctrl-Alt-F1 through Ctrl-Alt-F6 ... you get back to gnome with Ctrl-Alt-F7

---

### Post by revto on 2010-12-24
> **Crusty Old Fart said:**
> Did you get back to gnome with this?:
```

sudo service gdm start
[/code

when I tried that I got :

[CODE]gdm start/running, process 1439
```

and it came back to a virtual shell prompt

---

### Post by revto on 2010-12-24
> **Crusty Old Fart said:**
> There are six tty Virtual Shell processes running in the background all the time. 
You can get to any one of them from gnome at any time by pressing Ctrl-Alt-F1 through Ctrl-Alt-F6 ... you get back to gnome with Ctrl-Alt-F7

I have read about that. ctrl-alt-f1 is a root shell and it was recommended to only use a ctrl-alt-f2 or higher to not screw up the system.

---

### Post by Crusty Old Fart on 2010-12-24
> **revto said:**
> when I tried that I got :

```
gdm start/running, process 1439
```and it came back to a virtual shell prompt
If pressing Ctrl-Alt-F7 doesn't take you to gnome after you've started the service, then you probably won't be able to use the splitter with ubuntu2.

---

### Post by Crusty Old Fart on 2010-12-24
I hope that you can boot straight into gnome if you connect directly to the monitor again.

---

### Post by revto on 2010-12-24
> **Crusty Old Fart said:**
> I hope that you can boot straight into gnome if you connect directly to the monitor again.

Direct connect seems to work almost every time now if not every time on ubuntu2,  I am just wondering where the disconnect is. The splitter just switches between monitor streams (which should be direct connections except for the connection loss of having another coupler in the loop) and "should" have a direct connection minus being another coupler. The other comp seems to be fine working through it, I guess I'll have to try hooking it up directly tomorrow. 

Any other commands I should try or thoughts on the situation before I sign off?

---

### Post by Crusty Old Fart on 2010-12-24
Yup...My last thought on the situation is: Merry Christmas to you and your loved ones.

I think we've done everything we can here. For some reason, no matter what driver we tried, three of them to be exact (NV, Nvidia Binary - current, and the default Nouveau), none of them will work proper through the splitter.

Just the way it goes, I reckon.

I'll stay subscribed to this thread for a while. But at least it's nice to know that without the splitter, ubuntu2 should be a fine Linux box now.

All the Best to you. It's been a pleasure,

Crusty

---

### Post by rabbits on 2010-12-24
Dear Crusty and revto;  I just saw your post today and read the first and last page (=page 6).  I have nvidia 6150 graphics on an old Compaq laptop.  I found that installation of 9.10 and 10.04 is problematic with nVidia, but Maverick-10.10 is quite straightforward for me.  

If you just boot off the 10.10 Live CD and "install" while connected to the Internet, the correct "nvidia-173" driver  will be downloaded during your live testing or after install and you reboot; by running the jockey-gtk program ie. >

       > System > Administration >Additional Drivers.

Best wishes with 10.10 Maverick installation.

---

### Post by revto on 2010-12-24
Thank you for all of your help to get me to this point both with computer and my knowledge (where ever that may be). If you figure out anything about the SMB1 error, let me know. It is still rearing its ugly head. But like you said, maybe it is my monkey to bear with this machine. 

Merry christmas to you and all of yours and thank you for all of your help. Don't know how you put up with beginners like me but thank you for doing so. 
Thomas

---

### Post by Crusty Old Fart on 2010-12-24
> **rabbits said:**
> Dear Crusty and revto;  I just saw your post today and read the first and last page (=page 6).  I have nvidia 6150 graphics on an old Compaq laptop.  I found that installation of 9.10 and 10.04 is problematic with nVidia, but Maverick-10.10 is quite straightforward for me.  

If you just boot off the 10.10 Live CD and "install" while connected to the Internet, the correct "nvidia-173" driver  will be downloaded during your live testing or after install and you reboot; by running the jockey-gtk program ie. >

       > System > Administration >Additional Drivers.

Best wishes with 10.10 Maverick installation.
Well, rabbits...we have Lucid working very nicely now with the nouveau driver. After a week or so of beating our brains out, tonight we discovered that the source of most of the problems was the KVM splitter. Personally, I don't like to break things that I just finished fixing. That's just my style. Other people like to torture themselves...and that's okay...for them.

---

### Post by rabbits on 2010-12-24
No worries.  I could not tell by reading only page-6 whether you had solved the problem; sorry lazy to read the other pages.  The "jockey=gtk" (Additional Hardware) utility works well on 10.10 and even on 11.04 Natty; however Natty introduces another nVidia complexity with 3d and Unity.

Merry Christmas.

---

### Post by Crusty Old Fart on 2010-12-24
Thomas: 
You're mighty welcome. Beginners like you are true delights.

rabbits:
Yep...from my experiences with Linux, there seems to be certain combinations of kernels, drivers, BIOS versions, hardware...you name it, that just won't play nice together. Every Linux box I've built has been a huge challenge. When I finally get them running. I leave well enough alone. I usually let the software updates come in, but NEVER upgrade a distro that's working. Anyhow, thank you for popping in here to offer a helpful suggestion. But, after all we've been through, I don't think revto is going to cotton too well to the idea of starting all over with another big variable. But, who knows?

Take care,

Merry Christmas to you too.

---

### Post by Crusty Old Fart on 2010-12-25
Howdy Thomas:

After going through this thread again from beginning to end, I expect that this may be my last post to it. You should be in pretty good shape now as long as you aren't using your splitter on ubuntu2.

If, for any reason, things get all balled up in the future, you can always zero write your MBR and reinstall Lucid.

**The instructions and commands you need are in the posts listed below:**

[LIST]
[*]First, and most importantly, make sure that your monitor is connected directly to your computer, and NOT to the splitter, for all of the following procedure.
[*]To zero write your MBR: [post=10274077]Post #367[/post]
[*]To check the output from the zero write command: [post=10274100]Post #369[/post]
[*]Install Lucid using your Alternate 64-bit CD.
[list]
[*]If you need to burn a new CD, it is availble here: [http://releases.ubuntu.com//lucid/ub...nate-amd64.iso]("http://releases.ubuntu.com//lucid/ubuntu-10.04.1-alternate-amd64.iso")
[*]MD5 SUM = f3da7da6931e3160738b3067d79e346a
[/list]
[*]During the boot process after installation, edit the kernel options using the GRUB menu as you did in [post=10274329]Post #372[/post]
[*]Continuing with boot by pressing Ctrl-x should take you to the gnome login screen.
[*]The last thing we did was to configure your grub file. The instructions and commands to do that are in:
[LIST]
[*] [post=10274364]Post #378[/post]
[*][post=10274369]Post #379[/post]
[*][post=10274406]Post #382[/post], which has been edited to correct my mistake and to give you the output in [post=10274451]Post #385[/post] and [post=10274463]Post #387[/post]
[/LIST]
 
[/LIST]

Lastly, I'm going to pull in the link to Post #39 (for what it's worth) because it may not remain in my signature very much longer...
**[[COLOR=Red]revto Reference post #39[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10249945&postcount=39")**

I think that about wraps it up for me, other than hoping things go well enough for you to mark this thread as [SOLVED] some day.

Take care,

Crusty

---

### Post by ssulaco on 2010-12-25
> **Crusty Old Fart said:**
>  When I finally get them running. I leave well enough alone. I usually let the software updates come in, but NEVER upgrade a distro that's working.
Amen,Brother.Ive got a few more months left with Hardy and wont upgrade until the last moment,Hardy has been rock solid,Lucid (Live)runs great on my machine,I prefer to stick with the LTS...
anyway just wanted to say HATS OFF to you Crusty Old Fart,you've put alot of time in this thread helping Thomas.

---

### Post by Crusty Old Fart on 2010-12-26
> **ssulaco said:**
> ...
anyway just wanted to say HATS OFF to you Crusty Old Fart,you've put alot of time in this thread helping Thomas.
Nice of you to say that. Thank you.

---

### Post by revto on 2011-01-08
Hey Crusty, 

Hope all is well with you and yours. All is well on the homefront here  and I have been up and running with no switch and everything seems to be  great. And of course I had to get an itch to get a new monitor with DVI  and an HDMI hookup (which I haven't purchased yet). 

The itch came when we were working on the comp and a buddy gave me his  video card to try if it would work with different results than a black  screen. He didn't give it to me until we already solved the Nvidia  problem and I didn't want to rock the boat, and of course I want to  upgrade the monitor which (doesn't necessarily) mean I need a better  connection than VGA. 

 He gave me an "ATI Radeon X1650 512M 128B DDR2 P CIE" . I have checked  out the forums tonite and found a bunch of problems people had with it  but they were from 09 and before using ubuntu 9.04 and prior. 

I was wondering if you would try to install it, knowing what I know. I  would do this very often with windows and think nothing about changing  out hardware and would do it in a sec but with ubuntu I figured I would  see what you though and if there was any tricks to installing the  drivers or if I should just put it in and see what happens. 

Actually, I guess the first and most important question is the card is a  PCI Express 2.0 and my chipset say it can take a PCI Express x16  graphics slot. The board looks like it would fit the card and I am  having trouble trying figure out the difference between the two.

Here are some of the answers to my own last question, which sounds like a  "you can do it". I just figured that you have seen more than me and I  value your opinion. Thanks for your help. It is always appreciated. I tried to message you but it said you couldn't accept messages.

[http://discuss.extremetech.com/forums/thread/1004398567.aspx](http://discuss.extremetech.com/forums/thread/1004398567.aspx)
[http://answers.yahoo.com/question/index?qid=20071126230622AAKjALQ](http://answers.yahoo.com/question/index?qid=20071126230622AAKjALQ)

Thomas

---

### Post by Crusty Old Fart on 2011-01-09
> **revto said:**
> Hey Crusty, 

Hope all is well with you and yours. All is well on the homefront here  and I have been up and running with no switch and everything seems to be  great. And of course I had to get an itch to get a new monitor with DVI  and an HDMI hookup (which I haven't purchased yet).
Well Howdy Thomas:

Things are going just fine here. Glad to read that you're doing well too.

> **revto said:**
> 
The itch came when we were working on the comp and a buddy gave me his  video card to try if it would work with different results than a black  screen. He didn't give it to me until we already solved the Nvidia  problem and I didn't want to rock the boat, and of course I want to  upgrade the monitor which (doesn't necessarily) mean I need a better  connection than VGA. 

 He gave me an "ATI Radeon X1650 512M 128B DDR2 P CIE" . I have checked  out the forums tonite and found a bunch of problems people had with it  but they were from 09 and before using ubuntu 9.04 and prior. 

I was wondering if you would try to install it, knowing what I know. I  would do this very often with windows and think nothing about changing  out hardware and would do it in a sec but with ubuntu I figured I would  see what you though and if there was any tricks to installing the  drivers or if I should just put it in and see what happens.
Nope...plugging it in just to see what happens is not such a good idea. You're in no big fat rush, right? How about we learn a little bit more about what we're getting ready to do before we do it? We're not ready to be plugging things in yet.

> **revto said:**
> 
Actually, I guess the first and most important question is the card is a  PCI Express 2.0 and my chipset say it can take a PCI Express x16  graphics slot. The board looks like it would fit the card and I am  having trouble trying figure out the difference between the two.

Here are some of the answers to my own last question, which sounds like a  "you can do it". I just figured that you have seen more than me and I  value your opinion. Thanks for your help. It is always appreciated. I tried to message you but it said you couldn't accept messages.

[http://discuss.extremetech.com/forums/thread/1004398567.aspx](http://discuss.extremetech.com/forums/thread/1004398567.aspx)
[http://answers.yahoo.com/question/index?qid=20071126230622AAKjALQ](http://answers.yahoo.com/question/index?qid=20071126230622AAKjALQ)

Thomas

Well...maybe it can be done, and maybe it can't. If it _can_ be done, we'll figure out how to do it. If it _can't_ be done, then we'll find out why.

Before we get into this too far, I'd like to be sure about what combination of hardware we're going to be dealing with. So...

Have you thought enough about how you want all of your computers set up, at least concerning the "ultimate" combination of computers, monitors and driver cards?

If not, it might be a good idea to think about that a little more. It doesn't make much sense to fart around getting the Radeon card working in ubuntu2, if that isn't really where you ultimately intend to have it installed. In the event that you want to use a different computer than ubuntu2, then let me know and we can start looking at hardware specs for compatibility issues.

For now, I'll be working on finding out if the radeon card is compatible with the default Ubuntu "radeon" driver, which is an excellent driver, and whether the card is compatible with 64-bit architecture.

Here we go again. Fasten your safety harness!

Oh...one last thing...There were some idiots, whom I never met, who began sending me a bunch of crap. So, I locked down my messaging options as tight as I could make them. I'll punch a hole for you. However, working out problems is better done here on the boards where other folks might benefit from what we're doing.

---

### Post by Crusty Old Fart on 2011-01-09
Howdy Thomas:

**Before giving you any advice, I wanted to find answers to the following questions:**

[LIST=1]
[*]Will the default "radeon" driver, which is included in Lucid 10.04, drive the Radeon X1650 graphics card? Answer: Yes.
[*]Will the X1650 handle 64-bit architecture? I think so.
[*]Will the motherboard in ubuntu2 accept the X1650? Answer: Yes.
[*]Will the integrated Nvidia graphics chipset on the motherboard be automatically disabled when a graphics card is plugged in? Answer: Yes.
[/LIST]
**Here are the references:**[INDENT]_With regard to question #1:_ You'll find the X1650 listed as a supported video card on the manpage for radeon:[INDENT]```
man radeon
```[/INDENT]_With regard to question #2:_[INDENT]From the specification for the X1650 (Ref.: [http://www.amd.com/us/products/desktop/graphics/other/Pages/x1650-specifications.aspx](http://www.amd.com/us/products/desktop/graphics/other/Pages/x1650-specifications.aspx))

[LIST]
[*]64-bit floating point HDR rendering supported throughout the pipeline  (<-- Hopefully that means it will work fine with your 64-bit  architecture.)
[/LIST]
[/INDENT]_With regard to question #3:_[INDENT]From the specification for the X1650 (Ref.: [http://www.amd.com/us/products/desktop/graphics/other/Pages/x1650-specifications.aspx](http://www.amd.com/us/products/desktop/graphics/other/Pages/x1650-specifications.aspx))

[LIST]
[*]Native PCI Express x16 bus interface or...
[*]AGP 8x configurations also supported with AGP-PCI-E external bridge chip
[/LIST]
From the specification for your motherboard (Ref.: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00821657&tmp_track_link=ot_faqs/top_issues/en_us/c00821657/loc:2&lc=en&dlc=en&cc=us&product=3339301#N288](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00821657&tmp_track_link=ot_faqs/top_issues/en_us/c00821657/loc:2&lc=en&dlc=en&cc=us&product=3339301#N288))

[LIST]
[*]Expansion Slots:
[LIST]
[*]3 PCI slots
[*]1 PCI Express x16 graphics slot
[/LIST]
 
[/LIST]
It appears that depending on the configuration along the connector edge of the X1650, it should fit in one kind of slot or the other on the motherboard.
[/INDENT]_With regard to question #4:_[INDENT]From the specification for your motherboard (Ref.: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00821657&tmp_track_link=ot_faqs/top_issues/en_us/c00821657/loc:2&lc=en&dlc=en&cc=us&product=3339301#N288](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00821657&tmp_track_link=ot_faqs/top_issues/en_us/c00821657/loc:2&lc=en&dlc=en&cc=us&product=3339301#N288))

[LIST]
[*]*Integrated video is not available if a graphics card is installed.
[/LIST]
[/INDENT][/INDENT]So...Everything I've found here looks like the X1650 is a good enough match for ubuntu2 that you should be able to plug it in and the OS should run it without any problem. However, if I were you, after you install the X1650, I would boot from your 64-bit Live CD and see how that goes before booting from your installed OS. The "radeon" default driver is also included on the Live CD. You won't need to disable Kernel Mode Setting because the default "radeon" driver uses KMS and RandR to automatically configure your settings for your card and monitor during boot, just as the default "nouveau" driver configured your settings automatically for your Nvidia integrated graphics chipset. Just make sure that you are NOT connected through the splitter when you try any of this.

I'm curious to know how it goes.

Good luck,

Crusty

---

### Post by revto on 2011-01-10
After installing the card a few times not happy with the way it was sitting, it finally sat correctly and I connected and fired up with the live disk in the drive and the fan on the card sounded really loud. The monitor stayed in sleep mode and when I turned it off and back on it would just go to sleep signaling no power through the VGA cord. I pulled the card and fired it up and I am back to normal. So I tried it again and the card fan sounded normal but I got the same results. The card seemed to be in the exact same position each time (not cockeyed or ever having pins exposed, lock in the back engaged and the front tab in the slot). I must also add that I am not using the splitter. Although that would make for an interesting next 300 posts!

---

### Post by Crusty Old Fart on 2011-01-10
> **revto said:**
> After installing the card a few times not happy with the way it was sitting, it finally sat correctly and I connected and fired up with the live disk in the drive and the fan on the card sounded really loud. The monitor stayed in sleep mode and when I turned it off and back on it would just go to sleep signaling no power through the VGA cord. I pulled the card and fired it up and I am back to normal. So I tried it again and the card fan sounded normal but I got the same results. The card seemed to be in the exact same position each time (not cockeyed or ever having pins exposed, lock in the back engaged and the front tab in the slot). I must also add that I am not using the splitter. Although that would make for an interesting next 300 posts!
Well, shucks...After checking everything out for compatibility, except for compatibility between the video card and the monitor, I was thinking that this card was going to be as simple as plug and play. Not so, eh?...figures.

Now I'm thinking that the problem could be the result of:

[LIST]
[*]The card is toast...or...
[*]The card isn't compatible with your monitor.
[/LIST]
So, I wonder what kind of tests you could perform:

[LIST]
[*] Do you have a Windows OS that you could boot up with the X1650 card installed?
[*] And...do you have a different monitor that you could try?
[/LIST]
See where I'm going with this?

---

### Post by revto on 2011-01-11
I guess we have the culprit, the video card. I tried it in my win7 rig and got the same result as well as now not having any sound from the rig but I can figure that one out on my own, it is just windows. Nothing a good hard drive wipe won't solve. I guess I will check out some other video cards or just wait for something someone wants to get rid of then worry about the change. But on the same subject, I have noticed that youtube videos shown at full screen seem to have some lag and I have since started watching them in the normal youtube window instead of full screen. In the past I have been able to do full screen but that was also in 800 x 600. Wondering what your thoughts are on that since you know the specs on ubuntu2. Am I just lagging cause I'm just slow?

BTW: I got the sound back on the win7 rig. Just didn't want anyone in the forums loosing sleep over that! Obviously i'm kidding.

---

### Post by Crusty Old Fart on 2011-01-11
> **revto said:**
> I guess we have the culprit, the video card. I tried it in my win7 rig and got the same result as well as now not having any sound from the rig but I can figure that one out on my own, it is just windows. Nothing a good hard drive wipe won't solve.
Good job. I don't know anything about Windoze7, other than it's another overpriced, unsecure, POS OS from Microsuck. I'm digging in my heels and refusing to buy anything from those bastards for as long as I can get away with it. Still running XP Pro here and a ten year old version of Excel, which covers my needs just fine. I had a problem years ago when IE7 came out. After I installed that POS, I had to reinstall the drivers for my sound card EVERY time I rebooted. Needless to say, I removed IE7, installed Firefox and have never looked back. Maybe all you need to do to get your sound back is to reinstall the driver. Just a guess, and the only one I'll make since I really don't know jack about 7. Good luck.

> **revto said:**
> I guess I will check out some other video cards or just wait for something someone wants to get rid of then worry about the change. But on the same subject, I have noticed that youtube videos shown at full screen seem to have some lag and I have since started watching them in the normal youtube window instead of full screen. In the past I have been able to do full screen but that was also in 800 x 600. Wondering what your thoughts are on that since you know the specs on ubuntu2. Am I just lagging cause I'm just slow?Lagging video could be caused by so many things that it's hard to know where to start looking. Even if you had a bleeding edge, screamingly fast system, you could still get lags if the server sending out the video can't keep up with the demand, or there's a ton of traffic on your route to the server. So, the problem may not be on your end at all. You may notice differences in the performance of the streaming video at different times of the day. If I knew a little more about what is going on at Youtube, I might be of more help. But, I never go there. Youtube is blocked on my systems because they are owned by Google. And Google is pure evil...so is Facebook, and Yahoo, and Myspace, and Twitter, and Microsoft, and AOL, and a whole bunch of other domains that I have blocked in my hosts file so that my computer cannot access any of them, and I've written custom rules in my Adblock Plus Firefox Addon so that they can't access my systems. So, I'll have to punt on the Youtube question. As far as the Internet in general goes, I'm a lot more locked down than most people are.

Too bad the free video card turned out to be toast. If you'd like to study the specs on ubuntu2 before you spend any coin of the realm on a new card or monitor, you can find everything we know about that computer in: [B][[COLOR=Red]revto Reference post #39[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10249945&postcount=39")
[/B]
Lastly, if you run into anymore problems, it would probably be good to start a new thread rather than adding to this one. Now that you can send me private messages, you can send me a link to any thread you create if you'd like me to show up on it.

Take care, my friend.

All the best 'till we meet again,

Crusty

---

### Post by Crusty Old Fart on 2011-01-11
On second thought, there remains a remote possibility that the video card may not be toast. There could be settings in BIOS that need to be changed depending on what kind of slot you're plugging it into.

It also may be interesting to learn if your buddy who gave it to you ever had it running, and if he did, will it work for him if he tries to use it now. Just thinkin'.

---

### Post by revto on 2011-01-15
> **Crusty Old Fart said:**
> On second thought, there remains a remote possibility that the video card may not be toast. There could be settings in BIOS that need to be changed depending on what kind of slot you're plugging it into.

Thats very true. I forgot to check. I would hope it would plug-n-play  but that may not be the case and I have always used the onboard video on  both rigs. and haven't had to mess with the Bios video settings. 

> **Crusty Old Fart said:**
> It also may be interesting to learn if your buddy who gave it to you ever had it running, and if he did, will it work for him if he tries to use it now. Just thinkin'.

I know that my buddy had it in his rig for a week and running great and then pulled it to put in a dual output video card. That also was at least a year ago. I have asked him to try it again and I'm still awaiting the results.

My last question for this thread (I will have to start a new one if I decide to buy this card [http://www.newegg.com/Product/Product.aspx?Item=N82E16814102855&cm_sp=DailyDeal-_-14-102-855-_-Homepage](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102855&cm_sp=DailyDeal-_-14-102-855-_-Homepage) ) is should I use a proprietary driver? I thought that I was using one but checked to see and low and behold I am not. Also my video only goes to 1024 x 768. I thought it went to like 1280 x 1024, probably the driver issue and the "detect monitor" button doesn't have any results on either monitor, (see FYI).

When I go to system/admin/hardware drivers I have 3 shown, version 173, 96, and version current, which is recommended. In my 8.04 version the proprietary driver would not work but also I was running a 32 bit system on a 64 bit comp. It says that I need the prop driver to use the 3d effects and 3d desktop, which I am not familiar with, I got excited about not having windows a few years ago and jumped into ubuntu but didn't check out all the cool stuff that it can do. What are your thoughts on this?

FYI: I have updated my monitor to a Vizio 22" widescreen hdtv (720p) and it is connected with a regular VGA cable. It works great and prompted the video res. change that started this question.

---

### Post by Crusty Old Fart on 2011-01-15
> **revto said:**
> Thats very true. I forgot to check. I would hope it would plug-n-play  but that may not be the case and I have always used the onboard video on  both rigs. and haven't had to mess with the Bios video settings.
According to your motherboard (mobo) specs, your integrated graphics chipset gets automatically disabled when a video card is plugged in. My mobo has PCI slots and one AGP slot for video cards. If I plug a card into the AGP slot, I need to change a BIOS setting to select the AGP slot as the primary video interface. Otherwise, my BIOS assumes the primary video interface to be the first PCI slot on the mobo. You may have a similar setting in your BIOS. Some do, some don't.

> **revto said:**
> I know that my buddy had it in his rig for a week and running great and then pulled it to put in a dual output video card. That also was at least a year ago. I have asked him to try it again and I'm still awaiting the results.Maybe you BROKE it, Thomas! :cool:

> **revto said:**
> My last question for this thread (I will have to start a new one if I decide to buy this card [http://www.newegg.com/Product/Product.aspx?Item=N82E16814102855&cm_sp=DailyDeal-_-14-102-855-_-Homepage](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102855&cm_sp=DailyDeal-_-14-102-855-_-Homepage) ) is should I use a proprietary driver?You probably won't have to. The manpage for the default radeon driver lists that card as supported hardware. As I've mentioned before, the default radeon driver is excellent. I reckon the only way to know if you like whatever proprietary driver, that _might_ be available, better than the default driver, would be to install it and try it out. But, if you're happy with the default driver, then all that driver installation gymnastics may end up being a lot of hassle for nothing. Ultimately it's up to you.

> **revto said:**
> I thought that I was using one but checked to see and low and behold I am not.Nope. When we finally got ubuntu2 running, you seemed happy enough with  the default nouveau driver to keep it (see: [post=10274356]Post  #377[/post]).

> **revto said:**
> Also my video only goes to 1024 x 768. I thought it went to like 1280 x 1024, probably the driver issue and the "detect monitor" button doesn't have any results on either monitor, (see FYI). I don't think the resolution limit is a driver issue, but I'm not exactly sure. I think it may have more to do with your X configuration.

> **revto said:**
> When I go to system/admin/hardware drivers I have 3 shown, version 173, 96, and version current, which is recommended. In my 8.04 version the proprietary driver would not work but also I was running a 32 bit system on a 64 bit comp. It says that I need the prop driver to use the 3d effects and 3d desktop, which I am not familiar with, I got excited about not having windows a few years ago and jumped into ubuntu but didn't check out all the cool stuff that it can do. What are your thoughts on this?We tried to install the current version of the proprietary driver way back before we discovered the problem with the splitter. We could try it again if you want to. It's not just as simple as clicking on options in the gnome driver panels though. I could guide you through the process again if you want. But, I'd rather not waste my time if you're just going to order a new Radeon card from Newegg in a couple of days. However, if you want to see if your integrated chipset will work so much better with the proprietary driver that you won't buy the card, then maybe we should install it and see what happens. What say you? It shouldn't take too long if everything goes well (like it always does :cool: ).

---

### Post by Crusty Old Fart on 2011-01-15
In case you want to start without me, here are the instructions for installing the proprietary Nvidia driver:

**Step 1:** Lock your KVM splitter in your car.

**Step 2:** Remove the default nouveau driver.
```

sudo apt-get --purge remove xserver-xorg-video-nouveau
```**Step 3:** Add the PPA
```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```**Step 4:** Install the current Nvidia display drivers.
```

sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
```**Step 5:** Go to *System > Administration > Hardware Drivers* and make sure "Nvidia current" is activated.

**Step 6:** Reboot

That should do it. But, there still may be some configuration changes needed in GRUB and in X. I won't know until after you try rebooting. If you aren't able to get into Gnome after boot, you may need to add the nomodeset boot option to your default kernel in GRUB. Remember that?...Highlight your kernel (should be the top one, already highlighted), press e to edit it, add the nomodeset option to the end of the line containing the kernel, press Ctrl-x to continue booting.

Good luck.

---

