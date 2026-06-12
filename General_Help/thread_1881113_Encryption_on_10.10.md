---
title: "Encryption on 10.10"
date: 2011-11-14
forum: General Help
---

### Post by hinsonfan on 2011-11-14
Hi everyone, for a little background, I'm on a laptop (Inspiron 6000) using Ubuntu 10.10. About a year ago, my hard drive crashed and I didn't have a Windows boot disk so a friend put Ubuntu on it. It is not partitioned, the entire drive is Ubuntu. For all intents and purposes, I'm a total Linux newb, and I only use the computer for web surfing and editing documents. Overall, I'm very happy with it.

I want to secure the contents of my hard drive and have heard that encryption is the way to go. I've searched this forum, Wikipedia, and done Google searches and now my head is spinning with info so I'd appreciate some clarity. Please forgive my numerous questions. :redface:


My first question is what's the difference between encrypting a file/drive and the password required to log onto the computer?


I know there are some Linux-based encryption softwares, are they as secure as Truecrypt?

What does "mount" mean?

I want to protect as much of the drive as I can, which file would I select to encrypt? Would it be the home file? I know I can't encrypt the boot file.

Thanks.

---

### Post by Mark Phelps on 2011-11-15
Just so you know ... I'm not a fan of encryption.  It only keeps out the most inexperienced, and once someone gets physical access to your laptop, it's a waste of time.  Plus, we get lots of posts from folks who forgot their password or passphrase and ask how to find it -- which, of course, you can't.

But as to the difference you asked ... the login password only prevents someone from logging into the PC.  If they have a bootable CD or USB stick, and can get physical access to the laptop, they can boot using that and bypass any password you entered.  Also, there are tricks that can be used with Linux booting to bypass the password as well ... but I'm not going to describe them.

Encrypting a file or a drive will prevent access to that data without knowing a password or passphrase.  Even if someone copies off the file or drive, without the access keys, they can't EASILY get to the data.  But ... with the right hardware decription tools, they will be able to crack the key in a few hours or days.

I've used several laptops that came with whole-drive encryption, and it was a lot of trouble.  The encryption passphrase was synchronized with the OS login password -- but it would get out of synch and would take HOURS to fix.

---

### Post by ballantony on 2011-11-15
> **hinsonfan said:**
> 
 
What does "mount" mean?
 
Thanks.
 
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by mastablasta on 2011-11-15
> **Mark Phelps said:**
>  
Encrypting a file or a drive will prevent access to that data without knowing a password or passphrase. Even if someone copies off the file or drive, without the access keys, they can't EASILY get to the data. But ... with the right hardware decription tools, they will be able to crack the key in a few hours or days.

 
 
well if only they knew that...([http://en.wikipedia.org/wiki/TrueCrypt](http://en.wikipedia.org/wiki/TrueCrypt)):
 
>  
Operation Satyagraha
In July 2008, several TrueCrypt-secured hard drives were seized from a Brazilian banker [Daniel Dantas]("http://en.wikipedia.org/wiki/Daniel_Dantas"), who was suspected of financial crimes. The Brazilian National Institute of Criminology (INC) tried unsuccessfully for five months to obtain access to TrueCrypt-protected disks owned by the banker, after which they enlisted the help of the [FBI]("http://en.wikipedia.org/wiki/FBI"). The FBI used [dictionary attacks]("http://en.wikipedia.org/wiki/Dictionary_attack") against Dantas' disks for over 12 months, but were still unable to decrypt them.[[SIZE=2][35][/SIZE]]("http://en.wikipedia.org/wiki/TrueCrypt#cite_note-Dantas-34")

 
Since it is so easy to decrypt the data for you, perhaps you could offer FBI your services :-)
 
actually if you use some high bit key and difficult to crack passoword it is not as easy to crack the disk. you can see the vulnerabilities of Truecrpt in same article but to exploit them it requires such special conditions that are kind of hard to obtain.
 
the biggest problem in encrypting is really that if you forget the passowrd of if there is any small corruption you will not be able to access any of your files. encryption scramble all files and you need the key to unlock it. without it even FBI seems to have problems cracking it.

---

### Post by hinsonfan on 2011-11-15
Thanks for the replies. What's the difference between a key and a password?

---

### Post by Mark Phelps on 2011-11-15
> **mastablasta said:**
> ... but to exploit them it requires such special conditions that are kind of hard to obtain.

Agreed ... "hard" to obtain ... but not impossible.

What you said is what I meant when I said the "right ... tools".

Folks just need to know that encryption is not an absolute guarantee of protection.

---

### Post by mastablasta on 2011-11-16
> **hinsonfan said:**
> Thanks for the replies. What's the difference between a key and a password?
 
 
 
key is used to lock and unlock encrypted files while password allows you to use the key.
 
here is an e-book for encryption programme GPG4win that explains all this in the firts part (for novices):[http://wald.intevation.org/frs/download.php/775/gpg4win-compendium-en-3.0.0-beta1.pdf](http://wald.intevation.org/frs/download.php/775/gpg4win-compendium-en-3.0.0-beta1.pdf)
 
it's a really nice explaination of how encryption works with some funny/memorable pictures.

---

### Post by t0p on 2011-11-16
If someone had physical access to your computer (eg someone stole your laptop) he could remove the hard drive, put it in another computer, and all your data would be there, ripe for the picking.

When you install Ubuntu, you will be given the option to encrypt the disk.  This encryption means that the putative thief will install your hard drive into his computer, boot it up, and be utterly unable to read the data.

@Mark Phelps: Of course it is possible to crack encryption.  But it is very very very difficult to crack decent encryption.  The only vulnerability in Truecrypt that I can recall was a problem that *sometimes* an attacker could detect the presence of an encrypted volume on a drive - nt actually *access* it.  And in the UK criminal trials have failed due to the use of the Free encryption utility gpg, which the police seem incapable of cracking.  If the NSA turned one of their supercomputers to the task, I suppose they might be able to crack it efore the heat death of the universe... but is it very likely the NSA will want to access *your* files? (You're not a major player in al-Qaeda are you?)

---

### Post by Mark Phelps on 2011-11-16
> **t0p said:**
> ... But it is very very very difficult to crack decent encryption. 

I never said it was easy ...

If someone steals a Laptop and finds the drive encrypted, they will either trash the drive, replace it with another drive, or wipe the drive and reuse it.

So, most likely, the casual laptop thief is NOT going to gain access to data on an encrypted volume.  I never said they could.

In my case, I use Lojack for Laptops with my laptop.  I'd much rather have the laptop back than a $50 hard drive.  And, I admit to using encryption myself.  I'm just realistic about it not being an absolute guarantee of data protection.

---

### Post by hinsonfan on 2011-11-22
Thanks for the replies. Truecrypt wants asks if I should format for fat32 system or ntfs. How do I find out what I have? Thought I'd ask here instead of creating a new thread.

---

### Post by DapperMe17 on 2011-11-22
You can surely use FAT in setting up your Truecrypt crypt.

Truecrypt is a very nice utility.

Since you would appear to be fairly new to ecnrypting files...could I suggest that you consider using a program called Cryptkeeper?

I think it would be much simpler for you to use, at least to start with.

Here's a nice tutorial for you......[http://www.makeuseof.com/tag/encrypt-protect-computer-files-cryptkeeper-linux/](http://www.makeuseof.com/tag/encrypt-protect-computer-files-cryptkeeper-linux/)

---

