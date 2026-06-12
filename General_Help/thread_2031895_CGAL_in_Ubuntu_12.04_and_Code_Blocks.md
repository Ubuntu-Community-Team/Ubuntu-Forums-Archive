---
title: "CGAL in Ubuntu 12.04 and Code Blocks"
date: 2012-07-22
forum: General Help
---

### Post by anirbanghosh on 2012-07-22
I would like to use CGAL from Code Blocks. I am using Ubuntu 12.04. I have installed CGAL packages. 

I am trying with the following code.

```
#include <iostream>
#include <CGAL/Exact_predicates_inexact_constructions_kernel.h>
#include <CGAL/convex_hull_2.h>

typedef CGAL::Exact_predicates_inexact_constructions_kernel K;
typedef K::Point_2 Point_2;

int main()
{
  Point_2 points[5] = { Point_2(0,0), Point_2(10,0), Point_2(10,10), Point_2(6,5), Point_2(4,1) };
  Point_2 result[5];

  Point_2 *ptr = CGAL::convex_hull_2( points, points+5, result );
  std::cout <<  ptr - result << " points on the convex hull" << std::endl;
  return 0;
}

```From Ubuntu I got the following from terminal.

```
anirban@anirban-Studio-1555:~$ sudo dpkg -L libCGAL8
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libcgal8
/usr/share/doc/libcgal8/copyright
/usr/share/doc/libcgal8/changelog.Debian.gz
/usr/share/doc/libcgal8/README.Debian
/usr/lib
/usr/lib/libCGAL.so.8.0.0
/usr/lib/libCGAL_ImageIO.so.8.0.0
/usr/lib/libCGAL_Qt4.so.8.0.0
/usr/lib/libCGAL_Core.so.8.0.0
/usr/lib/libCGAL_Qt4.so.8
/usr/lib/libCGAL.so.8
/usr/lib/libCGAL_Core.so.8
/usr/lib/libCGAL_ImageIO.so.8


```In the linker section in code blocks I have tried using '-lcgal8' and also '-lCGAL8'.
In both cases, I get following message.

```
ld  cannot find -lcgal8
```But ```
-lCGAL
``` works, and I get the following messages.

```
obj/Debug/main.o||In function `Gmpq_rep':|
/usr/include/CGAL/GMP/Gmpq_type.h|50|undefined reference to `__gmpq_init'|
obj/Debug/main.o||In function `~Gmpq_rep':|
/usr/include/CGAL/GMP/Gmpq_type.h|51|undefined reference to `__gmpq_clear'|
obj/Debug/main.o||In function `Gmpq':|
/usr/include/CGAL/GMP/Gmpq_type.h|132|undefined reference to `__gmpq_set_d'|
obj/Debug/main.o||In function `CGAL::Gmpq::operator==(CGAL::Gmpq const&) const':|
/usr/include/CGAL/GMP/Gmpq_type.h|193|undefined reference to `__gmpq_equal'|
obj/Debug/main.o||In function `CGAL::Gmpq::operator<(CGAL::Gmpq const&) const':|
/usr/include/CGAL/GMP/Gmpq_type.h|194|undefined reference to `__gmpq_cmp'|
obj/Debug/main.o||In function `CGAL::Gmpq::operator-=(CGAL::Gmpq const&)':|
/usr/include/CGAL/GMP/Gmpq_type.h|286|undefined reference to `__gmpq_sub'|
obj/Debug/main.o||In function `CGAL::Gmpq::operator*=(CGAL::Gmpq const&)':|
/usr/include/CGAL/GMP/Gmpq_type.h|296|undefined reference to `__gmpq_mul'|
||=== Build finished: 7 errors, 0 warnings (0 minutes, 4 seconds) ===|

```

---

