---
title: "Mograso: modeling software make error in ubuntu"
date: 2010-05-25
forum: General Help
---

### Post by austinvishal on 2010-05-25
While i make the Mograso (modelling software)which is combination of C++ and fortran code, i get these errors in Ubuntu 10.01 
make  all-recursive
make[1]: Entering directory `/home/vishal/Desktop/mograso-1.0.1'
Making all in src
make[2]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src'
Making all in besselAmosOctave
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/besselAmosOctave'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/besselAmosOctave'
Making all in common
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/common'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/common'
Making all in MoGraSoTK
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/MoGraSoTK'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/MoGraSoTK'
Making all in MoGraSoUITK
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/MoGraSoUITK'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/MoGraSoUITK'
Making all in MoGraSo
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/MoGraSo'
g++  -g -O2 -O1   -o mograso  main.o mograsoJobFactory.o ../MoGraSoUITK/libmograsouitk.a ../MoGraSoTK/libmograsotk.a ../common/libcommon.a ../besselAmosOctave/libbessel.a -lpthread  -lxml2
../besselAmosOctave/libbessel.a(zbesh.o): In function `zbesh_':
/home/vishal/Desktop/mograso-1.0.1/src/besselAmosOctave/zbesh.f:285: undefined reference to `d_sign'
../besselAmosOctave/libbessel.a(zunhj.o): In function `zunhj_':
/home/vishal/Desktop/mograso-1.0.1/src/besselAmosOctave/zunhj.f:455: undefined reference to `pow_dd'
/home/vishal/Desktop/mograso-1.0.1/src/besselAmosOctave/zunhj.f:592: undefined reference to `pow_dd'
../besselAmosOctave/libbessel.a(zacon.o): In function `zacon_':
/home/vishal/Desktop/mograso-1.0.1/src/besselAmosOctave/zacon.f:44: undefined reference to `d_sign'
../besselAmosOctave/libbessel.a(zunk1.o): In function `zunk1_':
/home/vishal/Desktop/mograso-1.0.1/src/besselAmosOctave/zunk1.f:237: undefined reference to `d_sign'
../besselAmosOctave/libbessel.a(zunk2.o): In function `zunk2_':
/home/vishal/Desktop/mograso-1.0.1/src/besselAmosOctave/zunk2.f:292: undefined reference to `d_sign'
../besselAmosOctave/libbessel.a(zairy.o): In function `zairy_':
/home/vishal/Desktop/mograso-1.0.1/src/besselAmosOctave/zairy.f:264: undefined reference to `pow_dd'
../besselAmosOctave/libbessel.a(zacai.o): In function `zacai_':
/home/vishal/Desktop/mograso-1.0.1/src/besselAmosOctave/zacai.f:62: undefined reference to `d_sign'
collect2: ld returned 1 exit status
make[3]: *** [mograso] Error 1
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/MoGraSo'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1'
make: *** [all] Error 2


kindly help.Thanks in advance

---

### Post by austinvishal on 2010-05-25
i found out that d_sign  created due to underscore and pow_dd due to double** so i erased the necessary but im still not able to make the make check and make output are shown below
vishal@ubuntu:~/Desktop/mograso-1.0.1$ make check
Making check in src
make[1]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src'
Making check in besselAmosOctave
make[2]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/besselAmosOctave'
make[2]: Nothing to be done for `check'.
make[2]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/besselAmosOctave'
Making check in common
make[2]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/common'
make  wronskian besselp1
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/common'
g++  -g -O2 -O1   -o wronskian  testWronskian.o ./libcommon.a ../besselAmosOctave/libbessel.a -lpthread  -lxml2
source='testBesselP1.cpp' object='testBesselP1.o' libtool=no \
	depfile='.deps/testBesselP1.Po' tmpdepfile='.deps/testBesselP1.TPo' \
	depmode=gcc3 /bin/bash ../../depcomp \
	g++ -DHAVE_CONFIG_H -I. -I. -I../..   -O1 -I/usr/include/libxml2  -g -O2 -O1 -c -o testBesselP1.o `test -f 'testBesselP1.cpp' || echo './'`testBesselP1.cpp
g++  -g -O2 -O1   -o besselp1  testBesselP1.o ./libcommon.a ../besselAmosOctave/libbessel.a -lpthread  -lxml2
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/common'
make  check-TESTS
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/common'
FAIL: wronskian
PASS: besselp1
===================
1 of 2 tests failed
===================
make[3]: *** [check-TESTS] Error 1
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/common'
make[2]: *** [check-am] Error 2
make[2]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/common'
make[1]: *** [check-recursive] Error 1
make[1]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src'
make: *** [check-recursive] Error 1


make output

vishal@ubuntu:~/Desktop/mograso-1.0.1$ make
make  all-recursive
make[1]: Entering directory `/home/vishal/Desktop/mograso-1.0.1'
Making all in src
make[2]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src'
Making all in besselAmosOctave
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/besselAmosOctave'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/besselAmosOctave'
Making all in common
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/common'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/common'
Making all in MoGraSoTK
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/MoGraSoTK'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/MoGraSoTK'
Making all in MoGraSoUITK
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/MoGraSoUITK'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/MoGraSoUITK'
Making all in MoGraSo
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/MoGraSo'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/MoGraSo'
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src'
make[2]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src'
make[2]: Entering directory `/home/vishal/Desktop/mograso-1.0.1'
make[2]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1'
make[1]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1'

---

### Post by dino99 on 2010-05-25
maybe you will have better help with programming forum

---

