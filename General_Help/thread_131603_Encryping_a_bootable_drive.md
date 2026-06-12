---
title: "Encryping a bootable drive"
date: 2006-02-16
forum: General Help
---

### Post by andrewsawyer on 2006-02-16
Hiya,

I hope someone can tell me whether or not this is possible.

I read an article about Vista and its new option (which may be set as default) to encrypt the hard disk that it installs to.  I have read a how-to on how to do it with Debian (Sid I think), however it involves basically downloading the system completely from the repos.

You obviously have to have /boot in a separate partition else it won't be able to unencrypt, however does anyone know of any way of doing this in Ubuntu, or any programs out there that I might be able to use?

Any info would be much appreciated.

Andy

---

### Post by dcstar on 2006-02-17
[QUOTE=andrewsawyer]Hiya,

I hope someone can tell me whether or not this is possible.

I read an article about Vista and its new option (which may be set as default) to encrypt the hard disk that it installs to.  I have read a how-to on how to do it with Debian (Sid I think), however it involves basically downloading the system completely from the repos.

You obviously have to have /boot in a separate partition else it won't be able to unencrypt, however does anyone know of any way of doing this in Ubuntu, or any programs out there that I might be able to use?

Any info would be much appreciated.

Andy[/QUOTE]
There is a full HOWTO in the "Tips" section, search for it.

---

### Post by Mustard on 2006-02-17
Aside from the HOW TO in the 'Tips' section, there is a program called 'Truecrypt'.  You could try googling for them to see what you think of it.

---

### Post by Matthai on 2006-03-25
Truecrypt is not a solution, since we are talking about encrypting root partition (/)!

The solution is cryptsetup, but it is quite complicated to install. But next debian installer will have cryptsetup for / included.

And you are right: your /boot needs to be separated. BTW: you can also install tripwire to check /boot later...

---

