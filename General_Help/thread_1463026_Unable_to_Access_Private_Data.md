---
title: "Unable to Access Private Data"
date: 2010-04-26
forum: General Help
---

### Post by AllenC1983 on 2010-04-26
Ubuntu 8.10

During installation I decided to encrypt my home directory.  The problem occurred after I attempted to change my password.  Not only did my new password not register, I was unable to login to my account, giving me error messages such as:
     Could not update ICEauthority file /home/craig/.ICEauthority
     Problem with configuration server /usr/lib/libgconf2-4/gconf-sanity-check-2 status 256
     Could not create required folders:
          /home/craig/Desktop
          /home/craig/.nautilus
I sort of (fixed/broke) the situation by opening a terminal and logging into my /home/craig directory and deleted the .cache (or something like that) folder.  After that I was able to login, but to a default desktop(ie.  all settings seemed to revert that of a new install).  Apps I have installed are still accessible, but any files and folders I had in ./~ I am unable to access.  There is a symlink called "Access Your Private Data" but it doesn't seem to do anything.
Is there any way to restore my data, or is it hosed for good?

---

### Post by cariboo on 2010-04-26
Make sure all the files and directories in ~/ are owned by you and have a permission of at least 755. If sudo still works, open a termianl and type:

```
sudo chown -R user:user /home/user
```

where user = your user name, then type:

```
sudo chmod -R 755 /home/user
```

again user = your user name, you will probably get an error that it can't change the user name and permissions of ~/.gvfs, just ignore it. You then may be able to access your private data.

---

### Post by AllenC1983 on 2010-04-27
After searching around for a bit, I found that solution as well.  However, I got an error message to the effect that that particular directory does not exist.  An ls -l revealed nothing in the way of files or folders.  I believe I that in recovery mode from a root terminal.

Trying that after logging in doesn't help either.  Drive info shows basically that there is no space being used on /home even though there should be 10+gb in use.

I think I may just do a reinstall and remember in the future to back up my data on an external drive.

---

### Post by AllenC1983 on 2010-04-27
As an aside, is there a reason a password change would not register?  There may be another way to do it, but I used System > Administration > Users & Groups.  This whole mess started when I tried to change my password and it's something I try to do regularly.  I would like to prevent this from happening again whenever I try to change my password in the future.

---

