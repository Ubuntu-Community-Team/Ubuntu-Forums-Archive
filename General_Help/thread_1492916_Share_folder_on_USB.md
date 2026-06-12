---
title: "Share folder on USB"
date: 2010-05-25
forum: General Help
---

### Post by Fantasmo on 2010-05-25
Hi,

I would like to be able to run Ubuntu 10.04 from USB and copy files to a shared folder on the same USB stick that I could access from a Windows machine and vice versa.
I've created a folder on the USB stick from Windows but cannot find it via Ubuntu and vice versa.
I've created a shared folder from within Ubuntu but same issue.
Is it possible to do this? Would be very handy for me.

Thanks

---

### Post by rg_stephens on 2010-05-25
That *should* be fairly easy to do. Perhaps it's just looking in the wrong location?

---

### Post by 3rdalbum on 2010-05-25
Can I ask for clarification? The folder that you want to share is on the same USB stick as Ubuntu, and the Windows machine is physically the same computer as what you're running Ubuntu on?

If that's so, then I don't think you can do what you want to do - and "shared folders" is for sharing files across a network. Why don't you just mount the Windows partition from the Places menu in Ubuntu and put files directly onto your internal hard disk?

---

### Post by ajgreeny on 2010-05-25
You might be able to make a new partition on the ubuntu USB drive by shrinking the current ubuntu partition, and then that should be visible to both OSs, provided it is ntfs.  If it is a ext3 or ext4 partition, windows will not be able to see it, never mind read or write to it.  That is also why the shared folder will not work if it's on an ext partition, and whilst it *may* be possible with samba, I think the separate partition would be a better solution.

---

### Post by Fantasmo on 2010-05-25
I have a physical Windows based machine and run Ubuntu from a USB on other machines as and when required.

I believe that creating another partition on the USB stick is the solution. Thanks for all advise.

---

