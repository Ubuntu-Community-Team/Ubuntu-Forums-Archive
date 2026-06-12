---
title: "How to decrypt encrypted home folder?"
date: 2010-11-15
forum: General Help
---

### Post by binarylife on 2010-11-15
Hi 
How to decrypt encrypted home folder?Which is already encrypted ?
thanks

---

### Post by binarylife on 2010-11-15
help please:confused:

---

### Post by Enigmapond on 2010-11-15
My guess is that you need that password or GPG key that is was encrypted with.

---

### Post by binarylife on 2010-11-15
> **Enigmapond said:**
> My guess is that you need that password or GPG key that is was encrypted with.

I know the password , but how can I decrypt it ?
and i didn't mention that I can access it from the same user , but another one  no . 
and also from windows .
thanks

---

### Post by Enigmapond on 2010-11-15
Need to know just how you encrypted it. A little more information on what you did initially will help anyone here in providing a possible solution. The more information...the better the advise..:)

Cheers!

---

### Post by binarylife on 2010-11-15
> **Enigmapond said:**
> Need to know just how you encrypted it. A little more information on what you did initially will help anyone here in providing a possible solution. The more information...the better the advise..:)

Cheers!

Alright , simple , all that I did when first installed Ubuntu 10.10 last month , you know the installer ask me to create a new user name and so on ..
so I did ,and checked by mistake something saying :
encrypt home folder .
and that's it . 

more information , ask me and I'll try to answer 
Thanks a lot

---

### Post by binarylife on 2010-11-17
Any help ?

---

### Post by loungedaddy on 2010-11-22
I have a similar question. Encrypted during the 10.10 install, and I have the pass. Plus, the homefolder exists within it's own partition (the partition is marked "/home").

So I am curious how much of a chore it would be to, for exmaple, reinstall Ubuntu. Or install the next distro from scratch. 

I might give it a whirl myself soon in a "what happens when I do this...?" moment.

---

### Post by loungedaddy on 2010-11-22
With Windows, it's not that your home folder is encrypted. 

Windows doesn't read Linux partitions, unfortunately. So even without an encrypted home folder, Windows will not play nice with your other operating system. 

Incidently, I know there are some programs that allow Windows to read some Linux "ext2" and "ext3" file systems; but from what I have read, they are a chore to use, and yield mixed results.

And sadly ... Ubuntu 10.10 usues an ext4 file system. So *shrug* I think Windows won't read your home folder.

---

### Post by binarylife on 2010-11-22
> **loungedaddy said:**
> With Windows, it's not that your home folder is encrypted. 

Windows doesn't read Linux partitions, unfortunately. So even without an encrypted home folder, Windows will not play nice with your other operating system. 

Incidently, I know there are some programs that allow Windows to read some Linux "ext2" and "ext3" file systems; but from what I have read, they are a chore to use, and yield mixed results.

And sadly ... Ubuntu 10.10 usues an ext4 file system. So *shrug* I think Windows won't read your home folder.



No I have The same problem as you did . But I mean from Windows , I use a special program  to read ext4 ! So I can see all files on Ubuntu , but The problem is that I can't access the Home folder because it is encrypted , And I hope that someone will help us here ... 
Thanks btw.

---

### Post by surfer on 2010-11-22
the program that encrypts your home folder is called [eCryptFS]("https://launchpad.net/ecryptfs"). i strongly doubt that you will find a windows driver for it. haven't looked for it though... maybe you're lucky.

---

### Post by binarylife on 2010-11-22
[QUOTE=surfer;10148818]the program that encrypts your home folder is called [eCryptFS]("https://launchpad.net/ecryptfs"). i strongly doubt that you will find a windows driver for it. haven't looked for it though... maybe you're lucky.[/QUeeeOTE]

How to do it ??
Thanks

---

### Post by surfer on 2010-11-22
google?

---

### Post by surfer on 2010-11-22
by the way: your home directory is not encrypted with your password; the password encrypts the key that is really used to encrypt the files and directories.

on ubuntu, the relevant tools are:
```
ecryptfs-add-passphrase
ecryptfs-insert-wrapped-passphrase-into-keyring
ecryptfs-manager
ecryptfs-migrate-home
ecryptfs-mount-private
ecryptfs-rewrap-passphrase
ecryptfs-rewrite-file
ecryptfs-setup-private
ecryptfs-setup-swap
ecryptfs-stat
ecryptfs-umount-private
ecryptfs-unwrap-passphrase
ecryptfs-wrap-passphrase

```
the manpages will tell you what they are for.

---

### Post by clivejo on 2010-12-06
If your user account name is "user"

1) ```
sudo ecryptfs-unwrap-passphrase /home/user/.ecryptfs/wrapped-passphrase
``` 

Enter your account password for the user account, this will then display the encryption key, **take a note of this key,** if the user account password is wrong you won't be able to retrieve the key.

2)```
sudo ecryptfs-add-passphrase --fnek 
```

Enter the key you retrieved in step 1.  This will insert two auth tok with sig.  **Take a note of the second key.**

3) ```
sudo mount -t ecryptfs /home/user/.Private /home/user/Private 
```



[LIST]
[*]Enter your key (Noted in step one)
[*]Select: aes  (use the aes cipher)
[*]Select: 16  (use a 16 byte key)
[*]Enable plaintext passthrough: n  
[*]Enable filename encryption: y ) 
[*]Filename Encryption Key (FNEK) Signature:  (Enter the key noted in step 2)
[*]Since you are using superuser privileges instead of your regular user  account, you may get a warning that you might have entered the  passphrase wrong, even if you didn't. Continue the mount operation and don't save the key if it asks.
[/LIST]
Assuming you entered your key correctly, you should be able to temporarily access your data at  /home/user/Private

Good luck :tongue:

---

### Post by ubu-for on 2011-01-05
> **clivejo said:**
> Assuming you entered your key correctly, you should be able to temporarily access your data at  /home/user/Private

Thank you so much!

---

### Post by 86themachine on 2011-08-01
Thanks clivejo this was very helpful for me. I think your instructions should include making a directory for "Private" to mount to. 

In order for this to work don't you need to make a directory named Private to mount to?

sudo mkdir /home/user/Private

---

### Post by repelsteel on 2012-01-15
> **binarylife said:**
> [QUOTE=surfer;10148818]the program that encrypts your home folder is called [eCryptFS]("https://launchpad.net/ecryptfs"). i strongly doubt that you will find a windows driver for it. haven't looked for it though... maybe you're lucky.[/QUeeeOTE]

How to do it ??
Thanks


hi binarylife,
i had a ssd in my netbook with linux mint 12 on it and with an encrypted home-dir like yourself from the initial installation menu.  So i know my password.
Now my OS wont boot anymore so i booted a livedvd for mint 12 and with that i tried to access the old home-dir.
1. attach an external harddisk
2. in terminal cd to the encrypted home-dir:   cd /media/whatever/home/user
3. sudo ecryptfs-recover-private     (NOT eNcrypt......)
4. give your passsword
5. the home-dir will be copied to /tmp/xxxxxx
Now, nautilus file manager and the terminal cant access the copied dir and I am not sure what to do now but this worked for me:
6. sudo nautilus
7. with this 'root-nautilus' i can access the copied home-dir and copy all the files from there to the external harddisk

note: i believe it is not a smart policy to keep using nautilus with 'sudo', so only use it for this incident

Does this help?

---

### Post by happy.camper on 2012-04-24
Thanks a LOT clivejo, your post saved me so much time!

---

