---
title: "compiling inkscape 0.47"
date: 2009-12-07
forum: General Help
---

### Post by shiggydiggy on 2009-12-07
repo hasn't got the final so thought i build one.
I followed the instructions as per here
[http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu](http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu)
but this is what i got

```

In file included from /usr/include/c++/4.4/vector:65,
                 from ./2geom/utils.h:37,
                 from ./2geom/point.h:13,
                 from ./2geom/curve.h:43,
                 from ./2geom/path.h:43,
                 from ./2geom/svg-path.h:35,
                 from display/nr-arena-shape.cpp:15:
/usr/include/c++/4.4/bits/stl_vector.h: In instantiation of ‘std::vector<Geom::Path, std::allocator<Geom::Path> >’:
./2geom/path.h:680:   instantiated from here
/usr/include/c++/4.4/bits/stl_vector.h:171: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.4/README.Bugs> for instructions.
make[2]: *** [display/nr-arena-shape.o] Error 1
make[2]: Leaving directory `/home/stanley/inkscape-0.47/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/stanley/inkscape-0.47'
make: *** [all] Error 2

```

---

### Post by shiggydiggy on 2009-12-08
can anyone help me?
Is it honestly that hard to get the latest stable build of a program under linux? do I seriously have to run the 0.47 windows version under wine?

---

### Post by shiggydiggy on 2009-12-08
bump!

---

