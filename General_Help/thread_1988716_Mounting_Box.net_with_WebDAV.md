---
title: "Mounting Box.net with WebDAV"
date: 2012-05-28
forum: General Help
---

### Post by SyntheticShield on 2012-05-28
I am trying to mount my Box.net account using the following directions:

[Mount Your Box.com Account]("http://linuxfordummies.org/mount-your-box-com-account-in-linux/")

Its in line with all the other instructions Ive seen but I keep getting the following message:

```
/sbin/mount.davfs: file /etc/davfs2/secrets has wrong owner
```

I made a directory in my home folder called Box.net I then try to mount it with:

```
sudo mount /home/scotty/Box.net
```

I have checked, double checked and rechecked again and the login email address and password are absolutely correct.  So I am at a loss as to what the issue could be and hope someone can help out.

---

### Post by prshah on 2012-05-28
> **SyntheticShield said:**
> 
```
/sbin/mount.davfs: file /etc/davfs2/secrets has wrong owner
```

I made a directory in my home folder called Box.net I then try to mount it with:

```
sudo mount /home/scotty/Box.net
```


Your /etc/davfs2/secrets file should be owned (and in group) root. You can check this with the terminal command (Dash-Terminal)```
ls -l /etc/davfs2/secrets
``` You might have changed the permissions and/or user:group. 

Does your Box.net drive mount? I doubt it. If it does, then you can ignore the below advice.

If it doesn't please post the entry you have made in /etc/fstab for Box.net. if the entry is made as per the instructions, you shouldn't need to use sudo to mount.

Also, ensure that your user is part of the davfs2 group; you can check with ```
groups
```

If you can't get it to work, or still have doubts, please post back for more details with the outputs to the above commands.

---

### Post by SyntheticShield on 2012-05-28
The secrets file was owned by me as I did change it.  So I changed ownership back to root with chown root:root and got the following:

```

sudo mount /home/scotty/Box.net
/sbin/mount.davfs: file /etc/davfs2/secrets has wrong permissions

```

Then when I tried without sudo I got:

```

/sbin/mount.davfs:/home/scotty/.davfs2/davfs2.conf:24: system option in user configuration file

/sbin/mount.davfs: file /etc/davfs2/secrets has wrong permissions

```

I am part of the davfs2 group, which I used the following command to do so:

```

sudo adduser $USER davfs2

```

My fstab entry is:

```

https://www.box.com/dav /home/scotty/Box.net	davfs	rw,user,noauto 0 0

```

Ive also tried:

```

https://www.box.com/dav /home/scotty/Box.net	davfs	defaults,uid=scotty,gid=scotty	0	0

```

When I try to mount using the second fstab entry I get:

```

mount: only root can mount https://www.box.com/dav on /home/scotty/Box.net

```

When I use sudo to try and mount it, I get: 

```

/sbin/mount.davfs: file /etc/davfs2/secrets has wrong permissions

```

I appreciate your help.  I have not tried this before and when I tried to google it to find some answers I came up with nothing but instructions on how to set up the whole thing, nothing that addressed that particular issue.

---

### Post by prshah on 2012-05-28
> **SyntheticShield said:**
> The secrets file was owned by me as I did change it.  So I changed ownership back to root with chown root:root and got the following:
```

/sbin/mount.davfs: file /etc/davfs2/secrets has wrong permissions

```


As well as changing the ownership (root:root), you also have to change the permissions so that it is only (read/write)able by root, eg```
sudo chmod 600 /etc/davfs2/secrets
```

Everything else looks fine, it should work after the above change.

---

### Post by SyntheticShield on 2012-05-28
prshah, thank you so much for your help.  That seems to have done the trick.  I was able to mount the folder after that.  I did have to use sudo to do so though.

However, there were a couple of issues.  First, when I added a file to the folder, it was not showing up in my Box.net account.  Though after a while, it did finally show up in the Box.net account online.  Im not sure what caused that and in the grand scheme of things it is not a big deal though that did not occur when I connected directly to the account with WebDAV through the Connect to Server option in Nautilus.

The other issue was that when I rebooted the PC to see if the fstab entry would work, it did not.  I was prompted before getting back to the desktop with a message saying that it could not be mounted.

I sure wish they would just come out with a client for Ubuntu and be done with it and make it simple.  I have 50GB of storage space there and it would be nice to be able to sync my files to that.

The grand plan was to have that mount automatically, and then see if I could use Unison to sync files to the Box.net folder, which 'should' have sync'd file to box.net online.  It was a thought anyway.

I have another path I am going to pursue but I will have to make a post about it here as well to get some direction on how to go about it.  So thank you so much for your help.  For what it is worth, I have wrote down all you instructed to do so if I come back to this I should be able to set it up with little issue other than the automatically mounting on reboot.

---

