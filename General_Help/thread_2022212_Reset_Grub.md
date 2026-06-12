---
title: "Reset Grub"
date: 2012-07-10
forum: General Help
---

### Post by Kodeine on 2012-07-10
Salutations!

So I can't remember how long this problem has been going on for but it's been several months now. Ultimately sometimes when coming out of hibernation (no I'm not talking about those hypersleep pods they have in Alien) even though I've set the grub loader to wait for a second or so without out showing the menu (I used the hidden_timeout) it still shows the menu.

So instead of just seeing black for a second and then continuing to boot precise, providing I haven't pressed the escape key, it just shows me the menu anyway with no time out. This isn't always the case. This only happens once out of maybe ten times. I've used a utility entitled 'grub customizer' in the past to edit the grub loader. I've began to think it may have fouled up the grub loaders configuration files although it may be a kernel issue?

Sometimes (once out of say thirty-five times) the above problem will happen however in *addition* I won't be able to press the enter key to boot as pressing it does nothing. The keyboard and mouse don't seem to work? I have to press the shut down button on my tower and then turn it back on.

So ultimately may this be an issue with the kernel or the grub loader file? How would I be able to reset the grub loaders configuration to a default so I could see if it was grub customizers fault?

---

### Post by wilee-nilee on 2012-07-10
> **Kodeine said:**
> Salutations!

So I can't remember how long this problem has been going on for but it's been several months now. Ultimately sometimes when coming out of hibernation (no I'm not talking about those hypersleep pods they have in Alien) even though I've set the grub loader to wait for a second or so without out showing the menu (I used the hidden_timeout) it still shows the menu.

So instead of just seeing black for a second and then continuing to boot precise, providing I haven't pressed the escape key, it just shows me the menu anyway with no time out. This isn't always the case. This only happens once out of maybe ten times. I've used a utility entitled 'grub customizer' in the past to edit the grub loader. I've began to think it may have fouled up the grub loaders configuration files although it may be a kernel issue?

Sometimes (once out of say thirty-five times) the above problem will happen however in *addition* I won't be able to press the enter key to boot as pressing it does nothing. The keyboard and mouse don't seem to work? I have to press the shut down button on my tower and then turn it back on.

So ultimately may this be an issue with the kernel or the grub loader file? How would I be able to reset the grub loaders configuration to a default so I could see if it was grub customizers fault?

You can purge and reinstall grub to get to the stock set up, run these commands from the terminal in ubuntu.

```
sudo apt-get purge grub-pc grub-common
```then
```
sudo apt-get install grub-pc grub-common
```When asked after the second command where you want grub it is just the mbr, for example sda or sdb, depending what the HD is. Use the space key to tick this. Then just to be sure grub is updated run
```
sudo update-grub
```Your grub.cfg file will be back to stock then a as well, you can actually do all the tweaking from this file, rather then running the customizer if you like. The customizer is a good tool otherwise.

---

### Post by imachavel on 2012-07-10
wow uninstalling and resetting grub like that is dangerous

If you have a grub issue, you can use boot repair, either from the disk, or installing it from repository via sudo apt get install and I believe it's boot-repair. But if you are unsatisfied with how grub loads with your version of the kernel, then yes it's necessary to purge grub, then re install it. Which is dangerous since if you have other OS in grub they might need to have the master boot record reset, and grub re installed for them as well, since they will be looking for old grub.

The issue I mentioned isn't so much of an issue with several partitions of linux and grub re installed at the same time, but with linux and other partition OSes such as windows. What DOESN'T fail with windows huh? In which case don't use a fixmbr from windows recovery console. It will just turn into a master boot record reset war between the two partitions. In this case, use the boot repair cd, either burned from an .iso to a disk, at boot, or from the live cd, but not mounting the file system and running boot repair, but rather the repair boot button when you have the option to 'try' or 'install' linux.

This will fix all mbr and grub issues, if uninstalling and reinstalling grub doesn't satisfy your needs of specificity with the version of the kernel you are using

---

### Post by wilee-nilee on 2012-07-10
> **imachavel said:**
> wow uninstalling and resetting grub like that is dangerous


Hardly lol. ;)

I will say I recommend the bootrepair often but for a complete back to stock set up the tool is not really set up to do that a purge and reinstall is easy and a good way to learn this trick, a couple of commands and you are done.

---

### Post by imachavel on 2012-07-10
I've messed things up by un installing and reinstalling grub. Maybe not with the method you mentioned, but grub issues can be a real pain in the ***, if you uninstall and reinstall a grub that all partitions don't agree with, and then you need a new grub, and a mbr that is compatible with all partitions to allow all boot sectors to load at grub, long enough to pick the file system you want to use, and mount the appropriate OS

---

### Post by imachavel on 2012-07-10
for example this didn't harm me:

sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.0.0-17-generic
Found initrd image: /boot/initrd.img-3.0.0-17-generic
Found linux image: /boot/vmlinuz-3.0.0-16-generic
Found initrd image: /boot/initrd.img-3.0.0-16-generic
Found linux image: /boot/vmlinuz-3.0.0-15-generic
Found initrd image: /boot/initrd.img-3.0.0-15-generic
Found linux image: /boot/vmlinuz-3.0.0-14-generic
Found initrd image: /boot/initrd.img-3.0.0-14-generic
Found linux image: /boot/vmlinuz-3.0.0-13-generic
Found initrd image: /boot/initrd.img-3.0.0-13-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found memtest86+ image: /boot/memtest86+.bin
  No volume groups found
Found Linux Mint 11 Katya (11) on /dev/sda6
done

but I didn't choose to uninstall before updating grub. And if you choose a method that looks for the next version of grub for your kernel, that is a lot safer then choosing a new legacy grub or your own specified grub. Nothing is wrong with writing grub scripts, but your own script should be tested tremendously. I assume the grub updates are all tested by the ubuntu team for all OSes before being released. I myself had a problem with a friend who was a programmer, he wrote a legacy grub that worked with all versions of linux, lm, ubuntu, open suse, debian, and mac os x as well. But he didn't write the script with windows in mind. He purged someone's grub one day, and had a hell of a problem.

The windows partition wasn't showing up in grub, and when he reset the partition with windows recovery console, he had to fix mbr for windows. Now windows grub showed up, and linux partition wasn't shown. It was a real mess a total reformat was the only solution.

At that time I didn't know about linux boot-repair. I'm assuming your grub update uses the same grub version boot repair fixes and installs? Not trying to disagree with your method, just saying repairing grub can potentially damage files if done incorrectly.

---

### Post by wilee-nilee on 2012-07-10
> **imachavel said:**
> I've messed things up by un installing and reinstalling grub. Maybe not with the method you mentioned, but grub issues can be a real pain in the ***, if you uninstall and reinstall a grub that all partitions don't agree with, and then you need a new grub, and a mbr that is compatible with all partitions to allow all boot sectors to load at grub, long enough to pick the file system you want to use, and mount the appropriate OS

For only one last comment I will say you are assuming that your experience is the same as others. Personally this is an area I specialize in, and am very careful to be clear and concise in my instructions and am available for more work if needed, and know the others on the site who know this area quite well.

In life in general we have to be careful to not project our own reality and experiences into others as they have their own personal reality and experiences.

If my instructions were as dangerous as you suggest the others I know who know this even better then I would have commented. ;)

