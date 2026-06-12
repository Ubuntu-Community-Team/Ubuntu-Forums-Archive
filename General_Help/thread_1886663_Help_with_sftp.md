---
title: "Help with sftp"
date: 2011-11-25
forum: General Help
---

### Post by molipha on 2011-11-25
I'm having problems installing filezilla so I'm trying to figure out how to copy files from a usb device to a remote server. I am able to log into the server and the command prompt shows the server directory. From there, I'm stumped!

I imagine I would use cp, but I can't figure out how to specify the usb device and folder.

Many thanks.

---

### Post by searchfgold6789 on 2011-11-25
cp works like this:```
cp {source} {destination}
```Once you have plugged in your USB drive you can copy the files directly, but first you need to mount it. You need to find out what device you USB drive is, such as /dev/sdc1 (the "mount" command is useful for this), and then mount it like this {using /dev/sdc1 as an example. You also have to create a mounting directory first.}:```
sudo mkdir /mnt/usb 
sudo chown -R (Your username) /mnt/usb 
sudo mount /dev/sdc1 /mnt/usb
```Then copy the files:
```
cp /mnt/usb/foo/bar /destination/folder
```

---

### Post by zeroseven0183 on 2011-11-25
Assuming you have Ubuntu 11.10

1. Open Nautilus (or your Home Folder)
2. From the global menu, click File
3. Select Connect to Server...
4. Depending on the type of server, you either select Public FTP or FTP (with login)
5. Fill-up the IP Address or the hostname
6. Click Connect

Once another window is open, you can then copy the files from the USB drive to the FTP folder.

Additional step: You can actually copy first the files from the USB device to a local folder on your Ubuntu then to the remote server.

---

### Post by molipha on 2011-11-25
:d

---

### Post by searchfgold6789 on 2011-11-25
+1 zeroseven. I thought the issue was with server edition :D My solution will still work from the terminal though.

---

