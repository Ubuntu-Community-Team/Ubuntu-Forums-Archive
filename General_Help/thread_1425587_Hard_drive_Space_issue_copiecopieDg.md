---
title: "Hard drive Space issue? copie/copieDg"
date: 2010-03-09
forum: General Help
---

### Post by stonedparadox on 2010-03-09
okay.. 
 
so im running ubuntu remix on a 8gb Acer aspire one and iv got less then 1 gig of space left on the hard drive 

iv done all the usual go to janitor clean it up from there.. iv removed some games and unused programs iv emptied trash .. none of that really helped

i also cleared up the documents folder and so on

i then went and had a look for files that were  above 50 megs and i came across  3 files that were 1.2gig in size

messages
kern.log
sys.log .. 
those three files are taking up 3 gigs of space

i opened up messages (it took a while) and out came alot of copie and CopieDG garbage ..NONE of which i understand

this was just a bit of it 

r  8 20:33:24 demogirl06-laptop kernel: [88576.365911] recvmsg bug: copied 7C46FF88 seq 7C47052F
Mar  8 20:33:24 demogirl06-laptop kernel: [88576.365963] recvmsg bug: copied 7C46FF88 seq 7C47052F
Mar  8 20:33:24 demogirl06-laptop kernel: [88576.366014] recvmsg bug: copied 7C46FF88 seq 7C47052F
Mar  8 20:33:24 demogirl06-laptop kernel: [88576.366065] recvmsg bug: copied 7C46FF88 seq 7C47052F
Mar  8 20:33:24 demogirl06-laptop kernel: [88576.366117] recvmsg bug: copied 7C46FF88 seq 7C47052F
Mar  8 20:33:24 demogirl06-laptop kernel: [88576.366168] recg: copiedg: copieg: copieg: copieg: copieg: copiedg: copieg: copieg: copiedg: copiedg: copieg: copieg: copieg: copieg: copiedg: copieg: copieg: copieg: copieg: copiegg: copg: copiedg: copiedg: copiedg: copiedg: copg: copiedg: copig: copieg: copieg: copieg: copiedg: copieg: copieg: copieg: copieg: copieg: copieg: copied 7C4g: copieg: copiedg: copig: copiedg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copig: copieg: copieg: copieg: copieg: copiedg: copieg: copiedg: copiedg: copiedg: copiedg: copig: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copiegg: g: copieg: copieg: copieg: copieg: copiedg: copiedg: copig: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copiedg: copig: copieg: copieg: copieg: copieg: copieg: copied g: copieg: copieg: copieg: copieg: copiedg: copieg: copieg: cog: copiedg: c
Mar  8 20:33:24 demogirl06-laptop kernel: opiedg: copg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copiedg: copig: copieg: copieg: copieg: copieg: copieg: copied 7C4g: copiedg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copig: copiedg: copieg: copiedg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copiedg: copiedg: copg: copieg: copieg: copieg: copieg: copiedg: copig: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: g: copg: copiedg: copieg: copieg: copieg: copieg: copiedg: copieg: copieg: copieg: copiedg: copieg: copiedg: copiedg: copieg: copieg: copieg: copig: copied 7C46FF88 seq 7C47052F
Mar  8 20:33:24 demogirl06-laptop kernel: [88576.381545] recvmsg bug: copied 7C46FF88 seq 7C47052F
Mar  8 20:33:24 demogirl06-laptop kernel: [88576.381597] recvmsg bug: copied 7C46Fg: copiedg: copig: copieg: copieg: copieg: copieg: copieg: copiedg: copieg: copieg: copieg: copieg: copig: copieg: copieg: copieg: copiedg: copieg: copieg: copiedg: copiedg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copiedg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copiegg: copiedg: cg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copied 7Cg: copiedg: copieg: copiedg: copiedg: copig: copieg: copiedg: copiedg: copieg: copiedg: copieg: copieg: copieg: copieg: copieg: copiedg: copieg: copieg: copieg: copieg: copiedg: copieg: copieg: copiedg: copieg: copieg: copieg: copieg: copieg: copiedg: copieg: copieg: copieg: copieg: copieg: copieg: copiedg: copieg: copieg: copieg: copieg: copiedg: copiedg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copiedg: copig: copiedg: copieg
Mar  8 20:33:24 demogirl06-laptop kernel: : copieg: copieg: copieg: cog: copiedg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copieg: copig: copiedg: copieg: copieg: copiedg: copig: copieg: copied 7C46FFg: copiedg: copiedg: copig: copiedg: copieg: copiedg: copieg: copieg: copieg: copieg: copiedg: copiedg: copig: copieg: copieg: cog:g:

---

### Post by bumanie on 2010-03-09
How may kernels are listed on the grub screen? - if you have a few, you could get rid of some - they take up about 113-115mb each.
I guess you have tried > sudo apt-get autocleanYou could also try > sudo at-get autoremoveBe a bit careful with the last one, I have had it remove things I wanted, but it was easy to reinstall them again. 
If you don't need a fully fledged office suite, it might be an idea to get rid of the apps from Open Office you don't use - ie paint, presentation etc. If you only need a word processor you could get rid of open office altogether and use abi word instead, that would save space - it depends on your requirements are.

---

### Post by stonedparadox on 2010-03-09
iv tried both commands before i posted this topic and it cleaned up a bit but not much 


whether it removed stuff i/she needed i havent noticed

pardon my lack of knowledge but how would i installed multiple kernels was it through an update?

i presume what you mean when you sau how many kernels i have you mean the command 

uname -r ??

there is only 1 kernel

what would happen if i deleted those 3 files that are 1.2gb?

---

### Post by stonedparadox on 2010-03-10
anyone have any idea?

---

