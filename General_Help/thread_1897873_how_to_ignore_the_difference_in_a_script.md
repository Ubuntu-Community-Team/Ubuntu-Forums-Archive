---
title: "how to ignore the difference in a script ?"
date: 2011-12-20
forum: General Help
---

### Post by mimihu88 on 2011-12-20
in a directory there are both *.vob and *.VOB files

```
for i in *.vob
  do 
   xxxxx;
  done
```

How to do in the part "*.vob" so that the script will deal with both .vob and .VOB files?

Thanks.

---

### Post by SlugSlug on 2011-12-20
> **mimihu88 said:**
> in a directory there are both *.vob and *.VOB files

```
for i in *.vob
  do 
   xxxxx;
  done
```How to do in the part "*.vob" so that the script will deal with both .vob and .VOB files?

Thanks.


maybe

for i in `find . -iname *.vob --maxdepth 1`

do...

---

### Post by mimihu88 on 2011-12-20
```
for i in `find . -iname *.vob --maxdepth 1`

```

thanks but not working:
error```
find: unknown predicate `--maxdepth'
```

---

### Post by Lars Noodén on 2011-12-20
There's a typo. The double dash should be a single dash:

```

for i in `find . -iname *.vob -maxdepth 1`

```

---

### Post by mimihu88 on 2011-12-20
> **Lars Noodén said:**
> There's a typo. The double dash should be a single dash:

```

for i in `find . -iname *.vob -maxdepth 1`

```

still not ok

```
find: warning: you have specified the -maxdepth option after a non-option argument -iname, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.
```

---

### Post by SlugSlug on 2011-12-20
> **mimihu88 said:**
> still not ok

```
find: warning: you have specified the -maxdepth option after a non-option argument -iname, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.
```


3rd time lucky?

for i in `find . -iname  -maxdepth 1 *.vob `

---

### Post by nothingspecial on 2011-12-20
Use brace expansion, calling find is totally unnecessary


```
$ls
10.vob  1.vob  2.vob  3.vob  4.vob  5.vob  6.vob  7.vob  8.vob  9.vob
10.VOB  1.VOB  2.VOB  3.VOB  4.VOB  5.VOB  6.VOB  7.VOB  8.VOB  9.VOB
```
```
$ for i in ***.{vob,VOB}**; do cp "$i" "$i"_bak; done
```
```
$ ls
10.vob      1.vob_bak  3.vob      4.vob_bak  6.vob      7.vob_bak  9.vob
10.VOB      1.VOB_bak  3.VOB      4.VOB_bak  6.VOB      7.VOB_bak  9.VOB
10.vob_bak  2.vob      3.vob_bak  5.vob      6.vob_bak  8.vob      9.vob_bak
10.VOB_bak  2.VOB      3.VOB_bak  5.VOB      6.VOB_bak  8.VOB      9.VOB_bak
1.vob       2.vob_bak  4.vob      5.vob_bak  7.vob      8.vob_bak
1.VOB       2.VOB_bak  4.VOB      5.VOB_bak  7.VOB      8.VOB_bak
```

---

### Post by mimihu88 on 2011-12-20
> **SlugSlug said:**
> 3rd time lucky?

for i in `find . -iname  -maxdepth 1 *.vob `
not working :(
warning:
> find: paths must precede expression: 1
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]

---

### Post by nothingspecial on 2011-12-20
Why do you want to find the files?

You already know where they are.

---

### Post by mimihu88 on 2011-12-20
> **nothingspecial said:**
> Use brace expansion, calling find is totally unnecessary


```
$ls
10.vob  1.vob  2.vob  3.vob  4.vob  5.vob  6.vob  7.vob  8.vob  9.vob
10.VOB  1.VOB  2.VOB  3.VOB  4.VOB  5.VOB  6.VOB  7.VOB  8.VOB  9.VOB
```
```
$ for i in ***.{vob,VOB}**; do cp "$i" "$i"_bak; done
```
```
$ ls
10.vob      1.vob_bak  3.vob      4.vob_bak  6.vob      7.vob_bak  9.vob
10.VOB      1.VOB_bak  3.VOB      4.VOB_bak  6.VOB      7.VOB_bak  9.VOB
10.vob_bak  2.vob      3.vob_bak  5.vob      6.vob_bak  8.vob      9.vob_bak
10.VOB_bak  2.VOB      3.VOB_bak  5.VOB      6.VOB_bak  8.VOB      9.VOB_bak
1.vob       2.vob_bak  4.vob      5.vob_bak  7.vob      8.vob_bak
1.VOB       2.VOB_bak  4.VOB      5.VOB_bak  7.VOB      8.VOB_bak
```
I will chose to rename all to be .vob or VOB if it's so complicated 
if files more than 10?
I'm sure we can find a better solution:D

---

### Post by nothingspecial on 2011-12-20
It's not complicated. That was an example

```
for i in *.{vob,VOB}
  do 
   xxxxx;
  done
