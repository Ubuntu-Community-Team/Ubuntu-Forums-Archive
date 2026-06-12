---
title: "virtualbox-ose-dkms"
date: 2011-03-31
forum: General Help
---

### Post by Lithic on 2011-03-31
Hi,

This is a complete newbie question and have no Ubuntu or VirtualBox experience, except that I have just  installed Ubuntu 10.10 using VirtualBox 4.0.4.

I am trying to set up a shared folder and cannot get past this step -
[I]
ubuntu@ubuntu-VirtualBox:~$ VBoxManage sharedfolder add "Ubuntu Netbook 32 bit" -name "share" -hostpath /home/your/shared/folder/VirtualBoxShare/[/I]

which reports that there is no registered machine name 'Ubuntu Netbook 32 bit' etc.

If I then try VBoxManage list vms I get:

[I]ubuntu@ubuntu-VirtualBox:~$ VBoxManage list vms
WARNING: The character device /dev/vboxdrv does not exist.
     Please install the virtualbox-ose-dkms package and the appropriate
     headers, most likely linux-headers-generic.[/I]

But in looking through the installed packages in the Ubuntu Software Center both virtualbox-ose-dkms and linux-headers-generic are already installed...

So I'm at a loss about what to do next...?

Thanks!

---

