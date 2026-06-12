---
title: "grub 2 - dual ubuntu boot - UUID problem"
date: 2010-06-23
forum: General Help
---

### Post by yxlbaz on 2010-06-23
I am running kubuntu 10.04 with two identical instances of the op sys on partitions sda5 and sda7.  sda5 is my production system and is where grub2 is installed.  sda7 is a test system.

All is OK until update-grub runs.  sda5 is OK and the op sys on sda7 is discovered.  The only problem is that the grub.cfg entries for sda7 include references to the UUID for sda5.  I end up with 2 partitions mounted on /.  My fsck uses UUID= to mount filesystems.

This is copied from grub.cfg on sda7 before I fixed it manually -


### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-22-generic-pae (on /dev/sda7)" {
        insmod ext2
        set root='(hd0,7)'
        search --no-floppy --fs-uuid --set c8e8c121-aed4-4dc1-9527-91901bea4dc8
        linux /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=63f77f42-ddb0-4ae9-bdbf-3d263f7184ce ro quiet splash
        initrd /boot/initrd.img-2.6.32-22-generic-pae
}


- This is when 

/dev/sda7 UUID is c8e8c121-aed4-4dc1-9527-91901bea4dc8
/dev/sda5 UUID is 63f77f42-ddb0-4ae9-bdbf-3d263f7184ce

It seems that grub.cfg points to sda5 rather than sda7 for the kernel files.

I'm not sure why it should do this.  Perhaps there are reasons. I have fixed it by editing grub.cfg manually so that the UUID above references sda7 rather than sda5.

I assume that kernel updates will affect only the files on the currently mounted system?

Asking for help from those who know grub better than me.

Thanks

---

### Post by dino99 on 2010-06-23
you can run blkid to know all about your uuids

sudo blkid

then : sudo gedit /etc/fstab

to see differences if any

sudo grub-mkconfig
sudo update-grub

---

### Post by damien.caci on 2010-06-23
I have a question regarding something similar. Please bear in mind om not very experienced in linux :). My previous dual boot was Vista/Ubuntu and to make a long story short to reinstall grub i partitioned my harddrive a 3rd time to reinstall Ubuntu from LiveCD. Once i did this, i could not boot into my original Ubuntu partition. I have run sudo gedit /boot/grub/menu.lst but it is blank. I'm not sure what to do. I can boot into windows and my 2nd Ubuntu install, but i would like to access my original install because i have customized it to my liking and i don't want to do that again :P.

Thanks in advance,

damien.caci

---

### Post by dino99 on 2010-06-23
> **damien.caci said:**
> I have a question regarding something similar. Please bear in mind om not very experienced in linux :). My previous dual boot was Vista/Ubuntu and to make a long story short to reinstall grub i partitioned my harddrive a 3rd time to reinstall Ubuntu from LiveCD. Once i did this, i could not boot into my original Ubuntu partition. I have run sudo gedit /boot/grub/menu.lst but it is blank. I'm not sure what to do. I can boot into windows and my 2nd Ubuntu install, but i would like to access my original install because i have customized it to my liking and i don't want to do that again :P.

Thanks in advance,

damien.caci

in case you have created this menu.lst:
 sudo rm -f /boot/grub/menu.lst

sudo grub-mkconfig
sudo update-grub
( only grub-pc and grub-common have to be installed, look into synaptic to be sure before running the 2 commands above)

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by oldfred on 2010-06-23
Run the boot info script and maybe we can see if something is mis-configured.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by yxlbaz on 2010-06-24
Thanks for the info.

There is nothing strange about the disk config or UUIDs etc.  My fstabs are fine on each filesystem.  There are no problems after I edit grub.cfg and put in the correct UUID references.

The problem is that update-grub puts the wrong UUID references in for the os-prober section.  At least I think it's wrong. It may be intentional for some reason, but I have to edit grub.cfg each time the kernel is updated and update-grub runs.

Anyone know where I can read a bit about how the internals of grub 2 work?

Thanks

---

### Post by wilee-nilee on 2010-06-24
> **yxlbaz said:**
> Thanks for the info.

There is nothing strange about the disk config or UUIDs etc.  My fstabs are fine on each filesystem.  There are no problems after I edit grub.cfg and put in the correct UUID references.

The problem is that update-grub puts the wrong UUID references in for the os-prober section.  At least I think it's wrong. It may be intentional for some reason, but I have to edit grub.cfg each time the kernel is updated and update-grub runs.

Anyone know where I can read a bit about how the internals of grub 2 work?

Thanks

I would follow oldfred's advice to post the script, as it may show some anomalies.
For grub2 info.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

To be frank here I would not just look for information and apply it without confirmation on the forum by people like oldfred and a couple of others. You mentioned your level of experience so be careful.:p

---

### Post by yxlbaz on 2010-06-25
Thanks willee-nilee for the sound advice which I fully endorse.

Actually my reference to my experience was relative and applied mainly to grub 2.  I feel quite competent with this but I know that there are always many who know a bit more or a lot more about any specific problem.

I have around 20 yrs experience employed as sys admin with all sorts of unix systems. I am always respectful of advice but there is a level at which I am pretty sure of my ground.

It's all working OK but I would prefer not to have to edit grub.cfg after each kernel change.

Thanks

---

