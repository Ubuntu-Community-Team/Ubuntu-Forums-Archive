---
title: "Problem with Banshee and Music folder"
date: 2012-01-31
forum: General Help
---

### Post by coldjeanz on 2012-01-31
I'm running a dual boot with Win7 and Ubuntu 11.10. On Banshee the source of my music folder is located on my Windows drive. This works fine but when I turn off my computer and start Banshee up again it won't play any of my files because it changes my source back to "media" or something. So I have to reload all my music and it erases all the ratings and play counts. 

The only solution I can think of to this is to just place the music on my Ubuntu drive however there is more drive space on Windows and also I can't access Ubuntu files from Windows so it doesn't make sense to keep media on Ubuntu. Is there anything else I can do?

---

### Post by LeeCrites on 2012-01-31
On the one dual-boot system we are (currently) running banshee on, I did this:

1) I fixed the mounting so the windoze partition always mounts at a specified spot. It used to be /media/whatever, and sometimes it would mount and sometimes it wouldn't.

I just googled "mount windows partition" (I'm betting searching windoze might work, but probably not...) for the instructions.

2) I figured out what directory banshee was looking for, and made a symlink to the directory where the music files actually are.

I note that if banshee cannot find the directory it thinks should contain the music files that it will simply reset to the default one. What you are describing is exactly what I was experiencing, so I *assume* the problems are the same...

Now it works most of the time. I am still having problems with banshee, but they are different issues. The above solved those issues.

Lee

---

### Post by Dumbestcrayon on 2012-02-01
Edit your /etc/fstab file to include the necessary arguments for mounting. At the very end of the file add the code below (using your own information)

```
/dev/sda3	/media/Stuff/	ntfs-3g	defaults	0	0	
```

/dev/sda3 is the filesystem (or drive) to be mounted. Once you've booted into Ubuntu and mounted the drive you can find it by typing the command "mount" in the terminal. It will show you where the drive is mounted. 

/media/Stuff/ is the folder I chose to mount the drive to. You can put whatever you want there but /media/x is the standard for mounted (or loaded) devices. 

ntfs-3g is the mount type. This is tricky if you don't know the type but since you're using a Windows drive we can accurately presume that it's ntfs. You may have to apt-get install ntfs-3g. Make sure it's installed first before you reboot. 

You can check to see if it's installed by running the following command

```
dpkg --get-selections | grep ntfs-3g
```

Once you've saved the /etc/fstab you can reboot and your filesystem will be automatically mounted upon boot to the folder you specified. 


Hope this helps.

---

### Post by coldjeanz on 2012-02-01
Thanks for the replies. For now I just took the lazy way out and moved a copy of my music folder to Ubuntu. Oh well.

On a semi related matter my Banshee seems to close by itself randomly. It's not crashing it's just that the program will occasionally all of a sudden close after a song finishes. I don't get it.

---

### Post by Dumbestcrayon on 2012-02-01
You should probably put that in another thread, but I'll suggest running banshee from the terminal to see if any errors output there first.

If this thread is resolved mark it as "SOLVED" to prevent other people from trying to help :)

Thanks!

---

