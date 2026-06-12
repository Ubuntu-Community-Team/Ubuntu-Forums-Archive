---
title: "Problem with partition and latest update for Koala"
date: 2009-11-14
forum: General Help
---

### Post by jeust on 2009-11-14
I've updated yesterday the 9.10 version, and there was an option that dabbled with permissions and users.

I thought that it was only for accounts created from the update onwards... 

Silly me, as i can't access not even mount this partition

/dev/sda7   *       15621       29285   109764081    7  HPFS/NTFS

not even using mountmanager, or the storage device manager.

It isn't even mentioned in those programs.

Can i revert from the latest update, or work around the problem?

I'd really appreciate the help, as i need to work on some files there.

---

### Post by undecim on 2009-11-14
Are you a member of the plugdev group? I believe that is the group that gives users permission to removable media. (i.e. anything that isn't mounted by default in /etc/fstab, including non-removable drives)

Check by typing "groups" in a terminal, and see if one of the words that outputs is "plugdev"

If it's not there, add yourself to the plugdev group by typing "sudo gpasswd -a username plugdev" where username is your username

Then log out, log back in, and see if that fixes your problem.

---

### Post by jeust on 2009-11-14
> **undecim said:**
> Are you a member of the plugdev group? I believe that is the group that gives users permission to removable media. (i.e. anything that isn't mounted by default in /etc/fstab, including non-removable drives)

Check by typing "groups" in a terminal, and see if one of the words that outputs is "plugdev"

If it's not there, add yourself to the plugdev group by typing "sudo gpasswd -a username plugdev" where username is your username

Then log out, log back in, and see if that fixes your problem.

It doesn't fix it... thanks for the reply though :(

---

### Post by mikewhatever on 2009-11-14
> **jeust said:**
> I've updated yesterday the 9.10 version, and there was an option that dabbled with permissions and users.
..............


Can you elaborate on that option a bit. I've never seen anything like that during system updates.

---

