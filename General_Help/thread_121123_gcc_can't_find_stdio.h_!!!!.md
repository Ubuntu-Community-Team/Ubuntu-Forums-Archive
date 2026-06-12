---
title: "gcc can't find stdio.h ?!?!!?!"
date: 2006-01-24
forum: General Help
---

### Post by inaro on 2006-01-24
Hello,
I recently migrated to ubuntu from fedora and I have been extremely pleased with the Badger. Up until now.

Trying to compile a C program for a paper, I get this compiler error message:
```
main.c:1:19: error: stdio.h: &#916;&#949;&#957; &#965;&#960;&#940;&#961;&#967;&#949;&#953; &#964;&#941;&#964;&#959;&#953;&#959; &#945;&#961;&#967;&#949;&#943;&#959; &#942; &#954;&#945;&#964;&#940;&#955;&#959;&#947;&#959;&#962;

```
As you can imagine, my localization is greek, so the translation is more or less something like:
```
main.c:1:19: error: stdio.h: No such file or direcory

```

:confused: What the hell is this????? My compiler can't find standard C libraries?????

I found someone working a PPC had the exact same problem [http://ubuntuforums.org/archive/index.php/t-79569.html]("http://ubuntuforums.org/archive/index.php/t-79569.html")
But his solution, that is ldconfig -v does not fix mine..

Can anyone help??

---

### Post by endersshadow on 2006-01-24
Try this:

```
sudo apt-get install build-essential
```

---

### Post by nekoneko on 2007-11-04
I also had the same problem and this simple code helped:)))
Thanxx a lot.
If all the answers to my questions were found so easily by google...

---

### Post by Potatoj316 on 2008-03-10
I am expierencing the same problem, gcc cant find my header files.  I tried sudo apt-get install build-essential but it complains that there are unresolved dependencies.  

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed


how do I go about fixing this?

---

### Post by forrestcupp on 2008-03-10
try doing a 
```
sudo apt-get update
```
Then try to install it again.

---

### Post by mc4man on 2008-03-11
You may also want to ck. what version of libc6 you have. It's likely build-essential wants to install ver. 2.6.1 (of the -dev ) and you have something else like 2.7-5. If so you'll need to resolve that.

---

### Post by Potatoj316 on 2008-03-11
I ran apt-get update before I posted, I try installing the packages that it wants but says it cant install and eventually it gets to a package where it wants exactly this version but theres a newer version out so it cant get the old version and just dosen't install.

---

### Post by Potatoj316 on 2008-03-13
Ive had this problem before, I basically need to install an old version of a package.  How do I do that?

---

### Post by KaeseEs on 2008-03-13
> **Potatoj316 said:**
> Ive had this problem before, I basically need to install an old version of a package.  How do I do that?

[quote=man apt-get]
 A specific version of a package can be selected for installation by
           following the package name with an equals and the version of the
           package to select. This will cause that version to be located and
           selected for install.[/quote]

For instance,

```
sudo apt-get install libc6-dev=2.6.1-1ubuntu10
```

---

