---
title: "How to setup Sylpheed to work with GnuPG"
date: 2012-02-13
forum: General Help
---

### Post by rick_james on 2012-02-13
Hi. I use Sylpheed Version 3.2.0beta3 (Build 1122) 
GTK+ 2.24.6 / GLib 2.30.0
Operating System: Linux 3.0.0-16-generic (i686)

I set up GnuPG with Thunderbird which was easy but I checked Sylpheed's website and it says you have to compile it to make it work:

> GnuPG: Sylpheed can encrypt and sign your messages (also decrypt and verify the signatures of the incoming messages) using GnuPG. GnuPG follows the OpenPGP standard and is compatible with PGP. To enable this feature, you need to install GnuPG and GPGME (interface library to GnuPG). Enable this option with the --enable-gpgme configure switch.

It also says:

> 2.15 Q15 How do I enable GPG support in Sylpheed?

A. When compiling Sylpheed, make sure you add --enable-gpgme in the ./configure command. When that completes successfully, there is a "privacy" section in the Common preferences.

I'm a newbie and don't understand how to do that.  Do I have to do that?
 
Is there an easy way to sign/encrypt my email in Sylpheed?

Thunderbird is okay but it is slow and bloated, but perhaps that is because I have an old computer.  That's why I run Lubuntu (LXDE).

Thanks for any help.
I greatly appreciate it.

---

### Post by Rodney9 on 2012-02-14
Claws Mail is also lightweight, maybe not as light as Sylpheed, but very close with more features including GnuPG support (with GPGME). 

[http://www.claws-mail.org/features.php?section=general](http://www.claws-mail.org/features.php?section=general)

It is certainly much lighter than Thunderbird and has some good plugins.

It is available in Synaptic, just do a search for 'claws' and you will also see the plugins.


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

