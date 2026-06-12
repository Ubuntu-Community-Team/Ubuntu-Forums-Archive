---
title: "open foxit reader from command line"
date: 2010-05-09
forum: General Help
---

### Post by mrwawa on 2010-05-09
Hi all,

I like foxit reader, but would like to be able to open it at the command line.  However, I haven't been able to find out how to do it.  Does anyone know how?

Thanks

---

### Post by dcstar on 2010-05-10
> **mrwawa said:**
> Hi all,

I like foxit reader, but would like to be able to open it at the command line.  However, I haven't been able to find out how to do it.  Does anyone know how?

Thanks

Find out what launcher command it uses and run that.

---

### Post by mrwawa on 2010-05-10
That is what I need to know.  How does one find out the launcher command for installed programs?  I can't seem to find it for foxit reader.

---

### Post by luigi_mb on 2010-05-10
> **mrwawa said:**
> That is what I need to know.  How does one find out the launcher command for installed programs?  I can't seem to find it for foxit reader.

```

$ /home/luigi/Foxit/FoxitReader

```

You can create an alias in .bashrc

```

alias foxit='/home/luigi/Foxit/FoxitReader'

```

Replace "luigi" with your username. If you installed Foxit somewhere else, change the lines above accordingly. 


/luigi

---

### Post by mrwawa on 2010-05-12
Thanks a lot.  That worked perfectly.

---

