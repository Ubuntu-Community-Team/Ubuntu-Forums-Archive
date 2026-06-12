---
title: "How do I choose a drive to boot?"
date: 2011-09-16
forum: General Help
---

### Post by Jolicoeur on 2011-09-16
I have Ubuntu on my main hard drive and now I would like to load my  Vista onto a removable drive (it inserts into the tower).  If I were to  disconnect the Ubuntu drive and then install Vista would it install onto  the second drive? If yes, if I reconnect the Ubuntu drive and reboot  what will happen?  Is it easy to choose which drive to boot? I don't  care if they ever share a storage space, the Vista is for my wife to use  some programs and to keep her data on, also the Vista crashes every few  months and needs a reinstall.  My concern is how to choose the system  that I want to boot.  Thanks.

---

### Post by sikander3786 on 2011-09-16
The most simplest and the best of the choices would be to disconnect the Ubuntu drive as you said and then install Vista to the external drive. Once the installation completes, boot Vista and make sure everything is working properly before connecting the Ubuntu drive.

Now, with both of the drives connected, boot Ubuntu. Go to a Terminal and run this command:

```
sudo update-grub
```

It would add Vista to the Grub menu and if it isn't set to show by default when you boot your PC, it would automatically set it to. This way whenever you boot your PC, you'd have a choice to boot Vista from the Grub menu even without switching the HDD boot order.

If you want to do it the ugly way, you can switch the HDD boot order in Bios menu. The newer PCs come with a quick boot option as well (commonly by pressing F9), where you can quickly choose your boot drive.

The Grub method is the better one anyways.

---

### Post by Jolicoeur on 2011-09-16
THANKS

So, I input sudo udate-grub and that is all? Then reboot?  what will I see when I reboot? A clear choice?

---

### Post by sikander3786 on 2011-09-16
This kind of menu with an option to boot Vista at the very last:

[http://viswanathj.files.wordpress.com/2011/02/grub-menu.png](http://viswanathj.files.wordpress.com/2011/02/grub-menu.png)

Make sure you type the exact command as mentioned in my above post ;)

---

### Post by Mark Phelps on 2011-09-16
It's extremely unlikely that you will get Vista to install to an external drive.  The Windows installers simply will not allow you to do that.  Microsoft doesn't want folks walking around with a portable version of their OSs.

---

