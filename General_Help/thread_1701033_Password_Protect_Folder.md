---
title: "Password Protect Folder"
date: 2011-03-05
forum: General Help
---

### Post by -tr on 2011-03-05
Hi there. Is there a simple password protection element available for directories in Ubuntu 10.10? Basically I'm moving and family members will probably have access to my computer and root password at some point, and I'd like to be able to keep them out.

I know there are several programs out there that pump out some pretty serious encryption, but it's a fairly large folder and is added to quite frequently (plus I'm without internet on it until after the move). I've set it to hidden in an unused directory for now, and they're not computer savvy so they'd probably never find it as is, but even so I'd like to be safe.

Any help is appreciated!

---

### Post by juanfpina on 2011-03-05
You could always just hide the folder, and make it so you can only see it when files/folders are unhidden. That works for me.

---

### Post by jbiggs12 on 2011-03-05
create a folder on your computer and type
```
sudo mount -t ecryptfs /path/to/folder /path/to/folder
```
you saw me right, repeat the path twice.

after that, it gives you a couple of encryption options. make sure that you remember these for the next time you try to mount it.

enter in your password and hit enter, the drive should now be mounted. copy your files, when you want to lock the dir type
```
sudo umount /path/to/folder
```

The files should now be encrypted and unreadable. When you want to re-mount it, just re-type the first command. Cheers!!

Oh, and if you don't have ecryptfs installed (which you should if your version is later that 8.10), you can install it by typing
```
sudo apt-get install ecryptfs-utils
```

---

### Post by -tr on 2011-03-06
The folder's already hidden and apt-get doesn't work offline, but thanks.

Anyways, tried mounting with ecryptfs and i get "wrong fs type, bad option, bad superblock, missing codepage, or other error". Pretty vague error so I'm betting on missing codepage being the one. Will come back to this when I get back online.. Thanks again.

---

### Post by jbiggs12 on 2011-03-06
My bad. Try typing
```
ecryptfs-setup-private
```
instead. that should set up a "Private" folder in your home directory that you can play around with. 

Once you've set it up, run
```
mount.ecryptfs_private
```

and unmount with
```
umount.ecryptfs_private
```

Does it work now?

---

### Post by -tr on 2011-03-06
That one returns "'ecryptfs-setup-private' is not installed" etc. so guess that was the problem before, too. Also didn't help that i was throwing in an 'n' sometimes, thinking it was to be 'encryptfs'. =s

---

### Post by mcduck on 2011-03-06
Have you considered the simple option of just giving your family members their own user accounts to the computer?

That would be a lot easier than password protecting individual directories, and all your family members could have their own files, their own web browser bookmarks, e-mail accounts, desktop backgrounds and whatever each person likes to do with the computer.

Protecting each user's personal files form others would be as simple as changing the permission of the user's home directory (or any specific directory inside it) to not allow others to see it.

And if you want some of the family members to have admin rights, you can easily add them to his user account. (you of course shouldn't even *have* a root password, let alone give such password to anybody else).

---

### Post by nacho-wan on 2011-07-28
> **jbiggs12 said:**
> create a folder on your computer and type
```
sudo mount -t ecryptfs /path/to/folder /path/to/folder
```
you saw me right, repeat the path twice.

after that, it gives you a couple of encryption options. make sure that you remember these for the next time you try to mount it.

enter in your password and hit enter, the drive should now be mounted. copy your files, when you want to lock the dir type
```
sudo umount /path/to/folder
```

The files should now be encrypted and unreadable. When you want to re-mount it, just re-type the first command. Cheers!!

Oh, and if you don't have ecryptfs installed (which you should if your version is later that 8.10), you can install it by typing
```
sudo apt-get install ecryptfs-utils
```

Hi, maybe you could help me. I did an encrypted directory last week using these instructions. However yesterday and today I have been unable to mount the directory. 

Ubuntu does mount the drive but if I try to access from console or Nautilus I get a black screen and the following in my system log

```
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ] Call Trace:
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c11fc757>] ecryptfs_parse_tag_70_packet+0x2c7/0x580
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c11fa61b>] ecryptfs_decode_and_decrypt_filename+0xdb/0x150
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c11f3fd3>] ecryptfs_filldir+0x33/0xb0
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c118913e>] call_filldir+0x8e/0xc0
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c11f3fa0>] ? ecryptfs_filldir+0x0/0xb0
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c11892df>] ext3_dx_readdir+0x16f/0x220
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c11f3fa0>] ? ecryptfs_filldir+0x0/0xb0
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c1189892>] ext3_readdir+0x422/0x500
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c1132c00>] ? link_path_walk+0x720/0xb10
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c112feea>] ? path_put+0x1a/0x20
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c1133288>] ? do_path_lookup+0x68/0x120
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c113050b>] ? putname+0x2b/0x40
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c11f3fa0>] ? ecryptfs_filldir+0x0/0xb0
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c15097cd>] ? _raw_spin_lock+0xd/0x10
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c121b260>] ? security_file_permission+0x90/0xb0
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c1136e0e>] vfs_readdir+0x8e/0xb0
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c11f3fa0>] ? ecryptfs_filldir+0x0/0xb0
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c11f3f39>] ecryptfs_readdir+0x59/0xc0
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c1136ac0>] ? filldir64+0x0/0xf0
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c1136e0e>] vfs_readdir+0x8e/0xb0
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c1136ac0>] ? filldir64+0x0/0xf0
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c1136fba>] sys_getdents64+0x6a/0xc0
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ]  [<c1509bf4>] syscall_call+0x7/0xb
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ] Code: ff 8d b6 00 00 00 00 85 ff 74 c2 8d 4d f0 89 da 89 f8 e8 e8 19 00 00 eb b4 8d b6 00 00 00 00 55 89 e5 3e 8d 74 26 00 85 c0 74 0a <f0> ff 08 0f 94 c2 84 d2 75 02 5d c3 b8 e0 90 75 c1 e8 5e 4c e5 
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ] EIP: [<c12148ec>] key_put+0xc/0x30 SS:ESP 0068:d9d2dd5c
Jul 28 10:16:06 natty-inspiron kernel: [  XXX.ZZZZZZ] CR2: 00000000ffffff82
Jul 28 10:16:06 natty-inspiron kernel: [  198.083608] ---[ end trace 6399e1c24743e530 ]---
```

Please notice that the directory has  text passthrough enable and protected filenames. I left blank the passphrase for the filenames.

---

### Post by haqking on 2011-07-28
> **mcduck said:**
> Have you considered the simple option of just giving your family members their own user accounts to the computer?

That would be a lot easier than password protecting individual directories, and all your family members could have their own files, their own web browser bookmarks, e-mail accounts, desktop backgrounds and whatever each person likes to do with the computer.

Protecting each user's personal files form others would be as simple as changing the permission of the user's home directory (or any specific directory inside it) to not allow others to see it.

And if you want some of the family members to have admin rights, you can easily add them to his user account. (you of course shouldn't even *have* a root password, let alone give such password to anybody else).

+1

I am always reading posts about people having access to others files due to shared logins...baffles me.

least privelege all the time and discretionary access control through correct user management.

---

