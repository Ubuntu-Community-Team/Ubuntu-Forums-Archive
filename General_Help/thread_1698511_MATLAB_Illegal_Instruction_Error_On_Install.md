---
title: "MATLAB Illegal Instruction Error On Install"
date: 2011-03-02
forum: General Help
---

### Post by LASTGUY2GETPS2 on 2011-03-02
I'm trying to install MATLAB 2010A on a computer which does not have a SSE2 enabled processor (which MATLAB lists as a requirement). I was told that in order to do this, I have to change a line in the install script to:

```
#expr "`cat /proc/cpuinfo`" : '.* sse2 .*$'
echo 1
```

When I run the install script I get the following error:

```
 An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        Illegal instruction

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t
```

When I run the install script with * -t, I get far enough to enter my serial and add my license.dat file but when I go to start the installation I get:

```
Begin Installation ? ([y]/n)  y
Illegal instruction
```

Helps?

I guess what I am trying to do is found [here]("http://forums.freebsd.org/showthread.php?t=10076").
I am following the install guide from [here]("https://help.ubuntu.com/community/MATLAB").

---

### Post by LASTGUY2GETPS2 on 2011-03-02
bump?

---

### Post by LASTGUY2GETPS2 on 2011-03-03
Morning bump.

---

### Post by LASTGUY2GETPS2 on 2011-03-04
Ttt

---

### Post by LASTGUY2GETPS2 on 2011-03-06
Anyone?? :cry::cry::cry:

---

### Post by LASTGUY2GETPS2 on 2011-03-22
^^^

---

