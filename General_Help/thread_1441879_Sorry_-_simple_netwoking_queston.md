---
title: "Sorry - simple netwoking queston"
date: 2010-03-29
forum: General Help
---

### Post by Quarkrad on 2010-03-29
What/how is the best way to share/open/edit etc files across two Ubuntu PCs I have at home?  Read things about Samba etc but I do not have a windows environment.  All I have is two PCs, say 192.168.0.1 and 192.168.0.2 both running 9.10.  Is there a gui that can help? Thanks.

---

### Post by coffeecat on 2010-03-29
You don't need Windows to use samba. Although samba is based on Windows shares, it's a perfectly good way of sharing between two Linux machines.

On the first machine, open your home folder and create a folder to use as a share. Right-click on it and select 'sharing options'. You'll be prompted to install the necessary bits of samba. Follow the wizard, let it install whatever it needs, log out and in again, right-click on the folder again and complete setting up the share.

Do the same on the second machine. Now you should be able to access each share from the "other" machine. If you can't see the share by hostname (in Places > Network), you can either:

In a Nautilus window, File > Connect to server > Service type = Windows share, and use the 192.168.x.y address in the Server field.

Or:

Have a look at this:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Check all the points, but particularly Problem 3 and edit nsswitch.conf as described (and install windbind).

---

### Post by gmargo on 2010-03-29
I just use NFS.  Simple to set up and reliable.

---

### Post by fragos on 2010-03-29
I use NFS between my Desktop and Laptop as my server. Both being on the same LAN. On the server there must be an /etc/exports with the following. Replace the fields in {} with your information. In my example I'm giving access to the entire home folder tree. There can be multiple entries giving more clients permission.

/home/{Laptop user} {Desktop hostname}.local(rw)

This allows the Desktop to access the home folder of the laptop. Prior to Ubuntu 8.04 you need to run "sudo exportfs -rv" for the system to read /etc/exports. New versions do this for you at boot.

On the Desktop create a folder to mount to. In my case I placed that folder in my home folder.

On the Desktop side I run

sudo mount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

To un-mount I run

sudo umount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

You can extrapolate what to do from this working example. I chose not to use fstab to mount and wrote a couple of bash scripts that supply the parameters to the mount and umount commands.

---

