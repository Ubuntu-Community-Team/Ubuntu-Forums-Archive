---
title: "Botched Removal of Encrypted Home Folder"
date: 2011-06-19
forum: General Help
---

### Post by mrnatas20 on 2011-06-19
I followed the instructions here after searching around regarding removing the encryption of my home folder. [https://help.ubuntu.com/community/EncryptedPrivateDirectory]("https://help.ubuntu.com/community/EncryptedPrivateDirectory")

Here is what I followed specifically: 

> Perhaps an Encrypted Private Directory is not for you. To remove this setup:

Ensure that you have moved all relevant data out of your ~/Private directory
Unmount your encrypted private directory
 ```
$ ecryptfs-umount-private 
```
Make ~/Private writable again
 ```
$ chmod 700 ~/Private 
```
Remove ~/Private, ~/.Private, ~/.ecryptfs (Note: THIS IS VERY PERMANENT)
 ```
$ rm -rf ~/Private ~/.Private ~/.ecryptfs 
```
Uninstall the utilities
```
 $ sudo apt-get remove ecryptfs-utils libecryptfs0
``` 

Well I didn't have a ~/Private directory, but I forged on ahead nonetheless. After completing these steps, I rebooted and was confronted with several errors, one along the lines of 
not being able to read a .ICE in /home/nick/ and then Nautilus complained that no home directory existed, and there was one more error I can't quite remember.  I rebooted again after googling these errors and not finding anything relevant to decryption / encryption, and my desktop was restored to somewhat working order. I had my wireless drivers and my normal background, but instead of the normal contents of my home folder, all I had was the base template for home folders ('Documents', 'Music', etc..) with no file contents at all. 

 then tried to manually recover my home folder by following other instructions on the same page I posted, which were basically to unwrap the passphrase and use fnek to decrypt the folder from another linux partition (I tried using the LiveCD), but afterwards trying to read or copy the files in the mounted directory did not work at all. In fact, the first times I would try to access the files via an 'ls', my computer reverted to some tty-ish looking screen talking about how stacks couldn't be read or something, and then after going back into the interface via ctrl+alt+f7, the ls command was hanging. I tried doing some recursive copying from this supposed decrypted home folder, it hung as well..

Anyway, I am afraid I can't get access to my home folder documents anymore.  I recall not using the FNEK option once when I tried to mount the decrypted home folder and I got a bunch of encrypted folders, but this didn't really help me.  The given directions that have paid off for others who were simplying trying to read their unadulterated home folder from another partion will probably not work for me I fear, as I attempted to remove the encryption and instead screwed stuff up. 

Can anyone help me? 

P.S. I followed the instructions on 'Removing' the decryption from the Ubuntu page, I am mildly disappointed that Ubuntu offers an option to encrypt the home directory upon installation, which seemed nice at the time, but no formal way (or at least, from what it looks like, no way that doesn't destroy the home folder) to remove the decryption. I was annoyed that I couldn't read my home folder data from other o.s.s.  But that's beside the point, as my home folder now I can't read from any os :(

---

### Post by wildmanne39 on 2011-06-19
Hi, anytime the remove command is used like that it can be dangerous, did you remove your data first like it mentioned so in case of a problem you would have that data in another folder or on anther drive?

---

### Post by mrnatas20 on 2011-06-19
> **wildmanne39 said:**
> Hi, anytime the remove command is used like that it can be dangerous, did you remove your data first like it mentioned so in case of a problem you would have that data in another folder or on anther drive?

It told me to remove data from the ~/Private directory. I didn't even have that directory, only a ~/.Private directory. Before deleting it, I checked its contents and it was a bunch of ECRYPT data, nothing that was (visibly) going to be lost if I deleted that directory.

---

### Post by wildmanne39 on 2011-06-19
> **mrnatas20 said:**
> It told me to remove data from the ~/Private directory. I didn't even have that directory, only a ~/.Private directory. Before deleting it, I checked its contents and it was a bunch of ECRYPT data, nothing that was (visibly) going to be lost if I deleted that directory.Hi, ok I understand, there has got to be a better way then those instructions gave or at least there should be.

---

### Post by mrnatas20 on 2011-06-19
> **wildmanne39 said:**
> Hi, ok I understand, there has got to be a better way then those instructions gave or at least there should be.

So are you saying I'm out of luck then?

---