```

That's all you need to do. Like I said, you don't need to find files if you know where they are.

---

### Post by MartijnNL on 2011-12-20
Like nothingspecial says, there's no need to use find. But to just to clear the 'find' issue:

> **SlugSlug said:**
> 3rd time lucky?

for i in `find . -iname  -maxdepth 1 *.vob `


It would be:

```
find . -maxdepth 1 -iname *.vob
```

---

### Post by mimihu88 on 2011-12-20
I've tried before
```
for i in *.{vob,VOB}
```
The script will only deal with .VOB files but not .vob file
also
```
for i in *.${vob,VOB}
```
not working at all
-----------------------------------------------------------------
```
find . -maxdepth 1 -iname *.vob
```

error:
> MEncoder SVN-r31042-Ubuntu-RVM (C) 2000-2010 MPlayer Team
success: format: 0  data: 0x0 - 0x0
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

---

### Post by MartijnNL on 2011-12-20
Can you explain why you get an mplayer error? What is your script doing?

And note that I only posted the find part of the line. The full line should be:

```
for i in `find . -maxdepth 1 -iname *.vob`
```

---

### Post by mimihu88 on 2011-12-20
> **MartijnNL said:**
> Can you explain why you get an mplayer error? What is your script doing?

And note that I only posted the find part of the line. The full line should be:

```
for i in `find . -maxdepth 1 -iname *.vob`
```

```
#!/bin/bash
for i in *.vob
 do
   mencoder -endpos 10 -oac faac -vf crop=336:144:8:50,scale=-10:-1,harddup -ovc x264 -x264encopts threads=auto $i -o ${i/VOB/avi};
 done
```

---

### Post by MartijnNL on 2011-12-21
I don't know why mencoder gives an error. I thinks this is an independent issue from your original question. I don't really have experience with mencoder so can't help you with that.

---

### Post by nothingspecial on 2011-12-21
> **mimihu88 said:**
> I've tried before
```
for i in *.{vob,VOB}
```
The script will only deal with .VOB files but not .vob file
also


That is because you are only outputting the VOB files at the end of the script. (see the bits in read at the end of the script)

```
#!/bin/bash
for i in *.vob
 do
   mencoder -endpos 10 -oac faac -vf crop=336:144:8:50,scale=-10:-1,harddup -ovc x264 -x264encopts threads=auto $i -o [COLOR="Red"]${i/VOB/avi}[/COLOR];
 done
```

You need to use parameter expansion for any/both extensions that your variable contains.

```
#!/bin/bash
for i in *.vob
 do
   mencoder -endpos 10 -oac faac -vf crop=336:144:8:50,scale=-10:-1,harddup -ovc x264 -x264encopts threads=auto [COLOR="Red"]"$i"[/COLOR] -o [COLOR="Red"]"${i//.*/.avi}"[/COLOR];
 done
```

Also, always quote your variables.

---

### Post by mimihu88 on 2011-12-22
> **nothingspecial said:**
> That is because you are only outputting the VOB files at the end of the script. (see the bits in read at the end of the script)

```
#!/bin/bash
for i in *.vob
 do
   mencoder -endpos 10 -oac faac -vf crop=336:144:8:50,scale=-10:-1,harddup -ovc x264 -x264encopts threads=auto $i -o [COLOR="Red"]${i/VOB/avi}[/COLOR];
 done
```

You need to use parameter expansion for any/both extensions that your variable contains.

```
#!/bin/bash
for i in *.vob
 do
   mencoder -endpos 10 -oac faac -vf crop=336:144:8:50,scale=-10:-1,harddup -ovc x264 -x264encopts threads=auto [COLOR="Red"]"$i"[/COLOR] -o [COLOR="Red"]"${i//.*/.avi}"[/COLOR];
 done
```

Also, always quote your variables.

it makes no difference,the script will only deal with .VOB file
```
#!/bin/bash

for i in *.{vob,VOB}
 do
   mencoder -endpos 10 -oac faac -vf crop=336:144:8:50,scale=-10:-1,harddup -ovc x264 -x264encopts threads=auto "$i" -o "${i//.*/.avi}";
 done

```

---

