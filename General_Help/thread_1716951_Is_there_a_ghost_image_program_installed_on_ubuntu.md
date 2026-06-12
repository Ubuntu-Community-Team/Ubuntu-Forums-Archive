---
title: "Is there a ghost image program installed on ubuntu 9.10"
date: 2011-03-29
forum: General Help
---

### Post by mick463 on 2011-03-29
Hi there i have a computer running ubuntu 9.10 set up as a server in my classroom. I have ftp http and an internal mail server set up on it as well as other settings. I really want to  make a copy of the system so i have a back up of the os. i have figured out that i can attach a hdd to the computer and copy the os via the command line with an ubuntu live cd but this only works as long as the computer that is receiving the backup is exactly the same or the same computer. I would like to transfer the image to a portable hdd then install the os onto virtual box ( a virtual machine).
Is there a way to do this without buying expensive software. dose ubuntu 9.10 have a product similar to Norton ghost.
Thank you MIck463.

---

### Post by anglican on 2011-03-29
> **mick463 said:**
> Hi there i have a computer running ubuntu 9.10 set up as a server in my classroom. I have ftp http and an internal mail server set up on it as well as other settings. I really want to  make a copy of the system so i have a back up of the os. i have figured out that i can attach a hdd to the computer and copy the os via the command line with an ubuntu live cd but this only works as long as the computer that is receiving the backup is exactly the same or the same computer. I would like to transfer the image to a portable hdd then install the os onto virtual box ( a virtual machine).
Is there a way to do this without buying expensive software. dose ubuntu 9.10 have a product similar to Norton ghost.
Thank you MIck463.This is quite easy to do. First take a copy of your hard-drive. You will need a second hard-disk that is larger than your main disk. Then you can copy the primary HD with :
```
cat /dev/sda | VBoxManage convertfromraw stdin /path/on/second/disk/image.vdi NUMBEROFBYTES
```to determine the value for NUMBEROFBYTES use:
```
fdisk -l /dev/sda
```Then use the media manager in VirtualBox to add the newly converted drive. I'm assuming the drive you want to image is /dev/sda (the most likely option).

H

---

### Post by seawolf167 on 2011-03-29
You can also use [Clonezilla ]("http://www.clonezilla.org")to make an image of your hard drive, then restore that image to a blank VBox drive using the same method. [Here ]("http://jlorenzen.blogspot.com/2010/07/restoring-clonezilla-image-using.html")is a very quick result from a Google search.

---

### Post by mick463 on 2011-03-30
> **anglican said:**
> This is quite easy to do. First take a copy of your hard-drive. You will need a second hard-disk that is larger than your main disk. Then you can copy the primary HD with :
```
cat /dev/sda | VBoxManage convertfromraw stdin /path/on/second/disk/image.vdi NUMBEROFBYTES
```to determine the value for NUMBEROFBYTES use:
```
fdisk -l /dev/sda
```Then use the media manager in VirtualBox to add the newly converted drive. I'm assuming the drive you want to image is /dev/sda (the most likely option).

H

Thank you for your response. Doing it this way when i mount it on to my virtual machine do i have to create a drive on the virtual machine the same size as the drive on the real machine (80 Gig). Also do i need to run that command from a live cd.
Cheers mick463.

---

### Post by anglican on 2011-03-30
> **mick463 said:**
> Thank you for your response. Doing it this way when i mount it on to my virtual machine do i have to create a drive on the virtual machine the same size as the drive on the real machine (80 Gig). Also do i need to run that command from a live cd.
Cheers mick463.Initially the image will be the same size as the drive, but you can resize it to any size you want using ```
sudo VBoxManage modifyhd --resize <SIZE_IN_MB> filename.vdi
```Once you've resized the image you can use gparted in the VM to use the extra space for existing partitions (or adding new partitions). I don't think you need to boot a live CD to create the image.

H

---

### Post by mick463 on 2011-03-31
> **anglican said:**
> Initially the image will be the same size as the drive, but you can resize it to any size you want using ```
sudo VBoxManage modifyhd --resize <SIZE_IN_MB> filename.vdi
```Once you've resized the image you can use gparted in the VM to use the extra space for existing partitions (or adding new partitions). I don't think you need to boot a live CD to create the image.

H

Thank you for your help i will give it a go and let you know how it turns out.
Cheers mick463

---

