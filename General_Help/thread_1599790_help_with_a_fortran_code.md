---
title: "help with a fortran code"
date: 2010-10-18
forum: General Help
---

### Post by ubun_tut on 2010-10-18
hi,

i have some problem trying to run a fortran code. apologies if this is not the appropriate place to post.

i have downloaded the enclosed fortran codes from [http://code.google.com/p/scatterlib/](http://code.google.com/p/scatterlib/). in a nutshell, these codes calculate light scattering from a spherical particle. i first compile the 2 needed files with

```

gfortran bhmie.f callbhmie.f

```

then execute with "./a.out". it is able to run fine, and i can type in inputs. however, when i try to enter a complex number (the complex refractive index), it gives me errors like 

```

At line 33 of file callbhmie.f (unit = 5, file = 'stdin')
Fortran runtime error: bad integer for item 1 in list input

```

i tried a few different combinations during the input, such as 

```

1.55 -0.008
1.55, 0.008
1.55

```

but they all give errors similar to the one above. i am not familiar with fortran, but i suspect its the way i input the complex number. anyone knows how i can solve this?

---

