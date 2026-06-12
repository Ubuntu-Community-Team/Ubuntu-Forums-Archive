---
title: "Changing kernel hz to 1000hz"
date: 2012-04-04
forum: General Help
---

### Post by Gad. on 2012-04-04
My deepest apologies to the Ubuntu forums, but I do regret that I am a quite large noob at ubuntu. I only use ubuntu for a small game server that I have hosted on a VPS... And with this game server, I need to change the hz of the kernel to 1000hz to achieve the desirable FPS rate of the game server. Unfortunatly, I have only a single link that shows me how to do this. It is here: [http://stackoverflow.com/questions/8088901/compiling-kernel-in-ubuntu-on-ec2-no-errors-but-no-image-and-unchanged-after-r](http://stackoverflow.com/questions/8088901/compiling-kernel-in-ubuntu-on-ec2-no-errors-but-no-image-and-unchanged-after-r)

Although that shows a guide on how to do it, I do not feel comfortable playing with the kernel as it does not specifically say which line to do, when...

I have the same version, 10.04 lucid, and basically... I need a step by step guide on how to modify my kernel to run at 1000hz.

Any help would be -grealy- appreciated. Once again, I do apologize for my noobiness...

Thanks!

---

### Post by lykwydchykyn on 2012-04-04
Looks to me like these would be the resulting steps to take:

```

sudo apt-get build-dep linux-image-$(uname -r)
sudo apt-get build-dep linux
sudo apt-get install fakeroot build-essential
sudo apt-get install crash kexec-tools makedumpfile kernel-wedge
sudo apt-get install libncurses5 libncurses5-dev
sudo apt-get install libelf-dev asciidoc binutils-dev kernel-package

sudo apt-get install git

cd /usr/src
# This is 700mb so it takes a while to download and set up
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-lucid.git
cd ubuntu*
git checkout --track -b ec2 origin/ec2

fakeroot debian/rules clean
fakeroot debian/rules editconfigs
fakeroot debian/rules binary
#Takes about 40min
cd linux-*
sudo make menuconfig
# Processor type and features -> Timer frequency -> change to 1000HZ -> Exit -> Exit -> Yes (Save)

fakeroot debian/rules clean
fakeroot debian/rules binary-headers
fakeroot debian/rules binary-indep   #This does the headers, docs, and source

#check deb 2-3 files were created
cd ..
ls *.deb

sudo dpkg -i linux-*.deb
#reboot

```

I can't really vouch for this, but (surprisingly, to many) compiling a new kernel is a fairly safe thing to do.  It's not going to overwrite your old kernel, just provide you with another one which you can choose from the boot menu.  If it fails to boot, just select the old kernel when you boot again.

---

### Post by Gad. on 2012-04-04
Thanks, I'll do that. 

But one more question.

You mentioned something about selecting the one I want from the boot menu, what is this boot menu?

I'm using putty to connect to a VPS and I simply can only connect to it once it's on, I don't believe I see a "boot menu".

---

### Post by Cheesemill on 2012-04-04
Check with your VPS host before trying to compile a new kernel.

The VPS's that I have used in the past already run custom kernels that fit in with their infrastructure, so attempting to run a different kernel may break your VPS completely.

---

### Post by Gad. on 2012-04-04
> **Cheesemill said:**
> Check with your VPS host before trying to compile a new kernel.

The VPS's that I have used in the past already run custom kernels that fit in with their infrastructure, so attempting to run a different kernel may break your VPS completely.

It's really a "I'm on my own" here. It's a free VPS that my friend gave me due to me getting him a job. He runs his own VPS site, and lets me have it as long as I don't pester him about it :P.

Although if it breaks, I'm sure he'll help fix it. Because I'm going through with those original commands in the 2nd post. Although my previous post, I still need an answer to.

Thanks.

Any other ideas?

---

### Post by Cheesemill on 2012-04-04
It's not just a case of maybe breaking your VPS. Depending on the underlying hypervisor technology being used (Xen, KVM etc) it could well be impossible to run anything except the kernel you have currently installed.

As to your grub question, if you do install a custom kernel you will be able to set it to boot by default by editing the /boot/grub/menu.lst file. But be warned, if it fails to boot you have left yourself with an unbootable system which may be impossible to fix without having it reinstalled from scratch.

I really would check with your friend before attempting any of this.

---

### Post by Gad. on 2012-04-04
Alright, thanks for letting me know. I do know that it's not xen or kvm, but VB (virtualbox), as far as I know. I may be talking jibberish though...

I guess the best thing is to just pester my bud about it :P

---

### Post by Cheesemill on 2012-04-04
Also I've just noticed that the commands above have lines that are specific to virtual machines running on Amazons EC2 cloud service.

If you are not using Amazon EC2 as your VPS provider then some of the above commands are incorrect.

---

### Post by Cheesemill on 2012-04-04
> **Gad. said:**
> Alright, thanks for letting me know. I do know that it's not xen or kvm, but VB (virtualbox), as far as I know. I may be talking jibberish though...

I guess the best thing is to just pester my bud about it :P

If it is VirtualBox then you should be fine running a custom kernel, but you still have the problem of not being able to connect until after the machine has booted, making selecting different kernels in grub impossible if you only have SSH access.

---

### Post by Gad. on 2012-04-04
Yeah, I have SSH and FTP only. But could I still change the kernel the one way you suggested? I may just go ahead and risk it. There's not too much I could lose, and reinstallation is easy.

---

### Post by Gad. on 2012-04-04
I ran the first two lines of the commands, do I need to remove anything?

Could you perhaps show me how to change the kernel hz to 1000hz? I would absolutely love you if you did.

---

### Post by Cheesemill on 2012-04-04
Instead of recompiling yourself it would be easier just to install the preempt kernel that is already in the repositories. This has the 1000hz option set by default and is specifically designed for low latency servers:
```
sudo apt-get install linux-preempt
```

---

### Post by Gad. on 2012-04-04
I am currently downloading it. Should I just restart after it's finished, or are there any other commands. Sorry for my lack of knowledge in this situation!

Thank you so much for your help so far!

---

### Post by Cheesemill on 2012-04-04
I'm not sure if it will set it as the default kernel or not. To test just reboot then do:
```
uname -a
```
to list the running kernel.
If you don't see preempt anywhere in the output then you will have to edit /boot/grub/menu.lst and change the default kernel option.

---

### Post by Gad. on 2012-04-04
After install and restart I see:

Linux green 2.6.32-25-server #45-Ubuntu SMP Sat Oct 16 20:06:58 UTC 2010 x86_64 GNU/Linux

Which I assume is not the right one.

---

### Post by Gad. on 2012-04-04
And inside the boot/grub folder, I see no menu.lst file...

What do I do now?

---

### Post by Cheesemill on 2012-04-04
You are still using the old kernel, edit /boot/grub/menu.lst and change the default option to reference the new kernel.

At the moment it will probably be 'default 0', just change 0 to the correct kernel in the list (the count starts at 0 so if the preempt kernel is 3rd in the list you would have to change it to 'default 2'.

If you are unsure then just post your /boot/grub/menu.list file here and I'll take a look.

---

### Post by Gad. on 2012-04-04
> **Gad. said:**
> And inside the boot/grub folder, I see no menu.lst file...

What do I do now?

Sorry, I double posted, but the above is my current problem.


```
915resolution.mod            gcry_seed.mod       parttool.lst
acpi.mod                     gcry_serpent.mod    parttool.mod
affs.mod                     gcry_sha1.mod       password.mod
afs_be.mod                   gcry_sha256.mod     password_pbkdf2.mod
afs.mod                      gcry_sha512.mod     pbkdf2.mod
aout.mod                     gcry_tiger.mod      pci.mod
ata.mod                      gcry_twofish.mod    play.mod
ata_pthru.mod                gcry_whirlpool.mod  png.mod
at_keyboard.mod              gettext.mod         probe.mod
befs_be.mod                  gfxmenu.mod         pxeboot.img
befs.mod                     gfxterm.mod         pxecmd.mod
biosdisk.mod                 gptsync.mod         pxe.mod
bitmap.mod                   grldr.img           raid5rec.mod
bitmap_scale.mod             grub.cfg            raid6rec.mod
blocklist.mod                grubenv             raid.mod
boot.img                     gzio.mod            read.mod
boot.mod                     halt.mod            reboot.mod
bsd.mod                      handler.lst         reiserfs.mod
bufio.mod                    handler.mod         relocator.mod
cat.mod                      hashsum.mod         scsi.mod
cdboot.img                   hdparm.mod          search_fs_file.mod
chain.mod                    hello.mod           search_fs_uuid.mod
charset.mod                  help.mod            search_label.mod
cmp.mod                      hexdump.mod         search.mod
command.lst                  hfs.mod             serial.mod
configfile.mod               hfsplus.mod         setjmp.mod
core.img                     iso9660.mod         setpci.mod
cpio.mod                     jfs.mod             sfs.mod
cpuid.mod                    jpeg.mod            sh.mod
crc.mod                      kernel.img          sleep.mod
crypto.lst                   keystatus.mod       tar.mod
crypto.mod                   linux16.mod         terminal.lst
datehook.mod                 linux.mod           terminal.mod
date.mod                     lnxboot.img         terminfo.mod
datetime.mod                 loadenv.mod         test.mod
diskboot.img                 locale              tga.mod
dm_nv.mod                    loopback.mod        trig.mod
drivemap.mod                 lsmmap.mod          true.mod
echo.mod                     ls.mod              udf.mod
efiemu32.o                   lspci.mod           ufs1.mod
efiemu64.o                   lvm.mod             ufs2.mod
efiemu.mod                   mdraid.mod          uhci.mod
elf.mod                      memdisk.mod         usb_keyboard.mod
example_functional_test.mod  memrw.mod           usb.mod
ext2.mod                     minicmd.mod         usbms.mod
extcmd.mod                   minix.mod           usbtest.mod
fat.mod                      mmap.mod            vbeinfo.mod
font.mod                     moddep.lst          vbe.mod
fshelp.mod                   msdospart.mod       vbetest.mod
fs.lst                       multiboot2.mod      vga.mod
functional_test.mod          multiboot.mod       vga_text.mod
gcry_arcfour.mod             normal.mod          video_fb.mod
gcry_blowfish.mod            ntfscomp.mod        video.lst
gcry_camellia.mod            ntfs.mod            video.mod
gcry_cast5.mod               ohci.mod            videotest.mod
gcry_crc.mod                 part_acorn.mod      xfs.mod
gcry_des.mod                 part_amiga.mod      xnu.mod
gcry_md4.mod                 part_apple.mod      xnu_uuid.mod
gcry_md5.mod                 part_gpt.mod        zfsinfo.mod
gcry_rfc2268.mod             partmap.lst         zfs.mod
gcry_rijndael.mod            part_msdos.mod
gcry_rmd160.mod              part_sun.mod
```


That is everything under boot/grub

---

### Post by lisati on 2012-04-04
<aside>
Newer versions of grub don't use menu.lst
</aside>

---

### Post by Cheesemill on 2012-04-04
Odd, you shouldn't be able to boot at all without one. What is the output of:
```
ls -lha /boot/grub/
```

---

### Post by Gad. on 2012-04-04
> **lisati said:**
> <aside>
Newer versions of grub don't use menu.lst
</aside>

Is there another place that I should edit to load the correct kernel?

```
green@green:/home$ ls -lha /boot/grub/
total 1.5M
drwxr-xr-x 3 root root 4.0K 2012-04-04 18:56 .
drwxr-xr-x 3 root root 4.0K 2012-04-04 18:56 ..
-rw-r--r-- 1 root root 8.1K 2010-10-24 04:30 915resolution.mod
-rw-r--r-- 1 root root  11K 2010-10-24 04:30 acpi.mod
-rw-r--r-- 1 root root 4.5K 2010-10-24 04:30 affs.mod
-rw-r--r-- 1 root root 4.8K 2010-10-24 04:30 afs_be.mod
-rw-r--r-- 1 root root 4.8K 2010-10-24 04:30 afs.mod
-rw-r--r-- 1 root root 1.1K 2010-10-24 04:30 aout.mod
-rw-r--r-- 1 root root 7.9K 2010-10-24 04:30 ata.mod
-rw-r--r-- 1 root root 2.2K 2010-10-24 04:30 ata_pthru.mod
-rw-r--r-- 1 root root 2.7K 2010-10-24 04:30 at_keyboard.mod
-rw-r--r-- 1 root root 4.7K 2010-10-24 04:30 befs_be.mod
-rw-r--r-- 1 root root 4.7K 2010-10-24 04:30 befs.mod
-rw-r--r-- 1 root root 4.2K 2010-10-24 04:30 biosdisk.mod
-rw-r--r-- 1 root root 2.4K 2010-10-24 04:30 bitmap.mod
-rw-r--r-- 1 root root 2.9K 2010-10-24 04:30 bitmap_scale.mod
-rw-r--r-- 1 root root 2.0K 2010-10-24 04:30 blocklist.mod
-rw-r--r-- 1 root root  512 2010-10-24 04:30 boot.img
-rw-r--r-- 1 root root 2.6K 2010-10-24 04:30 boot.mod
-rw-r--r-- 1 root root  20K 2010-10-24 04:30 bsd.mod
-rw-r--r-- 1 root root 2.0K 2010-10-24 04:30 bufio.mod
-rw-r--r-- 1 root root 2.0K 2010-10-24 04:30 cat.mod
-rw-r--r-- 1 root root  512 2010-10-24 04:30 cdboot.img
-rw-r--r-- 1 root root 2.4K 2010-10-24 04:30 chain.mod
-rw-r--r-- 1 root root 2.0K 2010-10-24 04:30 charset.mod
-rw-r--r-- 1 root root 2.1K 2010-10-24 04:30 cmp.mod
-rw-r--r-- 1 root root 2.0K 2010-10-24 04:30 command.lst
-rw-r--r-- 1 root root 1.8K 2010-10-24 04:30 configfile.mod
-rw-r--r-- 1 root root  25K 2010-10-24 04:30 core.img
-rw-r--r-- 1 root root 2.8K 2010-10-24 04:30 cpio.mod
-rw-r--r-- 1 root root 1.6K 2010-10-24 04:30 cpuid.mod
-rw-r--r-- 1 root root 1.8K 2010-10-24 04:30 crc.mod
-rw-r--r-- 1 root root  825 2010-10-24 04:30 crypto.lst
-rw-r--r-- 1 root root 4.3K 2010-10-24 04:30 crypto.mod
-rw-r--r-- 1 root root 1.8K 2010-10-24 04:30 datehook.mod
-rw-r--r-- 1 root root 2.3K 2010-10-24 04:30 date.mod
-rw-r--r-- 1 root root 1.3K 2010-10-24 04:30 datetime.mod
-rw-r--r-- 1 root root  512 2010-10-24 04:30 diskboot.img
-rw-r--r-- 1 root root 1.9K 2010-10-24 04:30 dm_nv.mod
-rw-r--r-- 1 root root 5.4K 2010-10-24 04:30 drivemap.mod
-rw-r--r-- 1 root root 1.9K 2010-10-24 04:30 echo.mod
-rw-r--r-- 1 root root 6.3K 2010-10-24 04:30 efiemu32.o
-rw-r--r-- 1 root root  11K 2010-10-24 04:30 efiemu64.o
-rw-r--r-- 1 root root  24K 2010-10-24 04:30 efiemu.mod
-rw-r--r-- 1 root root 4.4K 2010-10-24 04:30 elf.mod
-rw-r--r-- 1 root root 1.7K 2010-10-24 04:30 example_functional_test.mod
-rw-r--r-- 1 root root 5.4K 2010-10-24 04:30 ext2.mod
-rw-r--r-- 1 root root 4.0K 2010-10-24 04:30 extcmd.mod
-rw-r--r-- 1 root root 5.8K 2010-10-24 04:30 fat.mod
-rw-r--r-- 1 root root 9.6K 2010-10-24 04:30 font.mod
-rw-r--r-- 1 root root 2.7K 2010-10-24 04:30 fshelp.mod
-rw-r--r-- 1 root root  121 2010-10-24 04:30 fs.lst
-rw-r--r-- 1 root root 2.6K 2010-10-24 04:30 functional_test.mod
-rw-r--r-- 1 root root 1.8K 2010-10-24 04:30 gcry_arcfour.mod
-rw-r--r-- 1 root root 8.0K 2010-10-24 04:30 gcry_blowfish.mod
-rw-r--r-- 1 root root  35K 2010-10-24 04:30 gcry_camellia.mod
-rw-r--r-- 1 root root  18K 2010-10-24 04:30 gcry_cast5.mod
-rw-r--r-- 1 root root 3.0K 2010-10-24 04:30 gcry_crc.mod
-rw-r--r-- 1 root root  19K 2010-10-24 04:30 gcry_des.mod
-rw-r--r-- 1 root root 3.2K 2010-10-24 04:30 gcry_md4.mod
-rw-r--r-- 1 root root 4.0K 2010-10-24 04:30 gcry_md5.mod
-rw-r--r-- 1 root root 2.6K 2010-10-24 04:30 gcry_rfc2268.mod
-rw-r--r-- 1 root root  19K 2010-10-24 04:30 gcry_rijndael.mod
-rw-r--r-- 1 root root 9.0K 2010-10-24 04:30 gcry_rmd160.mod
-rw-r--r-- 1 root root  17K 2010-10-24 04:30 gcry_seed.mod
-rw-r--r-- 1 root root  18K 2010-10-24 04:30 gcry_serpent.mod
-rw-r--r-- 1 root root 8.8K 2010-10-24 04:30 gcry_sha1.mod
-rw-r--r-- 1 root root 3.5K 2010-10-24 04:30 gcry_sha256.mod
-rw-r--r-- 1 root root 5.6K 2010-10-24 04:30 gcry_sha512.mod
-rw-r--r-- 1 root root  12K 2010-10-24 04:30 gcry_tiger.mod
-rw-r--r-- 1 root root  39K 2010-10-24 04:30 gcry_twofish.mod
-rw-r--r-- 1 root root  25K 2010-10-24 04:30 gcry_whirlpool.mod
-rw-r--r-- 1 root root 3.9K 2010-10-24 04:30 gettext.mod
-rw-r--r-- 1 root root  37K 2010-10-24 04:30 gfxmenu.mod
-rw-r--r-- 1 root root  11K 2010-10-24 04:30 gfxterm.mod
-rw-r--r-- 1 root root 3.7K 2010-10-24 04:30 gptsync.mod
-rw-r--r-- 1 root root  10K 2010-10-24 04:30 grldr.img
-r--r--r-- 1 root root 5.0K 2012-04-04 18:56 grub.cfg
-rw-r--r-- 1 root root 1.0K 2012-04-04 18:56 grubenv
-rw-r--r-- 1 root root 7.6K 2010-10-24 04:30 gzio.mod
-rw-r--r-- 1 root root 1.5K 2010-10-24 04:30 halt.mod
-rw-r--r-- 1 root root   16 2010-10-24 04:30 handler.lst
-rw-r--r-- 1 root root 1.7K 2010-10-24 04:30 handler.mod
-rw-r--r-- 1 root root 4.7K 2010-10-24 04:30 hashsum.mod
-rw-r--r-- 1 root root 7.3K 2010-10-24 04:30 hdparm.mod
-rw-r--r-- 1 root root 1.2K 2010-10-24 04:30 hello.mod
-rw-r--r-- 1 root root 2.4K 2010-10-24 04:30 help.mod
-rw-r--r-- 1 root root 3.2K 2010-10-24 04:30 hexdump.mod
-rw-r--r-- 1 root root 5.9K 2010-10-24 04:30 hfs.mod
-rw-r--r-- 1 root root 5.8K 2010-10-24 04:30 hfsplus.mod
-rw-r--r-- 1 root root 6.1K 2010-10-24 04:30 iso9660.mod
-rw-r--r-- 1 root root 5.7K 2010-10-24 04:30 jfs.mod
-rw-r--r-- 1 root root 5.8K 2010-10-24 04:30 jpeg.mod
-rw-r--r-- 1 root root  30K 2010-10-24 04:30 kernel.img
-rw-r--r-- 1 root root 2.0K 2010-10-24 04:30 keystatus.mod
-rw-r--r-- 1 root root 4.9K 2010-10-24 04:30 linux16.mod
-rw-r--r-- 1 root root 8.5K 2010-10-24 04:30 linux.mod
-rw-r--r-- 1 root root 1.0K 2010-10-24 04:30 lnxboot.img
-rw-r--r-- 1 root root 5.5K 2010-10-24 04:30 loadenv.mod
drwxr-xr-x 2 root root 4.0K 2010-10-24 04:30 locale
-rw-r--r-- 1 root root 3.1K 2010-10-24 04:30 loopback.mod
-rw-r--r-- 1 root root 1.3K 2010-10-24 04:30 lsmmap.mod
-rw-r--r-- 1 root root 4.1K 2010-10-24 04:30 ls.mod
-rw-r--r-- 1 root root 4.9K 2010-10-24 04:30 lspci.mod
-rw-r--r-- 1 root root 5.4K 2010-10-24 04:30 lvm.mod
-rw-r--r-- 1 root root 1.8K 2010-10-24 04:30 mdraid.mod
-rw-r--r-- 1 root root 2.1K 2010-10-24 04:30 memdisk.mod
-rw-r--r-- 1 root root 2.9K 2010-10-24 04:30 memrw.mod
-rw-r--r-- 1 root root 4.2K 2010-10-24 04:30 minicmd.mod
-rw-r--r-- 1 root root 4.2K 2010-10-24 04:30 minix.mod
-rw-r--r-- 1 root root 8.4K 2010-10-24 04:30 mmap.mod
-rw-r--r-- 1 root root 2.6K 2010-10-24 04:30 moddep.lst
-rw-r--r-- 1 root root 2.4K 2010-10-24 04:30 msdospart.mod
-rw-r--r-- 1 root root  11K 2010-10-24 04:30 multiboot2.mod
-rw-r--r-- 1 root root  11K 2010-10-24 04:30 multiboot.mod
-rw-r--r-- 1 root root  42K 2010-10-24 04:30 normal.mod
-rw-r--r-- 1 root root 3.5K 2010-10-24 04:30 ntfscomp.mod
-rw-r--r-- 1 root root 9.8K 2010-10-24 04:30 ntfs.mod
-rw-r--r-- 1 root root 4.4K 2010-10-24 04:30 ohci.mod
-rw-r--r-- 1 root root 2.1K 2010-10-24 04:30 part_acorn.mod
-rw-r--r-- 1 root root 2.2K 2010-10-24 04:30 part_amiga.mod
-rw-r--r-- 1 root root 2.6K 2010-10-24 04:30 part_apple.mod
-rw-r--r-- 1 root root 2.7K 2010-10-24 04:30 part_gpt.mod
-rw-r--r-- 1 root root   62 2010-10-24 04:30 partmap.lst
-rw-r--r-- 1 root root 3.4K 2010-10-24 04:30 part_msdos.mod
-rw-r--r-- 1 root root 2.3K 2010-10-24 04:30 part_sun.mod
-rw-r--r-- 1 root root   22 2010-10-24 04:30 parttool.lst
-rw-r--r-- 1 root root 4.4K 2010-10-24 04:30 parttool.mod
-rw-r--r-- 1 root root 1.9K 2010-10-24 04:30 password.mod
-rw-r--r-- 1 root root 3.0K 2010-10-24 04:30 password_pbkdf2.mod
-rw-r--r-- 1 root root 1.4K 2010-10-24 04:30 pbkdf2.mod
-rw-r--r-- 1 root root  900 2010-10-24 04:30 pci.mod
-rw-r--r-- 1 root root 2.5K 2010-10-24 04:30 play.mod
-rw-r--r-- 1 root root 6.5K 2010-10-24 04:30 png.mod
-rw-r--r-- 1 root root 2.7K 2010-10-24 04:30 probe.mod
-rw-r--r-- 1 root root 1.0K 2010-10-24 04:30 pxeboot.img
-rw-r--r-- 1 root root 1.4K 2010-10-24 04:30 pxecmd.mod
-rw-r--r-- 1 root root 5.5K 2010-10-24 04:30 pxe.mod
-rw-r--r-- 1 root root 1.4K 2010-10-24 04:30 raid5rec.mod
-rw-r--r-- 1 root root 2.8K 2010-10-24 04:30 raid6rec.mod
-rw-r--r-- 1 root root 5.8K 2010-10-24 04:30 raid.mod
-rw-r--r-- 1 root root 1.6K 2010-10-24 04:30 read.mod
-rw-r--r-- 1 root root 1.1K 2010-10-24 04:30 reboot.mod
-rw-r--r-- 1 root root 9.7K 2010-10-24 04:30 reiserfs.mod
-rw-r--r-- 1 root root 4.1K 2010-10-24 04:30 relocator.mod
-rw-r--r-- 1 root root 3.2K 2010-10-24 04:30 scsi.mod
-rw-r--r-- 1 root root 2.2K 2010-10-24 04:30 search_fs_file.mod
-rw-r--r-- 1 root root 2.3K 2010-10-24 04:30 search_fs_uuid.mod
-rw-r--r-- 1 root root 2.3K 2010-10-24 04:30 search_label.mod
-rw-r--r-- 1 root root 2.4K 2010-10-24 04:30 search.mod
-rw-r--r-- 1 root root 6.0K 2010-10-24 04:30 serial.mod
-rw-r--r-- 1 root root  690 2010-10-24 04:30 setjmp.mod
-rw-r--r-- 1 root root 5.5K 2010-10-24 04:30 setpci.mod
-rw-r--r-- 1 root root 4.0K 2010-10-24 04:30 sfs.mod
-rw-r--r-- 1 root root  12K 2010-10-24 04:30 sh.mod
-rw-r--r-- 1 root root 2.2K 2010-10-24 04:30 sleep.mod
-rw-r--r-- 1 root root 2.8K 2010-10-24 04:30 tar.mod
-rw-r--r-- 1 root root  134 2010-10-24 04:30 terminal.lst
-rw-r--r-- 1 root root 5.0K 2010-10-24 04:30 terminal.mod
-rw-r--r-- 1 root root 9.6K 2010-10-24 04:30 terminfo.mod
-rw-r--r-- 1 root root 5.1K 2010-10-24 04:30 test.mod
-rw-r--r-- 1 root root 2.9K 2010-10-24 04:30 tga.mod
-rw-r--r-- 1 root root 1.7K 2010-10-24 04:30 trig.mod
-rw-r--r-- 1 root root 1.3K 2010-10-24 04:30 true.mod
-rw-r--r-- 1 root root 5.0K 2010-10-24 04:30 udf.mod
-rw-r--r-- 1 root root 4.6K 2010-10-24 04:30 ufs1.mod
-rw-r--r-- 1 root root 4.9K 2010-10-24 04:30 ufs2.mod
-rw-r--r-- 1 root root 5.1K 2010-10-24 04:30 uhci.mod
-rw-r--r-- 1 root root 3.4K 2010-10-24 04:30 usb_keyboard.mod
-rw-r--r-- 1 root root 3.8K 2010-10-24 04:30 usb.mod
-rw-r--r-- 1 root root 3.8K 2010-10-24 04:30 usbms.mod
-rw-r--r-- 1 root root 3.5K 2010-10-24 04:30 usbtest.mod
-rw-r--r-- 1 root root 2.7K 2010-10-24 04:30 vbeinfo.mod
-rw-r--r-- 1 root root 7.8K 2010-10-24 04:30 vbe.mod
-rw-r--r-- 1 root root 3.0K 2010-10-24 04:30 vbetest.mod
-rw-r--r-- 1 root root 3.8K 2010-10-24 04:30 vga.mod
-rw-r--r-- 1 root root 2.8K 2010-10-24 04:30 vga_text.mod
-rw-r--r-- 1 root root  17K 2010-10-24 04:30 video_fb.mod
-rw-r--r-- 1 root root    4 2010-10-24 04:30 video.lst
-rw-r--r-- 1 root root 5.5K 2010-10-24 04:30 video.mod
-rw-r--r-- 1 root root 3.8K 2010-10-24 04:30 videotest.mod
-rw-r--r-- 1 root root 5.7K 2010-10-24 04:30 xfs.mod
-rw-r--r-- 1 root root  31K 2010-10-24 04:30 xnu.mod
-rw-r--r-- 1 root root 1.9K 2010-10-24 04:30 xnu_uuid.mod
-rw-r--r-- 1 root root 6.1K 2010-10-24 04:30 zfsinfo.mod
-rw-r--r-- 1 root root  24K 2010-10-24 04:30 zfs.mod

```

---

### Post by Cheesemill on 2012-04-04
> **lisati said:**
> <aside>
Newer versions of grub don't use menu.lst
</aside>

He's using Lucid, if I remember correctly that still used grub.

---

### Post by Cheesemill on 2012-04-04
OK, my mistake. I thought that 10.04 used grub but it looks like it uses grub2 instead.
What are the contents of /etc/default/grub

---

### Post by Gad. on 2012-04-04
That directory does not exist in my system:


```
green@green:/etc/default$ cd grub
-bash: cd: grub: Not a directory
green@green:/etc/default$ dir
apport         cron    halt        ntpdate           rcS      ssh    useradd
bootlogd       devpts  irqbalance  openbsd-inetd     rsync    tmpfs
console-setup  grub    locale      pure-ftpd-common  rsyslog  ufw
green@green:/etc/default$
```

---

### Post by Cheesemill on 2012-04-04
It's a file, not a directory. What is the output of:
```
cat /etc/default/grub
```

---

### Post by Gad. on 2012-04-04
My apologies!

```

green@green:/etc/default$ cat grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by Cheesemill on 2012-04-04
That's the one. Now if you can just tell me the output of:
```
sudo update-grub
```
I can tell you what changes you need to make.

---

### Post by Gad. on 2012-04-04
Here you go, and once again thanks for your help!


```
Found linux image: /boot/vmlinuz-2.6.32-25-server
Found initrd image: /boot/initrd.img-2.6.32-25-server
Found linux image: /boot/vmlinuz-2.6.32-24-server
Found initrd image: /boot/initrd.img-2.6.32-24-server
Found linux image: /boot/vmlinuz-2.6.32-40-preempt
Found initrd image: /boot/initrd.img-2.6.32-40-preempt
Found memtest86+ image: /boot/memtest86+.bin
done

```

---

### Post by Doug S on 2012-04-04
Hi,
 
This is what I do to install a test kernel (for example):```
sudo dpkg -i linux-image-3.4.0-030400rc1-generic-pae_3.4.0-030400rc1.201203312035_i386.deb
sudo dpkg -i linux-headers-3.4.0-030400rc1-generic-pae_3.4.0-030400rc1.201203312035_i386.deb
```
I am not sure this would apply for your case (change to your file names).

---

### Post by Gad. on 2012-04-04
> **Doug S said:**
> Hi,
 
This is what I do to install a test kernel (for example):```
sudo dpkg -i linux-image-3.4.0-030400rc1-generic-pae_3.4.0-030400rc1.201203312035_i386.deb
sudo dpkg -i linux-headers-3.4.0-030400rc1-generic-pae_3.4.0-030400rc1.201203312035_i386.deb
```
I am not sure this would apply for your case (change to your file names).

I do not understand what you are asking me to do. My knowledge of ubuntu is very limited to extremely basic commands. My apologies. I think I may ride this one out with Cheese, though. Thanks!

---

### Post by Cheesemill on 2012-04-04
OK then. Edit the /etc/default/grub file using:
```
sudo nano /etc/default/grub
```
and change the line that says GRUB_DEFAULT=0 to GRUB_DEFAULT=4 and then hit CTRL+O then CTRL+X to save it. Then run:
```
sudo update-grub
```
to update grub with the new configuration.
Reboot and you're done. To check you are using the new kernel you can use:
```
uname -a
```

---

### Post by Doug S on 2012-04-04
Ignore what I said, Chessemill has it right. Sorry for the distraction.

---

### Post by Gad. on 2012-04-04
```
green@green:~$ uname -a
Linux green 2.6.32-40-preempt #87-Ubuntu SMP PREEMPT Tue Mar 6 03:23:26 UTC 2012 x86_64 GNU/Linux
green@green:~$

```

I assume this is right. Does this mean my kernel is now running at 1000hz?

---

### Post by Cheesemill on 2012-04-04
It is indeed, well done :)

I know all of that seemed complicated but trust me, it would have made a lot more sense if you could see the boot menu when your machine was starting up.

---

### Post by Gad. on 2012-04-04
Indeed, I do believe you that the kernel is now running at 1000hz, but I do not believe it has solved my problem. Originally with my game server, the stats of the FPS, if I continually sent a query to view the FPS, would range from 100-600 randomly, even using under 50% cpu, and under 10% memory... Most game servers, which I believe could simply just be much more powerful in terms of hardware, queries show 1000FPS constantly. There is no change in FPS performance on my server, even after this kernel change. I apologize for your wasted time. Although I learned many new things about ubuntu, as you have too possibly. Thanks!

Unless anyone has any further experience in solving this issue, we can consider it solved.

---

### Post by cryptotheslow on 2012-04-05
I've no idea about your game server performance unfortunately.

However, bear in mind that if your system receives an updated kernel in the normal update cycle then your preempt kernel will move one place down the list. If / when that happens you will need to either
a. edit that grub config file to default to 5 rather than 4, then issue the update-grub command
b. remove/purge the oldest normal kernel, which if you use apt-get to do so will automatically do the update-grub

HTH

---

### Post by Cheesemill on 2012-04-05
> **cryptotheslow said:**
> a. edit that grub config file to default to 5 rather than 4, then issue the update-grub command

That would be 6 instead of 4. Each kernel update adds 2 new entries to grub, the normal boot and the recovery boot, but good spot.

Another option would be to remove all of the normal kernels. This way you won't have to keep altering the grub menu.

Gad. If you want to do this then post back and I'm sure we can talk you through it.

---

### Post by xyzzyman on 2012-04-07
You're running under virtualbox. So unless the host is also running a preemptable kernel, I think switching to one in the VM can actually decrease performance if anything... Don't quote me though.

---

### Post by mitcoes on 2012-05-07
Ubuntu Precise Pangolin

sudo apt-get install linux-preempt

This package does not exist.

We are with kernel 3.2.0.24

Does the package changed its name?

Or we need other way of doing this in Ubuntu PP

I think it is a must have for advanced desktop users or Ubuntu gamers, at least as an option at boot.

---

### Post by Cheesemill on 2012-05-07
> **mitcoes said:**
> Ubuntu Precise Pangolin

sudo apt-get install linux-preempt

This package does not exist.

We are with kernel 3.2.0.24

Does the package changed its name?

Or we need other way of doing this in Ubuntu PP

I think it is a must have for advanced desktop users or Ubuntu gamers, at least as an option at boot.
The preempt kernels are no longer being developed. You could try installing linux-lowlatency instead.

---

