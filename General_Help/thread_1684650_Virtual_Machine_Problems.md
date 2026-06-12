---
title: "Virtual Machine Problems"
date: 2011-02-09
forum: General Help
---

### Post by jhunter182 on 2011-02-09
Hello everyone, I have usually been quite successful in googling my questions on the internet and finding fixes for them. This time, I am unable to find anything remotely close to what I would like solved. I am a student running ubuntu and my school offers free autocad software to its students available for downloading and installing on their personal computers. I am running a linux machine and am unable to install this into linux. My computer is a dual-boot windows 7 and ubuntu 10.10. I have used a program called disk2vhd to create a virtual image of my windows machine and I suspect it would run perfectly although it won't work. I am using Virtualbox and I was not having an issue with that. My issue within this is that when I made a vhd of my windows OS, it also captured the grub bootloader. When I run my windows vhd file inside of virtualbox it gets stuck before it can even begin at "grub restore>". I haven't found any commands that work in that command prompt except for "ls" and "root". I would like to be able to use this cad software without having to reboot my computer as it is a pain to do so I would appreciate any and all help.

---

### Post by gordintoronto on 2011-02-09
Have you tried booting the vhd in Hyper-V?

When you created the vhd, did you specify to only include your C: drive?

---

### Post by zabsv on 2011-02-09
I would try booting the virtualbox from a windows cd and use that to restore the boot record of the virtual disk.
Try searching for something like "restore mbr <your windows version>" and you should find a solution.

---

### Post by jhunter182 on 2011-02-09
I do not have a windows installation cd as I got the computer as a gift as a graduation gift and I want to run windows in my linux machine so hyper-v is not an option as it is a virtual emulator designed to run other OS's in windows. I want to run windows in linux. I did specify for it to include only my C:/ drive but it still captures the grub bootloader and goes to the screen grub restore screen. is there a way I can restore the mbr without an installation disk and then capture the vhd and then restore the grub bootloader to get linux back? I would have a working vhd file then and everything should work, correct?

---

### Post by techunit on 2011-02-09
Why don't you just install the software in your windows partition? That is the reason you have it right? Don't bother with virtual machines if you don't need it.

---

### Post by jhunter182 on 2011-02-09
I never boot my computer into windows to do much if anything at all since I got a dual boot with linux. I want to have a virtual windows because i don't want to have to reboot my computer every time i need to run the programs I want to run. Also, linux has a native "C" compiler so all i do is type my programs (homework) into a text editor and tell it to compile. I like linux so much more, i just want to have a virtual machine for the few things in windows I want to do and then not have to shut my computer off to get back to linux

---

### Post by YesWeCan on 2011-02-09
Well, if you cannot replace Grub then you need to fix Grub. What if you created a Ubuntu VM and booted into it. Then, with Windows Virtual HD attached, run update-grub and install grub to the Windows disk? Like you might do in the real world.

---

### Post by techunit on 2011-02-12
> **jhunter182 said:**
> I never boot my computer into windows to do much if anything at all since I got a dual boot with linux. I want to have a virtual windows because i don't want to have to reboot my computer every time i need to run the programs I want to run. Also, linux has a native "C" compiler so all i do is type my programs (homework) into a text editor and tell it to compile. I like linux so much more, i just want to have a virtual machine for the few things in windows I want to do and then not have to shut my computer off to get back to linux
Then why keep windows around? It just doesn't make sense. You have a working solution.

If your installing Windows from your restore disk you are going to run into trouble because it is already installed on your system.

Good Luck.

---

### Post by jhunter182 on 2011-02-14
I haven't gotten rid of windows yet because I haven't gotten a working virtual machine of windows 7. I still need windows for some things until I can get it working properly. I do not have any restore disks or installation disks as I got the computer and it was preinstalled on it. I then proceded to install ubuntu 10.10 on it as a dual boot. Is there a way that I can make the windows bootloader the default? if I can do this then I think I can get my vhd file to work properly as it won't need ubuntu to run. I'll then just run an update-grub in linux and everything should fix itself I believe.

---

