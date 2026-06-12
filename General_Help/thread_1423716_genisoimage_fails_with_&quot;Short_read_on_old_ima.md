---
title: "genisoimage fails with &quot;Short read on old image&quot;"
date: 2010-03-07
forum: General Help
---

### Post by neurophyre on 2010-03-07
Hello, I'm attempting to use 'wodim' and 'genisoimage' to write a multi session CD-RW.  No matter what I specify for filesystem parameters (straight ISO9660 with -iso-level 2, or Joliet, or Rock Ridge) when I attempt to run 'genisoimage' to generate the second image, I get a "Short read on old image" error.

Sequence of commands ('1' and '2' are the directory names of the content for the subsequent sessions):

```

genisoimage -iso-level 2 -o session1.iso 1
wodim -multi -tao -data dev=/dev/sr0 session1.iso
wodim -msinfo
genisoimage -iso-level 2 -C 0,22440 -M /dev/sr0 -o session2.iso 2

```

The 0,22440 is reported by 'wodim -msinfo'.  The second 'genisoimage' command in that sequence fails with:

```
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Short read on old image
```

The charset error appears on generating the first ISO, I don't believe it's important.  I can mount the CD after the first ISO is burned and see the files (albeit with the filenames slightly altered according to the ISO9660 restrictions).

---

### Post by neurophyre on 2010-03-07
Presented for further consideration:

```
$ isoinfo -f -debug -i session1.iso 
/DATA1_BC_YOU.BIN;1
/SHA1_KH7YAE.256;1

$ isovfy session1.iso 
Root at extent 17, 2048 bytes
[0 0]
No errors found
```

Everything looks good, so I don't think it's related to the sparse hits I'm getting on Google for the "short read on old image" error.

---

