---
title: "&quot;Requires installation of untrusted packages&quot; error when installing Unity?"
date: 2010-10-31
forum: General Help
---

### Post by TheNerdAL on 2010-10-31
So I am trying to install Unity but it gives me an "Requires installation of untrusted packages" error and I don't know how to fix it. Can anyone help me? :( 

Thanks!

---

### Post by sikander3786 on 2010-10-31
Did you simply try changing the update server and choose the respective one for your territory?

Edit: It might also be being caused by a missing GPG key. Which ppa for unity did you add and how?

---

### Post by TheNerdAL on 2010-10-31
> **sikander3786 said:**
> Did you simply try changing the update server and choose the respective one for your territory?

Edit: It might also be being caused by a missing GPG key. Which ppa for unity did you add and how?

I just used the Ubuntu Software Center to install Ubuntu-Netbook which has Unity in it.

---

### Post by TheNerdAL on 2010-10-31
:(

---

### Post by TheNerdAL on 2010-10-31
A terminal command let me install it.

---

### Post by jook on 2010-11-24
> **TheNerdAL said:**
> A terminal command let me install it.

I hate when people do this. Don't just say you fixed it, tell HOW. Otherwise I get here from google looking for someone who's solved the issue I'm having, only to find that they didn't explain the fix.
Your message is useless to others.

---

### Post by jayshomebrew on 2010-12-04
I just came into this same problem. I installed playonlinux and ubuntu 10.10 update manager would give me the message as stated by this thread.

So here's how I resolved it:
1. open a terminal
2. [FONT="Courier New"]sudo apt-get update[/FONT]
3. [FONT="Courier New"]sudo apt-get upgrade[/FONT]

I got the output:

[FONT="Courier New"]The following packages will be upgraded:
  playonlinux
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,436kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
WARNING: The following packages cannot be authenticated!
  playonlinux
[COLOR="Magenta"]Install these packages without verification [y/N]? y[/COLOR]
.
.
.
[/FONT]

:)

---

### Post by tajiknomi on 2010-12-04
> **jook said:**
> I hate when people do this. Don't just say you fixed it, tell HOW. Otherwise I get here from google looking for someone who's solved the issue I'm having, only to find that they didn't explain the fix.
Your message is useless to others.

Try repairing your gpg keys using the following commands. Open an Applications->Accessories->Terminal and type:

```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5
```
then in the same terminal type:
```
apt-key add ~/.gnupg/pubring.gpg
```

---

### Post by ron177 on 2010-12-22
> **tajiknomi said:**
> Try repairing your gpg keys using the following commands. Open an Applications->Accessories->Terminal and type:

```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5
```then in the same terminal type:
```
apt-key add ~/.gnupg/pubring.gpg
```

I have the same problems exactly except that the Software Center doesn't allow me to install *any* softwares. It gives me the same error messages. I tried the solution you gave but it's not working. Is there anyone out there who can help me with this? Please!

---

### Post by sikander3786 on 2010-12-23
> **ron177 said:**
> I have the same problems exactly except that the Software Center doesn't allow me to install *any* softwares. It gives me the same error messages. I tried the solution you gave but it's not working. Is there anyone out there who can help me with this? Please!
Please post the complete output of this command.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by esperai on 2011-02-04
> **sikander3786 said:**
> Please post the complete output of this command.

```
sudo apt-get update && sudo apt-get upgrade
```

hi sorry to hijack and sorry for the wall of text but I'm having the same problem - no matter what I try and install I get that error.

