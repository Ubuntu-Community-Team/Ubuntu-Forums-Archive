---
title: "GRUB/BURG not setting the right UUID"
date: 2012-10-03
forum: General Help
---

### Post by maxi157 on 2012-10-03
Hello, I wasn't sure where to post this issue so I figured I could do it here. It's both a GRUB and BURG issue, both work the same way. 
Anyways, I have GRUB version 1.98-1ubuntu13. I just did some modifications to my partitions using GParted. Everything went fine and my other OSses were detected fine by the OS-prober script. I had a problem with my Archlinux partition though. The UUID is detected fine on the "--fs-uuid --set" line from /boot/burg/burg.cfg, since it matches the device UUID label on /dev/disk/by-uuid/ and the GParted right-click "information" option. However, the kernel line's UUID  (linux /boot/vmlinuz-linux root=UUID=ad4103fa-d940-47ca-8506-301d8071d467 ro quiet") doesn't match that UUID. I honestly don't know where that UUID came from. I've tried uncommenting the "GRUB_DISABLE_LINUX_UUID=true" line on /etc/defaults/burg so BURG could use a device label instead of the UUID, but after running update-burg, it still uses the UUID for the kernel line. I know I could just edit the burg.cfg file to use a device label instead of the UUID, or set the right UUID on the kernel line, but I want to do it the right way. Is there any way to make update-burg or burg-mkconfig commands use the right UUID? Oh, I've tried the same on GRUB, same results.

```
menuentry "Arch GNU/Linux, with Linux core repo kernel' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'gn$
        insmod ext2
        set root='(hd0,5)'
        search --no-floppy --fs-uuid --set 7d3f6e9b-90cf-4f1d-9290-dc4fba7ee1dc
        linux /boot/vmlinuz-linux root=UUID=ad4103fa-d940-47ca-8506-301d8071d467 ro quiet
        initrd /boot/initramfs-linux.img

```

---

### Post by oldfred on 2012-10-03
I do not know burg. 

Does your Arch install have a separate /boot? The os-prober usually tries to read grub.cfg or other boot files to copy boot stanzas from.

Just to see where everything is at and document all the installs, post the link to the BootInfo report from this:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by maxi157 on 2012-10-03
Sorry, I forgot to mention it works the exact same way GRUB does, I'll edit my post now. 
No, I have Arch in only one partition, it never caused me any trouble before. I'll try Boot-Repair and post the results here when I'm done.

---

### Post by maxi157 on 2012-10-04
HECK YEAH I was able to solve it.
As you said, OS-prober was reading the boot lines from the  grub.cfg of the other OSes. I just had to update the grub.cfg from the offending OSes (thus setting the right UUID in them. That's where the wrong UUID was coming from), then update Grub/Burg on my main partition. Thanks!

---

