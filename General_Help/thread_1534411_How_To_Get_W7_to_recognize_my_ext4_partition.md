---
title: "How To Get W7 to recognize my ext4 partition"
date: 2010-07-19
forum: General Help
---

### Post by amaz1ng on 2010-07-19
The problem: I have a file in my Ubuntu 10.04 home folder that I want to access from my Windows 7 install.

How can I get Windows 7 (64-bit) to recognize and view the files in my ext4 partition?

Thanks in advance.

---

### Post by rubylaser on 2010-07-19
I've never tried this as I don't have a Windows 7 machine at home, but here you go.
[http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/]("http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/")

---

### Post by etdsbastar on 2010-07-19
> **amaz1ng said:**
> The problem: I have a file in my Ubuntu 10.04 home folder that I want to access from my Windows 7 install.

How can I get Windows 7 (64-bit) to recognize and view the files in my ext4 partition?

Thanks in advance.

Ext3 is is the file system in Linux like  NTFS in Windows operating system. Accessing a Windows partition in  Linux is very simple nowadays as it provides native support with out  even a single driver. But to access a Linux   partition from Windows is one of the most difficult task for a  normal pc user, as Windows does not provide any support for Linux based  partitions. These days as Linux is advancing as a  regular Desktop Operating System, many of the users use both the  software in one single PC. So its necessary that the data from one OS is  accessible at the other end too. There are some useful tools for  Windows that can rescue you from this problem if you are an affected  one. The most recommended tool for this purpose is LTOOLS, which can  read and write files from your Windows file system to a ext2, ext3 or  ext4 partition.
 LTOOLS comes with two GUI’s and a set of  command line tools. One is a JAVA based GUI so called LTOOLSgui and the  other one is made of .NET programming  interface named LTOOLSnet. The installation of LTOOLS is like any other  Windows software installation and after the installation it creates one  start menu entry from where you can access all the tools to access your  Linux partition. LTOOLS can be run from any versions of Windows and its  very user friendly and easy to use.

Enjoy using ext3/ext4 on Windows.

[ Download the Software From Here]("http://www.it.fht-esslingen.de/%7Ezimmerma/software/ltools-6.12.zip").

---

### Post by amaz1ng on 2010-07-19
LTools crashed on install. While Ext2fsd claims to have worked, I can't browse the drive after restarting.

When I click on my ext4 drive (I labeled it D:), Windows wants to format it.

Thanks for the advice guys! Any other suggestions? I'll try the other ones that were mentioned in rubylaser's post.

---

### Post by etdsbastar on 2010-07-19
> **amaz1ng said:**
> LTools crashed on install. While Ext2fsd claims to have worked, I can't browse the drive after restarting.

When I click on my ext4 drive (I labeled it D:), Windows wants to format it.

Thanks for the advice guys! Any other suggestions? I'll try the other ones that were mentioned in rubylaser's post.

No problem, go with ruby laser, I don't know why this happened because i have used LTools perfectly on my dual-boot.

---

### Post by philinux on 2010-07-19
> **amaz1ng said:**
> The problem: I have a file in my Ubuntu 10.04 home folder that I want to access from my Windows 7 install.

How can I get Windows 7 (64-bit) to recognize and view the files in my ext4 partition?

Thanks in advance.

You'll need to create an NTFS partition. Windows cannot read ext4. Or sync the file with UbuntuOne and access ubuntuone from windows.

---

