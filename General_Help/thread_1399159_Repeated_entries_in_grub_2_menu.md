---
title: "Repeated entries in grub 2 menu"
date: 2010-02-05
forum: General Help
---

### Post by dpc_90 on 2010-02-05
Hi!

I'm running Ubuntu v.9.10.
I've made an update (don't ask me what) to Ubuntu.
Since I updated, the entry that allows me to run Ubuntu appears twice in grub 2 menu. How can I hide one of them?

Thank you!

---

### Post by oldos2er on 2010-02-05
Most likely the grub menu entries are for two different kernels, each with its own recovery mode settings. Can you post the output of **ls /boot** ?

---

### Post by dpc_90 on 2010-02-05
Sure, here it is:

abi-2.6.31-14-generic         memtest86+.bin
abi-2.6.31-19-generic         System.map-2.6.31-14-generic
config-2.6.31-14-generic      System.map-2.6.31-19-generic
config-2.6.31-19-generic      vmcoreinfo-2.6.31-14-generic
grub                          vmcoreinfo-2.6.31-19-generic
initrd.img-2.6.31-14-generic  vmlinuz-2.6.31-14-generic
initrd.img-2.6.31-19-generic  vmlinuz-2.6.31-19-generic

---

### Post by oldos2er on 2010-02-05
You just have the two kernels, vmlinuz-2.6.31-14-generic and vmlinuz-2.6.31-19-generic.

---

### Post by wojox on 2010-02-05
You can open a terminal and run:

```
sudo apt-get --purge linux-image-2.6.31-14-generic
```

```
sudo apt-get autoremove
```

---

### Post by scouser73 on 2010-02-05
> **dpc_90 said:**
> Sure, here it is:

abi-2.6.31-14-generic         memtest86+.bin
abi-2.6.31-19-generic         System.map-2.6.31-14-generic
config-2.6.31-14-generic      System.map-2.6.31-19-generic
config-2.6.31-19-generic      vmcoreinfo-2.6.31-14-generic
grub                          vmcoreinfo-2.6.31-19-generic
initrd.img-2.6.31-14-generic  vmlinuz-2.6.31-14-generic
initrd.img-2.6.31-19-generic  vmlinuz-2.6.31-19-generic

Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don’t need anymore.

The old kernels are deliberately left installed and on the menu so you can boot a previous kernel if you have trouble with a new one. But if the new one works, you can safely uninstall the old kernel, which will also result in the Grub menu being cleaned up.

Follow these steps to identify and remove any old kernels.

**1** - Go to **Terminal** and paste the following command: **uname -r**
It will print the version of the Linux kernel you are running, this is the one you want to keep. It should look something like this: ***2.6.20-16-generic***

**2** - Go to **Synaptic Package Manager** via the **System > Administration** menus

**3** - Paste this: **linux-image-2** into the search box of **Synaptic Package Manager**

**4** - Once you have located the old kernels, **hightlight** them and **right-click** then select **Mark For Complete Removal** then click **Mark** and then click **Apply**

The results should show every available and installed kernel. A green box on the left indicates that the package is installed. The only linux-image you want installed is the latest one.

[COLOR="Red"]**Be careful of what you remove. Ensure that you don’t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.**[/COLOR]

Your computer and Grub menu should now be free of old kernels.

---

### Post by WhiteHorse on 2010-02-05
```
sudo gedit /boot/grub/grub.cfg
```

Make changes to that file by removing the menu items you don't want. Then run:

```
sudo update-grub
```

---

### Post by drs305 on 2010-02-05
grub.cfg is different than menu.lst. It isn't meant to be edited. If tried, it won't work unless you first make it writable, even if you are editing it as root. 

Additionally, as soon as you run "sudo update-grub" the changes will be erased as grub.cfg will be regenerated.

Also, it is highly recommended using "gksu" or "gksudo" when opening graphical apps as root.
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by Leppie on 2010-02-05
i don't believe removing the default stock kernel is such a good idea. especially since it's the only other kernel besides the 19 version which only just was released. leaving the 14 kernel will provide you with an alternative in case the 19 kernel proves to cause issues on your system.
you can just hide the 14 kernel option in the menu. open the 10_linux script with an editor:
```
gksudo gedit /etc/grub.d/10_linux
```
find the next section and add the part in red:
```
while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"

[COLOR=Red]  #skip default stock kernel
  if [ "${version}" = "2.6.31-14-generic" ]; then
    break
  fi[/COLOR]
```save and exit the file, then run update-grub to regenerate your grub.cfg:
```
sudo update-grub
```your menu won't have the extra kernel anymore, but you will still be able to boot it if required.

---

