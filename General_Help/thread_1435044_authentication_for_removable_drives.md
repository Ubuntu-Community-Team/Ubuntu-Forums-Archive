---
title: "authentication for removable drives"
date: 2010-03-21
forum: General Help
---

### Post by linux_lenin on 2010-03-21
how to set up authentication for removable drives in ubuntu 9.10 ?

---

### Post by sisco311 on 2010-03-21
> **linux_lenin said:**
> how to set up authentication for removable drives in ubuntu 9.10 ?

Do you mean password authentication for mounting, unmounting, formatting... removable drives?

If so, then you have to edit the /usr/share/polkit-1/actions/org.freedesktop.udisks.policy file.
EDIT: I think in karmic it's /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy. Modify the commands accordingly.

First of all, backup the file. Open a terminal and run:
```
cd /usr/share/polkit-1/actions/
sudo cp org.freedesktop.udisks.policy org.freedesktop.udisks.policy-backup
cd
```

then open the file:
```
gksu gedit usr/share/polkit-1/actions/org.freedesktop.udisks.policy
```


An entry in the file looks like this:
```

  <action id="org.freedesktop.udisks.filesystem-mount">
    <description>Mount a device</description>
    <message>Authentication is required to mount the device</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

```

The description of each entry is self-explanatory, it's in human readable format.

