---
title: "delete old updates?"
date: 2010-08-25
forum: General Help
---

### Post by jfbooth on 2010-08-25
I have a small hard drive and need to be space conscious.  There is a folder:

/var/cache/apt/archives

and it looks like it contains a collection of past updates from update manager (I'm guessing).  The question is, what, if anything, can I delete from this folder (or anywhere else), the contents of which are listed below? Thank you in advance.

jb@jb-desktop:/var/cache/apt/archives$ ls
acpi-support_0.136.1_i386.deb
base-files_5.0.0ubuntu20.10.04.2_i386.deb
firefox-3.5_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_all.deb
firefox-3.5-branding_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_all.deb
firefox-3.5-gnome-support_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_all.deb
firefox_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb
firefox-branding_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb
firefox-gnome-support_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb
flashplugin-installer_10.1.82.76ubuntu0.10.04.2_i386.deb
gdm_2.30.2.is.2.30.0-0ubuntu3_i386.deb
ghostscript_8.71.dfsg.1-0ubuntu5.3_i386.deb
ghostscript-cups_8.71.dfsg.1-0ubuntu5.3_i386.deb
ghostscript-x_8.71.dfsg.1-0ubuntu5.3_i386.deb
gnome-keyring_2.92.92.is.2.30.3-0ubuntu1.1_i386.deb
gparted_0.5.1-1ubuntu3_i386.deb
icedtea-6-jre-cacao_6b18-1.8.1-0ubuntu1_i386.deb
icedtea-6-jre-cacao_6b18-1.8-4ubuntu3_i386.deb
ifupdown_0.6.8ubuntu29.1_i386.deb
language-pack-en_1%3a10.04+20100714_all.deb
language-pack-en-base_1%3a10.04+20100714_all.deb
language-pack-gnome-en_1%3a10.04+20100714_all.deb
language-pack-gnome-en-base_1%3a10.04+20100714_all.deb
libdbusmenu-glib1_0.2.9-0ubuntu3.1_i386.deb
libdbusmenu-gtk1_0.2.9-0ubuntu3.1_i386.deb
libdjvulibre21_3.5.22-1ubuntu4.1_i386.deb
libdjvulibre-text_3.5.22-1ubuntu4.1_i386.deb
libfreetype6_2.3.11-1ubuntu2.2_i386.deb
libgcr0_2.92.92.is.2.30.3-0ubuntu1.1_i386.deb
libgp11-0_2.92.92.is.2.30.3-0ubuntu1.1_i386.deb
libgs8_8.71.dfsg.1-0ubuntu5.3_i386.deb
libkpathsea5_2009-5ubuntu0.2_i386.deb
libldap-2.4-2_2.4.21-0ubuntu5.3_i386.deb
libldap2-dev_2.4.21-0ubuntu5.3_i386.deb
libmysqlclient16_5.1.41-3ubuntu12.6_i386.deb
libpam-gnome-keyring_2.92.92.is.2.30.3-0ubuntu1.1_i386.deb
libpcsclite1_1.5.3-1ubuntu4.1_i386.deb
libsmbclient_2%3a3.4.7~dfsg-1ubuntu3.1_i386.deb
libwbclient0_2%3a3.4.7~dfsg-1ubuntu3.1_i386.deb
libwxbase2.8-0_2.8.10.1-0ubuntu1.2_i386.deb
libwxbase2.8-dev_2.8.10.1-0ubuntu1.2_i386.deb
libwxgtk2.8-0_2.8.10.1-0ubuntu1.2_i386.deb
libwxgtk2.8-dev_2.8.10.1-0ubuntu1.2_i386.deb
linux-headers-2.6.32-24_2.6.32-24.39_all.deb
linux-headers-2.6.32-24_2.6.32-24.41_all.deb
linux-headers-2.6.32-24-generic_2.6.32-24.39_i386.deb
linux-headers-2.6.32-24-generic_2.6.32-24.41_i386.deb
linux-image-2.6.32-24-generic_2.6.32-24.39_i386.deb
linux-image-2.6.32-24-generic_2.6.32-24.41_i386.deb
linux-libc-dev_2.6.32-24.39_i386.deb
linux-libc-dev_2.6.32-24.41_i386.deb
lock
mysql-common_5.1.41-3ubuntu12.6_all.deb
openjdk-6-jre_6b18-1.8.1-0ubuntu1_i386.deb
openjdk-6-jre_6b18-1.8-4ubuntu3_i386.deb
openjdk-6-jre-headless_6b18-1.8.1-0ubuntu1_i386.deb
openjdk-6-jre-headless_6b18-1.8-4ubuntu3_i386.deb
openjdk-6-jre-lib_6b18-1.8.1-0ubuntu1_all.deb
openjdk-6-jre-lib_6b18-1.8-4ubuntu3_all.deb
partial
python-apt_0.7.94.2ubuntu6.2_i386.deb
samba-common_2%3a3.4.7~dfsg-1ubuntu3.1_all.deb
samba-common-bin_2%3a3.4.7~dfsg-1ubuntu3.1_i386.deb
smbclient_2%3a3.4.7~dfsg-1ubuntu3.1_i386.deb
software-center_2.0.7_all.deb
thunderbird_3.0.6+build2+nobinonly-0ubuntu0.10.04.1_i386.deb
tzdata_2010k-0ubuntu0.10.04_all.deb
tzdata-java_2010k-0ubuntu0.10.04_all.deb
ubufox_0.9~rc2-0ubuntu2.1_all.deb
update-manager_1%3a0.134.10_all.deb
update-manager-core_1%3a0.134.10_i386.deb
update-manager-kde_1%3a0.134.10_all.deb
upstart_0.6.5-7_i386.deb
w3m_0.5.2-2.1ubuntu1.1_i386.deb
wx2.8-headers_2.8.10.1-0ubuntu1.2_i386.deb
xserver-common_2%3a1.7.6-2ubuntu7.3_all.deb
xserver-xorg-core_2%3a1.7.6-2ubuntu7.3_i386.deb
xulrunner-1.9.2_1.9.2.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb

---

### Post by Rubi1200 on 2010-08-25
[http://ubuntuforums.org/showpost.php?p=800462&postcount=1](http://ubuntuforums.org/showpost.php?p=800462&postcount=1)

Has useful tips for cleaning up the system.

---

### Post by dabl on 2010-08-25
Strangely, the linked "how-to" does not give the one command that will clear your cache:

```
sudo apt-get clean
```

;)

---

### Post by jfbooth on 2010-08-25
Rubi1200, thank you for reminding me of this HOWTO .. I had forgotten about it.

Dabi, thank you for the added tip.  I ran it .. it did not 'return' anything so I assume it deleted 'whatever'.  I assume the intent was to 'run' the command:

sudo apt-get clean

to further do some 'cleaning'.

thank you both for your 'noob' patience and you help.

---

