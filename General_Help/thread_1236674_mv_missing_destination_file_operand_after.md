---
title: "mv: missing destination file operand after"
date: 2009-08-10
forum: General Help
---

### Post by tpradeep369 on 2009-08-10
have some files like this

/home/li/dat/002_S_1018/mpr/m12/I8720/nii/rm002S1018L12.nii

/home/li/dat/002_S_1018/mpr/bsl/I40817/nii/rm002S1018L11.nii

i want to rename them according to the directory

like this
002_S_1018-bsl-I40817-rm002S1018L112.nii
002_S_1018-m12-I87204-rm002S1018L120.nii

here is the command i used
find `pwd` -name "rm*.nii" | awk -F/ '{ print "mv "$5"-"$7"-"$8"-"$10}' | sh

but it gives me this
mv: missing destination file operand after `011_S_0003-bsl-I32237-rm011S0003L09.nii'
Try `mv --help' for more information.

any fixes???

Thanks,
Pradeep

---

### Post by sanderj on 2009-08-10
> **tpradeep369 said:**
> 

find `pwd` -name "rm*.nii" | awk -F/ '{ print "mv "$5"-"$7"-"$8"-"$10}' | sh

but it gives me this
mv: missing destination file operand after `011_S_0003-bsl-I32237-rm011S0003L09.nii'
Try `mv --help' for more information.



In the mv-command, aren't you missing the destination (like the error message says)? Now it's just a "mv blabla" command. I think you should say "mv blablab ~" or somethinge like that.

---

### Post by tpradeep369 on 2009-08-10
Thank you i just figured it out

another problem 

is there any way to separate the name using two file seps 
like - and _

-F "-" and -F "_"

Thanks,
Pradeep

---

### Post by tpradeep369 on 2009-08-10
never mind 

it supports regular expressions
awk -F"_|-" '{ print $1" .....

---

