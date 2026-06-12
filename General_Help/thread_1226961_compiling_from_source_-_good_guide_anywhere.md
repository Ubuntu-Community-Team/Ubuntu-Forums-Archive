---
title: "compiling from source - good guide anywhere?"
date: 2009-07-30
forum: General Help
---

### Post by pabc on 2009-07-30
I need a more recent version of mono then is available in the repos (need 2.4, only 2.0 is there).

So it looks like I'll have to grab the source from the mono site and compile it. Proly no big deal to a lot of people but it's daunting to me.

is there a guide available anywhere to help me out?

---

### Post by apjone on 2009-07-30
Its mainly just the command below in a terminal after a cd to source directory. but also check out [http://www.maximumpc.com/article/howtos/howto_compile_programs_from_source_linux](http://www.maximumpc.com/article/howtos/howto_compile_programs_from_source_linux) (found via a quick google)

```
 ./configure && make && sudo make install
```

---

### Post by realzippy on 2009-07-30
...what about looking at the mono project?:

[http://mono-project.com/Compiling_Mono](http://mono-project.com/Compiling_Mono)

---

### Post by pabc on 2009-07-30
thank you. I feel a tool for not googling before asking now but I assumed it would be more complicated than (I hope) it will be.

---

### Post by realzippy on 2009-07-30
OK,step by step:

Click:

[http://ftp.novell.com/pub/mono/sources/mono/mono-2.4.2.3.tar.bz2](http://ftp.novell.com/pub/mono/sources/mono/mono-2.4.2.3.tar.bz2)

and download the tarball (to Desktop),then unpack it (rightclick,unpack here)

Open a terminal.Type:

 [CENTER][/CENTER]cd Desktop

then type:

 [CENTER][/CENTER]cd mono-2.4.2.3/

then type:

[CENTER][/CENTER]./configure --prefix=/usr/local; make; make install

what happens?

---

### Post by pabc on 2009-07-30
and another good link 
[http://blog.ruski.co.za/page/Install-Mono-on-Ubuntu.aspx](http://blog.ruski.co.za/page/Install-Mono-on-Ubuntu.aspx)

---

### Post by directhex on 2009-07-30
[https://launchpad.net/~directhex/+archive/monoxide](https://launchpad.net/~directhex/+archive/monoxide)

[http://www.mono-project.com/Parallel_Mono_Environments](http://www.mono-project.com/Parallel_Mono_Environments)

[http://mjhutchinson.com/journal/2007/11/08/how_not_break_mono](http://mjhutchinson.com/journal/2007/11/08/how_not_break_mono)

---

