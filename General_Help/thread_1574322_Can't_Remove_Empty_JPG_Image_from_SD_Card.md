---
title: "Can't Remove Empty JPG Image from SD Card"
date: 2010-09-14
forum: General Help
---

### Post by dodle on 2010-09-14
I transferred some pictures from an SD card then 'shift+delete'ed them from the card.  But I forgot to 'unmount' the card before I removed it from its slot.  Now when I insert the card, it shows that there are a bunch of JPG images on the card but they cannot be viewed or deleted.  Here is the output when I try to delete them:

```
:/media/NIKON D3000/DCIM/100D3000$ rm DSC_0328.JPG
rm: cannot remove `DSC_0328.JPG': Read-only file system
:/media/NIKON D3000/DCIM/100D3000$ sudo rm DSC_0328.JPG
rm: cannot remove `DSC_0328.JPG': Read-only file system
```

It is very annoying.  I'm sure formatting the card would solve the problem, but there are still some pictures on there that I would like to leave.  Plus, there should be a way to do this without formatting.  It seems like a very big bug to me.

---

### Post by JCM_Pico on 2010-09-14
you may try *sudo rm [file]*, it's strange but it work some times...

---

### Post by coffeecat on 2010-09-14
> **dodle said:**
> It seems like a very big bug to me.

Sounds like a very big and useful feature to me. You've corrupted a Microsoft filesystem with an unclean unmount and now Linux is trying to prevent any further damage by mounting it read-only. And the fact that you can't view some of the pictures suggests a bad corruption of the fie allocation table. Don't forget that FAT filesystems (as you get on SD cards) are both prehistoric and fragile.

You could try chkdsk from a Windows machine.

---

### Post by dodle on 2010-09-14
> **JCM_Pico said:**
> you may try *sudo rm [file]*, it's strange but it work some times...

Tried it, does not work.

> **coffeecat said:**
> Sounds like a very big and useful feature to me.

I'm sure that Linux handles media formatted with EXT2/3/4 file systems just fine.  But most digital cameras still use FAT32.  So whether I like it or not, I still have to deal with that file system, and I have to deal with it on my Ubuntu computer.  I just think it's a little annoying that now I have to wait until I am ready to transfer all of the pictures from my card, then format the card with my camera in order to get rid of those files.

---

### Post by coffeecat on 2010-09-14
> **dodle said:**
> I'm sure that Linux handles media formatted with EXT2/3/4 file systems just fine.  But most digital cameras still use FAT32.  So whether I like it or not, I still have to deal with that file system, and I have to deal with it on my Ubuntu computer.  I just think it's a little annoying that now I have to wait until I am ready to transfer all of the pictures from my card, then format the card with my camera in order to get rid of those files.

I'm not sure what ext2/3/4 has to do with anything. There's a reason digital cameras use FAT32. 

Agreed that it's annoying, but a similar thing happened to me, but using  Windows. This was a few years ago - I was using Linux but the then  Linux kernel didn't have the driver for  my SD card reader. In my case it  was the camera that corrupted the filesystem on the card - some random  event when I took a picture. I was able - with difficulty - to access  most of the pictures with Windows XP and copy them, but not to delete or view the corrupted ones. I had to reformat the card in the camera to be able  to use it again - after copying the pictures I was able to rescue.

I think one just has to be aware of the limitations of FAT32, whatever OS you are using on your computer, and be prepared for just this sort of thing. Mac users as well as Windows users would have the same problem.

---

