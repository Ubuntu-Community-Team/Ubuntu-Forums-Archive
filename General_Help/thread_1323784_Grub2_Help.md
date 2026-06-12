---
title: "Grub2 Help"
date: 2009-11-12
forum: General Help
---

### Post by wickwack on 2009-11-12
Hi everyone, im new to this forum, i recently installed ubuntu 9.10 and i am loving it... everything has been quite smooth, just looking for some tweaks to really make my machine sing...

Mainly my questions are about Grub2...

i had a pc with a SATA drive with WinXP and Win7 installed on separate partitions, win7 bootloader would allow access to Win7 o earlier os (WinXP)..

then i installed an older IDE drive planning to install ubuntu 9.10 on it.. i knew this drive would boot first from previous Win trials... so i disconected my SATA drive and installed Ubuntu on the IDE drive, then reconnected SATA drive and did sudo update-grub...

GRUB2 then added a Windows7 (loader) to the boot menu... i can access all my os now... but if i want windows i must select it on GRUB2 and then use the Win7 bootloader to select between WinXP and Win7... which kinda sucks..

is it possible to boot to WinXP or Win7 directly, making GRUB bypass the Win7 Bootloader? i thought removing the chainloader +1 entry would solve this.. but actually if i remove chainloader +1 from either entry i cant even leave GRUB2 and reach the windows bootloader... i manually added entries for both Win partitions but somehow whatever partition in the SATA i direct grub2 towards the win7 bootloader always comes up first...

Now im thinking maybe removing the earlier os entry from the Win7 bootloader and that way i could quickly access Win7 without going thru the loader... but could i get to XP after doing that? also i didnt want to have to tweak the Win7 booloader in case i remove the IDE drive at some point... but honestly im willing to do anything to get this to work...

sorry for the long post, ive googled around and havent been able to find much help for this situation and grub2... i would assume this should be doable since it probably was on grub1 and this is after all an improved version right? thanks for reading

---

### Post by mikewhatever on 2009-11-12
I really don't see why it sucks, and no, you can't bypass the Windows bootloader.

---

### Post by wickwack on 2009-11-12
well is sucks because it increases the OS load time, and also because its not really a triple boot, but just a double boot over a double boot...

i see you have quite some experience, but i kinda want to ask for another opinion on this, there certainly must be away to use a single bootloader... if its not grub then maybe i can make the win7 loader boot linux?

---

### Post by halj32 on 2009-11-12
you can use windows bootloader to boot windows & linux, you can do it with windows bcdedit( for options just type in "CMD" bcdedit /?), just point it to the linux partition, you may get a few errors when you first use it but the second boot seems to go smooth.
or you can get easybcdedit here (free)
neosmart.net/dl.php?id=1

you dont need to use GRUB

---

### Post by mikewhatever on 2009-11-12
> **wickwack said:**
> well is sucks because it increases the OS load time, and also because its not really a triple boot, but just a double boot over a double boot...

Does it really boot noticeably slower? I also dual boot, and as soon as Windows is selected in the menu, it just boots, no delays.

> i see you have quite some experience, but i kinda want to ask for another opinion on this, there certainly must be away to use a single bootloader... if its not grub then maybe i can make the win7 loader boot linux?

I've no experience with that :), but it should be possible to tell Windows bootloader to boot Ubuntu, however, wouldn't it be a redirection for the Windows bootloader to Grub? Anyway, I'd like to hear what other think too.

---

### Post by wickwack on 2009-11-12
well i think grub could actually be disabled, or be made to boot without showing itself... just by uncommenting the hidden = true command thingy...

the thing is im planning on installing osx86 on the ubuntu drive as well, and ive seen guides for using grub to boot osx86... so i was trying to get grub to do the job... 

but ill check around to see if i can use win7 loader to boot osx86 too, if possible then i guess win7 loader it is...

or maybe i can uninstall grub2 and install grub legacy as there seems to be a lot more tutorials and support for it... oh well, ill keep this post updated until i find a solution... thanks!

---

### Post by wickwack on 2009-11-12
think i found a solution... apparently osx86 can be booted using windows boot loader... good ol uncle gates representing!

4th post from the top by **[[B][COLOR=#0099ff]limneos[/COLOR]**]("http://www.sevenforums.com/member.php?u=401"):

[/B][http://www.sevenforums.com/installation-setup/2774-osx-windows-7-dual-boot.html](http://www.sevenforums.com/installation-setup/2774-osx-windows-7-dual-boot.html)

---

