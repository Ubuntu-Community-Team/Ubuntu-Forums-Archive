---
title: "Broken graphics -Nvidia mismatch after update,"
date: 2011-05-01
forum: General Help
---

### Post by Sun_Coaster on 2011-05-01
Broken graphics after nvidia update. 
ReBoot ends at a login prompt and nothing on CTL-ALT-F7,

On a 10.10 gnome 2.32 machine with an Nvidia GEforce210.

Today an update came through the update manager for the following:
nvidia-current
nvidia-glx-185
nvidia-current-modaliases

After a reboot, it would not start a GUI.
I've seen this before, and either updating the module or updating the driver should fix it.
[B]
Option One:[/B]
CTL-ALT-F1, then login
```
sudo su -
apt-get install linux-headers-$(uname -r)
apt-get install linux-image-$(uname -r)
shutdown -g0
```----------------------------------
If that does not work, and in this case there was a driver mismatch:
> fgrep NVRM /var/log/messages
:
NVRM: API mismatch: the client has the version 270.41.06, but
NVRM: this kernel module has the version 260.19.36.  Please
NVRM: make sure that this kernel module and all NVIDIA driver
NVRM: components have the same version.[B]Option Two: install a new nvidia driver.
[/B]CTL-ALT-F1, then login
```
sudo su -
service gdm stop
rm /tmp/.X*-lock
wget download.nvidia.com/XFree86/Linux-x86/270.41.06/NVIDIA-Linux-x86-270.41.06.run
chmod 777 N*06.run
./NVIDIA-Linux-x86-270.41.06.run
nvidia-xconfig

shutdown -g0
```Now everything works as it should.
I hope this may help others.

Rob 
HTPC: Giada N20, Maverick Meerkat, Gnome 2.32, Moomex, Cairo. XBMC, LiveStation, RadioTray etc.
Notebook: EEE dual boot Win7/Natty Narwhal, Unity->Classic->Gnome3.

---

### Post by rtsome on 2011-05-02
I have same "api mismatch" message after installation of new (270) proprietary driver and reboot.
Nothing above helps.
amd64 architecture.

---

### Post by solitaire on 2011-05-02
You have to purge ALL the Nvidia drivers before installing the latest drivers.

The same happened to me last week. Can't remember the exact commands, but basically the Nvidia installer does not remove all of the old drivers during the upgrade. So you need to purge all your Nvidia drivers then install the latest drivers.

---

### Post by rtsome on 2011-05-02
That did the trick.

---

