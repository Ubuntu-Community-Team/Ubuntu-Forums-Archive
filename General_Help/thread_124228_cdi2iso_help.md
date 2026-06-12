---
title: "cdi2iso help"
date: 2006-02-01
forum: General Help
---

### Post by PrincessPeach on 2006-02-01
I'm trying to burn a discjuggler (cdi) image using linux.  I googled and found [cdi2iso]("http://developer.berlios.de/projects/cdi2iso/") which turns the cdi into an iso which I can then burn.  I downloaded the source to compile, but when I do a ./Makefile, I get this:

```

./Makefile: line 1: all:: command not found
./Makefile: line 4: clean:: command not found

```

Am I doing something wrong or missing something? I have build-essentials already.

---

### Post by sanone on 2006-07-04
The way I installed cdi2iso is by downloading the latest package for SuSE:

[http://download2.berlios.de/cdi2iso/cdi2iso-0.1-1_suse93.i586.rpm](http://download2.berlios.de/cdi2iso/cdi2iso-0.1-1_suse93.i586.rpm)

And installed it with "alien"

```
sudo alien -i cdi2iso-0.1-1_suse93.i586.rpm
```

That's all.. no need to compile this little tool.

---

### Post by alecz20 on 2008-07-12
I compiled using Geany, an the program executes, but I get the following error:

"Segmentation fault (core dumped)"

Is the initial image bad?

---

