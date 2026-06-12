---
title: "gimp fourier plugin"
date: 2012-02-11
forum: General Help
---

### Post by bobb40 on 2012-02-11
Has anyone managed to install the gimp fourier plugin?  If so, how?

I got the source (fourier-0.4.1.tar.gz) and installed the prerequisites (libfftw3-3, libfftw3-dev, libgimp2.0, and libgimp2.0-dev) but running "make" lists many "undefined references".  Adding many -I directives to Makefile eliminated the "undefined references", but still leaves a mess.

Suggestions would be appreciated.

---

### Post by mdizzle on 2013-03-24
> **bobb40 said:**
> Has anyone managed to install the gimp fourier plugin?  If so, how?

I got the source (fourier-0.4.1.tar.gz) and installed the prerequisites (libfftw3-3, libfftw3-dev, libgimp2.0, and libgimp2.0-dev) but running "make" lists many "undefined references".  Adding many -I directives to Makefile eliminated the "undefined references", but still leaves a mess.

Suggestions would be appreciated.

For me, I had to change the order of params in the Makefile: libraries should go last. find the lines:

```
fourier: fourier.c
	$(GCC) $(CFLAGS) **[COLOR="#FF0000"]$(LIBS)[/COLOR]** -o fourier fourier.c
```

and change it to:

```
fourier: fourier.c
	$(GCC) $(CFLAGS) -o fourier fourier.c **[COLOR="#008000"]$(LIBS)[/COLOR]**
```

---

