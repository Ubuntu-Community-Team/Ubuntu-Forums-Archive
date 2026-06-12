---
title: "no need to remove older kernels?"
date: 2011-11-14
forum: General Help
---

### Post by Chiel92 on 2011-11-14
Hi,

I've got a question about the old kernels listed in the grub menu.
I once had them nicely hidden behind an entry named "Previous versions" or something. So every time there was a new kernel, I didn't have to clean up the grub menu manually by removing the old kernels, because they were stored in one menu entry.

Now I installed another distro, but I don't know how to get the above working. When I search on google for this, I only see how to remove them. But I would like to save me some work :) Don't like to remove them each time.

Any hints appreciated.

---

### Post by oldos2er on 2011-11-14
Does the other distro use grub2? If so you could try Grub Customizer, [http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by Chiel92 on 2011-11-14
Thanks for replying. It's a nice gui to edit grub settings!
But I cannot find the feature I meant.

---

### Post by drs305 on 2011-11-14
The 'previous linux' option was introduced with Grub 1.99 as part of it's 'submenu' feature.

Check to see if your other OS is using Grub 1.99, and if not, see if you can upgrade to Grub 1.99. 

If you can't upgrade the other OS, you could always let your Ubuntu Grub control the boot process, even if you have the default set to boot the other one.

---

### Post by Chiel92 on 2011-11-14
> **drs305 said:**
> The 'previous linux' option was introduced with Grub 1.99 as part of it's 'submenu' feature.

Check to see if your other OS is using Grub 1.99, and if not, see if you can upgrade to Grub 1.99. 

If you can't upgrade the other OS, you could always let your Ubuntu Grub control the boot process, even if you have the default set to boot the other one.

How can I do the latter?

---

### Post by drs305 on 2011-11-14
> **Chiel92 said:**
> How can I do the latter?

If you boot into your Ubuntu installation in the normal manner (not with the LiveCD), just run the following. It will write the MBR to point to your existing Ubuntu Grub. If your boot drive is not **sda**, change the command to point to the correct drive.
```
sudo grub-install /dev/**sda**
sudo update-grub
```

You can read about some of the Grub 1.99 features (and how to set the default if it's hidden in the submenu) here:
[Grub 1.99 Changes]("http://ubuntuforums.org/showthread.php?p=10720322#post10720322")
[Grub 1.99 Submenus]("http://ubuntuforums.org/showthread.php?p=10720316#post10720316")

---

### Post by Chiel92 on 2011-11-15
Thanks, that worked.
I have to revise the info I gave in the first post, since it appears that this distro was not the one with the "previous versions" entry. I guess it was another one (yeah, tried many distros recently) which I deinstalled already.

Anyway, I found out that my grub version is GNU GRUB 1.98-1ubuntu12. I will try to install 1.99.

---

### Post by Chiel92 on 2011-11-15
I cannot find information about how to upgrade grub to 1.99.
And do I get it right if I say that grub 1.99 is a version of grub2?

---

### Post by drs305 on 2011-11-15
> **Chiel92 said:**
> I cannot find information about how to upgrade grub to 1.99.
And do I get it right if I say that grub 1.99 is a version of grub2?

Yes, Grub 1.99 is just the latest version of Grub 2.

I do a lot of experimenting with Grub 2 and always make backups to my current installation. Therefore I do things that I wouldn't recommend to others. ;-)

I would advise you to just keep your current version of Grub 2 until you upgrade to a newer version of Ubuntu. Both Natty and Oneiric have Grub 1.99, as will the new LTS due out next spring. But upgrading an entire OS just to get a new version of Grub 2 seems a bit overkill.

The problem is that Grub 1.99 has quite a few packages that have to be updated to accommodate it, although there are only 3 main Grub 2 packages: grub-common, grub-pc, and grub-gfxpayload-lists. It would be easy to restore Grub 1.98, but would be very difficult to restore the rest of your system to its original state.

If I edit the /etc/apt/sources.list, replacing 'lucid' with 'oneiric' for the 'main' repository, update the sources with "sudo apt-get update", and then attempt to install Grub 1.99, this is what I get. ***In no case should you run "sudo apt-get upgrade" with the 'oneiric' repository enabled***:

```
drs64@hb1:~$ **sudo apt-get install --reinstall grub-common grub-pc**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binutils cpp-4.4 debianutils dpkg friendly-recovery gcc-4.4 gcc-4.4-base
  gcc-4.6-base grub-gfxpayload-lists grub-pc-bin grub2-common ifupdown
  initramfs-tools initramfs-tools-bin initscripts lib32gcc1 lib32stdc++6
  libc-bin libc-dev-bin libc6 libc6-dev libc6-i386 libgcc1 libgmp10 libgomp1
  liblzma2 libmpfr4 libnih-dbus1 libnih1 libpopt0 libstdc++6 make mountall
  multiarch-support pkg-config upstart xz-utils
Suggested packages:
  binutils-doc gcc-4.4-locales gcc-4.4-multilib libmudflap0-4.4-dev
  gcc-4.4-doc libgcc1-dbg libgomp1-dbg libmudflap0-dbg libcloog-ppl0 libppl-c2
  libppl7 multiboot-doc grub-emu xorriso rdnssd glibc-doc make-doc graphviz
  xz-lzma
The following NEW packages will be installed:
  gcc-4.6-base grub-gfxpayload-lists grub-pc-bin grub2-common libgmp10
  liblzma2 libmpfr4 multiarch-support xz-utils
The following packages will be upgraded:
  binutils cpp-4.4 debianutils dpkg friendly-recovery gcc-4.4 gcc-4.4-base
  grub-common grub-pc ifupdown initramfs-tools initramfs-tools-bin initscripts
  lib32gcc1 lib32stdc++6 libc-bin libc-dev-bin libc6 libc6-dev libc6-i386
  libgcc1 libgomp1 libnih-dbus1 libnih1 libpopt0 libstdc++6 make mountall
  pkg-config upstart
30 upgraded, 9 newly installed, 0 to remove and 1048 not upgraded.
Need to get 28.5MB of archives.
After this operation, 3,248kB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

As you can see, it would update a lot of additional packages which may or may not affect your current OS. I've done it, but I have a high pain threshold.

If you try this, be sure to change the sources.list back to 'lucid' as soon as you are done installing Grub 1.99.

---

### Post by Chiel92 on 2011-11-15
Ah, this gives me a bit more insight in how things work :)
Thanks a lot!

---

### Post by Chiel92 on 2011-12-01
> **drs305 said:**
> 
You can read about some of the Grub 1.99 features (and how to set the default if it's hidden in the submenu) here:
[Grub 1.99 Changes]("http://ubuntuforums.org/showthread.php?p=10720322#post10720322")
[Grub 1.99 Submenus]("http://ubuntuforums.org/showthread.php?p=10720316#post10720316")


Hi,

I yesterday installed 11.10, with grub 1.99 installed, but it seems that the submenu feature doesnt work. At least not for the kernels on the other OS's I have listed there.
What do I have to do to turn that on?

Regards

---

### Post by drs305 on 2011-12-01
> **Chiel92 said:**
> Hi,

I yesterday installed 11.10, with grub 1.99 installed, but it seems that the submenu feature doesnt work. At least not for the kernels on the other OS's I have listed there.
What do I have to do to turn that on?

Regards

I don't believe there is a direct option to 'turn on' submenus for 30_os-prober. However, since Grub 2 uses scripts, you can modify the menu by adding a few scripts to make the entire content of 30_os-prober a submenu. 

If you are interested in doing this I can post them.

---

### Post by Chiel92 on 2011-12-01
Well, it's not that necessary for me to change it, but thanks for your offer.
I just thought it was nothing more than just getting a newer grub version.

---

### Post by stinkeye on 2011-12-01
> **drs305 said:**
> I don't believe there is a direct option to 'turn on' submenus for 30_os-prober. However, since Grub 2 uses scripts, you can modify the menu by adding a few scripts to make the entire content of 30_os-prober a submenu. 

If you are interested in doing this I can post them.

Hi drs305,
I would like to know how to do this.
I have two other linux installs as well as an xp install that I use rarely and would like to know how to hide them.

---

### Post by drs305 on 2011-12-01
> **stinkeye said:**
> I would like to know how to do this.
I have two other linux installs as well as an xp install that I use rarely and would like to know how to hide them.

You could modify the /etc/grub.d/30_os-prober script itself, but it would be overwritten if the package is updated. 

I do it with a script I run after the grub file is created, using 'sed' to modify the finalized script. The easiest way, however, is to add two simple scripts, one run on each side of 30_os-prober. The end result is that all entries normally added by 30_os-prober will now be located in a submenu and not displayed directly on the main page.

Create */etc/grub.d/29_custom* and */etc/grub.d/31_custom* scripts to add the *submenu* structure to the "### BEGIN /etc/grub.d/30_os-prober ###" section of the Grub menu.
[LIST=1]
[*]Create the two scripts.
[*]Make them executable.
[*]Update Grub.
[/LIST]

1. Create the scripts. The text in [COLOR="DarkRed"]dark red[/COLOR] are comments that appear as update-grub is run to provide visual indication the scripts are running. The text in [COLOR="DarkRed"]**bold dark red**[/COLOR] is the title which will be displayed in the Grub menu. Either or both may be changed to whatever you would like to see.
```
gksu gedit /etc/grub.d/29_custom /etc/grub.d/31_custom
```
29_os-prober:
> #!/bin/sh
echo "[COLOR="DarkRed"]Creating 30_os-prober submenu (29_custom)[/COLOR]" >&2
exec tail -n +7 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

submenu "[COLOR="DarkRed"]**30_os-prober Submenu Title Here**[/COLOR]" --class custom {


31_os-prober:
> #!/bin/sh
echo "[COLOR="DarkRed"]Closing 30_os-prober submenu (31_custom)[/COLOR]" >&2
exec tail -n +7 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

}


2. Make the new scripts executable:
```
sudo chmod +x /etc/grub.d/29_custom /etc/grub.d/31_custom
```

3. Update Grub (and watch the terminal for the custom script comments)
```
sudo update-grub
```

---

### Post by stinkeye on 2011-12-02
Thanks, worked perfectly.
Now there is only 1 entry in grub
with the sub menus
> Previous Linux Versions
Other Installs

---

