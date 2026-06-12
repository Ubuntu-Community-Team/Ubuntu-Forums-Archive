---
title: "Mounting SMB through Nautilus vs FStab"
date: 2012-03-28
forum: General Help
---

### Post by MadsRC on 2012-03-28
So, I've got myself a little NAS, and 100mbit cabling.

I can mount the Windows share 2 ways. Either through Nautilus (Connect to Server -> Windows Share) or I can add the following to my fstab:
```
//server/share /mnt/mountname cifs credentials=/etc/cifspwd,iocharset=utf8,mode=0777,dir_mode=07*&#8203;77 0 0
```

If I do it though Nautilus, I can achieve writing speeds of up to 7.8MByte/s. Problem is though, that if I stream a video from the server to VLC, VLC won't allow me to browse the server for subtitles.

If I mount it with FStab, I can achieve writing speeds of up to 12MByte/s. I can browse all files, even from inside applications, since they will be located at /etc/mountname. Problem is though, that the window manager seems to crash sometimes.

Anybody know why the big difference in writing speeds? It is the same files, approximately 95GByte that I get the different speeds with.

Also, seems as though files are owned by Root, when mounting them with the FStab... But I guess I can get around that by having the mnt point in my home folder.

Does the Nautilus way use some kind of Secure connection that encrypts and decrypts the data, hence the difference in speeds, or what is happening?

---

### Post by bab1 on 2012-03-28
> **MadsRC said:**
> So, I've got myself a little NAS, and 100mbit cabling.

I can mount the Windows share 2 ways. Either through Nautilus (Connect to Server -> Windows Share) or I can add the following to my fstab:
```
//server/share /mnt/mountname cifs credentials=/etc/cifspwd,iocharset=utf8,mode=0777,dir_mode=07*&#8203;77 0 0
```

If I do it though Nautilus, I can achieve writing speeds of up to 7.8MByte/s. Problem is though, that if I stream a video from the server to VLC, VLC won't allow me to browse the server for subtitles.

If I mount it with FStab, I can achieve writing speeds of up to 12MByte/s. I can browse all files, even from inside applications, since they will be located at /etc/mountname. Problem is though, that the window manager seems to crash sometimes.
Are you saying Gnome crashes?  Or do you mean Nautilus?
> 
Anybody know why the big difference in writing speeds? It is the same files, approximately 95GByte that I get the different speeds with.

Also, seems as though files are owned by Root, when mounting them with the FStab... But I guess I can get around that by having the mnt point in my home folder.

Does the Nautilus way use some kind of Secure connection that encrypts and decrypts the data, hence the difference in speeds, or what is happening?

Nautilus uses gvfs-fuse (a userland virtual filesystem) when mounting the share.  When you mount the share via **fstab** you are using kernel routines.  You can see this from the terminal using the **mount **command,  It you should see this with a Nautilus mount of the share```
gvfs-fuse-daemon on /home/bab/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bab)

```
All of the parameters used in gvfs are available to be used in fstab.  Using **uid** and **gid** along with **user** will allow you to own the files and directories on the fstab mount.  The man pages explain it pretty well```
man mount
man mount.cifs
```

The speed differential is most likely due to tuning parameters used by gvfs-fuse.

---

