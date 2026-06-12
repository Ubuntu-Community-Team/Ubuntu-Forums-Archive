---
title: "ubuntu won't boot up after update of drivers in recovery mode"
date: 2011-11-17
forum: General Help
---

### Post by sancho_el_turcho on 2011-11-17
Ubuntu won't boot up. After grub, the cursor blinks for a long time, then I get some messages about apparmor starting bluetooth and pulseaudio  and lastly
cgroup already mounted or /dev/cgroups/cpu busy
according to mtab cgroup is already mounted on /dev/cgroups/cpu  

Here's what I tried to do

I'm using oneiric ocelot on a Dell T3400 workstation. I tried to upgrade NVIDIA driver downloaded from nvidia's website, I went into recovery mode using grub, chose to remount r/w, dropped into root shell and I installed the driver, rebooted using sudo reboot. Now ubuntu won't start. So any ideas to what is going on?

---

### Post by sancho_el_turcho on 2011-11-17
So, the problem was in the update of nvidia drivers. I tried several things don't know what really worked. I don't know if this is really necessary, but I ran apt-get remove --purge nvidia* and ran the nvidia installer script again. It gave a bunch of errors. Rebooted , ran the nvidia installer script , and was asked if I wanted to disable nouvae module. I said yes. That seemed to fix things. At reboot ubuntu booted up properly.
Anyway the lesson is.
Make sure to remove previous versions of drivers before installation
Try to follow the instructions [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) here which will probably causes least amount of headache.

---

