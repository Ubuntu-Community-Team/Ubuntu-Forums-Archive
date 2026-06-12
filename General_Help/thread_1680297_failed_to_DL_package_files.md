---
title: "failed to DL package files????"
date: 2011-02-02
forum: General Help
---

### Post by liquidmonkey on 2011-02-02
am running ubunutu (10.10) in a oracle VM virtualbox and have been getting some errors with my update manager the last few days. 


i open the update manager
enter password
download seems to start
then pops up FAILED TO DOWNLOAD PACKAGE FILES and a CHECK YOUR INTERNET CONNECTION message.

weird thing is that i was able to download and install updates just fine a few days ago.

any ideas as to what could be the problem?



here are the packages from the error...

Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-sso-client/ubuntu-sso-client_1.0.4-0ubuntu1_all.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-sso-client/ubuntu-sso-client_1.0.4-0ubuntu1_all.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-dev_2.12.1-0ubuntu8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-dev_2.12.1-0ubuntu8_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-dev-bin_2.12.1-0ubuntu8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-dev-bin_2.12.1-0ubuntu8_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1022.35_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1022.35_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-bin_2.12.1-0ubuntu8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-bin_2.12.1-0ubuntu8_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.12.1-0ubuntu8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.12.1-0ubuntu8_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/u/udev/libudev0_162-2.1_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/u/udev/libudev0_162-2.1_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_162-2.1_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_162-2.1_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/o/openldap/libldap-2.4-2_2.4.23-0ubuntu3.2_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/o/openldap/libldap-2.4-2_2.4.23-0ubuntu3.2_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.142.20_all.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.142.20_all.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.142.20_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.142.20_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.4.4-6ubuntu2.1_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.4.4-6ubuntu2.1_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupscgi1_1.4.4-6ubuntu2.1_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupscgi1_1.4.4-6ubuntu2.1_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsdriver1_1.4.4-6ubuntu2.1_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsdriver1_1.4.4-6ubuntu2.1_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.4.4-6ubuntu2.1_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.4.4-6ubuntu2.1_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsmime1_1.4.4-6ubuntu2.1_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsmime1_1.4.4-6ubuntu2.1_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsppdc1_1.4.4-6ubuntu2.1_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsppdc1_1.4.4-6ubuntu2.1_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.4.4-6ubuntu2.1_all.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.4.4-6ubuntu2.1_all.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.4.4-6ubuntu2.1_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.4.4-6ubuntu2.1_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.4.4-6ubuntu2.1_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.4.4-6ubuntu2.1_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-ppdc_1.4.4-6ubuntu2.1_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-ppdc_1.4.4-6ubuntu2.1_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.4.4-6ubuntu2.1_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.4.4-6ubuntu2.1_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_2.32.0.1-0ubuntu1_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_2.32.0.1-0ubuntu1_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_2.32.0.1-0ubuntu1_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_2.32.0.1-0ubuntu1_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_2.32.0.1-0ubuntu1_all.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_2.32.0.1-0ubuntu1_all.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebackend1.2-0_2.30.3-2ubuntu2_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebackend1.2-0_2.30.3-2ubuntu2_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_2.30.3-2ubuntu2_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_2.30.3-2ubuntu2_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-7_2.30.3-2ubuntu2_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-7_2.30.3-2ubuntu2_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-13_2.30.3-2ubuntu2_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-13_2.30.3-2ubuntu2_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata1.2-1_2.30.3-2ubuntu2_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata1.2-1_2.30.3-2ubuntu2_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata-google1.2-1_2.30.3-2ubuntu2_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata-google1.2-1_2.30.3-2ubuntu2_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_2.30.3-2ubuntu2_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_2.30.3-2ubuntu2_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_2.30.3-2ubuntu2_all.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_2.30.3-2ubuntu2_all.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_2.30.3-2ubuntu2_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_2.30.3-2ubuntu2_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution/libevolution_2.30.3-1ubuntu7_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution/libevolution_2.30.3-1ubuntu7_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.30.3-1ubuntu7_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.30.3-1ubuntu7_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.30.3-1ubuntu7_all.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.30.3-1ubuntu7_all.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.30.3-1ubuntu7_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.30.3-1ubuntu7_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_3.6.12+build1+nobinonly-0ubuntu0.10.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_3.6.12+build1+nobinonly-0ubuntu0.10.10.1_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_3.6.12+build1+nobinonly-0ubuntu0.10.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_3.6.12+build1+nobinonly-0ubuntu0.10.10.1_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_3.6.12+build1+nobinonly-0ubuntu0.10.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_3.6.12+build1+nobinonly-0ubuntu0.10.10.1_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber_2.32.0.2-0ubuntu1_all.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber_2.32.0.2-0ubuntu1_all.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber-service_2.32.0.2-0ubuntu1_all.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber-service_2.32.0.2-0ubuntu1_all.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-gtk_0.5.10-0ubuntu5.1_all.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-gtk_0.5.10-0ubuntu5.1_all.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-common_0.5.10-0ubuntu5.1_all.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-common_0.5.10-0ubuntu5.1_all.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/u/udev/libgudev-1.0-0_162-2.1_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/u/udev/libgudev-1.0-0_162-2.1_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/u/utouch-grail/libutouch-grail1_1.0.15-0ubuntu1_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/u/utouch-grail/libutouch-grail1_1.0.15-0ubuntu1_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/s/simple-scan/simple-scan_2.32.0-0ubuntu3_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/s/simple-scan/simple-scan_2.32.0-0ubuntu3_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_3.0.5_all.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_3.0.5_all.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.12+build1+nobinonly-0ubuntu0.10.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.12+build1+nobinonly-0ubuntu0.10.10.1_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_2.32.0-0ubuntu3_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_2.32.0-0ubuntu3_i386.deb) 404  Not Found [IP: 130.239.18.173 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/i/indicator-sound/indicator-sound_0.4.9-0ubuntu1_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/i/indicator-sound/indicator-sound_0.4.9-0ubuntu1_i386.deb) 404  Not Found [IP: 130.239.18.173 80]

---

### Post by drewsus on 2011-02-02
Is your connection in the VM working otherwise? 

Open **Synaptic Package Manager** and go to *Settings -> Repositories*. Change "Download from:" to either "Main Server" or click other and then search for the best server. 

Then, close SPM and open terminal. 
Type in these commands:
```
sudo apt-get update
sudo apt-get upgrade
```

 And report back

---

### Post by liquidmonkey on 2011-02-08
thanks for the tip.
turns out i only needed to change my download location to the MAIN SERVER and then everything worked again.
only had 400 updates waiting ;)


thanks!

---

### Post by drewsus on 2011-02-08
g-g-g-g-g-g-reat! Glad I could help.

---

