---
title: "Find command doesn't work"
date: 2012-03-10
forum: General Help
---

### Post by eborigene on 2012-03-10
I used to find expressions in any type of file or almost (I mean .doc, odt, txt, pdf ...) with this command:

find . -exec grep "hello world" '{}' \; -print

Now everytime I try it in my shell it returns nothing at all.

I am missing something?

---

### Post by josephmills on 2012-03-10
> **eborigene said:**
> I used to find expressions in any type of file or almost (I mean .doc, odt, txt, pdf ...) with this command:

find . -exec grep "hello world" '{}' \; -print

Now everytime I try it in my shell it returns nothing at all.

I am missing something?
one way
```
find / -name '*.doc' 
```
tie together ? 
```
find . \( -name '*.doc' -o -name '*.txt' \)  -print
```
there is a super super super cool page on find here 
[http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

---

### Post by eborigene on 2012-03-10
```
find / -name '*.doc' 
```
tie together ? 
```
find . \( -name '*.doc' -o -name '*.txt' \)  -print
```

Thank you very much for your help, but I meant expressions within the file which, with the commands find and grep, I used to get printed on the shell.

---

### Post by llamabr on 2012-03-10
Maybe it would help if you give a non hello world example of what you expect, and what it's doing.  copy/paste the output.

---

### Post by eborigene on 2012-03-12
> **llamabr said:**
> Maybe it would help if you give a non hello world example of what you expect, and what it's doing.  copy/paste the output.


Thank you but this time it worked:



serve@serve-Aspire-4315:~/Documents/ENEIAS-2012$ find . -exec grep "primarii" '{}' \; -print
Primarii cives fogem da peste em XII 11: Pestifera tunc lues urbem invaserat; primarii cives 
No livro XIII a propósito de Génova: nterea Prosper Adurnus et Ubiectus Fliscus ad Mediolanensem defecere, plebs fame attrita clamare, populus libertatem asserere, cives primarii nunc hoc nunc illud consulere, incerta omnia esse in civitate.
./TEMPO/ruinas_ostia_commentarii.txt
primarii procinctus sunt: qui angulorum prehendendorum / operisque
suppeditent. Caetera omnis hominum manus et numerus hisce primariis
/ quid una uniuersis: quid paucioribus primariis ciuibus: quid
transuersos interia cito: quorum nexu et adminiculo primarii inter se
plus securitatis et minus suspitionis afferet quod si ab ea primarii
/142/406/ domus proprium sit / omnibus pene ac maxime primariis in
bus sub rectis uero et prope sub puluinari cellis primariis:
dem laxior primariis tectis non sufficientibus circumaddi
pulpita erant istiusmodi. Vnam ex primariis in theatro parti
<SPAN LANG="en-US">rent . Sed sunt quoque publica nonnulla: quae non nisi primariis</SPAN>
praestantissimis alia ponet locis primariis: alia etiam colloca
./ALBERTI/alberti_archimedestextdereaedificatoria24novL_2010.html
interserendos diximus. Alii uero et hi quidem primarii procinctus
nus et numerus hisce primariis prout usus postulet obtemperabunt
oribus primariis ciuibus: quid minorum multitudini conueniat.
cito: quorum nexu et adminiculo primarii inter se his iuncti deti
feret quod si ab ea primarii ciues non excluderentur illud non
domus proprium sit / omnibus pene ac maxime primariis in
bus sub rectis uero et prope sub puluinari cellis primariis:
dem laxior primariis tectis non sufficientibus circumaddi
pulpita erant istiusmodi. Vnam ex primariis in theatro parti
rent . Sed sunt quoque publica nonnulla: quæ non nisi primariis
præstantissimis alia ponet locis primariis: alia etiam colloca
serve@serve-Aspire-4315:~/Documents/ENEIAS-2012$ 

May the problem is memory resources (by the way I am using an external disk as boot drive; the internal is damaged; sometimes it causes problems due, I guess, to the instability of the USB; than I have to do chkdsk to clear blocks).

---

### Post by Vaphell on 2012-03-12
the question is: why do you need find at all? ```
grep -r 'primarii' .
``` would achieve the same result

---

### Post by eborigene on 2012-03-13
> **Vaphell said:**
> the question is: why do you need find at all? ```
grep -r 'primarii' .
``` would achieve the same result

I cann't say it does for it has been running for 10 minutes with no result, whereas 

find . -exec grep "primarii" '{}' /dev/null \; -print

has finished the job in one or two minutes.

---

### Post by matt_symes on 2012-03-13
Hi

What about using the --include switch to limit searching to specific files.

From man grep

> --include=GLOB
              Search only files whose base name matches GLOB (using wildcard matching as described under --exclude).

```
grep --include="*.{doc,txt,odt}" -r "primarii" *
```

EDIT:

You may still want to pipe errors into the bit bucket.

Kind Regards

---

### Post by Vaphell on 2012-03-13
> **eborigene said:**
> I cann't say it does for it has been running for 10 minutes with no result, whereas 

find . -exec grep "primarii" '{}' /dev/null \; -print

has finished the job in one or two minutes.

very strange, **grep -r <pattern> .** will run a recursive search for given pattern in current dir, which is pretty much exactly what your find line does.
No doubt grepping for 'while' in my home dir returns a lot of bash script lines.

---

### Post by matt_symes on 2012-03-13
Hi

> **Vaphell said:**
> very strange, **grep -r <pattern> .** will run a recursive search for given pattern in current dir, which is pretty much exactly what your find line does.
No doubt grepping for 'while' in my home dir returns a lot of bash script lines.

I assumed it was because of the time it was taking, not because it would not find the pattern, and where he might be in the filing system. That's why i suggested the include glob.

I can't see much wrong with your grep command.

Kind regards

---

### Post by Vaphell on 2012-03-13
i suspect some screwup because i don't see why it would spend 10 minutes and return absolutely nothing. Grep returns matching lines on the fly, it doesn't wait for anything so there should be something in the output. And i would assume grep doesn't add much (if any) overhead, if anything it would be the other way around with find+grep being more wasteful.
I'd expect grep being much faster as it is a tool specifically tailored for the task at hand, not a generalist like find. I roughly tested on my small dir with commands run 10x with *time* and find solution was like 100 times slower.

---

### Post by eborigene on 2012-03-15
> **matt_symes said:**
> Hi

What about using the --include switch to limit searching to specific files.

From man grep



```
grep --include="*.{doc,txt,odt}" -r "primarii" *
```

EDIT:

You may still want to pipe errors into the bit bucket.

Kind Regards


Off they go:

serve@serve-Aspire-4315:~/Documents/ENEIAS-2012$ grep --include="*.{doc,txt,odt}" -r "primarii" *
serve@serve-Aspire-4315:~/Documents/ENEIAS-2012$ 

It didn't take much time. The same in another directory (almost the same files):
serve@serve-Aspire-4315:/media/PHILIPS UFD/ENEIAS_2012$ grep --include="*.{doc,txt,odt}" -r "primarii" *
serve@serve-Aspire-4315:/media/PHILIPS UFD/ENEIAS_2012$ 

Best regards

---

### Post by Vaphell on 2012-03-15
certainly you should forget about grepping doc and odt files, they are not plain text and grep can't get to their contents (odt is zip in reality and doc is god-knows-what)

indeed including *.{abc,def} seems to fail while feeding series of --include='*.ext' works.

```
$ grep -r --include="*.{sh,py}" 'bin' .
$ grep -r --include="*.sh" --include="*.py" 'bin' .
./syntax.sh:#!/bin/bash
./abc/cr.sh:#!/bin/bash
...
```

why grep -r fails you i have no idea. btw you can add -i to make your search case insensitive.

---

### Post by matt_symes on 2012-03-15
Hi

> indeed including *.{abc,def} seems to fail while feeding series of --include='*.ext' works.

The globbing does work.

This is a contrived example but..

```
matthew@matthew-Aspire-7540:~/test$ ls
t.sh  tt.py  ttt.txt
matthew@matthew-Aspire-7540:~/test$ cat t.sh 
!#/bin/bash
echo "hello"
matthew@matthew-Aspire-7540:~/test$ cat tt.py 
# This file is empty

matthew@matthew-Aspire-7540:~/test$ cat ttt.txt 
!#/bin/bash

matthew@matthew-Aspire-7540:~/test$ grep --include="*.{sh,py,txt}" "bin" *
t.sh:!#/bin/bash
ttt.txt:!#/bin/bash
matthew@matthew-Aspire-7540:~/test$
```

Kind regards

---

### Post by Vaphell on 2012-03-15
probably you have newer grep version, on my 10.04 it doesn't do that as you can see in the output from my previous post (GNU grep 2.5.4)

---

### Post by matt_symes on 2012-03-15
Hi

```
matthew@matthew-Aspire-7540:~/test$ grep --version
grep (GNU grep) 2.10
Copyright © 2011 Free Software Foundation, Inc.
Licence GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by Mike Haertel and others, see <http://git.sv.gnu.org/cgit/grep.git/tree/AUTHORS>.
matthew@matthew-Aspire-7540:~/test$ 
```

Kind regards

---

