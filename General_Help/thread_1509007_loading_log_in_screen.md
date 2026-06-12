---
title: "loading log in screen"
date: 2010-06-13
forum: General Help
---

### Post by Velencoyy on 2010-06-13
Hey guys I'm a complete noobie at Linux/Ubuntu I had Linux on my computer for about 7 months now all was going great until I tried to update my 8.04 to 8.10 everything was going good.

My computer shut off randomly when battery died now my computers log in screen won't show. Ive searched everywhere for solutions but none work for me.

The area where I put user and pass is completely black but I have mouse control its all I see a loading mouse pointer.

When ever I try to do sudo Apt get update I get things like " w: failed to fetch [http://security.Ubuntu.com/dists/jaunty-security/release.gpg](http://security.Ubuntu.com/dists/jaunty-security/release.gpg) 
There's a lot of them similar to that one failed to fetch

I've also tried to do compiz thing also I had no luck doing so anyone know how to resolve?

Sorry for any errors/misspelled words I'm currently using my android phone.

---

### Post by Velencoyy on 2010-06-14
Oh and my computer specs are;
Dell latitude c400
Intergrated Intel processer/ video card 
512mb ram 
80gb harddrive
Pentium III processer

---

### Post by Velencoyy on 2010-06-15
Tried a couple of new methods to get information onto this errors I'm having when I go to root terminal I type in startx and 

(EE)AIGLX error: dlopen of usr/lib/drive/i915_dri.so failed (/usr/lib/dri/i915_dri.so:  undefined symbol: _glapi_tls_context)

(EE) AIGLX reverting to software rendering 
Atom 4,CARD32 4, Unsigned long 4 the xkeyboard keymap compiler (xkbcomp) reports 

>error no symbols named pc105 in the include file us 
>exiting 
>Abandoning symbol file default 

Errors from xkbcomp are not fatal to the x server 

Waiting for x server to shut down freefontpathl:FPE usr/share/fonts/x11/Misc, refcount is 2, should be 1; fixing.

Root@user-desktop:/home/user#

---

### Post by Velencoyy on 2010-06-16
Bump

---

### Post by warfacegod on 2010-06-16
I suggest a fresh install of Ubuntu. Use a LiveCD to backup your files. I also suggest creating a /home partition and marking it as such during the install process.

---

