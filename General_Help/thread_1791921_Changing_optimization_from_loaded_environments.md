---
title: "Changing optimization from loaded environments"
date: 2011-06-27
forum: General Help
---

### Post by salmontres on 2011-06-27
Hi guys,

I'm connecting to a supercomputer running Ubuntu and it requires us to use the 'module' command to set up our environment. (Environment variables, options, etc.)

So, for instance, if I want to use Intel compilers for a build, I type 'module load intel/12.0' before I try to compile. My question is this: how can I tell exactly what's being loaded with this command? I know the Intel compilers are loaded, but how do I know what options are being used? (In this case, I want to use the option -O2 for a lighter optimization. How should I specify this?)

---

### Post by Gyokuro on 2011-06-27
Hi,

every SC has somewhere a FAQ or some kind of a quickstart guide which should explain the basic commands and therefore you should search for such a guide at your SC.

module add intel/12.0

then

icc -o helloworld -O2 helloworld.c

---

