---
title: "Installing fonts and other stuff"
date: 2006-06-26
forum: General Help
---

### Post by chris9902 on 2006-06-26
Hi,

I have installed linux so I can test my web work without paying for a server but a couple of things have me stumped.

1) How do I install flash (I have AMD64 arc and keep getting errors)

2) Can I read/write to the files on my Windows hdd (NTFS)

3) How do I install fonts like Verdana?

4) Do I need to install Nvidia drivers. Everything works ok but it seems to lag when scrolling and it did this on my Windows PC before I got around to installing the drivers. I have a 7800GT so what would I need?

Thanks very much for any help.

---

### Post by Ramses de Norre on 2006-06-26
1) are you using 64bit? or just an amd 64 but running on 32 bit?

2) Read: yes; write: no; More [info]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only").

3) sudo aptitude msttcorefonts (I think it's in the package)

4) Installing the drivers will give you 3d rendering and better performance, take a look [here]("http://doc.gwos.org/index.php/Install_Nvidia_driver").

---

### Post by chris9902 on 2006-06-26
thanks a lot for the help.

I'm using the file "ubuntu-6.06-dvd-amd64.iso"

can I install "ubuntu-6.06-dvd-i386.iso" even though I have a AMD64 because i've been getting quite a lot of errors saying things are not built for this arc.

Thanks again.

---

