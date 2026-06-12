---
title: "kernal Problem - Upgrading Packages and/or Kernals"
date: 2009-12-19
forum: General Help
---

### Post by Gosport on 2009-12-19
I have been getting the "Kernal Problem" message "Your system encountered a serious kernel problem.  Your system might become unstable now and might need to be restarted.  you can help developers to fix the problem by reporting it."

Then, before I try to report the problem a new error pops up this time an "Application Problem".  "sorry, the program "npviewer.bin closed unexpectidly..." and I am given the option of reporting the problem.

I first try to report the "Kernal Problem" and I get "Invalid problem report" "This problem report is damaged and cannot be processed. IOError(13, 'Permission denied')"

So I close that window and try to report the "Application Problem".  Again I get an error "Problem in nspluginwrapper"  The problem cannot be reported: you have some obsolete package version installed. Please upgrade the following packages and check if the problem still occures: libavahi-client3, libavahi-common-data, libavahi-common3, libgtk2.0-0, libgtk2.0-common, libpython2.6, python, python-minimal, python2.6, python2.6-minimal, tzdata, x11-common

I think my question is, where is a good "how to" for upgradeing packages?
I have a 64 bit version of Karmic and this problem seems to have started when I upgraded.

Thank you.

---

### Post by Gosport on 2009-12-19
I am also getting this error message:

The problem cannot be reported:

You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

seahorse-plugins, adduser, devicekit-disks, initscripts, libavahi-client3, libavahi-common-data, libavahi-common3, libavahi-glib1, libgail-common, libgail18, libgtk2.0-0, libgtk2.0-common, libgudev-1.0-0, libnautilus-extension1, libpython2.6, libudev0, python, python-minimal, python2.6, python2.6-minimal, sysv-rc, sysvinit-utils, tzdata, upstart, x11-common

---

### Post by Sin@Sin-Sacrifice on 2009-12-19
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by Gosport on 2009-12-20
That was simple, I think.  Thank you.  I just copied and ran each line individually (I had to enter my administrator password after the first and I answered "y" for each additional question.  I haven't seen any errors yet, so it looks good.

---

