---
title: "Home Directory Full, Can't log in"
date: 2006-02-26
forum: General Help
---

### Post by tux-curious on 2006-02-26
As you may have gotten from the header, I allowed my home directory to get so full that I dont' have enough space left to write to my log in file.

Does anyone know any way to get past this? Or any way to delete stuff without logging in? Or any ways to recover files from this locked down disk? 

Also, I will quite possibly do this again in the future, is there any way to make some sort of buffer to prevent this?

Sorry, and thanks.:KS

---

### Post by Ramses de Norre on 2006-02-26
Can you login as root through the recovery mode? Or is the root accounts home at the same partition?

---

### Post by tux-curious on 2006-02-26
[QUOTE=Ramses de Norre]Can you login as root through the recovery mode? Or is the root accounts home at the same partition?[/QUOTE]

I dunno, I didn't even know you could log in as root with Ubuntu. 

Is there a default root passwrd? I didn't set one, I always use my normal password for all the root functions. 

JSYK, it wont' let me log in through the termanal either.

What about a live cd? Does anyone know any live Cds that could help me delete a few files off my hard disk?

-Steven

EDIT: I'm pretty sure its on the same partition but I really couldn't tell you for sure.

---

### Post by Ramses de Norre on 2006-02-26
You can choose recovery mode in grub which gives you a root shell.
But I think the live cd is better, I didn't thought of it myself yet;) 
The ubuntu live cd will probably be the best, you know ubuntu after all.
You can dowload it from [http://www.ubuntu.com/download]("http://www.ubuntu.com/download")
Then mount your file system and delete some files.

---

### Post by tux-curious on 2006-02-26
> **Ramses de Norre]You can choose recovery mode in grub which gives you a root shell.
But I think the live cd is better, I didn't thought of it myself yet said:**
> http://www.ubuntu.com/download[/URL]
Then mount your file system and delete some files.

Thanks, this is probably the nicest forum I know.

Anywhere else I probably would have been flamed off the board.

Do you, or anyone, have experiance mounting the filesystem from a live cd? I've never figured out how to do that.

EDIT: Only seven hours until I can try it out! woot!

---

### Post by Ramses de Norre on 2006-02-26
in terminal: ```
sudo mount -t ext3 /dev/hda /mnt
```
and change hda to the partition your home is on.
The partition is accesable through /mnt then.

---

### Post by dcstar on 2006-02-27
And deleting everything in the /tmp directory is a good place to start.

---

### Post by RAOF on 2006-02-27
[QUOTE=dcstar]And deleting everything in the /tmp directory is a good place to start.[/QUOTE]
If that doesn't work, clearing out your apt-cache can work wonders.  My Dapper root was full because I had 1.1GB of cached .debs ;)  sudo aptitude clean will allow you to do that.

---

### Post by Zeroangel on 2006-02-27
Yeah, also your firefox cache is stored at home/$USER/.mozilla/firefox/$FIREFOXPROFILE/Cache

---

### Post by nocturn on 2006-02-27
[QUOTE=Ramses de Norre]Can you login as root through the recovery mode? Or is the root accounts home at the same partition?[/QUOTE]

Regardless, you should be able to log in.
Most filesystems reserve some space for root, just for cases like this.

---

### Post by queenorych on 2006-02-27
Empty your trash too could help

rm -R ~/.Trash/*

---

### Post by Zeroangel on 2006-02-27
Ah, and I nearly forgot! When in the terminal, navigate to your home directory and type in the following command:```
du | sort -n
```That is basically like a big LS, but for folders, and it sorts them by size. Very useful for troubleshooting space issues.

Also, consider adding a second HD and mounting that as your /home/username directory.

---