Now if you want password authentication by an admin user in order to mount an external drive, then change the authentication mode from **yse** to **auth_admin** or **auth_admin_keep** (it's like auth_admin but the authorization is kept for a brief period):
```

  <action id="org.freedesktop.udisks.filesystem-mount">
    <description>Mount a device</description>
    <message>Authentication is required to mount the device</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>**auth_admin_keep**</allow_active>
    </defaults>
  </action>

```

You can change the authentication mode in other entries in a similar way.

Save the file and close the editor & you're done.

HTH

---

### Post by linux_lenin on 2010-03-22
Only empty text file is open.

---

### Post by sisco311 on 2010-03-22
> **linux_lenin said:**
> Only empty text file is open.

What's the output of:
```
pkaction
```and```
ls /usr/share/polkit-1/actions/
```?

---

### Post by tinsami1 on 2010-03-23
> **sisco311 said:**
> Now if you want password authentication by an admin user in order to mount an external drive, then change the authentication mode from **yse** to **auth_admin** or **auth_admin_keep** (it's like auth_admin but the authorization is kept for a brief period):
```

  <action id="org.freedesktop.udisks.filesystem-mount">
    <description>Mount a device</description>
    <message>Authentication is required to mount the device</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>**auth_admin_keep**</allow_active>
    </defaults>
  </action>

```

You can change the authentication mode in other entries in a similar way.

Save the file and close the editor & you're done.

HTH


Can this be used to allow regular users to mount read-only while allow admin users to mount read-write?

---

### Post by linux_lenin on 2010-03-23
**output of pkaction**

com.hp.hplip.policy
com.ubuntu.devicedriver.policy
com.ubuntu.systemservice.policy
com.ubuntu.usbcreator.policy
gdm.policy
org.debian.apt.policy
org.freedesktop.consolekit.policy
org.freedesktop.devicekit.disks.policy
org.freedesktop.devicekit.power.policy
org.freedesktop.devicekit.power.qos.policy
org.freedesktop.network-manager-settings.system.policy
org.freedesktop.policykit.policy
org.freedesktop.SystemToolsBackends.policy
org.gnome.clockapplet.mechanism.policy
org.gnome.cpufreqselector.policy
org.gnome.gconf.defaults.policy
screenresolution-mechanism.policy
gurulenin@gurulenin-desktop:~$ pkaction
org.freedesktop.devicekit.disks.drive-ata-smart-selftest
org.gnome.clockapplet.mechanism.settime
org.freedesktop.devicekit.disks.filesystem-lsof
com.hp.hplip.installplugin
org.debian.apt.change-repository
org.freedesktop.devicekit.disks.drive-ata-smart-retrieve-historical-data
org.freedesktop.devicekit.disks.filesystem-check
com.ubuntu.devicedriver.info
org.debian.apt.add-vendor-key
org.freedesktop.devicekit.disks.filesystem-mount
com.ubuntu.screenresolution.mechanism.dontzap
org.freedesktop.devicekit.disks.drive-detach
org.freedesktop.devicekit.disks.filesystem-unmount-others
org.freedesktop.devicekit.disks.linux-md
org.freedesktop.devicekit.disks.drive-eject
com.ubuntu.systemservice.setnoproxy
org.gnome.gconf.defaults.set-system
org.freedesktop.network-manager-settings.system.wifi.share.protected
org.debian.apt.install-packages
org.debian.apt.cancel-foreign
org.debian.apt.remove-vendor-key
org.freedesktop.devicekit.disks.cancel-job-others
com.ubuntu.devicedriver.install
org.freedesktop.network-manager-settings.system.hostname.modify
com.ubuntu.usbcreator.image
org.freedesktop.devicekit.power.hibernate
org.debian.apt.upgrade-packages
org.debian.apt.remove-packages
org.freedesktop.devicekit.disks.filesystem-check-system-internal
org.gnome.gconf.defaults.set-mandatory
org.freedesktop.devicekit.disks.drive-ata-smart-refresh
org.gnome.cpufreqselector
org.freedesktop.policykit.grant
com.ubuntu.systemservice.setproxy
org.freedesktop.systemtoolsbackends.self.set
org.debian.apt.upgrade-system
org.freedesktop.devicekit.power.suspend
org.debian.apt.get-trusted-vendor-keys
org.freedesktop.devicekit.power.qos.request-latency-persistent
org.freedesktop.devicekit.disks.filesystem-mount-system-internal
org.gnome.clockapplet.mechanism.configurehwclock
com.ubuntu.devicedriver.check
org.freedesktop.network-manager-settings.system.wifi.share.open
org.freedesktop.consolekit.system.restart
org.freedesktop.devicekit.disks.luks-lock-others
org.freedesktop.systemtoolsbackends.set
org.freedesktop.consolekit.system.restart-multiple-users
org.debian.apt.install-file
org.freedesktop.policykit.revoke
org.freedesktop.devicekit.power.qos.cancel-request
org.debian.apt.update-cache
org.freedesktop.devicekit.power.qos.set-minimum-latency
org.freedesktop.policykit.read
org.freedesktop.devicekit.disks.luks-unlock
org.freedesktop.devicekit.disks.drive-set-spindown
org.freedesktop.network-manager-settings.system.modify
com.ubuntu.systemservice.ispkgsystemlocked
com.ubuntu.systemservice.getproxy
com.ubuntu.usbcreator.bootloader
org.gnome.displaymanager.settings.write
org.gnome.clockapplet.mechanism.settimezone
com.ubuntu.systemservice.getkeyboard
org.freedesktop.devicekit.disks.change
com.ubuntu.systemservice.setkeyboard
com.ubuntu.devicedriver.update
org.freedesktop.devicekit.power.qos.request-latency
com.ubuntu.usbcreator.mount
org.freedesktop.devicekit.disks.change-system-internal
org.freedesktop.consolekit.system.stop
org.freedesktop.policykit.modify-defaults
org.freedesktop.devicekit.disks.filesystem-lsof-system-internal
com.ubuntu.usbcreator.format
org.freedesktop.policykit.exec
org.freedesktop.devicekit.disks.inhibit-polling
org.freedesktop.consolekit.system.stop-multiple-users
com.ubuntu.screenresolution.mechanism.configure


**output of ls /usr/share/polkit-1/actions/**

com.hp.hplip.policy
com.ubuntu.devicedriver.policy
com.ubuntu.systemservice.policy
com.ubuntu.usbcreator.policy
gdm.policy
org.debian.apt.policy
org.freedesktop.consolekit.policy
org.freedesktop.devicekit.disks.policy
org.freedesktop.devicekit.power.policy
org.freedesktop.devicekit.power.qos.policy
org.freedesktop.network-manager-settings.system.policy
org.freedesktop.policykit.policy
org.freedesktop.SystemToolsBackends.policy
org.gnome.clockapplet.mechanism.policy
org.gnome.cpufreqselector.policy
org.gnome.gconf.defaults.policy
screenresolution-mechanism.policy

---

### Post by sisco311 on 2010-03-24
You have to edit the /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy file:
```
sudo cp /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy{,-backup}
```

```
gksu gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy
```


> **tinsami1 said:**
> Can this be used to allow regular users to mount read-only while allow admin users to mount read-write?

Nope.

---

### Post by linux_lenin on 2010-03-26
oh great. Its working perfectly


thank you so much dear friend !!!!!!!!!!

mail your email address to <snip>

---

### Post by harreid on 2012-11-19
Thanks for all the above info sisco311.

I now have my usb external drive mounted and I can read from it, problem  is now I can't write to it, I get the message "you are not the owner"   and I can't edit permissions. I'm hoping you can help me again.

Many thanks.
  [[COLOR=#DD4814]****[/COLOR]]("http://ubuntuforums.org/member.php?u=244665")

---

### Post by wildmanne39 on 2012-11-19
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

