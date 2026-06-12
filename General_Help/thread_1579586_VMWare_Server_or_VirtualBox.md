---
title: "VMWare Server or VirtualBox?"
date: 2010-09-22
forum: General Help
---

### Post by ibates on 2010-09-22
I run Ubuntu 10.04 LTS on one HDD, and Windows XP Pro on another separate physical drive.  Ubuntu is my primary system being used probably 95% of the time.

But I need to be able to process files on my Windows XP HDD from within a Virtual Machine running on the Ubuntu Linux OS (or by some other method if one exists) such that I can do the jobs with Ubuntu running that I am currently doing by painstakingly rebooting each time I want to run a program under Windows.

I seek advice.

What is the simplest, and/or most effective way of doing this.

I have had a go at doing it according to the User Manual on VirtualBox 3.2.8, and despite being able to create a .vmdk file using the method described, I cannot gain access to it.

I have tried to install VMWare Server and, to say the least, that resulted in pure farce.  Doubtless my fault, but nonetheless, VMWare have to take some of the credit for their instructions being so complicated - as I read them at least.

Is there another alternative which doesn't cost me an arm and a leg?

Any suggestions will be taken seriously.  I am sick and tired of rebooting several times per session what with having to wait for so long each time for Windows to boot up.

---

### Post by halovivek on 2010-09-22
You can install any one of VMware or virtual box.
my experience is VMware is good in linux.
I am using VMware and its doing Great.

---

### Post by Jesus_Valdez on 2010-09-22
Personally I use Virtualbox and I have never face any problem, What .vmdk file can't you gain access to?

I use Virtualbox with XP in order to run certain software that only runs well on Windows, I edit those files either under Virtualbox or under my Windows partition without any problem.

---

### Post by tangchengguang on 2010-09-22
I prefer to VirtualBox. I have used VirtualBox for a long time and there is no problem. you can try again or turn to Google for help.

---

### Post by ibates on 2010-09-22
Thanks for all that.  It seems that these two are the only real alternatives.

In response to the question "What .vmdk file can't you gain access to?"; I am referring to the .vmdk file I have created using the syntax

*VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk - rawdisk /dev/sdc*

where* /path/to/file.vmdk* is, as it suggests, the path to the .vmdk file, and */dev/sdc* is the name of the HDD on which my Windows system and files reside.

If you believe there is something wrong with this, please advise me.  I am not all that confident about it all. particularly when it doesn't work for me.

---

### Post by ibates on 2010-09-22
Halvivek

Thank you for your thoughts.  What guidance (if any) did you use for installing VMWare Server?

I followed the User Manual instructions, step by step, but the installation produced error after error, so many times in fact that I lost all control of what was going on.  So I abandoned it, tried again, got essentially the same results, and abandoned it again.  I think I did it about five times, until finally, in exasperation, I gave up altogether and decided it was not a good option.

Is there a better option from VMWare than Server?

---

### Post by HermanAB on 2010-09-22
Howdy,

VMware Server 2.x is best avoided.  You should either use VMware Workstation ($80) or Vmware Player (free).

---

### Post by SeijiSensei on 2010-09-22
> **ibates said:**
> In response to the question "What .vmdk file can't you gain access to?"; I am referring to the .vmdk file I have created using the syntax

*VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk - rawdisk /dev/sdc*

I've never had to create anything from the command line using VB in Ubuntu.  I've just downloaded and installed the .deb file, then ran VirtualBox and clicked the "New" icon to start the VM creation wizard.  

It appears that .vmdk is a [VMWare file type]("http://en.wikipedia.org/wiki/VMDK") that Virtualbox can use.  Unless you are intending to run both VB and VMWare as virtual machine managers, I see no value in this approach.  Personally I'd just choose VirtualBox and use its GUI application for all the tasks, and I'm generally a command-line guy myself.

---

### Post by herdivet on 2010-09-27
I think many replies missed the original point.  The question is using a virtual machine to access an existing installation of Windows XP, not creating a vdisk and installing the OS on it.

That is the reason for using the createrawfmdk command.

When I tried this, the error I get appears to be related to access rights to the device holding the Windows XP installation.  Running 'sudo VirtualBox' appears to be a quick/dirty way around it.

Is this the same error that you are getting?

Bill

---

