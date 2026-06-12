---
title: "ubuntu live usb casper-rw RO mode"
date: 2010-04-14
forum: General Help
---

### Post by ebhomepc on 2010-04-14
Hi all im new to the forum but i have been using ubuntu for some time i relly need my question answering please. OK i have got ubuntu live setup on usb boots fine i have a casper-rw setup on a fat32 drive that all works fine but now i have my ubuntu setup all fine with all the changes i like done so i would like to no how to boot into the persistent mode but in readonly. So what i would have is all my changes but not any more so i cant mess it UP? PLEASE HELP.

---

### Post by elhigu on 2010-10-12
I was trying to to the same thing, since I couldn't get isolinux to understand persistent switch for reading casper-rw file when I boot from DVD.

This method will not remove stuff that has been in original live-cd that you have removed in persistent mode, so it might mess up things... I should check out how filesystem.squashfs and casper-rw are normally merged when livecd is booted in persistent mode and fix that part where I combine two fs images to one.

I did following procedure to copy everything from casper-rw filesystem image to filesystem.squashfs image. I did this with osx so I didn't just mount filesystem.squashfs but I actually extracted modified and recompressed it. There might be some errors in following, since I did not test this on linux. 

Naturally before staring you should backup whole memorystick :)

1. extract filesystem.squashfs content: 

sudo unsquashfs -d extracted_squashfs path_to_your_live_usb/casper/filesystem.squashfs

2. mount your casper-rw (I did use macfuse and fuse-ext2, but with linux it's easier with loopback device)

sudo mkdir -p /mnt/casper-rw
sudo mount -o loop,ro path_to_your_live_use/casper-rw /mnt/casper-rw

3. copy all data from casper-rw to extracted_squashfs image

cd extracted_squashfs
sudo cp -p -R -P -f /mnt/casper-rw/*  .

4. regenerate filesystem.squashfs

sudo mksquashfs extracted_squashfs path_to_your_live_use/casper/filesystem.squashfs -noappend

If this gives e.g. zlib error you can try with different switches... with me -processors 1 helped. Also compressing switches could help if anything else does not.

Now you should have everything from casper-rw in nonpersistent squashfs image, you should boot from stick without "persistent" kernel parameter.

Then you should maybe regenerate manifest and md5sum etc. files. For that there is instructions in [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) and [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

Hope that this helps someone, this should work on any OS that can compile squashfs-tools and mount ext2 partitions.

Good luck, Mikael Lepistö

Actually zlib fail happened few times also with processors 1 switch, so looks like it's just about luck, when mksquashfs does not fail. 

I also did not find a way to mount aufs filesystems on os x, so finally I had to do combining casper with squashfs in linux in virtualbox which was like 1000 times easier than tying to battle with this on osx. I just mounted squashfs filesystem and casper-rw and then mounted them as aufs like this:

sudo mount -t squashfs -o loop,ro filesystem.squashfs /mnt/squashfs
sudo mount -o loop,rw casper-rw /mnt/casper-rw
sudo mount -t aufs -o br:/mnt/squashfs=ro:/mnt/casper-rw none /mnt/aufs

And copied combined files to os x as tar which seems to handle links etc. better (or at least easier without any extra options) than plain copy

tar -cvvf shared_directory/aufs.tar -C /mnt aufs

And then untarred aufs.tar in osx and repeated step 4 with aufs directory to generate new filesystem.squashfs.

However generated bootable iso still does not looks identical to my live usb system :( 

Anyone has ideas e.g. how to enable persistent (which just would mount casper-rw in readonly mode) mode also when booting from dvd isolinux instead of syslinux?

---

