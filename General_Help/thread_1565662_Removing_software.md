---
title: "Removing software"
date: 2010-09-01
forum: General Help
---

### Post by kljuc on 2010-09-01
Hi. I am quite new to linux. I would like to install more recent version of a certain software, but before that, I have to remove the old version. This software is not obtained through repositories (well, you know, you download the package, ./configure, ./make etc.), so I'm not sure how to remove it. I would appreciate any help.

---

### Post by sikander3786 on 2010-09-01
Nearly all software come with a read me file containing the uninstall instructions.

Or alternatively cd into the source directory and type

```

sudo make uninstall

```

That should do it.

Regards.

---

### Post by 4ebees on 2010-09-01
> **kljuc said:**
> Hi. I am quite new to linux. I would like to install more recent version of a certain software, but before that, I have to remove the old version. This software is not obtained through repositories (well, you know, you download the package, ./configure, ./make etc.), so I'm not sure how to remove it. I would appreciate any help.



Install 'checkinstall'.

This will help with packages you compile.

When you get to the bit that says 'make install' you instead type:

checkinstall (as root of course :))

Then if you want to remove the package you use:

sudo dpkg -r <insert/name/of/package>

e.g.:

sudo dpkg -r motherinlaw

:)

This will then remove the package for you.

Checkinstall is one of my favourite apps.

---

### Post by sikander3786 on 2010-09-01
> **4ebees said:**
> 

sudo dpkg -r motherinlaw



Nice example :lolflag:. Me too want to try that.

---

