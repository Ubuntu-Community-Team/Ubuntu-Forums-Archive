---
title: "LAN Setup"
date: 2010-10-19
forum: General Help
---

### Post by bill-lancaster on 2010-10-19
2 PCs (wl-Dimension-3000 and bill-Vostro-200)

I want to share the filesytem on wl-Dimension-3000.

On wl-Dimension-3000

/etc/exports contains this line

/home              192.168.1.0/24(rw,sync,no_root_squash)


Then running "sudo /etc/init.d/nfs-kernel-server restart" produces this message:-

 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                               exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.0/24:/home".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

                                                                         [ OK ]
 * Starting NFS kernel daemon                                            [ OK ] 

I thinks this is OK so far.

On bill-Vostro-200

"sudo mount wl-Dimension-3000:/home /mnt/home"  produces:-

mount.nfs: Failed to resolve server wl-Dimension-3000: No address associated with hostname


Can anyone help?

---

### Post by lrgmmc on 2010-10-19
Hey Have a look here. seams to be what you are trying to do.
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by lindsay7 on 2010-10-19
I all you want to do is look at and transfer files on the two computers, this is easy.

[http://my.opera.com/ubuntunerd1/blog/share-files-between-two-ubuntu-computers-via-ssh](http://my.opera.com/ubuntunerd1/blog/share-files-between-two-ubuntu-computers-via-ssh)

---

### Post by bill-lancaster on 2010-10-19
Phew!  Went through everything in /SettingUpNFSHowTo

$ sudo  mount -t nfs4 -o proto=tcp,port=2049 nfs-server:/ /mnt

resulted in

mount.nfs4: Failed to resolve server nfs-server: No address associated with hostname

also

$ sudo  mount -t nfs4 -o proto=tcp,port=2049 nfs-server:/users /home

resulted in

mount.nfs4: Failed to resolve server nfs-server: No address associated with hostname

have checked that both filesystems are NFSv4.
both computers are running Ubuntu 10.10

any ideas?

---

### Post by bill-lancaster on 2010-10-19
Re SSH

Thanks for the idea.  I already used it and it worked fine.  I want to access the server files from code and couldn't find a way of addressing the ssh mount

---

### Post by SeijiSensei on 2010-10-19
> **bill-lancaster said:**
> mount.nfs4: Failed to resolve server nfs-server: No address associated with hostnamep

Put an entry into /etc/hosts on the client that has the IP address and name for "nfs-server".

> **bill-lancaster said:**
> Re SSH

Thanks for the idea.  I already used it and it worked fine.  I want to access the server files from code and couldn't find a way of addressing the ssh mount

You can create an entry in /etc/fstab using the sshfs filesystem type.  See [this thread](http://ubuntuforums.org/showthread.php?t=430312) for details.

---

### Post by bill-lancaster on 2010-10-20
thanks for suggesting "/etc/fstab using the sshfs filesystem type" etc.
After an hour or two of fiddling I failed again!
However, following this line I tried using scp commands which enables me to transfer files.
Hooray!

---

### Post by sanjibeceltic on 2010-10-20
I have 5 computer in my office with Linux OS can you tell me how to setup the LAN connection?

[http://www.capmaison.com]("http://www.capmaison.com/")

[http://www.thebodyholiday.com]("http://www.thebodyholiday.com/")

---

### Post by SeijiSensei on 2010-10-20
> **bill-lancaster said:**
> However, following this line I tried using scp commands which enables me to transfer files.

If you're going to use scp in a script, you should implement [shared key authentication]("http://en.gentoo-wiki.com/wiki/SSH_Public_Key_Authentication") if you haven't already.  You'll avoid needing to use a password that way.

@sanjibeceltic

I suggest you start a separate thread and provide more details about what you need.  Do you already have network hardware in place?  A router of some kind?  What steps have you already taken?

---

