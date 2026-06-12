---
title: "Installing octave3.0 in Ubuntu 11.04"
date: 2011-06-06
forum: General Help
---

### Post by zainka on 2011-06-06
Hi

I try to compile Octave3.0.5 version in Ubuntu 11.04 since it is a dep. for a private tool I am about to use. However, I get the following error:


> ../libcruft/libcruft.so: undefined reference to `d_cnjg'
../libcruft/libcruft.so: undefined reference to `do_lio'
../libcruft/libcruft.so: undefined reference to `z_sqrt'
../src/liboctinterp.so: undefined reference to `e_wsfe'
../libcruft/libcruft.so: undefined reference to `i_len'
../libcruft/libcruft.so: undefined reference to `d_int'
../libcruft/libcruft.so: undefined reference to `z_abs'
../libcruft/libcruft.so: undefined reference to `d_imag'
../libcruft/libcruft.so: undefined reference to `pow_dd'
../libcruft/libcruft.so: undefined reference to `i_indx'
../libcruft/libcruft.so: undefined reference to `s_wsfi'
../libcruft/libcruft.so: undefined reference to `d_sign'
../libcruft/libcruft.so: undefined reference to `i_nint'
../libcruft/libcruft.so: undefined reference to `s_stop'
../libcruft/libcruft.so: undefined reference to `e_wsfi'
../libcruft/libcruft.so: undefined reference to `pow_ii'
../libcruft/libcruft.so: undefined reference to `r_sign'
../libcruft/libcruft.so: undefined reference to `s_wsle'
../libcruft/libcruft.so: undefined reference to `pow_zi'
../libcruft/libcruft.so: undefined reference to `s_cmp'
../libcruft/libcruft.so: undefined reference to `d_lg10'
../libcruft/libcruft.so: undefined reference to `s_copy'
../libcruft/libcruft.so: undefined reference to `s_cat'
../libcruft/libcruft.so: undefined reference to `e_wsle'
../src/liboctinterp.so: undefined reference to `do_fio'
../libcruft/libcruft.so: undefined reference to `i_dnnt'
../src/liboctinterp.so: undefined reference to `s_wsfe'
../libcruft/libcruft.so: undefined reference to `pow_di'
../libcruft/libcruft.so: undefined reference to `pow_ri'
../libcruft/libcruft.so: undefined reference to `z_div'
../libcruft/libcruft.so: undefined reference to `d_mod'
collect2: ld returned 1 exit status
make[2]: *** [octave] Error 1
make[2]: Leaving directory `/home/evidvid/dep/octave-3.0.5/src'
make[1]: *** [src] Error 2
make[1]: Leaving directory `/home/evidvid/dep/octave-3.0.5'
make: *** [all] Error 2


 I know octave 3.0 was not ment for 11.04, but as long as I cant get my company to redo their tools I am stuck for the moment or I need to downgrade to an earlier version of Ubuntu and taht WILL cause other problems.

Breg
VV

---

