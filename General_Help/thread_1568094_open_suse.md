---
title: "open suse"
date: 2010-09-04
forum: General Help
---

### Post by cowboy7305 on 2010-09-04
I have windows 7 and ubuntu 10.04 on my computer and i want to know if i can load open suse11.3 beside them just to have a look to see what its like,and if i can is there any thing i nead to know on how to do it 
many thanks

---

### Post by M93 on 2010-09-04
if u just want to try it then its better not to boot it along with the others just install it in virtualbox

---

### Post by srs5694 on 2010-09-04
It's certainly possible. Installing it in an emulator (VirtualBox, QEMU, or whatever), as M93 suggests, will help minimize risks -- triple-booting means you'll need to resize at least one partition, there may be glitches with the boot loader installation and configuration, and if you make a mistake when specifying partitions for OpenSUSE, you could wipe out Ubuntu or Windows. If you're comfortable with such operations, these risks are not great, but if you just muddle along with OS installations, using an emulator is probably wise.

If you go for a side-by-side installation, I'd say the trickiest part is the boot loader installation. I don't recall what options OpenSUSE presents, but it's probably safest to tell it not to install a boot loader at all, if that's possible. You can then reconfigure your Ubuntu boot loader to include the OpenSUSE kernels and configurations. The second safest option is to have OpenSUSE install its own version of GRUB, but to install it in its own boot partition rather than in the disk's MBR. You can then have Ubuntu's version of GRUB either chain-load OpenSUSE's GRUB much like it chain-loads the Windows boot loader, or directly load the OpenSUSE kernel(s).

---

### Post by azertyh on 2010-09-05
hi,
2 weeks ago, i was on dual-boot xp/ubuntu and i wanted to try some distros. i install zenwalk, just skip lilo (the zenwalk's bootloader) at installation to stay with grub2 of ubuntu. the 3 os work perfectly.
read carefully opensuse's manual.

---

### Post by HermanAB on 2010-09-05
I second the Virtualbox suggestion.

Once you have you base system working, the last thing you want is mess it up with a bad install of something else.  With Virtualbox or VMware Player, the world is your oyster and you can run as many different systems simultaneously as your hardware can handle.

---

### Post by Davor &#268;engija on 2010-09-07
> **cowboy7305 said:**
> I have windows 7 and ubuntu 10.04 on my computer and i want to know if i can load open suse11.3 beside them just to have a look to see what its like,and if i can is there any thing i nead to know on how to do it 
many thanks

Hi,

5 days ago I installed kubuntu for the first time, after using suse since v8.x or something. My laptop died so I took that chance to get rid of opensuse (11.3) and go with kubuntu. Basically, what you will get from opensuse is:
- uglier default user interface - fonts are just terrible, at least on KDE (default)
- really nice system administration tool, yast. It's great.
- NetworkManager with a bunch of problems, frequent upgrades and overall bad taste.
- everything else is pretty much the same, but kubuntu looks more polished and visually consistent.

However, opensuse installation is really easy, it can be installed in parallel to other OS's and generally, it won't mess up your boot configuration, just to be sure to do your disk partitioning correctly. It would be a good idea to prepare the partitions with some windows tool, write down the details and then install suse on the selected partition, without the need to do the disk reorganization during installation. Boot loader is quite smart and it never messed up the existing configuration, at least for me.

Anyway, virtual box, vmware or even live boot cd of opensuse would be safer option.

Good luck!

---

### Post by uRock on 2010-09-07
I agree with the VBox suggestions. It is the way to go when you just want to see how an OS looks. I have installed many in the VBox and I am glad I did, as I deleted them after a few minutes of probing.

---

### Post by sgosnell on 2010-09-07
I tend to install them on USB drives or SDHC cards.  It's quick and easy, and simple to reformat them.  An 8GB drive will easily hold a full install, and they only cost a few dollars.

---

### Post by garvinrick4 on 2010-09-07
install and when installing boot there is selection to not install boot at all. It is a little tricky to fine but under a tab called boot. It is using grub legacy not grub2 so do not need it.
 After install go to Ubuntu install and update-grub and will be in  your grub menu. Have done it with OpenSuSe and Fedora and is just fine. If you have a seperate /home is nice
you can share. Takes about 4 gig or so to make nice install. So 8 to 10 gig plenty if not
having a lot of home or have /home previously.

---

### Post by Rubi1200 on 2010-09-07
> **garvinrick4 said:**
> install and when installing boot there is selection to not install boot at all. It is a little tricky to fine but under a tab called boot. It is using grub legacy not grub2 so do not need it.
 After install go to Ubuntu install and update-grub and will be in  your grub menu. Have done it with OpenSuSe and Fedora and is just fine. If you have a seperate /home is nice
you can share. Takes about 4 gig or so to make nice install. So 8 to 10 gig plenty if not
having a lot of home or have /home previously.
+1
Also, this little tip (please read and don't make the same mistake!!!):
[http://ubuntuforums.org/showpost.php?p=9804183&postcount=6](http://ubuntuforums.org/showpost.php?p=9804183&postcount=6)

---

### Post by sgosnell on 2010-09-07
You do want to install grub, but on the USB drive, not on your internal HDD.

---

### Post by bodhi.zazen on 2010-09-07
Side note : IMO after a while all Linux distros are about the same under the skin. gnome is gnome (and kde is kde) on any distro.

Each distro has a few unique quarks, but if you can run Fedora, Debian, Slackware, and Gentoo, you can run most anything.

---

