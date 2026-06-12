---
title: "Signing the Code of Conduct - command doesn't work"
date: 2009-10-29
forum: General Help
---

### Post by Eyore15 on 2009-10-29
I've been trying for the past couple of days to sign the code of conduct in Lanuchpad.  I managed to sort through getting a gpg key established and recognized (no mean trick for me).  I download the text file by following the link provided at Launchpad.  I verify the file is in tact by opening it in OOo.  Here's where the hiccup comes in.  

When I issue the gpg -- clearsign command [dialogue follows], I consistently get the error message that there is no such file or directory.

<<dialogue on>>

gpg --clearsign UbuntuCodeofConduct-1.0.1.txt

You need a passphrase to unlock the secret key for
user: "mark c. miller <mr.mcmiller@gmail.com>"
1024-bit DSA key, ID 20674986, created 2009-06-30

gpg: can't open `UbuntuCodeofConduct-1.0.1.txt': No such file or directory
gpg: UbuntuCodeofConduct-1.0.1.txt: clearsign failed: file open error

<<dialogue off>>

I know the file is there.  I can see it.  I can open it. I tried changing the name (don't know what good I thought it would do, but I had to try something.  Didn't make any difference.


Got any ideas?

---

### Post by Giblet5 on 2009-10-29
What is the file's mode?

```
ls -l UbuntuCode*
```

Try setting the mode to 644 ```
chmod 644 UbuntuCode*.txt
```

I wasn't asked to sign anything, but I've been a launchpad user for a long time. Things change.

---

### Post by lpeter on 2009-11-11
Same issue, tried changing the mod as per your kind suggestion:  

[INDENT] lpeter@lpeter-laptop:~$ ls -l UbuntuCodeofConduct-1.0.1.txt
ls: cannot access UbuntuCodeofConduct-1.0.1.txt: No such file or directory
lpeter@lpeter-laptop:~$ chmod 644 UbuntuCodeofConduct-1.0.1.txt
chmod: cannot access `UbuntuCodeofConduct-1.0.1.txt': No such file or directory
[/INDENT] 
I do not need to do this, I guess.  Was just trying to get on board with the system.  Much as Mr Miller, I am not sure, being a new guy.

Thanks for any suggestions.

---

### Post by scouser73 on 2009-11-11
I've just been having the same problems myself with this, I must have wasted a good two hours faffing with this.

---

### Post by lpeter on 2009-11-11
Solved.

Nevermind.  Thanks.  The answer is here:  
[INDENT][http://ubuntuforums.org/showthread.php?p=5870284](http://ubuntuforums.org/showthread.php?p=5870284)
[/INDENT]I needed to move the file to a location and then tell terminal where that location was.

---

