---
title: "Bash &quot;set&quot; oddity: a full script from ImageMagick"
date: 2009-10-30
forum: General Help
---

### Post by brycenesbitt on 2009-10-30
If I type the bash builtin command "set", I expect to get a list of all the environment variables known to bash.  I get this, but also a 4000 line ImageMagic script.  Anyone else see this?

```

$ set
BASH=/bin/bash
BASH_ARGC=()
 ...
XDG_SESSION_COOKIE=a6fd5512e7f19c3ab95e2a6b487f94b5-1256748309.3168-540610352
_=
bash205='3.2.39(1)-release'
bash205b='3.2.39(1)-release'
bash3='3.2.39(1)-release'
_ImageMagick () 
{ 
...
quote_readline () 
{ 
    local t="${1//\\/\\\\}";
    echo \'${t//\'/\'\\\'\'}\'
}
set_prefix () 
{ 
    [ -z ${prefix:-} ] || prefix=${cur%/*}/;
    [ -r ${prefix:-}CVS/Entries ] || prefix=""
}

$ echo $bash3
3.2.39(1)-release

```

---

### Post by mbeach on 2009-10-30
odd. Yes, I do get it as well.

2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux

Version: ImageMagick 6.4.5 2009-06-04 Q16 OpenMP [http://www.imagemagick.org](http://www.imagemagick.org)
Copyright: Copyright (C) 1999-2008 ImageMagick Studio LLC

Ubuntu 9.04

---

### Post by lavinog on 2009-10-30
it's normal

---

### Post by diesch on 2009-10-30
*set* lists not only shell variables but also shell functions. Use *env* if you want only variables.

---

### Post by brycenesbitt on 2009-10-30
Ok, if it is normal, how do I list and unset "shell functions"?

The "env" command is not document as a bash built-in, AFIK.

---

### Post by lavinog on 2009-10-30
maybe a script could be used.
Why do you want to unset them?

---

### Post by diesch on 2009-10-30
> **brycenesbitt said:**
> Ok, if it is normal, how do I list and unset "shell functions"?

Why do you want to do that?

> **brycenesbitt said:**
> 
The "env" command is not document as a bash built-in, AFIK.

Yes it's a separate program. As it is required by the POSIX standard you can be pretty sure it's everywhere installed where you have a Bash (and at a lot of places where you don't have a Bash, too)

---

