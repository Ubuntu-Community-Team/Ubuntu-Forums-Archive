---
title: "Removing old kernels"
date: 2009-10-05
forum: General Help
---

### Post by chris.martin2 on 2009-10-05
I'm dual booting Ubuntu and Windows, with limited free space on my Ubuntu partition.  I noticed the large number of kernels piling up in my grub boot menu and decided that would be a good place to free up some hard drive space.  I opened Synaptic, searched for linux-image, and found two old kernels and deleted them.  I still, however, have 4 more kernel entries in my boot.lst (plus the recovery mode for each),  but I can't seem to find these to delete them.  My boot.lst is being regenerated,  so somewhere in that script, it is finding evidence of these kernels,  but synaptic can't find them.

Any ideas how to find and delete these?

Chris

---

### Post by slakkie on 2009-10-05
Which Ubuntu version are you using?

---

### Post by chris.martin2 on 2009-10-05
I'm using Jaunty,  my current kernel version is 2.6.28-15-generic, but also showing up are 2.6.22-16-generic,2.6.22-15-generic, 2.6.22-14-generic, and 2.6.20-16-generic

---

### Post by slakkie on 2009-10-05
```

rmkernel () {
        local cur_kernel=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
        local kernel_pkg="linux-(image|headers|ubuntu-modules|restricted-modules)"
        local meta_pkg="${kernel_pkg}-(generic|i386|server|common|rt|xen|ec2)"
        sudo aptitude purge $(dpkg -l | egrep $kernel_pkg | egrep -v "${cur_kernel}|${meta_pkg}" | awk '{print $2}')
}

```

Put this in your .bashrc file, then source .bashrc (or run bash) and then rmkernel. It will remove all your kernels except your running kernel.

---

### Post by arrange on 2009-10-05
Which kernels are installed (find out via Synaptic or by running **dpkg -l | grep linux-image**)?

---

### Post by chris.martin2 on 2009-10-05
slakkie - when running that script, it rewrites the grub menu, and I'm getting this output:[FONT=monospace]

Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.22-16-generic
Found kernel: /boot/vmlinuz-2.6.22-15-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/vmlinuz-2.6.20-16-generic
Found kernel: /boot/memtest86+.bin

So I'm guessing that those are still there.  Can I just go to /boot and delete the listed files(with the exception on the first one, of course)


arrange - I only get linux-image-2.6.28-15-generic, and linux-image-generic from that command,  which is why Synaptic isn't able to do anything with it


[/FONT]

---

### Post by slakkie on 2009-10-05
Yeah, should be save to remove them. They come from a different releases.. 


2.6.20.x is from 7.04
2.6.22.x is from 7.10

See also [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_history_of_common_programs](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_history_of_common_programs)

---

### Post by scouser73 on 2009-10-05
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

### Post by Foxcow on 2009-10-06
> **scouser73 said:**
> Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don’t need anymore.

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



Thank you!

---

### Post by ispy on 2009-10-06
forgive me if i'm wrong, but won't ```
apt-get autoremove
``` delete old kernels?

---

### Post by arrange on 2009-10-06
> **ispy said:**
> forgive me if i'm wrong, but won't ```
apt-get autoremove
``` delete old kernels?

Generally speaking - no.

---

### Post by chris.martin2 on 2009-10-06
Thanks all for the replies.  The specific problem was that synaptic was NOT detecting these kernels.  As slakkie pointed out, they are from previous releases of Ubuntu[which is probably why Synaptic no longer recognizes them], so I will simply search out these specific files and delete them.

---

### Post by witeshark17 on 2010-03-18
In my case the search *linux-image* works :popcorn:

---

### Post by soltanis on 2010-03-18
Generally removing all kernels except your running one is a bad idea. You should keep at least one or two older kernels to fall back on.

---

### Post by witeshark17 on 2010-03-19
> **soltanis said:**
> Generally removing all kernels except your running one is a bad idea. You should keep at least one or two older kernels to fall back on. Yes, I only deleted 2; there are still 3 previous on my system. :popcorn:

---

### Post by wangsuda on 2010-03-19
> **soltanis said:**
> Generally removing all kernels except your running one is a bad idea. You should keep at least one or two older kernels to fall back on.
As stated earlier, I keep my original kernel and the latest one. No real reason why.

---

### Post by witeshark17 on 2010-03-19
I really prefer to keep the previous 2 or 3 as a precaution. :popcorn:

---

### Post by Cariboo1938 on 2010-05-15
> **scouser73 said:**
> 
......you can safely uninstall the old kernel, which will also result in the Grub menu being cleaned up.

Follow these steps to identify and remove any old kernels.

**1** - Go to **Terminal** and paste the following command: **uname -r**
It will print the version of the Linux kernel you are running, this is the one you want to keep. It should look something like this: ***2.6.20-16-generic***

**2** - Go to **Synaptic Package Manager** via the **System > Administration** menus

