---
title: "need command"
date: 2006-03-13
forum: General Help
---

### Post by Peter Sommer-Larsen on 2006-03-13
hey ppl

I have unpacked af file, and i need to make a script to gather them all.

My problem is just, that all the file name are capital;

START.EXE
CFG.INI

... so on..

Is there a command, so I can transform them to small letters..

start.exe
cfg.ini

And one more question.. is there a "attrip" command in linux ??
or well.. ofcause there is.. but what is it called..??

thx

Peter

---

### Post by Dullin on 2006-03-13
I found a little script that will do it but it's not recursive..

```
 #!/bin/sh
 for i in *
 do
 j=`echo $i | tr '[A-Z]' '[a-z]'`
 mv $i $j
 done

```

---