```
-sendto-empathy_2.32.1-0ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_2.32.1-0ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_2.32.1-0ubuntu1.1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/lcms/liblcms1_1.18.dfsg-1ubuntu2.10.10.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler7_0.14.3-0ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib5_0.14.3-0ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevdocument3_2.32.0-0ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevview3_2.32.0-0ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.32.0-0ubuntu1.3_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince-common_2.32.0-0ubuntu1.1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_2.32.0-0ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebackend1.2-0_2.30.3-2ubuntu2.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_2.30.3-2ubuntu2.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_2.30.3-2ubuntu2.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-7_2.30.3-2ubuntu2.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-13_2.30.3-2ubuntu2.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata1.2-1_2.30.3-2ubuntu2.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata-google1.2-1_2.30.3-2ubuntu2.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_2.30.3-2ubuntu2.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_2.30.3-2ubuntu2.1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_2.30.3-2ubuntu2.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/libevolution_2.30.3-1ubuntu7.3_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.30.3-1ubuntu7.3_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.30.3-1ubuntu7.3_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-exchange/evolution-exchange_2.30.3-0ubuntu2_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_3.6.13+build3+nobinonly-0ubuntu0.10.10.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_3.6.13+build3+nobinonly-0ubuntu0.10.10.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_3.6.13+build3+nobinonly-0ubuntu0.10.10.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcalctool/gcalctool_5.32.0-0ubuntu4_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gconf/gconf-defaults-service_2.31.91-0ubuntu3.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gdb/gdb_7.2-1ubuntu3_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgpod/libgpod4_0.7.95-1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/udev/libgudev-1.0-0_162-2.2_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox-plugins_0.13.1-0ubuntu6_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/brasero/libbrasero-media1_2.32.0-0ubuntu2.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox-plugin-cdrecorder_0.13.1-0ubuntu6_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.32.0-0ubuntu1.3_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.32.0-0ubuntu1.3_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/media-player-info/media-player-info_12-1~maverick1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox_0.13.1-0ubuntu6_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/libgvfscommon0_1.6.4-0ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-fuse_1.6.4-0ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/libwbclient0_3.5.4~dfsg-1ubuntu8.2_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.5.4~dfsg-1ubuntu8.2_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-backends_1.6.4-0ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs_1.6.4-0ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber_2.32.2-0ubuntu2_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber-service_2.32.2-0ubuntu2_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_3.10.6-1ubuntu10.2_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/libsane-hpaio_3.10.6-1ubuntu10.2_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_3.10.6-1ubuntu10.2_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_3.10.6-1ubuntu10.2_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/libhpmud0_3.10.6-1ubuntu10.2_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-cups_3.10.6-1ubuntu10.2_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/h/humanity-icon-theme/humanity-icon-theme_0.5.3.3_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/i/ibus/libibus2_1.3.7-1ubuntu4_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/i/ibus/ibus_1.3.7-1ubuntu4_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/i/ibus/python-ibus_1.3.7-1ubuntu4_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/i/ibus/ibus-gtk_1.3.7-1ubuntu4_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/i/indicator-appmenu/indicator-appmenu_0.0.13-0ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-gtk_0.5.10-0ubuntu5.2_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-common_0.5.10-0ubuntu5.2_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupscgi1_1.4.4-6ubuntu2.3_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsdriver1_1.4.4-6ubuntu2.3_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsmime1_1.4.4-6ubuntu2.3_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsppdc1_1.4.4-6ubuntu2.3_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgpod/libgpod-common_0.7.95-1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore3_6.6.2.6-1ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickwand3_6.6.2.6-1ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/libpam-gnome-keyring_2.92.92.is.2.31.91-0ubuntu4.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-utils_0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio_0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-x11_0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-gconf_0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-bluetooth_0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-esound-compat_0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse-mainloop-glib0_0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse-browse0_0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse0_0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple-bin_2.7.3-1ubuntu3.2_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.7.3-1ubuntu3.2_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_2.32.0-0ubuntu3.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client-gnome_1.4.5-0ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xdg-utils/xdg-utils_1.0.2+cvs20100307-1ubuntu0.1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/libsyncdaemon-1.0-1_1.4.5-0ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client_1.4.5-0ubuntu1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/python-ubuntuone-client_1.4.5-0ubuntu1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/utouch-grail/libutouch-grail1_1.0.16-0ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity/libunity0_0.2.46-0ubuntu5_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.7.7.dfsg-4ubuntu0.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/light-themes/light-themes_0.1.8.3_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.38.3_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-22_2.6.35-22.35_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-22-generic_2.6.35-22.35_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.5.4~dfsg-1ubuntu8.2_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus-share/nautilus-share_0.7.2-13.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.5.4~dfsg-1ubuntu8.2_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.5.4~dfsg-1ubuntu8.2_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-graphics-drivers-96/nvidia-96-modaliases_96.43.19-0ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_3.2.1-7ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_3.2.1-7ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-draw_3.2.1-7ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_3.2.1-7ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_3.2.1-7ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_3.2.1-7ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-math_3.2.1-7ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_3.2.1-7ubuntu1.1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_3.2.1-7ubuntu1.1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_3.2.1-7ubuntu1.1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_3.2.1-7ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base-core_3.2.1-7ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.2.1-7ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8o-1ubuntu4.3_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth-theme-ubuntu-logo_0.8.2-2ubuntu5.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.14.3-0ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/python-cupshelpers_1.2.3+20100723-0ubuntu8.1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.7.7.dfsg-4ubuntu0.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/papyon/python-papyon_0.5.1-0ubuntu2_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/simple-scan/simple-scan_2.32.0-0ubuntu4_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon-gtk_0.31+bzr506-0ubuntu5_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/aptdaemon_0.31+bzr506-0ubuntu5_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon_0.31+bzr506-0ubuntu5_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_3.0.7_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_5.5p1-4ubuntu5_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.7.2p7-1ubuntu2.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-common_1.2.3+20100723-0ubuntu8.1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-gnome_1.2.3+20100723-0ubuntu8.1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-udev_1.2.3+20100723-0ubuntu8.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/telepathy-haze/telepathy-haze_0.4.0-1ubuntu0.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/tomboy/tomboy_1.4.2-0ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubufox/xul-ext-ubufox_0.9~rc2-0ubuntu5.1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubufox/ubufox_0.9~rc2-0ubuntu5.1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-system-tools/gnome-system-tools_2.32.0-0ubuntu1.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity/unity_0.2.46-0ubuntu5_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/netbook-meta/ubuntu-netbook_2.035_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/uuid-runtime_2.17.2-0ubuntu1.10.10.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.9.0-0ubuntu7.3_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.9.0-0ubuntu7.3_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.3.2-6ubuntu3.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.12.0-1ubuntu5.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.13+build3+nobinonly-0ubuntu0.10.10.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/i/indicator-sound/indicator-sound_0.5.0.1-0ubuntu2_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gexiv2/libgexiv2-0_0.2.0-0ubuntu2.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox-ubuntuone-music-store/rhythmbox-ubuntuone-music-store_0.1.9-0ubuntu1_all.deb  Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
callie@ubuntu:~$ sudo apt-get update
Err http://security.ubuntu.com maverick-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com maverick Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com maverick-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
callie@ubuntu:~$ id

```

