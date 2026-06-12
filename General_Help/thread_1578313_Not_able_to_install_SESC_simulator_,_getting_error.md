---
title: "Not able to install SESC simulator , getting error"
date: 2010-09-20
forum: General Help
---

### Post by LYnkas on 2010-09-20
Hi , 
          I have ubuntu 10.04 on Vmware installed in Win 7 . 

I am trying to install SESC simulator  by following this tutorial  " [http://manio.org/sesc-tutorial-1-instaall-whole-sesc-step-by-step-577.html]("http://manio.org/sesc-tutorial-1-instaall-whole-sesc-step-by-step-577.html")" .  

I installed gcc as in the tutorial . But when I try to build the SESC  , I was able to complete till 8th step successfully . As in the 8th step , I gave this command 

```
$./build-1-binutils.
```

And I get the  same error which he mentions : 

```

errorgcc -W -Wall -Wstrict-prototypes -Wmissing-prototypes -g -O2 -o ar arparse.o arlex.o ar.o not-ranlib.o arsup.o rename.o binemul.o emul_vanilla.o bucomm.o version.o filemode.o  ../bfd/.libs/libbfd.a ../libiberty/libiberty.a ./../intl/libintl.a


arlex.o: In function `main&#8217;:

/home/manio/sescutils/build-mipseb-linux/obj/binutils-build/binutils/arlex.c:1: multiple definition of `main&#8217;

arparse.o:/home/manio/sescutils/build-mipseb-linux/obj/binutils-build/binutils/arparse.c:1: first defined here

ar.o: In function `main&#8217;:

/home/manio/sescutils/src/binutils/binutils/ar.c:342: multiple definition of `main&#8217;

arparse.o:/home/manio/sescutils/build-mipseb-linux/obj/binutils-build/binutils/arparse.c:1: first defined here

bucomm.o: In function `make_tempname&#8217;:

/home/manio/sescutils/src/binutils/binutils/bucomm.c:425: warning: the use of `mktemp&#8217; is dangerous, better use `mkstemp&#8217; or `mkdtemp&#8217;

ar.o: In function `mri_emul&#8217;:

```

I tried a lot . Still the error keeps coming . 

Can someone help ? I need to install this SESC simulator urgently for my project .

---

### Post by LYnkas on 2010-09-21
bump ........

Can someone help ?

---

### Post by fitzfitsahero on 2010-10-14
Looks like you're trying to install the utilities to build programs for the simulator.  Follow these steps found on the sesc homepage:

cvs -d:pserver:anonymous@sesc.cvs.sourceforge.net:/cvsroot/sesc login 			  
		cvs -z3 -d:pserver:anonymous@sesc.cvs.sourceforge.net:/cvsroot/sesc co -P sesc 			

then follow the README in the directory

---

