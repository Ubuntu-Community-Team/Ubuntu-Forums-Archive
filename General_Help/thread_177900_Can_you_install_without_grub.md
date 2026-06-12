---
title: "Can you install without grub?"
date: 2006-05-17
forum: General Help
---

### Post by DougC on 2006-05-17
Hi all,

I can't for the life of me remember the installation process, but is it possible to not install grub on any partition?

I'm going to triple boot with windows & suse; so i want to use SUSE's grub to but Ubuntu. Just curious as I realise if required I could just install grub on the ubuntu partition.

many thanks

---

### Post by dickohead on 2006-05-17
If you can't skip the Ubuntu Grub installation, you can always just boot into SuSE and rerun the grub installer from there.

---

### Post by Mustard on 2006-05-17
I'm pretty certain that when you reach the question on installing grub on the MBR, with the installer, if you answer 'No', then it installs grub to the ubuntu root partition rather than to the MBR.  So I would just answer 'No' to that question and that would retain your current grub setup.  Then you could go into your /boot/grub/ folder in ubuntu and copy and paste the relevant menu.lst entries into your SUSE /boot/grub/menu.lst.

---

### Post by DougC on 2006-05-17
Yeah thats what I thought, no big deal; would be slightly nicer to have the option to skip the grub install but hey ho.

Thanks all.

---

### Post by Herman on 2006-05-17
I agree with Mustard, if you choose 'No', as Mustard suggested, you can re-boot during the install using SUSE [grub's command line]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") to find the new Ubuntu kernel and boot it until you have the chance to edit SUSE grub's menu.lst as already mentioned.

There are two other ideas that I know of and have tested several times that have proven to be good. 

One is to choose 'No' when asked if you want to install Grub to MBR,  but choose to install GRUB to (fd0) and have a floppy disk in the floppy disk drive. Grub will be installed on a floppy disk that way and you can boot of that to complete your install and edit your  SUSE /boot/grub/menu.lst later. You must have your BIOS set to boot from floppy disk prior to beginning the install if you want to do it this way. That will give you a nice alternative boot method at the same time. You can just keep your grub boot floppy somewhere in case you need it some day.

Another alternative is to instead choose 'Go Back', which will put you in the Ubuntu Installer Main Menu. Then you can go down one line, and choose 'Install Lilo boot loader to hard disk'. On the next panel, you can choose 'Install Lilo to a target' and choose the line something similar to 'dev/hda: new Ubuntu partition'.
Lilo can safely remain unused in your Ubuntu installation and will also allow you to easily skip installing Grub to MBR. You will still need a way to re-boot during the install.
Either use SUSE [grub's command line]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"), or use  [GAG Boot Manager]("http://users.bigpond.net.au/hermanzone/p12.htm")  to re-boot with. Installing Lilo is another idea that has an added advantage of giving you a good emergency boot alternative in case anything ever goes wrong with SUSE or SUSE's GRUB. You never know when it might come in handy to have an extra method of booting up your sleeve. Just in case you can't get a grub menu at all, you can still boot Ubuntu via Lilo with GAG Boot Manager.
Mustard's suggestion will also do that just as well. I just think it's a good idea to include more alternatives in the same thread in case they might suit someone who is doing a search for this subject. I hope this will help someone. Regards, Herman :D

---

### Post by DougC on 2006-05-17
Floppy!!! what one of them :) Don't have those anymore.

Thanks herman i'm ok with reinstalling grub etc, I just couldn't remember is ubuntu had an option to not install it.

Thanks anyway though.

---

