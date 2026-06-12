---
title: "GNU g++ compiler options"
date: 2012-08-30
forum: General Help
---

### Post by newport_j on 2012-08-30
For the GNU g++ compiler what do the following options mean?
 
DSSE_SUPPORT
DDTECT_FALSE_SHARING
DX86_32BIT
march=core2
msse3
 
I know that some of these are on the internet, but not all. I have googled many of them an came up with nothing or a definition in another language besides English.
 
If there is a website that tells what these are that would be fine. 
 
I just got hit or miss or partial answers when I googled them.
 
Any help appreciated. Thanks in advance.
 
Newort_j

---

### Post by Pand5461 on 2012-08-30
Flags starting with -D tell preprocessor to Define a macro. -DSSE_SUPPORT means that SSE_SUPPORT will be defined. It is usually used for conditional compilation, e.g.
```
#ifdef SSE_SUPPORT
<some code>
#endif

```
will actually be translated into machine codes only if there is a macro named SSE_SUPPORT.

Flags starting with -m are machine-specific flags.

And actually, all this info can be found via
```
man g++
```

---

