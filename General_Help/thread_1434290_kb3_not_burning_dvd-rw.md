---
title: "kb3 not burning dvd-rw"
date: 2010-03-20
forum: General Help
---

### Post by cd-r80 on 2010-03-20
k3b cannot burn dvd-rw. It says bad fs super block etc...?


[ 2512.683309] UDF-fs: No VRS found
[ 2512.683320] UDF-fs: No partition found (1)
[ 2512.765326] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2512.817322] ISO 9660 Extensions: RRIP_1991A
[ 3493.613625] UDF-fs: No anchor found
[ 3493.613635] UDF-fs: No partition found (1)
[ 3497.679954] ISOFS: Unable to identify CD-ROM format.

---

### Post by sahabcse on 2010-03-20
is it k3b or kb3....

i think error in media

try to use nero linux or brasero

---

### Post by cd-r80 on 2010-03-20
I already tested the drive & disk on Vista. No media errors.

---

### Post by srs5694 on 2010-03-20
Are you trying to burn an image file that you obtained elsewhere, or create a completely fresh DVD from files on your system? If the latter, then something is seriously messed up with your DVD-creation chain, but I can't tell what -- either the creation of the filesystem is bad or the identification of the created filesystem is bad. (Under Linux, the filesystem is created and then burned to disc.)

If you're trying to burn an image that you obtained from somewhere else, then what is it? If it's supposed to be something fairly normal, then the Linux tools *should* be able to identify them, but it's conceivable that it's just weird enough that they can't, but that it would still work OK. If it's something unusual, it could be that it's fine, too. If you want to try burning it to disc despite the warnings, you can use the command line:

```

growisofs -Z /dev/dvd=foo.iso

```

You may need to adjust the device filename (/dev/dvd) and the image filename (foo.iso) to suit your system and file.

---

### Post by cd-r80 on 2010-03-21
I was only burning data DVD-RW when problems started. Erased On Vista & burned Ubuntu.iso only for testing. Cannot read the disc when in Linux. k3b does not recognise disc. Cannot erase disc on linux. I tested one Disk more now (DVD-RW). K3b does not erase it correctly.Then it cannot mount it again. A month ago I erased it with k3b & burned it ok. ( same machine).

I have to reinstall Xubuntu I think. After trying compiz.the machine has freezed many times and I was forced to use magic keys.

---

