---
title: "Where is the man page of mkisofs?"
date: 2010-07-16
forum: General Help
---

### Post by asbesto on 2010-07-16
As stated above,

```


asbesto@gemini:~$ man mkisofs
No manual entry for mkisofs
See 'man 7 undocumented' for help when manual pages are not available.
asbesto@gemini:~$ 


```

Is this a bug or a misconfiguration of the new Ubuntu? 

](*,)

---

### Post by Rubi1200 on 2010-07-16
Sorry, can't answer your original question, but Googling worked for me:

[http://www.linuxmanpages.com/man8/mkisofs.8.php](http://www.linuxmanpages.com/man8/mkisofs.8.php)

See also here:

[http://manpages.ubuntu.com/manpages/lucid/man7/undocumented.7.html](http://manpages.ubuntu.com/manpages/lucid/man7/undocumented.7.html)

---

### Post by asbesto on 2010-07-16
I reply by myself, having discovered an incredible stupid thing:

```
asbesto@gemini:~$ mkisofs
genisoimage: Missing pathspec.
Usage: genisoimage [options] -o file directory ...

Use genisoimage -help
to get a list of valid options.

Report problems to debburn-devel@lists.alioth.debian.org.

```

:shock:

So, 

```

asbesto@gemini:~$ man genisoimage

GENISOIMAGE(1)                                                  
NAME
       genisoimage  -  create ISO9660/Joliet/HFS filesystem with optional Rock
       Ridge attributes

```

](*,)

This is one of the most STUPID thing I saw on a GNU/Linux system. Not mantaining the backward compatibility with the past is a very bad thing, a very stupid choice that must be avoided when possible - and here is so simple to avoid: just a link, or two word in a mkisofs man page.

[-X

I'm really astonished about the way Open source software is going in these years!

[-(

---

### Post by chrb on 2012-04-12
> **asbesto said:**
> 
This is one of the most STUPID thing I saw on a GNU/Linux system. 


There is a Launchpad bug for this : [https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/489077](https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/489077)

---

### Post by uRock on 2012-04-12
Back to sleep old thread.

---

