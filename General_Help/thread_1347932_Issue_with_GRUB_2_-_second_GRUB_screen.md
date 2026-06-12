---
title: "Issue with GRUB 2 - second GRUB screen"
date: 2009-12-06
forum: General Help
---

### Post by wiseloki on 2009-12-06
In short, my problem is that GRUB 2 that came with 9.10 now has a second GRUB menu accessed from the "Windows XP" option that I want to delete - but I have no idea how to go about it. Hence the cry for help.

Now a long explanation of how I got where I am and a detailed description af what is happening.

I'd bought a Lenovo X60s as a replacement for my IBM T42 as the T42 had a wireless hardware issue. The X60 came with XP Pro, and I decided I wanted to go for a dual-boot installation. I started by creating a live CD from a download of 9.10, went to resize the XP partition and set up separate /; /home and swap partitions, but after resizing the XP partition I got a warning that the XP partition wouldn't be used, (I had options to associate it to /windows or /dos, but I didn't really understand the decision and was worried about losing XP) so I decided to install using the live CD option of installing Ubuntu alongside XP. I restarted the machine and got the GRUB screen I was used to, booted both XP and Ubuntu and both ran OK, found my network etc. So far, so good.

Then I decided to use the info one of the posts in this forum to create a separate /home partition by running the live CD again and resizing the / partition down to about 11Gb and using the space created. The issue came with trying to get the live CD to run. An X60 doesn't have an optical drive, so I'd used a USB DVD drive for the first installation, using one of the BIOS options to boot from an alternative device (F12). When I tried this again, I could not get the laptop to boot from the USB DVD, so I used the option when running the live CD in XP where if the PC won't boot from the CD there is an option to use a CD boot assister. This option downloaded a file to the computer and told me to reboot. When I rebooted again I got GRUB which allowed me to go into Ubuntu as before, but the XP option took me not to XP, but to another GRUB screen with only two options, XP Pro and Ubuntu. The XP Pro option booted the machine in XP as before, but the Ubuntu option now ran and booted from the live CD in the USB DVD.

I then used the partitioner to resize the / partition and create a new  /home partition with no problems, rebooted and Ubuntu ran fine. But now the problem I want help with.

On start, GRUB shows the usual list of boot options with a couple of versions of Ubuntu, memtest, and XP Pro down the bottom. The Ubuntu options boots Ubuntu as normal. The XP Pro option still takes me to the second GRUB screen with the two options; XP Pro and Ubuntu. Selecting Ubuntu from this second screen then gives a message 
“Completing the installation” with a countdown, which then leads to a black screen with the Ubuntu symbol in the 9.10 silver and there it hangs (I think it's trying to access the USB DVD, which is no longer there). If I hit "Esc" I get a message 

"CP: Cannot start '/custom – installation/initrd-override/*' No such file or directory” and a repeating
stdin: error 0
stdin: error 0
over and over, scrolling down the screen for evermore.

Can anyone tell me how to delete the CD boot helper files and/or modify GRUB so that I don't get the second screen from the XP Pro option in the first GRUB screen?

It's not a big issue as I intend to boot to Ubuntu most time, but I like a tidy laptop and I'd really like to get rid of a boot option that leads to a hang.

---

### Post by wiseloki on 2009-12-19
Bump. No Grub experts willing or able to help?

I get the impression that Grub is modular, with each line in the start-up screen calling a different file to boot that particular OS or kernel version. If this is the case (and apologies if my explanation is not in correct Ubuntu-speak) could I not fix the problem by finding the file or subroutine that the "Windows XP" line on the first Grub screen calls and editing or replacing it with the standard one so that it goes straight to XP when selected and not to the second Grub screen?

---

### Post by Leppie on 2009-12-19
have you checked the installed applications in xp? i suspect that you can remove the 2nd grub from within xp (as you installed it from within xp as well, if i understand correctly).

---

### Post by wiseloki on 2009-12-19
Hi Leppie - thanks for the input.

I'd never actually thought that it might be an XP issue, as I'd seen the Grub screen and assumed it was in Ubuntu. I went into XP and looked in the "Install programs" list in Control Panel, and there, sure enough, was an Ubuntu entry. I deleted this file and rebooted. 

Now if I select the XP option from the first Grub, I still get the second Grub screen, as before. The "XP Professional" option still boots XP, but the "Ubuntu" option in this second screen doesn't give the hang, it now gives the following error message

"Missing or corrupt file <Windows root>\system32\hal.dll Please reinstall a copy". And there it sits.

I rebooted and checked that both OS's still boot OK - they do - and had a second look down the XP "Remove programs" list, but I couldn't see anything that didn't look like it didn't belong to XP or the Thinkpad

So you were partly right. But I'm still left with the dilemma of finding the source of and removing this second grub screen I get when I select XP at the first.

---

### Post by wiseloki on 2009-12-22
Fixed it.

Leppie gave me the clue that it was a Windows issue. 

I checked around and found that Wubi (for it appears it was Wubi that had been installed to force the X60 to boot from the external CD) had altered the XP "boot.ini" file to add an extra line - this gave the second screen with the two alternative boot choices. When I deleted Wubi from XP the boot.ini file remained modified.

I edited "boot.ini" back to one used for a standard XP Pro installation and the problem was fixed - only one Grub screen and it boots straight through to XP when selected.

Thanks Leppie.

---

