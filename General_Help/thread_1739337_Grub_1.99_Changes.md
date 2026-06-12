---
title: "Grub 1.99 Changes"
date: 2011-04-25
forum: General Help
---

### Post by drs305 on 2011-04-25
This post provides a brief introduction to Grub 1.99. It presents a few of the differences with earlier versions of Grub "2" - Grub 1.97~beta or Grub 1.98.  The actual version of Grub 2 distributed with Ubuntu 11.04, Natty Narwhal, is Grub 1.99 RC1. 

**[COLOR="Navy"]Background:[/COLOR]**

With the end of official support for Ubuntu 9.10, Karmic Koala, Grub 2 is now the default bootloader for the entire Ubuntu Desktop family. 

Grub 1.99's improvements are especially noteworthy for users booting non-EXT 2/3/4 filesystems. Video capabilities are improved, there are support enhancements for Zen, btrfs, EFI, DM-RAID, grub scripting, USB hotplugging and lots more. For a more complete list of what's new for Grub 1.99, see the [_release announcement_]("http://lists.gnu.org/archive/html/grub-devel/2011-01/msg00082.html") from Vladimir Serbinenko. For detailed descriptions of Grub 1.99, see the [_GNU Grub 1.99 Manual_]("http://www.gnu.org/software/grub/manual/grub.html").


**[COLOR="Navy"]Submenus[/COLOR]**
In order to reduce the GRUB menu entries visible on boot, Grub 1.99 will incorporate a submenu feature in the main OS section of the menu. Only the latest kernel (plus its recovery mode if enabled) will be visible. If additional kernels are available, a new entry on the main menu will appear: "Previous Linux versions". Access to these additional kernels is gained by highlighting and selecting this menu, at which time a second page will display.

Users can still set an older kernel as the default, but the format of the *GRUB_DEFAULT=* setting in */etc/default/grub* has changed. Please refer to the following thread for more details on the submenu feature.
[**Grub 1.99 Submenus**]("http://ubuntuforums.org/showthread.php?p=10720316")

**[COLOR="Navy"]Settings & Command Changes[/COLOR]**


[LIST=A]
[*]**Installation**


[LIST]
[*]Grub will be upgraded to 1.99RC1 during an online upgrade to Natty or with a clean installation.
[*]*grub-gfxpayload-lists* is a new dependency for grub-pc (Grub 2). It is used to help the graphical handoff from Grub to the kernel.
[*]Previous releases of Ubuntu will not be upgraded to 1.99RC1. If desired, the user could temporarily change the *main* repository to *natty*, install grub-common, grub-pc and grub-gfxpayload-lists, then return the repository to the installed release. *Upgrade only the specified packages. Doing an update of all packages with a combination of natty and another release will likely break your system.*
[/LIST]


[*]**--boot-directory=** option when using ***grub-install***, ***grub-set-default***, or ***grub-reboot***


[LIST]
[*]**[COLOR="DarkRed"]NOTE to Forum Helpers![/COLOR]** This change is bound to create a bit of confusion in cases where the user needs to repoint the MBR to the actual partition with the Grub files. For several years we have been using the "--root-directory" switch. While the old command/switch will still work, it might be useful when/if using the new switch this change is empahsized. When using the "--boot-directory" switch, don't forget that the specified path must also contain grub's parent folder (normally 'boot').
[*]When using the *grub-install*, *grub-set-default*, or *grub-reboot* commands, the new '--boot-directory' option is used to specify the target folder DIR/grub; i.e. the folder into which the *grub* folder will be installed. If the switch is not used, /boot/grub is assumed.
[*]The default folder is */boot/grub* if not specified.

[*]Examples:
[INDENT]To install on a currently-running Ubuntu installation located on the *sda* drive:
```
sudo grub-install /dev/sda
```[/INDENT]


