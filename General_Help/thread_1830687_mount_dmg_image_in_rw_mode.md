---
title: "mount dmg image in rw mode"
date: 2011-08-22
forum: General Help
---

### Post by berto1234 on 2011-08-22
Hy everyone,
I've a problem from a lot of time which i cannot resolve, so I'm calling your help

Usually I connect to my ubuntu pc with my mac and I write files into a dmg shared image

Now I'd mount the same dmg file from ubuntu and add files in the image, but I can't mount it in read/write mode

can someone help me? I tried with this command:

sudo mount -t hfsplus -o loop,umask=0 '/media/dati3/prova.dmg' /media/dmg

or adding the -rw option but the system mounts the dmg image just in read only mode.

I tried with a journaled dmg file system and with a not-journaled dmg image

thanks to all you
Alberto

---

