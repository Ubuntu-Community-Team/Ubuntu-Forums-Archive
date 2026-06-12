---
title: "Is there a &quot;system report&quot; similar to Fedora's sosreport for Ubuntu?"
date: 2011-12-03
forum: General Help
---

### Post by LycoLoco on 2011-12-03
Hi all!

I'm wanting to reinstall my system and am moving from partitions to LVM. I know that I can back up all of my files by hand, and have already done so, but I was also wondering if there's a system report for Ubuntu similar to the sosreport on Fedora that collects files such as what kernel is running, what drivers are loaded, and various configuration files for common services and puts them into an archive file. This would make my life easier in the future if I want to make backups of the system files.

Thanks in advance!

---

### Post by Habitual on 2011-12-04
n/m

---

### Post by Lars Noodén on 2011-12-04
Store for later:

```

dpkg --get-selections > packages.txt

```

To restore:

```

sudo dpkg --set-selections < packages.txt
sudo apt-get -u dselect-upgrade

```

That will get your system files, but not the configuration files.  You'll have to get those separately.

---

### Post by oldfred on 2011-12-04
Not familiar with sosreport. But I normally run these as part of my rsync backup.

Various hardware listings/configurations
dpkg --get-selections > ubuntu-files
bash ~/Downloads/boot_info_script.sh
lshw -html > ~/hardware_info.html
udevadm info --export-db > file.txt
dmidecode > bios.txt

Boot info script you have to download, but I think all the rest is just Linux.

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

