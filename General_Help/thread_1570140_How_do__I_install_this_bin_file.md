---
title: "How do  I install this bin file?"
date: 2010-09-07
forum: General Help
---

### Post by saskatchewan on 2010-09-07
Hi

I downloaded this from Adobe and I can't figure out how to install it?


AdbeRdr9.2.3.4-1_i486linux_enu.bin


I tried chmod from the terminal but no luck

---

### Post by RJ12 on 2010-09-07
first try this
./AdbeRdr9.2.3.4-1_i486linux_enu.bin

if that doesn't work try

sh AdbeRdr9.2.3.4-1_i486linux_enu.bin

---

### Post by saskatchewan on 2010-09-07
This is what it gave me


shawn@shawn-laptop:~/Desktop$ ./AdbeRdr9.2.3.4-1_i486linux_enu.bin
bash: ./AdbeRdr9.2.3.4-1_i486linux_enu.bin: Permission denied
shawn@shawn-laptop:~/Desktop$ sh AdbeRdr9.2.3.4-1_i486linux_enu.bin
AdbeRdr9.2.3.4-1_i486linux_enu.bin: 1: Syntax error: "(" unexpected
shawn@shawn-laptop:~/Desktop$ ./AdbeRdr9.2.3.4-1_i486linux_enu.bin
bash: ./AdbeRdr9.2.3.4-1_i486linux_enu.bin: Permission denied

---

### Post by howefield on 2010-09-07
Prefix the command with sudo ie,

```
sudo ./AdbeRdr9.2.3.4-1_i486linux_enu.bin
```

```
sudo sh AdbeRdr9.2.3.4-1_i486linux_enu.bin
```

---

### Post by RJ12 on 2010-09-07
How could I forget the sudo!?!? LOL! I am so sorry!

---

### Post by saskatchewan on 2010-09-07
even with sudo I still get this


shawn@shawn-laptop:~/Desktop$ sudo sh AdbeRdr9.2.3.4-1_i486linux_enu.bin
AdbeRdr9.2.3.4-1_i486linux_enu.bin: 1: Syntax error: "(" unexpected
shawn@shawn-laptop:~/Desktop$ ^C
shawn@shawn-laptop:~/Desktop$

---

### Post by howefield on 2010-09-08
> **saskatchewan said:**
> even with sudo I still get this


shawn@shawn-laptop:~/Desktop$ sudo sh AdbeRdr9.2.3.4-1_i486linux_enu.bin
AdbeRdr9.2.3.4-1_i486linux_enu.bin: 1: Syntax error: "(" unexpected
shawn@shawn-laptop:~/Desktop$ ^C
shawn@shawn-laptop:~/Desktop$

Is this Adobe Reader that you are installing, any reason why you don't get it from the repository ? (the package is acroread)

What you are installing appears to be an older version, not current. There is also a .deb package on the Adobe site which is likely to install easier than the .bin package.

---

### Post by saskatchewan on 2010-09-08
I tried searching for acroread in the repositories but no luck.  I found a listing for acoread fonts but, when I tried to install them, it said that I need acoread and that it was not available.

Very strange.

---

### Post by inameiname on 2010-09-08
Here is what comes up when doing this:

$ sudo apt-cache policy acroread
acroread:
  Installed: (none)
  Candidate: 9.3.3-1lucid1
  Version table:
     9.3.3-1lucid1 0
        500 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages
        500 [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Packages


Seems as though it's it there, so long as you have that repo added as above.

---

### Post by howefield on 2010-09-08
I think you may need to enable the Partner repository to get it.

System  >Administration > Software Sources > Other Software tab > Partner

and reload your sources, you'll find it then.

---

### Post by saskatchewan on 2010-09-08
I got it installed.

Thanks!!

---