---

### Post by sikander3786 on 2011-02-05
@ **esperai**:

Welcome to the forums :-)

I hope you are able to browse the internet successfully.

And seems like your DNS settings are not working properly. Your router might have been configured as the DNS server and that returns problems like this while retrieving repository information.

You can either use your ISP's DNS server or if you don't know them, try the Google DNS. See Linux instructions on this page.

[http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

Let us know how that goes ;-)

---

### Post by teknotuck on 2011-03-05
Noticed a few people have this error which I too had, the problem a few have shown here is in relation to the package playonlinux as shown in the message below
---
WARNING: The following packages cannot be authenticated!
  playonlinux
Install these packages without verification [y/N]? n
---

If this is your issue, here is your fix. run this command as a regular user

gpg  --recv-keys E0F72778C4676186

This will generate some output as shown below.
gpg: requesting key C4676186 from hkp server keys.gnupg.net
gpg: key C4676186: public key "PlayOnLinux Packaging (PlayOnLinux packaging keys) <packages@playonlinux.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1


Once you have the new key then you need to import it into the system as shown below.

sudo apt-key add ~/.gnupg/pubring.gpg


Once you have done this doing your updates will not generate the error message about untrusted packages and updates should proceed as before.
:popcorn:

---

### Post by icspres on 2011-03-06
I'm having the same problem. I've just installed easypeasy on a couple of ASUS netbooks. Every software package I try to install throws this error. I've manually entered my DNS settings and know they're correct. I've checked that my server is the U.S. server. I've also used the instructions here to get a new key. Still getting the same error. What's next? Thanks in advance.