[*]To install from the LiveCD to an Ubuntu partition mounted on sda's /mnt:
[INDENT]```
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```
[*]Grub will be placed in the *sda* MBR and point to *[I]/mnt/boot/grub*[/I]
[*]This command is equivalent to the former "sudo grub-install --root-directory=/mountpoint /dev/sda", which will still work and would place the grub folder in the same location (*sda* MBR and the mounted partition's */boot/grub* folder.)[/INDENT]
[/LIST]



[*]**Configuration Settings in */etc/default/grub***


[LIST]
[*]GRUB_DISABLE_RECOVERY= 
[INDENT]Replaces GRUB_DISABLE_LINUX_RECOVERY= in */etc/default/grub*[/INDENT]


[*]GRUB_BACKGROUND=/path/image
[INDENT]Introduced in later versions of Grub 1.98, this setting allows the user to designate the location of a .png, .tga, or .jpg/.jpeg image to be used as a background image on the Grub screen. 
[/INDENT]

[INDENT]A separate post details how to use this capability and how to set the menu text and background colors.
[/INDENT]


[*]To see a complete list of available options for /etc/default/grub, run the following command and then refer to the GNU Grub manual for a description.
[INDENT]```
grep DEVICE -A40 /usr/sbin/grub-mkconfig
```
[/INDENT]
[/LIST]

[*]**Menuentry Change** [COLOR="Red"]Error Alert![/COLOR]

[INDENT]```
search --no-floppy --fs-uuid **--set=root** <UUID>
```
[/INDENT]

[LIST]Replaces "search --no-floppy --fs-uuid [COLOR="Red"]--set[/COLOR] <UUID> in */boot/grub/grub.cfg* (auto-generated)[/LIST]

[INDENT]If an old menuentry or a custom menu using the older convention "--set <UUID>" is used, expect one of the following errors when attempting to boot:[/INDENT]

[INDENT][INDENT][COLOR="Red"]Error: No Argument Specified[/COLOR]
[COLOR="Red"]Error: Invalid Signature[/COLOR][/INDENT][/INDENT]
[/LIST]

**[COLOR="Navy"]Repairing Grub Problems[/COLOR]**
There are enough differences between Grub 1.99 and previous versions that it is necessary to use the same version when attempting to repair Grub via a LiveCD. In other words, don't try to repair a Natty Grub problem with a Maverick LiveCD, or vice versa. This includes running the "grub-install" command to rewrite the MBR information.

**[COLOR="Navy"]Inputs Welcome:[/COLOR]**
If you are familiar with changes to common entries in Grub 2 brought about by this upgrade to 1.99 RC1, please feel free to add to this thread.

**[COLOR="Navy"]Links:[/COLOR]**
[**Grub 1.99 Submenus**]("http://ubuntuforums.org/showthread.php?p=10720316")
[**Grub 1.99 Drop-In Backgrounds**]("http://ubuntuforums.org/showthread.php?p=10622069")

---

### Post by mörgæs on 2011-04-26
Thanks! This will come in handy.

There has been a lot of talk recently about deleting old posts in the fora and trying to crank up the wiki. Wasn't this post a good candidate for going to the wiki?

---

### Post by coffeecat on 2011-04-26
Thanks very much for this. Bookmarked.


> **drs305 said:**
> 
[LIST=A]
[*]**--boot-directory=** option when using ***grub-install***, ***grub-set-default***, or ***grub-reboot***
[LIST]
[*]**[COLOR=DarkRed]NOTE to Forum Helpers![/COLOR]** This change is bound to create a bit of confusion in cases where the user needs to repoint the MBR to the actual partition with the Grub files.
[/LIST]
 
[/LIST]


And even more confusion when the OP is vague about which version of Ubuntu they are running grub from! :) Will you, or someone, be updating the Community Documentation Grub 2 page once Natty is released? Specifically here:

[https://help.ubuntu.com/community/Grub2#SIMPLEST%20-%20Copy%20GRUB%202%20Files%20from%20the%20LiveCD](https://help.ubuntu.com/community/Grub2#SIMPLEST%20-%20Copy%20GRUB%202%20Files%20from%20the%20LiveCD)

---

### Post by drs305 on 2011-04-26
> **coffeecat said:**
> 
And even more confusion when the OP is vague about which version of Ubuntu they are running grub from! :) Will you, or someone, be updating the Community Documentation Grub 2 page once Natty is released?

I hope to go through the entire doc and update the contents. There are a couple of points: the community doc's emphasis is on packages for LTS versions, which still use 1.98. I will make note of some of the important changes to 1.99 in the doc, as well as expand on Grub 1.98's improvements. 

Another limitation of that doc is that it is still sorely lacking information on lots of Grub 2's capabilities: RAID, non-EXT formats, etc. The Grub 2 developers don't seem to contribute to the community docs, and I don't use or have the knowledge to document many of them. I always like to encourage others able to update the Ubuntu Community Docs to jump in.

As far as the wiki, I have published a number of topics on the Ubuntu wiki but Grub 2 just isn't one of them (other than helping build the initial pages). Anyone who wants to take any of my work and transfer it to the wiki is welcome to do so.

---

### Post by drummerdp on 2011-05-05
Hi,
 
I just upgraded to release 11.04 and now grub cannot find the icons at boot time. The theme works otherwise with the animated clock, but no selection icons. Everything worked fine in release 10.10 with grub 1.98, but grub 1.99 seems to have a problem.
 
One of my menuentries follows:
 
menuentry "Ubuntu 11.04     On MBR disk" --class ubuntu {
 gfxpayload=1024x768
 set root='(hd0,msdos2)'
 linux /vmlinuz      root=/dev/sda2  verbose
 initrd /initrd.img 
}
 
There is a file named **ubuntu.png** in   **/boot/grub/themes/winter/icons**   
which is where it should be. I also tried setting the icondir variable, but that didn't work either. Am I missing something?

---

### Post by drs305 on 2011-05-05
> **drummerdp said:**
> 
There is a file named **ubuntu.png** in   **/boot/grub/themes/winter/icons**   
which is where it should be. I also tried setting the icondir variable, but that didn't work either. Am I missing something?

I don't use themes so I'm not the one to ask. Many of those that do probably won't visit this thread. 

Since your menuentry looks fairly standard, I would suspect the file to concentrate on would be you theme file. I don't know if Grub 1.99's ability to boot an image file located in /boot/grub is interfering with theme images or not, but it's a possibility. To simply have the winter image as a background, try placing a copy in /boot/grub. I don't know about the icons.

Here is the applicable section of the Grub 1.99 manual. Perhaps you will find some guidance there:
[http://www.gnu.org/software/grub/manual/grub.html#Theme-file-format]("http://www.gnu.org/software/grub/manual/grub.html#Theme-file-format")

---