Grub is a challenge but after you understand the basic use it is really quite easy.

---

### Post by imachavel on 2012-07-10
well right I wasn't referring to your instructions so much as just taking a swing at this in general. If OP follows your instructions to the T, no problem should occur. I even tested updating grub command on my own pc and posted the output to show it's harmless. Just to OP: follow those instructions to to T, and don't go googling about ways to uninstall and reinstall grub to a legacy version or what not. Not assuming you would. Wilee-Nilee thanks for the advice

---

### Post by Kodeine on 2012-07-10
My disk has a 4.2GB extended partition and another 4.2GB swap space partition as well as a NTFS 107GB partition for which I store Windows games on ( windows eight is booted via external drive not installed to disk ) then finally the remainder is 889GB EXT4 for ubuntu.

So there's only one partition that holds a bootable operating system. If I follow wilee-nilee's instructions will it work with all the separate partitions on my disk?

---

### Post by YannBuntu on 2012-07-12
Hello
Like Wilee, I generally prefer to give short instructions, but here we can't.

> You can purge and reinstall grub to get to the stock set up, run these commands from the terminal in ubuntu.

```
sudo apt-get purge grub-pc grub-common
```then
```
sudo apt-get install grub-pc grub-common
```When asked after the second command where you want grub it is just the mbr, for example sda or sdb, depending what the HD is. Use the space key to tick this. Then just to be sure grub is updated run
```
sudo update-grub
```Your grub.cfg file will be back to stock then a as well, you can actually do all the tweaking from this file, rather then running the customizer if you like. The customizer is a good tool otherwise.

This method is not dangerous, and correctly purges and reinstalls GRUB, but only works in specific cases (being able to boot into the system to repair, no EFI, no LVM, no RAID, no /boot, no /usr), and won't purge GRUB-Customizer tweaks.
Boot-Repair's "Purge GRUB" option should take care of all of this. (however some GRUB-Customizer modifications may remain, please tell me if you notice some).

---

