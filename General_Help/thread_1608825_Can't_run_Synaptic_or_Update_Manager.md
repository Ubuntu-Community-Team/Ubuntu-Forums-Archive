---
title: "Can't run Synaptic or Update Manager"
date: 2010-10-29
forum: General Help
---

### Post by purple-spear on 2010-10-29
I've been running Xubuntu for almost a year, and haven't had any problems with it up till last week, when Update Manager said it couldn't install a lib package. Several days later, I saw the update notif saying that there were 12 available updates, so I went to install them, and it wouldn't install any of them. Now, if I try to start Update or Synaptic in any way, they'll open for about five seconds and then close. Any ideas why or how I can fix this?

---

### Post by J V on 2010-10-29
Have you tried opening them in a terminal and checking the output?

```
synaptic
```

Or something like this perhaps?

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by drs305 on 2010-10-29
Run the following commands and post the error messages, if any:
```

gksudo synaptic &
sudo apt-get update
sudo apt-get upgrade
```

The error messages should tell us where the problem is.

---

### Post by purple-spear on 2010-10-29
Running ```
sudo apt-get update && sudo apt-get upgrade
``` gave me this:

vanessa@vanessa-desktop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for vanessa: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  firefox firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support
  firefox-branding firefox-gnome-support icedtea-6-jre-cacao libc-bin
  libc-dev-bin libc6 libc6-dev libc6-i686 libnspr4-0d libnss3-1d libss2
  linux-image-2.6.32-25-generic openjdk-6-jre openjdk-6-jre-headless
  openjdk-6-jre-lib thunderbird ttf-symbol-replacement update-manager
  update-manager-core update-manager-kde wine wine1.2 xulrunner-1.9.2
27 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 87.7MB/121MB of archives.
After this operation, 3,719kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe ttf-symbol-replacement 1.2-0ubuntu6~lucid5 [56.6kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libc-bin 2.11.1-0ubuntu7.5 [723kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libc6 2.11.1-0ubuntu7.5 [3,779kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libc6-i686 2.11.1-0ubuntu7.5 [1,228kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libc-dev-bin 2.11.1-0ubuntu7.5 [213kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libc6-dev 2.11.1-0ubuntu7.5 [4,839kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe wine1.2 1.2-0ubuntu6~lucid5 [10.5MB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main update-manager 1:0.134.11 [803kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main update-manager-core 1:0.134.11 [200kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main firefox-gnome-support 3.6.12+build1+nobinonly-0ubuntu0.10.04.1 [81.0kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main firefox-branding 3.6.12+build1+nobinonly-0ubuntu0.10.04.1 [208kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main firefox 3.6.12+build1+nobinonly-0ubuntu0.10.04.1 [11.3MB]
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe firefox-3.5 3.6.12+build1+nobinonly-0ubuntu0.10.04.1 [80.4kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe firefox-3.5-branding 3.6.12+build1+nobinonly-0ubuntu0.10.04.1 [80.4kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe firefox-3.5-gnome-support 3.6.12+build1+nobinonly-0ubuntu0.10.04.1 [80.4kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main icedtea-6-jre-cacao 6b18-1.8.2-4ubuntu2 [346kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main openjdk-6-jre-lib 6b18-1.8.2-4ubuntu2 [5,776kB]
Get:18 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main openjdk-6-jre-headless 6b18-1.8.2-4ubuntu2 [27.3MB]
Get:19 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main openjdk-6-jre 6b18-1.8.2-4ubuntu2 [258kB]
Get:20 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main thunderbird 3.0.10+build1+nobinonly-0ubuntu0.10.04.1 [10.4MB]
Get:21 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main update-manager-kde 1:0.134.11 [50.0kB]
Get:22 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe wine 1.2-0ubuntu6~lucid5 [39.9kB]
Get:23 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main xulrunner-1.9.2 1.9.2.12+build1+nobinonly-0ubuntu0.10.04.1 [9,384kB]
Fetched 87.7MB in 9min 58s (147kB/s)                                           
Preconfiguring packages ...
(Reading database ... 173553 files and directories currently installed.)
Preparing to replace linux-image-2.6.32-25-generic 2.6.32-25.44 (using .../linux-image-2.6.32-25-generic_2.6.32-25.45_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.32-25-generic ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.32-25-generic_2.6.32-25.45_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done
Preparing to replace ttf-symbol-replacement 1.1.42-0ubuntu4 (using .../ttf-symbol-replacement_1.2-0ubuntu6~lucid5_all.deb) ...
Unpacking replacement ttf-symbol-replacement ...
Preparing to replace libc-bin 2.11.1-0ubuntu7.4 (using .../libc-bin_2.11.1-0ubuntu7.5_i386.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for fontconfig ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.32-25-generic_2.6.32-25.45_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by drs305 on 2010-10-29
You are having an installation problem with linux-image-2.6.32-25-generic.

You can check which kernel you are currently running with:
```
uname -r
```

You may be running an earlier kernel (like -23 rather than -25, or just a earlier version of the same one (2.6.32-25.32 vs 2.6.32-35.45).

If you are running the same kernel (-25) if you have an earlier kernel available via Grub you may first want to boot into that one. If not, you can try to clear it from your running system anyway. It shouldn't make a difference but won't hurt to use a different version if possible.

Try this, which may clear the error by trying to fix any broken packages:

```
sudo apt-get -f install
```

If that doesn't work, try clearing your cache and the dpkg list:
```
sudo apt-get clean
sudo dpkg --clear-avail
sudo apt-get update

```

---

### Post by purple-spear on 2010-10-29
Now I can run Update manager, but it still gives me the same error report as before.

---

### Post by drs305 on 2010-10-29
If you are still getting this error:
> Unpacking replacement linux-image-2.6.32-25-generic ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.32-25-generic_2.6.32-25.45_i386.deb (--unpack):

Try clearing it with this:
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/linux-image-2.6.32-25-generic_2.6.32-25.45_i386.deb
sudo apt-get -f install
```

---

### Post by purple-spear on 2010-10-29
That did it! Thanks so much.

---

