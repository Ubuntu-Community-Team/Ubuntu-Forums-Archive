---
title: "Dual Boot Ubuntu 12.04 - 10.04"
date: 2012-04-18
forum: General Help
---

### Post by caveman7 on 2012-04-18
Hey guys. I'm currently using Ubuntu 12.04 Beta 2. I wanted to dual boot Ubuntu 10.04. Is that possible? Will Ubuntu 10.04's older grub version replace 12.04's newer version?

**UPDATE**

I installed 10.04 and 12.04's grub is replaced by the older version. Anybody knows how to upgrade the grub?

---

### Post by oldfred on 2012-04-19
If you run sudo update-grub your 10.04 install should see the 12.04 install and let you boot it.

Then when booted into the 12.04 install run this.

sudo grub-install /dev/sda

But each install has remembered to reinstall grub to sda on major updates. So you only want your main install to remember and get the other to forget.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions - if you uncheck everything then it should not reinstall.

---

