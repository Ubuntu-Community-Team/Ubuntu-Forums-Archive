---
title: "make -j, two targets: compiles files twice??"
date: 2010-06-09
forum: General Help
---

### Post by jonas_t on 2010-06-09
hey,

i have a "general" problem with parallel make builds. if i use make -j to trigger parallel builds in conjunction with to targets, say

make -j foo bar

while foo and bar share dependencies (e.g., foo and bar depend on target foobar), then make compiles the files of foobar twice, often resulting in corrupted output...

has anyone else experienced this problem yet and/or knows how to fix it? i don't think that this issue is related to incorrect/incompletely given dependencies in the makefile, is it??

thanks in advance,
jonas

---

