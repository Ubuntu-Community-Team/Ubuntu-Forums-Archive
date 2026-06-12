---
title: "encrypted backup to DVD"
date: 2011-01-15
forum: General Help
---

### Post by oldmankit on 2011-01-15
I would like to periodically (perhaps once a year) burn all of my files (photos etc.) to DVD, to give to a friend to store at his house.  I do regular backups to an external harddrive.

I have over 20GB, so I guess about 5 DVDs, to backup.

My ideal solution would be for them to be encrypted, only to be decrypted if I have a major problem (laptop+external hard drive become inaccessible).

What would be the best way to do this?  I could create a password-protected .rar file, but I've noticed these can be cracked using freely-available software.

I use ecryptfs to store sensitive data on my laptop.  Should I encrypt data using ecryptfs before burning to DVD?

---

### Post by XeonBloomfield on 2011-01-15
Are you doing only files backup or partition snap shot?

You can use other compression format than RAR. 
RAR protection is nothing for password breaking software now...

You can compress it to file or files and use that command for it:

```
gpg -c <file_name>
```
It will ask you for password for that file and encrypt it.

```
gpg <file_name>.gpg
```
It will ask for your password for that file and decrypt it.

---

### Post by oldmankit on 2011-01-17
> **XeonBloomfield said:**
> Are you doing only files backup or partition snap shot?

You can use other compression format than RAR. 
RAR protection is nothing for password breaking software now...

You can compress it to file or files and use that command for it:

```
gpg -c <file_name>
```It will ask you for password for that file and encrypt it.

```
gpg <file_name>.gpg
```It will ask for your password for that file and decrypt it.

Just the files.  Thanks for the tip.

I guess the best thing is going to be create tar files from folders, encrypt using gpg, and then burn the encrypted files to DVD.

Should I be careful about a maximum size for the tar files?  I am thinking of read errors from the DVD making a whole tar archive unusable.  How about 500MB as a maximum size, making about 10 tar files per DVD?  I could periodically check the DVDs for read errors.  Is there an easy way to do that?

---

### Post by aeiah on 2011-01-17
id use truecrypt. the advantage over gpg is that it's pretty trivial to decrypt on a windows system as well as linux, should you have to access something on a random computer. its strong and secure too, of course.

---

### Post by Rhubarb on 2011-01-17
If you're worried about scratches / corrupt DVDs for your backups, I recommend you give **dvdisaster** a shot from the ubuntu repos.

> dvdisaster provides a margin of safety against data loss on CD and DVD media caused by scratches or aging media. It creates error correction data which is used to recover unreadable sectors if the disc becomes damaged at a later time.

- This should work quite well for big tarred up (and encrypted) files.

---

### Post by coffeecat on 2011-01-17
> **aeiah said:**
> id use truecrypt. the advantage over gpg is that it's pretty trivial to decrypt on a windows system as well as linux,

Are you saying that gpg is trivial to decrypt? I'm intrigued. Do you have any references to support that?

---

### Post by XeonBloomfield on 2011-01-17
Using "gpg" command is really simple way and it's not an easy encryption.

You can use ZIP, RAR or something what you want. After creating archives use "gpg" command as I wrote.

It's everything what you need to do.

---

### Post by oldmankit on 2011-01-18
I have plenty of information here to work with, thank you very much to all.  I will probably try using tar, truecrypt and dvddisaster.

> **coffeecat said:**
> Are you saying that gpg is trivial to decrypt? I'm intrigued. Do you have any references to support that?

I think the poster meant that truecrypt has multiplatform support and that gpg doesn't. I don't the s/she was commenting on the security of the encryption methods.

---

### Post by coffeecat on 2011-01-18
> **oldmankit said:**
> I think the poster meant that truecrypt has multiplatform support and that gpg doesn't. I don't the s/she was commenting on the security of the encryption methods.

Thanks. I see that now. I misread the post to mean that gpg was trivially easy to decrypt in Windows. :) Which would have been a surprise. :-s

---

