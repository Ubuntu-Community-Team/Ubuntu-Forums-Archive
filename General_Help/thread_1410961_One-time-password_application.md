---
title: "One-time-password application"
date: 2010-02-19
forum: General Help
---

### Post by And1945 on 2010-02-19
Hello,

I am wondering, if there exist an application, that you type your root password into, it remembers it, and you have root access until logout/reboot.

Thanks in advance, because I would prefer it that way.

---

### Post by lloyd_b on 2010-02-19
> **And1945 said:**
> Hello,

I am wondering, if there exist an application, that you type your root password into, it remembers it, and you have root access until logout/reboot.

Thanks in advance, because I would prefer it that way.

First off, Ubuntu doesn't *have* a root password.  By default, the root account is disabled.

Instead, it uses the "sudo" command, which allows a user to run a command as root, if that user's account is configured to do so in the "sudoers" file or the person is a member of the "admin" group.

"sudo" typically "times out" after 15 minutes, forcing the person to enter their password again, but the "sudoers" file can be modified to change this time out, potentially having it *never* time out, which is what I think you're trying to accomplish.

Lloyd B.

---

### Post by snowpine on 2010-02-19
It is possible to create a root account in Ubuntu so that you can do anything you want without a password. However, it is *extremely* unrecommended, so you will not find the answer on these forums. Google is your friend if you insist on compromising your security in this fashion. :)

---

### Post by And1945 on 2010-02-19
Is there no way to "copy" the root or sudo permissions to my user?

---

### Post by And1945 on 2010-02-21
I take it as there is no way. Except editing the etc/sudoers file, which apparently is against ubuntu security policy.

Im just having a hard time making sudo this and sudo that a part of a productive day.

For example. I make websites. And when I install a LAMP or xampp, I dont have permissions to add folder how I want to the folder where those applications are installed. It is somewhat annoying to have to go to the terminal typing sudo nautilus, and then give myself the rights to put whatever I want in that folder.

A request for future releases of ubuntu... a semi-root permission, which gives users semi-elevated rights. For example put files where they want. But still need the sudo for editing operating system important files.

I do not believe this would compromise security.

---

### Post by bmckee on 2010-02-21
Use sudo -i to keep elevated priv until you log out of it.

Editing the sudoers file is certainly not 'against security policy' - that file is there for a reason.

---

### Post by mcduck on 2010-02-21
> **And1945 said:**
> I take it as there is no way. Except editing the etc/sudoers file, which apparently is against ubuntu security policy.

Im just having a hard time making sudo this and sudo that a part of a productive day.

For example. I make websites. And when I install a LAMP or xampp, I dont have permissions to add folder how I want to the folder where those applications are installed. It is somewhat annoying to have to go to the terminal typing sudo nautilus, and then give myself the rights to put whatever I want in that folder.

A request for future releases of ubuntu... a semi-root permission, which gives users semi-elevated rights. For example put files where they want. But still need the sudo for editing operating system important files.

I do not believe this would compromise security.

You should just add yourself to the "www-data" -group to give your normal user permissions to the LAMP data directory. Or, if you just use the syste to develop the web sites, use Apache's configuration to create a site in your user's home directory.

Pretty much all this kind of tasks can be handles easily by correct use of the user/gropu system in Linux. Creating a"semi-root" account as you described sounds highly insecure, and I can't really iamgine any sitaution that would require such permissions. Besides, write permission also means permission to delete files, so you can't have permisison to add stuff to system directories wthiout having the permissions to delete and edit stuff in system directories..

---

### Post by And1945 on 2010-02-21
> **bmckee said:**
> Use sudo -i to keep elevated priv until you log out of it.

Editing the sudoers file is certainly not 'against security policy' - that file is there for a reason.

My bad, misread something on the security discusion forum...

> **mcduck said:**
> You should just add yourself to the "www-data" -group to give your normal user permissions to the LAMP data directory. Or, if you just use the syste to develop the web sites, use Apache's configuration to create a site in your user's home directory.

Pretty much all this kind of tasks can be handles easily by correct use of the user/gropu system in Linux. Creating a"semi-root" account as you described sounds highly insecure, and I can't really iamgine any sitaution that would require such permissions. Besides, write permission also means permission to delete files, so you can't have permisison to add stuff to system directories wthiout having the permissions to delete and edit stuff in system directories..

Every time I edit in groups I end up having no permissions, and I have to re-install

---

### Post by junapp on 2010-02-21
> **mcduck said:**
> You should just add yourself to the "www-data" -group to give your normal user permissions to the LAMP data directory. Or, if you just use the syste to develop the web sites, use Apache's configuration to create a site in your user's home directory.


yes, do this. +1 to this advice.

```
sudo adduser and1945 www-data
```

---

### Post by And1945 on 2010-02-21
> **junapp said:**
> yes, do this. +1 to this advice.

```
sudo adduser and1945 www-data
```

That "code" works for all folders that says "whine, you do not have the permissions" ... just write the complete location?

---

### Post by mcduck on 2010-02-21
> **And1945 said:**
> That "code" works for all folders that says "whine, you do not have the permissions" ... just write the complete location?

no, that code adds your user to group "www-data", and /var/www has write permissions for all users who belog to group "www-data". As you can see, the command doesn't actually have any location in it, only a group name.

(still, don't try to add your user to "root" grop even though most of the system directories would have full permissions for root user/group, that would just break things)

What other directories you need to constantly write to?

---

### Post by And1945 on 2010-02-22
My other partitions.

I also says I dont have permissions for that. I have edited it, though.

---

### Post by mcduck on 2010-02-22
> **And1945 said:**
> My other partitions.

I also says I dont have permissions for that. I have edited it, though.

THat depends on what type of partitions they are. If they use any Widn ows filesystem (FAT, NTFS) you simply define the permisisons you want to sue for the whole partition in /etc/fstab, since the fileystems themselves lack any support for users/gropus and permisisons as Linux uses them.

For any Linux filesystem, you can safely just chown the partition's mountpoint to your user. Or the plugdev group, which would give permissions for all normal user accounts).

---

