---
title: "Installation error of Loris on Karmic"
date: 2010-01-21
forum: General Help
---

### Post by AkiraBergman on 2010-01-21
I jumped over the Python and Csound headers hurdles of the configure file, now I get the following error. Any suggestions?

> nuri@nuri:~/loris-1.6$ make
make  all-recursive
make[1]: Entering directory `/home/nuri/loris-1.6'
Making all in csound
make[2]: Entering directory `/home/nuri/loris-1.6/csound'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/nuri/loris-1.6/csound'
Making all in src
make[2]: Entering directory `/home/nuri/loris-1.6/src'
if /bin/bash ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I..    -I/usr/include/csound  -g -O2 -MT libloris_la-FourierTransform.lo -MD -MP -MF ".deps/libloris_la-FourierTransform.Tpo" -c -o libloris_la-FourierTransform.lo `test -f 'FourierTransform.C' || echo './'`FourierTransform.C; \
	then mv -f ".deps/libloris_la-FourierTransform.Tpo" ".deps/libloris_la-FourierTransform.Plo"; else rm -f ".deps/libloris_la-FourierTransform.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/csound -g -O2 -MT libloris_la-FourierTransform.lo -MD -MP -MF .deps/libloris_la-FourierTransform.Tpo -c FourierTransform.C  -fPIC -DPIC -o .libs/libloris_la-FourierTransform.o
In file included from /usr/include/stdio.h:907,
                 from /usr/include/fftw3.h:50,
                 from FourierTransform.C:137:
/usr/include/bits/stdio.h: In function 'int Loris::fgetc_unlocked(FILE*)':
/usr/include/bits/stdio.h:56: error: invalid use of incomplete type 'struct _IO_FILE'
/usr/include/stdio.h:45: error: forward declaration of 'struct _IO_FILE'
/usr/include/bits/stdio.h:56: error: invalid use of incomplete type 'struct _IO_FILE'
/usr/include/stdio.h:45: error: forward declaration of 'struct _IO_FILE'
/usr/include/bits/stdio.h:56: error: cannot convert 'FILE*' to 'Loris::_IO_FILE*' for argument '1' to 'int Loris::__uflow(Loris::_IO_FILE*)'
/usr/include/bits/stdio.h:56: error: invalid use of incomplete type 'struct _IO_FILE'


---

