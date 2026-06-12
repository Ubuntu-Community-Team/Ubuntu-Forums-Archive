---
title: "Install Lubuntu using Lubi (not Wubi)"
date: 2012-07-22
forum: General Help
---

### Post by oslub on 2012-07-22
Hello.

I have this laptop with Windows 7 and Ubuntu 12.04 in dual-boot and I really would like to have Lubuntu 12.04 as well to boot from it whenever I am using battery only and I just need to do some simple tasks.

I found this Lubi installer (Linux Ubuntu Installer) which allows to do the same thing Wubi does, except it installs any of Ubuntu derivatives and does it from Linux and not Windows. It is exactly what I needed, installing Lubuntu without having to burn to USB stick, mess again with the partitions, I have the iso downloaded already, it would be just install and use. And I don't care that it is not independent from the host system because Ubuntu will continue to be my main system.

I've tried already to proceed as described [here]("http://lubi.sourceforge.net/lubi.html"), however, even though all process was easy to follow and appeared to have been successfully executed, when I reboot PC, there isn't Lubuntu option to boot from in the Grub Menu.

Then I checked the requirements and it states that [I]Lubi will not work on any systems using LVM, EVMS, or another logical  volume manager, or filesystems other than ext2, ext3, reiserfs, vfat,  ntfs, jfs, or xfs.

[/I]My Ubuntu partition default filesystem is ext4, which is not listed in here. This may possibly be the reason why it doesn't work. Is there anyway to make Lubi work on ext4 filesystem? I've been on[ this thread]("http://ubuntuforums.org/showthread.php?t=441918&highlight=lubi+ext4&page=5") already and some other people have this issue as well, but there is no activity in there for over an year and no further updates about this.

---

### Post by Frogs Hair on 2012-07-22
I think Lubi is a dead project. [https://answers.launchpad.net/lubi/+question/189671](https://answers.launchpad.net/lubi/+question/189671)  . The link displays the 7.04 release which would rule out using Lubi on 12.04.

---

### Post by Lyfang on 2012-07-22
Try run from the Terminal & reboot:
```
sudo update-grub
```

If that does not solve the problem, in the short term perhaps VirtualBox may work, this could mean very slow performance compared running from a "normal" installation. However I know Lubuntu 12.04 with LXDE is a very fast system & light on resources compared to Ubuntu.

---

### Post by oslub on 2012-07-22
> **Lyfang said:**
> Try run from the Terminal & reboot:
```
sudo update-grub
```If that does not solve the problem, in the short term perhaps VirtualBox may work, this could mean very slow performance compared running from a "normal" installation. However I know Lubuntu 12.04 with LXDE is a very fast system & light on resources compared to Ubuntu.

I did it but no luck. 

I think the main problem may be lack of support to GRUB2, which is confirmed in [here]("https://answers.launchpad.net/lubi/+question/189671").

I wanted to use Lubi because it would be a very practical way to install Lubuntu, in which I could boot into when in battery mode. VirtualBox requires boot Ubuntu anyway, I use VB frequently but it doesn't fulfill this particular purpose. 

Lubi has so much potential, specially for those trying the alpha and beta versions, I was thinking about using it to try the newcoming feature, web apps on Unity, too bad it is not developed anymore, someone should grab it and update it, it is a very interesting project. Also there were some rumours that Lubuntu 12.04 would have its own Wubi, but it seems that it hasn't been accomplished as well.

---

### Post by oslub on 2012-07-22
> **Frogs Hair said:**
> I think Lubi is a dead project. [https://answers.launchpad.net/lubi/+question/189671](https://answers.launchpad.net/lubi/+question/189671)  . The link displays the 7.04 release which would rule out using Lubi on 12.04.

Yes indeed, thank you for that information.

The lack of support for GRUB2 is probably the main issue. Well, I have to resort the conventional way in order to get Lubuntu on my laptop, Live-CD and install. 

Just for the fun, I will create a separate ext3 partition with GParted to shelter Lubi filesystems and see if there is any change.

---

### Post by Lyfang on 2012-07-22
Why did you mark the thread as [SOLVED]? Have you considered trying to install (is done at your own risk as usual!) GRUB v1?

---