---

### Post by oldos2er on 2011-03-06
icspres, can you run **sudo apt-get update** in a terminal and post the output here?

---

### Post by icspres on 2011-03-06
Uhh...no need. It's working now. Thanks, Ann. Must have had something to do with the order or some such. I did this update command yesterday, the rest today, but doing the update command one more time has done the trick. Thanks so much, all of you. This is cool. I was into UNIX 20 years ago, briefly, and haven't given it much thought since. But netbooks serve a very important need for me, and are utterly useless with windows in terms of processing power. This is great. Very excited. Thanks.

---

### Post by oldos2er on 2011-03-06
Glad you resolved it, enjoy Ubuntu.

---

### Post by Bucic on 2011-05-07
I don't think it's a package specific issue so I've decided to post here

```

...@nx6125:~$ sudo apt-get update && sudo apt-get upgrade
Ign http://pl.archive.ubuntu.com natty InRelease
Ign http://pl.archive.ubuntu.com natty-updates InRelease                       
Ign http://archive.canonical.com natty InRelease                               
Ign http://extras.ubuntu.com natty InRelease                                   
Hit http://pl.archive.ubuntu.com natty Release.gpg                             
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://security.ubuntu.com natty-security InRelease                        
Hit http://pl.archive.ubuntu.com natty-updates Release.gpg                     
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://pl.archive.ubuntu.com natty Release                                 
Hit http://security.ubuntu.com natty-security Release.gpg                      
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://deb.opera.com stable InRelease                                      
Hit http://archive.canonical.com natty Release                                 
Hit http://extras.ubuntu.com natty Release                                     
Hit http://pl.archive.ubuntu.com natty-updates Release                         
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://security.ubuntu.com natty-security Release                          
Hit http://deb.opera.com stable Release.gpg                                    
Hit http://pl.archive.ubuntu.com natty/main Sources                            
Ign http://ppa.launchpad.net natty InRelease                          
Hit http://pl.archive.ubuntu.com natty/restricted Sources                      
Hit http://deb.opera.com stable Release                                        
Hit http://pl.archive.ubuntu.com natty/universe Sources                        
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://archive.canonical.com natty/partner Sources                         
Hit http://pl.archive.ubuntu.com natty/multiverse Sources                      
Get:1 http://ppa.launchpad.net natty Release.gpg [316 B]                       
Hit http://archive.canonical.com natty/partner amd64 Packages                  
Hit http://pl.archive.ubuntu.com natty/main amd64 Packages                     
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://pl.archive.ubuntu.com natty/restricted amd64 Packages               
Get:2 http://ppa.launchpad.net natty Release.gpg [316 B]                       
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://pl.archive.ubuntu.com natty/universe amd64 Packages                 
Hit http://extras.ubuntu.com natty/main amd64 Packages                         
Hit http://security.ubuntu.com natty-security/main Sources                     
Get:3 http://ppa.launchpad.net natty Release.gpg [316 B]                       
Hit http://pl.archive.ubuntu.com natty/multiverse amd64 Packages               
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://security.ubuntu.com natty-security/restricted Sources               
Ign http://pl.archive.ubuntu.com natty/main TranslationIndex                   
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://pl.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Hit http://security.ubuntu.com natty-security/universe Sources                 
Ign http://pl.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://ppa.launchpad.net natty Release.gpg                                 
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Ign http://pl.archive.ubuntu.com natty/universe TranslationIndex               
Get:4 http://ppa.launchpad.net natty Release [9,762 B]                         
Hit http://pl.archive.ubuntu.com natty-updates/main Sources                    
Ign http://ppa.launchpad.net natty Release                                     
Hit http://security.ubuntu.com natty-security/main amd64 Packages              
Hit http://pl.archive.ubuntu.com natty-updates/restricted Sources              
Get:5 http://ppa.launchpad.net natty Release [9,738 B]                         
Hit http://security.ubuntu.com natty-security/restricted amd64 Packages        
Hit http://pl.archive.ubuntu.com natty-updates/universe Sources                
Hit http://pl.archive.ubuntu.com natty-updates/multiverse Sources              
Hit http://security.ubuntu.com natty-security/universe amd64 Packages          
Get:6 http://ppa.launchpad.net natty Release [9,773 B]                         
Hit http://pl.archive.ubuntu.com natty-updates/main amd64 Packages             
Ign http://ppa.launchpad.net natty Release                                     
Hit http://security.ubuntu.com natty-security/multiverse amd64 Packages        
Hit http://ppa.launchpad.net natty Release                                     
Hit http://pl.archive.ubuntu.com natty-updates/restricted amd64 Packages       
Ign http://archive.canonical.com natty/partner Translation-en_US               
Hit http://pl.archive.ubuntu.com natty-updates/universe amd64 Packages         
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://ppa.launchpad.net natty Release                                     
Hit http://pl.archive.ubuntu.com natty-updates/multiverse amd64 Packages       
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://ppa.launchpad.net natty/main Sources/DiffIndex                      
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://pl.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://ppa.launchpad.net natty/main amd64 Packages/DiffIndex               
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://pl.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://pl.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://deb.opera.com stable/non-free Translation-en                        
Ign http://pl.archive.ubuntu.com natty-updates/universe TranslationIndex       
Get:7 http://ppa.launchpad.net natty/main Sources [701 B]            
Get:8 http://ppa.launchpad.net natty/main amd64 Packages [1,379 B]             
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://ppa.launchpad.net natty/main Sources/DiffIndex                      
Ign http://ppa.launchpad.net natty/main amd64 Packages/DiffIndex       
Ign http://ppa.launchpad.net natty/main TranslationIndex               
Hit http://ppa.launchpad.net natty/main Sources                        
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                        
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com natty-security/multiverse Translation-en        
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US     
Ign http://security.ubuntu.com natty-security/restricted Translation-en        
Ign http://pl.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://security.ubuntu.com natty-security/universe Translation-en_US       
Ign http://pl.archive.ubuntu.com natty/main Translation-en                     
Ign http://security.ubuntu.com natty-security/universe Translation-en          
Ign http://pl.archive.ubuntu.com natty/multiverse Translation-en_US            
Ign http://pl.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://pl.archive.ubuntu.com natty/restricted Translation-en_US            
Ign http://pl.archive.ubuntu.com natty/restricted Translation-en               
Ign http://pl.archive.ubuntu.com natty/universe Translation-en_US              
Ign http://pl.archive.ubuntu.com natty/universe Translation-en                 
Ign http://pl.archive.ubuntu.com natty-updates/main Translation-en_US          
Ign http://pl.archive.ubuntu.com natty-updates/main Translation-en             
Ign http://pl.archive.ubuntu.com natty-updates/multiverse Translation-en_US    
Ign http://pl.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://pl.archive.ubuntu.com natty-updates/restricted Translation-en_US    
Ign http://pl.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://pl.archive.ubuntu.com natty-updates/universe Translation-en_US      
Ign http://pl.archive.ubuntu.com natty-updates/universe Translation-en         
Err http://ppa.launchpad.net natty/main Sources                                
  404  Not Found
Err http://ppa.launchpad.net natty/main amd64 Packages                         
  404  Not Found
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Fetched 12.8 kB in 12s (1,043 B/s)                                             
W: GPG error: http://ppa.launchpad.net natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61E091672E206FF0
W: GPG error: http://ppa.launchpad.net natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43BB102C405A15CB
W: Failed to fetch http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

