---
title: "Yet another VM / Dual-boot Question"
date: 2011-09-03
forum: General Help
---

### Post by MarkEastwood on 2011-09-03
Hi,

I am new to ubuntu and there is something I would like to be able to do with it. Its probably a no brainer for anyone with experience running virtual machines.

My system has 2 drives, one with ubuntu (which is currently my preferred system) and one with windows (unfortunately vista and also unfortunate that I cant get away from it since it contains some software that I need).

I am currently able to boot into either system, but what I would like to do is boot up in ubuntu and then run a virtual machine that is actually the windows operating system already installed on the other drive, so that there would be in effect two ways of using my vista system, one is to boot it directly and the other is by virtual machine through ubuntu, and changes made using one method to be reflected when using the the other.

Is this generally achievable using VM software?

---

### Post by apollothethird on 2011-09-03
> **MarkEastwood said:**
> Hi,

I am new to ubuntu and there is something I would like to be able to do with it. Its probably a no brainer for anyone with experience running virtual machines.

My system has 2 drives, one with ubuntu (which is currently my preferred system) and one with windows (unfortunately vista and also unfortunate that I cant get away from it since it contains some software that I need).

I am currently able to boot into either system, but what I would like to do is boot up in ubuntu and then run a virtual machine that is actually the windows operating system already installed on the other drive, so that there would be in effect two ways of using my vista system, one is to boot it directly and the other is by virtual machine through ubuntu, and changes made using one method to be reflected when using the the other.

Is this generally achievable using VM software?

Yes.  It's easily done.  When in (pure) Windows Vista save all your important data to a shared drive or partition.  Use this drive or partition as your configured "My Documents" area.

You can easily install VirtualBox from the repo.  Just type VirtualBox in the Ubuntu Launchmenu.  Then follow the prompts from the VirtualBox to install Windows Vista.  Make the same drive or partition your default data drive.  Configure your "My Documents" area to be that drive.

If you use Outlook in Vista, configure your system to find your "personalfiles.pst" file there also.  When you boot between Pure Vista and VM Vista the files would be common.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by MarkEastwood on 2011-09-03
Thanks for the quick reply

Maybe I am misunderstanding, but what I am trying to do is not reinstall an operating system but to point to an install that already exists. I want this operating system to be usable as is, and just boot to it through ubuntu as the virtual machine. Its not data that Im worried about but programs that are installed that I cant easily get back. Is this what you meant?

I am trying to add the hard disk to the virtual machine I created in VirtualBox, but it doesn't allow me to select this drive. I can click on add when I select a folder in this drive, but nothing happens.

---

### Post by e79 on 2011-09-03
> **MarkEastwood said:**
> 
I am currently able to boot into either system, but what I would like to do is boot up in ubuntu and then run a virtual machine that is actually the windows operating system already installed on the other drive, so that there would be in effect two ways of using my vista system, one is to boot it directly and the other is by virtual machine through ubuntu, and changes made using one method to be reflected when using the the other.

Is this generally achievable using VM software?

As far as I know, it cannot be done. Your only choice would be to do a P2V (Physical to Virtual), cloning your physical Vista Installation and turning it into a Virtual Machine, with the help of [VMware Converter]("http://www.vmware.com/products/converter/") or this [P2V conversion]("http://www.virtualbox.org/wiki/Migrate_Windows") from VirtualBox per example.

The reason is the virtualisation software can only read virtual machine files, as .vdi for VirtualBox and .vmdk for VMware.

Hope this help

---

### Post by apollothethird on 2011-09-03
> **MarkEastwood said:**
> Thanks for the quick reply

Maybe I am misunderstanding, but what I am trying to do is not reinstall an operating system but to point to an install that already exists. I want this operating system to be usable as is, and just boot to it through ubuntu as the virtual machine. Its not data that Im worried about but programs that are installed that I cant easily get back. Is this what you meant?

I am trying to add the hard disk to the virtual machine I created in VirtualBox, but it doesn't allow me to select this drive. I can click on add when I select a folder in this drive, but nothing happens.

The Virtual Machines are machines that are created by the Virtual Software.  The will not boot already running OS'.  You can use Clonezilla to backup your already installed OS and use the restore option to bring that installation back to a Virtual machine.  That will be the best option for retaining your setups and avoiding a tull reinstall.

I understand now you're saying something different.  You're saying you want to Boot to an already installed OS, form it's native position.  But I don't think that's possible.

While I think of it, it theory it appears that there could be a way since you can select a physical Optical drive and boot to it natively.  I'll have to see what some of the experts have to say as to why it won't work.

It might be something very technical that would have to be provided by the VM developers ([http://virtualbox.org](http://virtualbox.org) or [http://vmware.com](http://vmware.com)).

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

