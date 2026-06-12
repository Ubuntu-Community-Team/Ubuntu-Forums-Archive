---
title: "How to build 2.6.34 amd64 kernel with load balancing patches for Lucid"
date: 2010-05-20
forum: General Help
---

### Post by rockorequin on 2010-05-20
This thread describes how to build a 2.6.34 kernel with load-balancing to cut down the number of load balancing wakeups. Running powertop on my amd64 PC shows that this kernel cuts down the number of wakeups by around 30%. See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524281/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524281/) for more details. 

1. Open a gnome-terminal and get root privileges:

```
sudo -s
```

2. Install required packages for building the kernel:

```
apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev
```

3. Download the 2.6.34 kernel source file:

```
cd /usr/src
wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.34.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.34.tar.bz2)
```

4a. Download the diff file for the patch from [http://lkml.org/lkml/diff/2010/5/21/435/1](http://lkml.org/lkml/diff/2010/5/21/435/1) and save as (eg) patch-load-balancing.diff. Move it to /usr/src once you have downloaded it.


5. Untar the source file:

```
cd /usr/src
tar xjf linux-2.6.34.tar.bz2
```

6. Link /usr/src/linux to the resulting folder:

```
cd /usr/src
# the folder linux may exist as a symlink from previously; if so, remove it
if [ -e linux ]; then rm linux; fi
ln -s linux-2.6.34 linux
```

7. Copy a configuration file to /usr/src/linux/.config (see attached for my 2.6.34 amd64 one or you can copy one of the ones in /boot/config* - but if you use eg the 2.6.32 file, you'll need to answer lots of questions when you start building because there are many new options in 2.6.34).

You can also get a valid configuration file by downloading deb files from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/) for your configuration (amd64 or x86), installing them, and copying the /boot/config-2.6.34-02630* file it creates to /usr/src/linux/.config. (This is how I created the attached one.)


8. Optional: Edit configuration file

```
cd /usr/src/linux
make menuconfig
```

and edit it to desired settings, eg 32 bit, turn debug on or off.

NOTE: for Lucid, you must have these settings in .config or it won't boot:

CONFIG_DEVTMPFS=y
CONFIG_DEVTMPFS_MOUNT=y


9a. Apply the load-balancing patch:

```
cd /usr/src/linux
patch -p1 < ../patch-load-balance.diff
```

Two hunks of the patch fail if you're patching against 2.6.34, so you have to manually edit the affected files. It patches against 2.6.35-rc1 just fine (although note that one of the hunks in the ureadahead trace patch below fails in 2.6.35-rc1.)

9b. (Optional) I also recommend installing the trace patch (attached) so ureadahead can configure itself to boot faster. Assuming it is in /usr/src:

```
cd /usr/src/linux
patch -p1 < ../0001-trace-add-trace-events-for-open-exec-an.patch

```

See [http://swiss.ubuntuforums.org/showthread.php?t=1434502](http://swiss.ubuntuforums.org/showthread.php?t=1434502) for more details.




10. Build kernel

```
cd /usr/src/linux
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-generic kernel_image kernel_headers
```

11. Install kernel and headers

```
cd /usr/src
dpkg -i *linux-2.6.34-*deb
```

12. Special last checks before rebooting:

a) I've noticed that make-kpkg/dpkg -i does not always create the /boot/initrd* file in Lucid. This will stop the kernel from booting. Try:

```
ls /boot/config-2.6.34-generic
```

If it shows nothing, create one with:

```
update-initramfs -c -k linux-2.6.34-generic
update-grub
```

If it didn't create it, you are probably missing a symlink in the /etc/kernel/postinst.d folder. To make dpkg create the initramfs file next time, do:

```
sudo ln -s /usr/share/doc/kernel-package/examples/etc/kernel/postinst.d/initramfs /etc/kernel/postinst.d/initramfs
```


b) If you're running nvidia proprietary drivers, run:

```
dkms status
```

and check that nvidia is listed as installed for the 2.6.34 kernel. If not, you'll need to install them separately.


13. Reboot and good luck... if the new kernel fails to boot, you should still be able to boot into the stock 2.6.32 kernel to try and figure out what went wrong, uninstall the 2.6.34 kernel, etc.


There are lots of web references on building the kernel, eg refer to [http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel](http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel).

---

### Post by feistybill on 2010-05-29
Thanks for this tutorial! I guess most people don't know about powertop, but since I used it and saw the huge number of load balancing wakeups I've been looking for a solution. So, thanks for your post :)

---

### Post by rockorequin on 2010-06-01
> **feistybill said:**
> Thanks for this tutorial!... :)

No worries! So did you succeed in patching and building the kernel? At least one person in the related bug says that the patched kernel made things worse, although it looks like they installed from a PPA rather than built it from scratch.

---

### Post by kircher on 2010-06-09
Firstly, I would like to raise a few issues. The procedure you have listed to do this kernel compile aren't in order. The first problem is that you list the trace patch procedure 4b before the kernel files have been untarred, so there is nothing to patch. Second problem is at step 6 where you are removing the /usr/src/linux directory that was not supposed to exist yet. They are simple errors, and it's not a big deal. I would remove the rm linux procedure in step 6, and then move step 4b and call it 6a or something.

My other issue is that doing:
```
fakeroot make-kpkg --initrd --append-to-version=-generic kernel_image kernel_headers
``` fails and I am at a loss to figure out why. These are the errors I got after trying to compile using the above command:
```
make[3]: *** [arch/x86/kernel/asm-offsets.s] Error 1
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.34'
make[1]: *** [debian/stamp/conf/kernel-conf] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.34'
make: *** [debian/stamp/conf/minimal_debian] Error 2
Failed to create a ./debian directory: Bad file descriptor at /usr/bin/make-kpkg line 971.
root@desktop:/usr/src/linux#
```

If any one knows what's happening here, it would be great if I could find out. I had a look at line 971 of /usr/bin/make-kpkg, but I don't know perl and I don't know if that is really the problem. I am using a custom .config file that I created using make menuconfig. I successfully patched the kernel code with the trace patch and the load balancing patch, and manually edited the sched.c and sched.h file, but the actual compilation failed.

I am attempting to build 2.6.34 for an AMD64 system. I have attached my .config file, for what it's worth, as well as the make-kpkg file

---

### Post by rockorequin on 2010-06-09
Thanks for the tips, I've moved things around to match.

Re the make-kpkg problem, you could try editing /usr/bin/make-kpkg and make it print out the command that is failing:

```
      # We call system, and not exec, since we are just creating a
      # ./debian dir here, _then_ we go and do the real command.
      print "Executing: $alt_cmd"
      system ($alt_cmd) == 0
        or die "Failed to create a ./debian directory: $!";

```

Executing the command directly might give a better idea as to why it is failing.

---

### Post by kircher on 2010-06-10
It seems that it may have been my custom .config file that was the problem. I used yours and it is compiling as we speak. I had selected Opteron/Athlon64/Hammer/K8 instead of generic-x86-64 in the processor selection, this may have been the problem, but I don't know

---

