---
title: "OT: Is VMWare faster than the real deal???"
date: 2006-04-11
forum: General Help
---

### Post by yamagami on 2006-04-11
Hi all, 

I've noticed something very strange recently: I'm running win 2000 on a vmware player and it seems to work extremly fast. even boots up faster than the real OS used to. 
Also at work my boss is running win xp on a vmware workstation on his laptop (not a fast one but with 1.5Gb of ram), with apache and a java app server running (jrun4) and it seems that serving up the application off his vmware instance is actually *faster and more responsive* then if he used his actual OS to do it... Is that possible or just an 'optical illusion'?

Could running an OS in vmware be actually faster than running it normaly?

Harel
:o

---

### Post by Al3xanR0 on 2006-04-11
[QUOTE=yamagami]Hi all, 

I've noticed something very strange recently: I'm running win 2000 on a vmware player and it seems to work extremly fast. even boots up faster than the real OS used to. 
Also at work my boss is running win xp on a vmware workstation on his laptop (not a fast one but with 1.5Gb of ram), with apache and a java app server running (jrun4) and it seems that serving up the application off his vmware instance is actually *faster and more responsive* then if he used his actual OS to do it... Is that possible or just an 'optical illusion'?

Could running an OS in vmware be actually faster than running it normaly?

Harel
:o[/QUOTE]

It may be that the hardware that VMware is emulating may very well be faster than that which you have/had w2k installed on originally

---

### Post by yamagami on 2006-04-11
This just adds to the magic that is Vmware...

---

### Post by az on 2006-04-11
Anything I ever installed in vmware ran about four times slower than the original.

I never filed a bug becuase it is proprietary software and I don't care.

---

### Post by yamagami on 2006-04-13
I was expecting it to run 4  or more times slower. Even VmWare themselves told us to expect thing to run a bit slower.  But to our surprise, it runs faster. WAY faster! It's mad... 

It is proprietary software that's true, but it's also quality software. And the fact that it is proprietary does not make it any less 'good'.

---

### Post by az on 2006-04-13
[QUOTE=yamagami]I was expecting it to run 4  or more times slower. Even VmWare themselves told us to expect thing to run a bit slower.  But to our surprise, it runs faster. WAY faster! It's mad... 

It is proprietary software that's true, but it's also quality software. And the fact that it is proprietary does not make it any less 'good'.[/QUOTE]

Yes, but the fact that it is good does not take away from the fact that I give up my freedom to know what my computer is doing if I run it.  No thanks.

You don't have to be a fan of software freedom to use Ubuntu - and lot's of people could care less and use it happily.  Whatever turns you on.  

You do, however, have to accept the EULA to use proprietary software....

---

### Post by heislord5 on 2006-04-13
azz is that your picture or william shatner?

---

### Post by NeghVar on 2006-04-13
> azz is that your picture or william shatner?

I think its both, but on another note... William shatner doesn't exist, everyone knows that William Shatner was just a charector played by Captain Kirk after he travelled back in time and got stuck here...

Back to the original question. Does your windows box have any viruses/spyware/resource hog programs (ie windows, other bloatware)? I know when I ran it it seemed comparable but I dont no because ive never sat with a stop watch and timed it.

---

### Post by towsonu2003 on 2006-04-14
[QUOTE=azz]
I never filed a bug becuase it is proprietary software and I don't care.[/QUOTE]
I couldn't agree with you more. To be honest, I don't see any difference between qemu (with kemu) and vmware. The only reason I'm using vmware is bc I installed it... once I switch to dapper (clean install, repartition etc), I'll be using qemu exclusively (and try Xen as well). 

In vmware, I use dsl (damn small linux) and the mouse jumps all around (like an overdosed coffee mug). And it's slow, with dsl :confused: anyway, if I were using qemu, I'd have filed a bug already. 

PS. Yes, kemu is proprietary. give the developer a break. check out wikipedia for an open source kemu-like module for qemu (QVMsomething). 

As per the OP, I run win xp, and it's definitely slower both in qemu and vmware than in real life (dual boot)...

---

### Post by yamagami on 2006-04-14
We run vmware at work (where licenses are affordable). Most of our servers are either Red Hats or Solaris but we do run some windows enviroments since some clients run that for some obscure reason we never really understood. Our desktops all run windows unfortunatly and I was not allowed to run linux exclusivly ("You can dual boot if ya like, but you must run windows").

Each of our windows boxes runs a java app server as well as various other win apps. no spyware or other crap like that (that I know of at least).  The vmware runs just the java app server + apache and our application. But the host machine runs the usual Ms office apps. And that machine serves me the app significantly faster. unexplained. voodoo i guess. 

As for 'free/proprietary/open' software debate:
I'm not an extreme person. I'm more of a middle-man. I like to have the freedom and flexibility to turn this or that way which is not really easy to do when you live in one of the extreme sides - one direction is always 'blocked'.
I use linux because I like computers, and I *know* that it is a better OS. Windows is for people who do not like computers but are forced to used them (and also have a certain level of masochism). 
I'll always prefer the free and open choice of software considering that it is indeed better then proprietary versions. I won't use inferior software just because its 'open'. I didn't try qemu or kemu or xen yet. But I'm sure I will once I get round to it (vmware was my first encounter with that type of software).  
Btw - I still use a windows box to run my music studio. I dn't think there is a *realistic* alternative to Cubase on any platform (I'm a cubase user since version 1 and it's hard to replace).

Harel

---

