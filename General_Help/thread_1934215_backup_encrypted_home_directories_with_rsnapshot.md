---
title: "backup encrypted home directories with rsnapshot"
date: 2012-03-01
forum: General Help
---

### Post by midden on 2012-03-01
I am setting up rsnapshot to backup local disks to an external drive (eventually this will be a remote NAS, but for now it is a local eSATA HD). My question is how to set up the backup so that encrypted home directories are backed up correctly.

I want to avoid massive copies of the encrypted directories but I can't figure out how to decrypt them and then backup (I realize that the backup will not be encrypted in this case). So, my questions are:

1) How do I decrypt local drives for an rsnapshot backup (where rsnapshot is run as root through cron)?
2) Is there a way to re-encrypt the backed-up data? 

Thanks for your help.

midden

---

### Post by Paddy Landau on 2012-03-02
This is a question that I have wondered about. I wish there were an easy solution.

> **midden said:**
> 1) How do I decrypt local drives for an rsnapshot backup (where rsnapshot is run as root through cron)?
The way to do this is to have some sort of a script that runs before rsnapshot to decrypt the relevant folders -- however, you need the decryption keys (two per user)! Alternatively, get every user with an encrypted folder to log in at the same time before running rsnapshot. Be sure to exclude all point-folders (i.e. folders beginning with a dot) in the /home folder (e.g. *.ecryptfs*).

Additionally, and unfortunately, decryption is poorly documented. Although it is straightforward, try finding the instructions! I spent over two weeks searching; I eventually managed, but decided not to bother trying again.

 > **midden said:**
> 2) Is there a way to re-encrypt the backed-up data?
If you need your backup to be encrypted, I suggest you back up without encryption but to an encrypted device. [TrueCrypt]("http://www.truecrypt.org/") is the only package I know of that is free, reliable and cross-platform, although I presume there are others.

---

### Post by midden on 2012-03-02
Thanks Paddy. The encryption thing is driving me insane -- on the one hand we want to encrypt our data, but on the other we need to leave our data in plain view on the backup side. I will look into Truecrypt, but really wish there was a more omnibus method for securely storing AND backing up data.

If anyone has other suggestions I am all ears.

midden

(Of course regardless of my attempts at data security, reality will more likely play out as portrayed in xkcd [http://xkcd.com/538/](http://xkcd.com/538/))

---

### Post by Paddy Landau on 2012-03-02
> **midden said:**
> The encryption thing is driving me insane...
I don't know your circumstances, but is it possible to create a script that runs for just a single user only -- but make it automatically start when a user signs in? Then, when each user logs in, rsnapshot kicks in to back up just that user for as long as he is logged in.

You will miss any changes made to a user's folder when that user is not logged in, but probably that's not a big issue.

If you enter a command in [FONT=Lucida Console]/etc/profile[/FONT], it will be executed every time a user logs in.

> **midden said:**
> ... on the one hand we want to encrypt our data, but on the other we need to leave our data in plain view on the backup side...
With TrueCrypt, once the device is mounted, it remains mounted until either you dismount it (via TrueCrypt) or log off (whoever is running TrueCrypt -- and, of course, root could do that, so rebooting would dismount the device).

> **midden said:**
> (Of course regardless of my attempts at data security, reality will more likely play out as portrayed in xkcd [http://xkcd.com/538/](http://xkcd.com/538/))
Well, yes, of course, LOL! Encryption deters but does not prevent.

---

