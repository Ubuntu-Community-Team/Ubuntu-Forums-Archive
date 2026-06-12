---
title: "vm.swappiness setting"
date: 2011-06-26
forum: General Help
---

### Post by sandman3838 on 2011-06-26
Hello

Lately I have been reading up on vm.swappiness.

What range would you recommend I look at, my system is:

 - AMD 64 X2 6000
 - 8 GB on-board memory
 - plenty of HD space

Usually I have only one or two programs open at a time....

Thanks.

---

### Post by scottiewhite on 2011-06-26
Hey, I've neber used Wubi as ive always just installed straight to a seperate HD, but as far as ive seen most people with 4+ Gb of RAM set vm.swappiness=10 so that's my recomendation. 

though i have mine as vm.swappiness=2 (no that is not a typo) running a phenom x6 with 8G of RAM and Backtrack 5 (Ubuntu 10.04 Lucid with some extra's more or less) runs Flawlessly - my $0.02 :)

---

### Post by Sylslay on 2011-06-26
My is
vm.swappiness=1


deflaut 
vm.swappiness=10

I change ysterday, 1,5gb ram on my system

vm.swappiness=0 is swap off

---

