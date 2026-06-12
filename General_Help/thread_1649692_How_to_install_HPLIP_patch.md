---
title: "How to install HPLIP patch ??"
date: 2010-12-20
forum: General Help
---

### Post by simon0404 on 2010-12-20
I have been having the issue with my printer, where it will not print using both cartridges, and just mixes the colours to try and make black....

I have found the following patch, but would like to know how to apply it???

[http://launchpadlibrarian.net/55605129/add-lidil-two-cartridge-modes.patch](http://launchpadlibrarian.net/55605129/add-lidil-two-cartridge-modes.patch)



Thanks in advance,
Simon.

---

### Post by luigi_mb on 2010-12-20
You need to get the source code of the program you want to patch. Apply the patch and recompile. See also

[CODE]
man patch
{/CODE]

/luigi

---

### Post by simon0404 on 2010-12-21
> **luigi_mb said:**
> You need to get the source code of the program you want to patch. Apply the patch and recompile. See also

[CODE]
man patch
{/CODE]

/luigi

Thanks,


I'm assuming I would need to do this in Terminal??

But what commands would I need to use please??

---

### Post by luigi_mb on 2010-12-21
Yes, you would need to open a terminal. Unpack the source file:

```

cd ~
tar xvf sourcefile.tar.gz

```

replacing "sourcefile.tar.gz" with the HLIP source package.

Then cd to the folder created by tar, and read the instructions (usually README and INSTALL). 

To apply the patch, read the instructions provided with the patch, which should tell you where put the patch code relative to the code you need to patch, so that the "patch" utility can do its job. 

```

$ patch -p1 < [file.patch]

```

(the letter following -p is an ell, not a one).

/luigi

---

### Post by simon0404 on 2010-12-22
I couldn't find any instructions for the patch, but made a guess and tried using the following;

> 
patch -p1 < hplip-3.10.9/prnt/drv/add-lidil-two-cartridge-modes.patchThe output was;

> patching file prnt/drv/hpcups.drv.in
Hunk #1 FAILED at 4778.
Hunk #2 FAILED at 4988.
Hunk #3 FAILED at 7480.
Hunk #4 FAILED at 7492.
Hunk #5 FAILED at 7891.
Hunk #6 FAILED at 7903.
Hunk #7 FAILED at 8286.
Hunk #8 FAILED at 8298.
8 out of 8 hunks FAILED -- saving rejects to file prnt/drv/hpcups.drv.in.rej
patching file prnt/drv/hpijs.drv.in
Hunk #1 FAILED at 4411.
Hunk #2 FAILED at 4879.
Hunk #3 FAILED at 5347.
3 out of 3 hunks FAILED -- saving rejects to file prnt/drv/hpijs.drv.in.rej
patching file prnt/drv/hpijs.drv.in.template
Hunk #1 FAILED at 2221.
Hunk #2 FAILED at 2403.
Hunk #3 FAILED at 2599.
3 out of 3 hunks FAILED -- saving rejects to file prnt/drv/hpijs.drv.in.template.rejI also tried changing the file permissions of that folder to read & write, with no difference....

Did I guess the wrong folder??

---

### Post by simon0404 on 2010-12-22
Following my post above, I have now resolved this....... I will post later to describe how I done it!! :popcorn:

---

### Post by simon0404 on 2010-12-22
> I extracted the hplip-3.10.9.tar.gz
I moved the "add-lidil-two-cartridge-modes.patch" to the hplip-3.10.9/prnt/drv/ directory
I made a copy of the prnt/drv/ folder, directly in the home folder
I ran the command: $                                                  patch -p1 < hplip-3.10.9/prnt/drv/add-lidil-two-cartridge-modes.patch
I then moved the  prnt/drv/ folder in the home directory, (which had now been patched), back to the hplip-3.10.9 directory, overwriting as necessary.
I ran the installer in the hplip-3.10.9 directory as normal
I can confirm that the above fixed the print issue I had been having, and I can now print with both cartridges at once.

Thanks luigi_mb for the assistance, and hopefully this post is useful to somebody else with the same problem.

---