**3** - Paste this: **linux-image-2** into the search box of **Synaptic Package Manager**

**4** - Once you have located the old kernels, **hightlight** them and **right-click** then select **Mark For Complete Removal** then click **Mark** and then click **Apply**

[COLOR="Red"]**Be careful of what you remove. Ensure that you don’t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.**[/COLOR]



Is it OK to remove
>linux-headers-2.6._old-generic
>linux-headers-2.6._old
too?

---

### Post by gansvv on 2010-07-04
My boot partition is full and so I am getting errors in kernel upgrade.

```

dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-28-server_2.6.24-28.70_amd64.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./boot/vmlinuz-2.6.24-28-server': No space left on device

```

I only have commandline access to the server. When I try to remove an unused kernel

```

sudo apt-get remove  linux-image-2.6.24-23-server

```

I get this error:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  linux-image-server: Depends: linux-image-2.6.24-28-server but it is not going to be installed
  linux-ubuntu-modules-2.6.24-23-server: Depends: linux-image-2.6.24-23-server but it is not going to be installed
  linux-ubuntu-modules-2.6.24-28-server: Depends: linux-image-2.6.24-28-server but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Basically, it dings for any and every apt-get upgrade or install. 
Should I remove the .bak files from the boot partition to clear up space? Is this safe?

---

### Post by sgosnell on 2010-07-04
First, do what it says.  Run ```
sudo apt-get -f install
``` That will clear your broken packages, then you can remove whatever you like, as long as it isn't the kernel in use.

---

### Post by gansvv on 2010-07-05
Yes, I did try ```
apt-get -f install.
```

However, it seems I broke apt when I cleared some space and removed .bak files. Somehow it only ran partially; it got stuck with full 100% /boot partition and now, I get this error for the above command:

```

sudo apt-get -f install
[sudo] password for xxxxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-27 adblock-plus linux-headers-2.6.24-27-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-23-server
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 21.9MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 126702 files and directories currently installed.)

Removing linux-ubuntu-modules-2.6.24-23-server ...
FATAL: Could not open '/boot/System.map-2.6.24-23-server': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-23-server
Cannot find /lib/modules/2.6.24-23-server
update-initramfs: failed for /boot/initrd.img-2.6.24-23-server
dpkg: error processing linux-ubuntu-modules-2.6.24-23-server (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-23-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How can I restore "/boot/System.map-2.6.24-23-server"? Or can I just update apt to indicate it should check for that?

---

### Post by sgosnell on 2010-07-05
It's saying that kernel no longer exists.  It should already be gone.  Try update-grub and see if it's still shown in the grub menu.

---

### Post by gansvv on 2010-07-05
No its not. The kernel is gone.

```

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-28-server
Found kernel: /vmlinuz-2.6.24-27-server
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

How can I repair APT?

---

### Post by sgosnell on 2010-07-05
Apt is just a front-end for dpkg.  Try using Synaptic and see what it shows installed.  What you've already done should be sufficient, though.

---

### Post by topet2k12001 on 2010-08-02
> **scouser73 said:**
> Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don’t need anymore.

The old kernels are deliberately left installed and on the menu so you can boot a previous kernel if you have trouble with a new one. But if the new one works, you can safely uninstall the old kernel, which will also result in the Grub menu being cleaned up.

Follow these steps to identify and remove any old kernels.

**1** - Go to **Terminal** and paste the following command: **uname -r**
It will print the version of the Linux kernel you are running, this is the one you want to keep. It should look something like this: ***2.6.20-16-generic***

**2** - Go to **Synaptic Package Manager** via the **System > Administration** menus

**3** - Paste this: **linux-image-2** into the search box of **Synaptic Package Manager**

**4** - Once you have located the old kernels, **hightlight** them and **right-click** then select **Mark For Complete Removal** then click **Mark** and then click **Apply**

The results should show every available and installed kernel. A green box on the left indicates that the package is installed. The only linux-image you want installed is the latest one.

[COLOR=Red]**Be careful of what you remove. Ensure that you don’t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.**[/COLOR]

Your computer and Grub menu should now be free of old kernels.

Hi, new Ubuntu user here. Thanks for the instructions. Very straightforward and very easy to use!

---

### Post by Thras0 on 2011-01-08
tnkx for the info. i was looking for a way to clear my screen a bit

---

### Post by rajbeer_singh on 2011-01-12
hey 
      i have copied ur code into .bashrc file...but how to execute that file..and tell me all others commands

---

### Post by sgosnell on 2011-01-12
~/.bashrc is read (executed, if you will) every time you open a terminal.  If you want to see changes immediately without closing the terminal you're in, use ```
source .bashrc
```.

---

### Post by shokoup on 2011-02-06
> **scouser73 said:**
> Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don’t need anymore.

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


thank you>>>very useful and easy solution

---

### Post by wildmanne39 on 2012-07-08
Old thread closed.

---

