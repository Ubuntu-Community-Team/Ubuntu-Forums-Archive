---
title: "Can't use gimp"
date: 2010-10-17
forum: General Help
---

### Post by Xupz on 2010-10-17
Hello,

When I try to open GIMP, either it does not open at all, or it stops after a few minutes' use. It's driving me mad.

Here is what I got the last time it “crashed”, but I have no idea whether it's always the same error occurring.
> ***MEMORY-ERROR***: gimp[3092]: GSlice: assertion failed: sinfo->n_allocated > 0
gimp: terminated: Abandon

(script-fu:3095): LibGimpBase-WARNING **: script-fu: wire_read(): errorActually there are also a few errors reported when I successfully launch GIMP:
> gimp: wire_read(): error
louise@Banquise:~$ gimp
/usr/local/lib/gimp/2.0/plug-ins/helpbrowser: error while loading shared libraries: libgtkhtml-2.so.0: cannot open shared object file: No such file or directory

(gimp:3092): LibGimpBase-WARNING **: gimp: wire_read(): error
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:3092): LibGimpBase-WARNING **: gimp: wire_read(): errorI don't know if they are relevant.

I once tried to uninstall it and re-download it, to no avail.
 

Please, if someone can help me... I need a software akin to photoshop for an assignment and this will be very troublesome if I can't use GIMP at all.

PS: I'm on Ubuntu Lucid and trying to open GIMP 2.6.11 (I think)

---

### Post by Xupz on 2010-10-17
Ah! I've finally found out what the source of the problem was, thanks to someone else. I had first installed GIMPshop and THAT was the nasty software tampering with GIMP. I uninstalled the former, and the latter works perfectly now :)

Sorry for useless thread ~

---

