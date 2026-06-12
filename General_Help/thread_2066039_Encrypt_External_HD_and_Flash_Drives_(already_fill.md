---
title: "Encrypt External HD and Flash Drives (already filled w/data)"
date: 2012-10-03
forum: General Help
---

### Post by johnsmoke on 2012-10-03
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]Ok, so I have a Mybook external hard drive and some thumb/flash drives. I already have them filled with documents and things. My question is - is there a way to encrypt these devices at this point so that if someone were to steal them, they would not have access to the information on the drive? 
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by coldraven on 2012-10-03
I think that you are asking for trouble if you try that.
It would make more sense to copy the files to another encrypted medium, then when you are positive that you can access the data to delete the originals.
Sorry I cannot help you with a command that would do that.

---

### Post by Mark Phelps on 2012-10-03
The only encryption products I know that can do this are TrueCrypt and DiskCryptor -- which only run on MS Windows.  In all other cases, you have to start with an empty volume.

---

### Post by johnsmoke on 2012-10-03
> **coldraven said:**
> I think that you are asking for trouble if you try that.
It would make more sense to copy the files to another encrypted medium, then when you are positive that you can access the data to delete the originals.
Sorry I cannot help you with a command that would do that.
 
I hear what you are saying. I guess this would work, correct? - [FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]
[http://www.myapitips.com/2011/06/19/install-truecrypt-to-encrypt-folders-in-ubuntu-11-04/](http://www.myapitips.com/2011/06/19/install-truecrypt-to-encrypt-folders-in-ubuntu-11-04/)
[/SIZE][/FONT][/SIZE][/FONT] 
With this I can make an encrypted folder. At that point I should just be able to drag the files I want encrypted into it? 
 
Also, say I need to update to a new version of Ubuntu at some point... how would my files be transferred over or kept? Also, what if Truecrypt eventually ceases to exist - would I still be able to acess my files w/older versions of the program? Anyway, sorry for all the questions, I just want to know exactly what I am doing before I attempt this.

---

### Post by johnsmoke on 2012-10-08
> **johnsmoke said:**
> I hear what you are saying. I guess this would work, correct? - [FONT=Helv][SIZE=2]
[SIZE=2][FONT=Helv][http://www.myapitips.com/2011/06/19/install-truecrypt-to-encrypt-folders-in-ubuntu-11-04/](http://www.myapitips.com/2011/06/19/install-truecrypt-to-encrypt-folders-in-ubuntu-11-04/)[/FONT][/SIZE]
[/SIZE][/FONT]
With this I can make an encrypted folder. At that point I should just be able to drag the files I want encrypted into it? 
 
Also, say I need to update to a new version of Ubuntu at some point... how would my files be transferred over or kept? Also, what if Truecrypt eventually ceases to exist - would I still be able to acess my files w/older versions of the program? Anyway, sorry for all the questions, I just want to know exactly what I am doing before I attempt this.
 
Anyone?

---

### Post by johnsmoke on 2012-10-11
Bueller?

---

### Post by piratebill on 2012-10-11
What I would do is copy all the data off the drive, and then create encrypted partitions with LUKS ([https://help.ubuntu.com/community/EncryptedFilesystemHowto3](https://help.ubuntu.com/community/EncryptedFilesystemHowto3)).  I've done it and it works great.  Note, only linux systems will be able to read said drive afterwards.

EDIT:
if the wiki page above doesn't work (it looks to be fairly old), the arch linux wiki is kept up to date ([https://wiki.archlinux.org/index.php/Dm-crypt_with_LUKS](https://wiki.archlinux.org/index.php/Dm-crypt_with_LUKS))

---

### Post by RamseyT on 2012-10-11
TrueCrypt now has a a Linux build. You can use that to encrypt and save the existing data. Select the Entire drive option then select Encrypt in place. It is slower but it will work.

Test on the least valuable item first. :)

---

