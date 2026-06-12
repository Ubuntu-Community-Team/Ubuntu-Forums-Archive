---
title: "Chroot ssh and encrypt home directory"
date: 2011-11-21
forum: General Help
---

### Post by dbgsports on 2011-11-21
Hi

I want to accomplish 2 things.

1. Chroot users using either ssh or sftp
2. Encrypt a users home directory 

I can do either but the problem arises when I try to do both at the same time. It all comes down to permissions....

To chroot the home directory needs to be owned by root.
To encrypt it needs to be owned by the user 

Anyone got a way I can accomplish both of these? 
Note: Encrypting the entire disk using the encrypt LVM option doesn't provide what I want. I want to control this per user.

Happy to use any version of Ubuntu as its a new install.

Thanks

DBG

---

### Post by dbgsports on 2011-11-21
Further note.
I am happy with any solution which encrypts a users data when they are not logged in and keeps them from getting outside their home directory when they are.

---

### Post by dbgsports on 2011-12-09
Turned out to be a reasonably easy solution for sftp.
Your users will need to put their file in a subdirectory but that suits my needs.

Just create a subdirectory, in this case its called userfiles. Make it the users home directory but have ssh chroot to /home/$username.

That way you keep chroot happy by root owning the chroot directory and encrypt-utils happy because the user owns their home directory.

I used OpenSSH_5.3p1  on Lucid. I read ChrootDirectory doesnt work for versions earlier than 4.8.


apt-get install ecryptfs-utils
addgroup sftp (gid for the group turned out to be 1001)
adduser --encrypt-home --gid=1001 --home=/home/test3/userfiles test3

Edit /etc/ssh/sshd_config. Comment out the existing 
Subsystem line and paste the below. (group based. use Match User for user based)

Subsystem sftp internal-sftp

Match group sftp
       X11Forwarding no
       ChrootDirectory /home/%u
       AllowTcpForwarding no
       ForceCommand internal-sftp
Match



YOU SHOULD RECORD YOUR MOUNT PASSPHRASE AND STORE IT IN A SAFE LOCATION.
ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase
THIS WILL BE REQUIRED IF YOU NEED TO RECOVER YOUR DATA AT A LATER TIME.

---

