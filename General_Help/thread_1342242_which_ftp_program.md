---
title: "which ftp program?"
date: 2009-11-30
forum: General Help
---

### Post by spiky001 on 2009-11-30
hi i,am looking to put a ftp server on my machine so i can access it from another locaton i was hoping to get advice on what 1 to install? I have looked to at apache but not sure if i need all of it. I,m just looking at uploading /downloading files then accessing from local lan as i need them

---

### Post by snake_eyes on 2009-11-30
# install 'proftpd' with GUI
> sudo apt-get install proftpd gadmin-proftpd ucf

# For security reasons add the following lines to /etc/proftpd/proftpd.conf
> DefaultRoot ~
IdentLookups off
ServerIdent on "FTP Server ready."


Cheers,

---

### Post by spiky001 on 2009-11-30
hi snake just 1 other thing can i make my 2nd had drive availble with this program for the sharing also can i connect with a windows pc?

---

### Post by t0p on 2009-11-30
If you install **sshd** to the computer you wish to access remotely, you will then be able to reach it through **Places > Connect to Server...**.  You'll then be presented with a choice of protocols in a drop-down menu.  This will include **Public FTP**, **SSH**, amongst others.

If you select SSH, you'll then be able to click-and-drag files from one computer to the other via a Nautilus (File Manager) Window.

---

### Post by snake_eyes on 2009-11-30
Hello,

> sudo apt-get install samba smbfs system-config-samba

and then see my post at: [http://ubuntuforums.org/showthread.php?t=1342186](http://ubuntuforums.org/showthread.php?t=1342186)

---

