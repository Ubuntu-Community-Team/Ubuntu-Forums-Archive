---
title: "slrn newsreader yEnc?"
date: 2011-09-04
forum: General Help
---

### Post by mrwall-e on 2011-09-04
Not sure if this is in the right place, but figured I'd give it a shot.

I use slrn for newsreading, and I wanted to download some binary files which were encrypted with yEnc. I used the "#" key to select the files I wanted to download, and they successfully downloaded into a file (I'm using the version from the repos, so it's past version 0.9.8 which had the problem of not downloading yEnc'ed files properly). Next, it asked me whether or not I wanted to decode the file, so I said yes. It expanded into all of the files I selected (which are documents), and they were all of type application/octet-stream, so they could not be opened. Any ideas?

Thanks for any help.

---

### Post by oldos2er on 2011-09-04
I think that once you've decoded the files, you need to open them with the program they're intended to be read with, e.g. using Evince or Okular to open *.pdf files.

---

### Post by andrew.46 on 2011-09-06
Hmmm.... I only really use text groups so I am not all that familiar with decoding binaries. The FAQs have a small section though:

[http://www.slrn.org/docs/slrn-FAQ-3.html#ss3.3](http://www.slrn.org/docs/slrn-FAQ-3.html#ss3.3)

which may or may not be useful? Interesting to see if the Ubuntu slrn package is compiled against uudeview:

```

andrew@skamandros~$ **[COLOR="Red"]slrn --version[/COLOR]**
slrn pre1.0.0-26
	* Note: This version is a developer preview.
S-Lang Library Version: 2.2.3
Compiled on: Sep  7 2011 13:21:06
Operating System: Linux

COMPILE TIME OPTIONS:
 Backends: +nntp +slrnpull +spool
 External programs / libs: -canlock -inews +ssl **[COLOR="Red"]+uudeview [/COLOR]**+iconv
 Features: +decoding +emphasized_text +end_of_thread +fake_refs +gen_msgid
    -grouplens -msgid_cache +piping +rnlock +spoilers -strict_from
 Using 64 bit integers for article numbers.

DEFAULTS:
 Default server object:     nntp
 Default posting mechanism: nntp

```

I will have to see if individual.net has some suitable groups, but I suspect they are strictly text only.....

---

