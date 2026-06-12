---
title: "RAR password remover"
date: 2009-12-27
forum: General Help
---

### Post by Leppie on 2009-12-27
Anybody knows a good tool to crack/remove archive passwords?

Thanks

---

### Post by howefield on 2009-12-27
rarcrack

But the success rate seems to be variable, and it might take some time to process.

---

### Post by Leppie on 2009-12-27
i downloaded the package, but compiling produced warnings:
> $ make
gcc -pthread rarcrack.c `xml2-config --libs --cflags` -O2 -o rarcrack
rarcrack.c: In function &#8216;crack_thread&#8217;:
rarcrack.c:206: warning: comparison between pointer and integer
rarcrack.c:205: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
rarcrack.c: In function &#8216;init&#8217;:
rarcrack.c:283: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 3 has type &#8216;char (*)[300]&#8217;
rarcrack.c:317: warning: ignoring return value of &#8216;fscanf&#8217;, declared with attribute warn_unused_result


---

