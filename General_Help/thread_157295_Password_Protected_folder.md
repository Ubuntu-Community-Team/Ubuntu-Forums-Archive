---
title: "Password Protected folder"
date: 2006-04-08
forum: General Help
---

### Post by truNWA on 2006-04-08
Is there any way to make a password protected folder in ubuntu?

---

### Post by nanotube on 2006-04-08
hm, well the obvious way would be to have it owned by root, and with 700 permissions - that way you would have to know the root password to read the stuff. would that suit you?

---

### Post by dermotti on 2006-04-08
Ide be interested in this too. Permissions just arent good enough sometimes. What i you want to hide the contents of the folder? It Doesnt take a genius to figure out what **nude.jpg** is :-)

---

### Post by truNWA on 2006-04-08
[QUOTE=dermotti]Ide be interested in this too. Permissions just arent good enough sometimes. What i you want to hide the contents of the folder? It Doesnt take a genius to figure out what **nude.jpg** is :-)[/QUOTE]


lol



but seriously I wanted something to use for my school laptop..... teachers will literally go though our laptop oi it is left open and on.

I would prefer a random or the user password instead of root.

---

### Post by souki on 2006-04-08
you can use an encrypted loop device
```
dd if=/dev/zero of=mycryptofs bs=1k count=5000
losetup -e AES256 /dev/loop0 mycryptofs
Password(min 20 chars):
mkfs -t ext2 /dev/loop0
mount -t ext2 /dev/loop0 /mnt/crypto
```

to stop, do
```
umount /mnt/crypto
losetup -d /dev/loop0
```

---

### Post by nanotube on 2006-04-08
[QUOTE=dermotti]Ide be interested in this too. Permissions just arent good enough sometimes. What i you want to hide the contents of the folder? It Doesnt take a genius to figure out what **nude.jpg** is :-)[/QUOTE]

if the folder's permissions are 700, and owned by root, then others cannot list the files in that folder at all. so that would serve the purpose. :) although it's true, that permissions are certainly not the best tool for the job. the solution souki has suggested seems nice.

---

### Post by nanotube on 2006-04-08
[QUOTE=truNWA]lol



but seriously I wanted something to use for my school laptop..... teachers will literally go though our laptop oi it is left open and on.

I would prefer a random or the user password instead of root.[/QUOTE]

hm, why not lock screen before you leave your laptop? and set the screensaver to lock screen after 5 min or some short time like that.

that's what i do on my laptop, and i dont even store anything "sensitive" on it. 

after all, even if you have an encrypted filesystem, once you access it and type in your password, and then forget to close it, and walk away, it's just as accessible as if it wasnt encrypted. so the solution to your problem is not fancy folder control, but being diligent about locking your screen when you walk away. setting a nice kb shortcut for "lock screen" is a big step in the right direction.

---

### Post by truNWA on 2006-04-09
i could but one of the conditions of my school letting me use ubuntu is that the have to have my account pass, so all my teachers have it.



and souki, how would i link that to a folder in the teminal?

---

### Post by nanotube on 2006-04-09
trunwa,
now, pardon my language, but, WTF kinda school is that??? ive never heard of such a thing ever. 
what you have on YOUR computer is YOUR choice, they cannot dictate that (i always thought).

and btw, if they can require you to give up your user password, can they not also require you to give up your encrypted folder password? i mean, that's just a quick "give it to me or else" away, aint it?

---

### Post by truNWA on 2006-04-09
Ummmm it's a school issued laptop; i asked to get ubuntu on there; they said yes(mainly because our principal uses Gentoo); i had to give up my passwords and stuff. but this is ment to be a temperary solution..... i would make new folders everytime they ask for a password( i know it sounds stupid but it will work)

---

### Post by Prospero2006 on 2006-04-09
Truecrypt is what I use to encrypt filesystems. 
It sounds like the perfect solution for your situation.

Pros

---

### Post by souki on 2006-04-09
[QUOTE=truNWA]and souki, how would i link that to a folder in the teminal?[/QUOTE]

I don't really understand your problem, but I can explain you how I use this:
- I have an usb key with a lot of sensible informations, like password and private keys
- all these informations are stored in one encrypted file
- I mount this file has needed (read or write) and it appears as any others folders

if you have a lot of different folders to set up (with many different passwords) this solution is not viable because you cannot have a lot of loop devices (I think it's 8 on ubuntu)

cheers

---

### Post by souki on 2006-04-09
[QUOTE=Prospero2006]Truecrypt is what I use to encrypt filesystems. 
It sounds like the perfect solution for your situation.

Pros[/QUOTE]

It sounds interesting, it is very similar to the solution I use but with a graphic interface and ease of portability between os

I've tried the breezy deb on their website but it does not work on dapper

any idea ?

---

### Post by nanotube on 2006-04-09
[QUOTE=truNWA]Ummmm it's a school issued laptop; i asked to get ubuntu on there; they said yes(mainly because our principal uses Gentoo); i had to give up my passwords and stuff. but this is ment to be a temperary solution..... i would make new folders everytime they ask for a password( i know it sounds stupid but it will work)[/QUOTE]

ah, school-issued laptop, that makes sense, then. 

well, truecrypt or whatever has been recommended may be a nice solution - but it may be even easier to just store your files on a usb key, that you keep with you at all times.

---

### Post by Randomskk on 2006-04-09
Using a USB key would be easy, also you could hide the folder.
By default, the file browsers will not show folders or files starting in . - so name your folder .stuff or whatever, password protect if you want (chmod 700 could do that nicely) and then they won't even know you have a password protected folder, so can't ask for the password.

---

### Post by Celerex on 2006-04-09
Back when USB Keys were small I had a very similar situation. I needed to have a very private directory that only I could access. So I used a combination of the above suggested techniques.

I used loopCrypto (now dm-crypt) to encrypt a directory under my home dir. The key for decrypting was stored on a USB key I carried with me. Scripts were used to attempt a mount when a USB key was inserted (and the key was found) and a script to unmount when USB keys were removed. As long as I remembered to remove the key when I got up for my computer the directory was safe.

These days your best bet would be to use a USB key. I've heard of wireless ones that as long as you're sitting there it connects. If you can find one of these it'd be perfect for your situation (as long as you can stand outside of range or turn it off when your laptop is being 'searched').

Using sudo you may be able to implement a directory permission scheme, if you gave up your passwords (including root) then this is moot. :)

---

### Post by thepocketdrummer on 2008-02-08
I'm in the same boat sort of.

Is there any way just to make the folder ask you for a password like synaptic does when it runs?

---

### Post by PeterJS on 2008-02-08
> **thepocketdrummer said:**
> I'm in the same boat sort of.

Is there any way just to make the folder ask you for a password like synaptic does when it runs?

That how the root ownership 700 permissions suggested on the first page works.

Another option is Cryptkeeper, it works pretty well, and it's nice and pointy clicky.
[http://www.getdeb.net/app/Cryptkeeper](http://www.getdeb.net/app/Cryptkeeper)

---

### Post by euler_fan on 2008-02-08
TrueCrypt 5.0 released just after 7.10 came out but there is now a nice GUI and a very nice .deb for Ubuntu on their downloads page. Best part is if you make the container small enough you can just pull it right off of the machine to a flash drive.

EF

---

### Post by bodhi.zazen on 2008-02-09
There is also gpg:

[http://www.cyberciti.biz/tips/linux-or-unix-password-protecting-files.html](http://www.cyberciti.biz/tips/linux-or-unix-password-protecting-files.html)

---

