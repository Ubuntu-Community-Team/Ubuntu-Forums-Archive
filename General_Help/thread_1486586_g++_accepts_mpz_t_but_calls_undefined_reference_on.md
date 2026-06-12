---
title: "g++ accepts mpz_t but calls undefined reference on mpz_add and others"
date: 2010-05-18
forum: General Help
---

### Post by FRed_is_dead_7x on 2010-05-18
Compiling the following code:

#include <iostream>
#include <gmp.h>

int main()
{
	mpz_t fibb1, fibb2;
	mpz_init_set_str (fibb1, "1", 10);
	mpz_init_set_str (fibb2, "1", 10);
	mpz_t (temp);
	std::cout << "1\n1\n";
	for (int i = 0; i < 50; ++i)
	{
		mpz_add (temp, fibb1, fibb2);
		mpz_set (fibb1, temp);
		std::cout << fibb1 << "\n";
		mpz_add (temp, fibb1, fibb2);
		mpz_set (temp, fibb2);
		std::cout << fibb2 << "\n";
	}

	mpz_clear (temp);
	mpz_clear (fibb1);
	mpz_clear (fibb2);

	return 0;
}

The code compiles, "g++ -lgmpxx -lgmp ./main.cpp", but running it causes this:

1
1
*** glibc detected *** ./fibb: realloc(): invalid pointer: 0x0000000000400bd5 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f720a981dd6]
/lib/libc.so.6(realloc+0x2e1)[0x7f720a9877e1]
/usr/lib/libgmp.so.3(__gmp_default_reallocate+0x1c)[0x7f720b42ebcc]
/usr/lib/libgmp.so.3(__gmpz_realloc+0x3a)[0x7f720b447b1a]
/usr/lib/libgmp.so.3(__gmpz_add+0x191)[0x7f720b438221]
./fibb[0x400a8a]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7f720a92aabd]
./fibb[0x400969]
======= Memory map: ========
00400000-00401000 r-xp 00000000 08:08 11927734                           /home/XXXXXXX/projects/fibb/fibb
00600000-00601000 r--p 00000000 08:08 11927734                           /home/XXXXXXX/projects/fibb/fibb
00601000-00602000 rw-p 00001000 08:08 11927734                           /home/XXXXXXX/projects/fibb/fibb
00d5d000-00d7e000 rw-p 00000000 00:00 0                                  [heap]
7f720a69c000-7f720a703000 r-xp 00000000 08:07 1141                       /usr/local/lib/libgmp.so.10.0.1
7f720a703000-7f720a902000 ---p 00067000 08:07 1141                       /usr/local/lib/libgmp.so.10.0.1
7f720a902000-7f720a903000 r--p 00066000 08:07 1141                       /usr/local/lib/libgmp.so.10.0.1
7f720a903000-7f720a90c000 rw-p 00067000 08:07 1141                       /usr/local/lib/libgmp.so.10.0.1
7f720a90c000-7f720aa72000 r-xp 00000000 08:05 156                        /lib/libc-2.10.1.so
7f720aa72000-7f720ac71000 ---p 00166000 08:05 156                        /lib/libc-2.10.1.so
7f720ac71000-7f720ac75000 r--p 00165000 08:05 156                        /lib/libc-2.10.1.so
7f720ac75000-7f720ac76000 rw-p 00169000 08:05 156                        /lib/libc-2.10.1.so
7f720ac76000-7f720ac7b000 rw-p 00000000 00:00 0 
7f720ac7b000-7f720ac91000 r-xp 00000000 08:05 63                         /lib/libgcc_s.so.1
7f720ac91000-7f720ae90000 ---p 00016000 08:05 63                         /lib/libgcc_s.so.1
7f720ae90000-7f720ae91000 r--p 00015000 08:05 63                         /lib/libgcc_s.so.1
7f720ae91000-7f720ae92000 rw-p 00016000 08:05 63                         /lib/libgcc_s.so.1
7f720ae92000-7f720af14000 r-xp 00000000 08:05 160                        /lib/libm-2.10.1.so
7f720af14000-7f720b114000 ---p 00082000 08:05 160                        /lib/libm-2.10.1.so
7f720b114000-7f720b115000 r--p 00082000 08:05 160                        /lib/libm-2.10.1.so
7f720b115000-7f720b116000 rw-p 00083000 08:05 160                        /lib/libm-2.10.1.so
7f720b116000-7f720b208000 r-xp 00000000 08:07 383                        /usr/lib/libstdc++.so.6.0.13
7f720b208000-7f720b408000 ---p 000f2000 08:07 383                        /usr/lib/libstdc++.so.6.0.13
7f720b408000-7f720b40f000 r--p 000f2000 08:07 383                        /usr/lib/libstdc++.so.6.0.13
7f720b40f000-7f720b411000 rw-p 000f9000 08:07 383                        /usr/lib/libstdc++.so.6.0.13
7f720b411000-7f720b426000 rw-p 00000000 00:00 0 
7f720b426000-7f720b485000 r-xp 00000000 08:07 3011                       /usr/lib/libgmp.so.3.5.0
7f720b485000-7f720b684000 ---p 0005f000 08:07 3011                       /usr/lib/libgmp.so.3.5.0
7f720b684000-7f720b685000 r--p 0005e000 08:07 3011                       /usr/lib/libgmp.so.3.5.0
7f720b685000-7f720b68a000 rw-p 0005f000 08:07 3011                       /usr/lib/libgmp.so.3.5.0
7f720b68a000-7f720b68d000 r-xp 00000000 08:07 18139                      /usr/local/lib/libgmpxx.so.4.2.1
7f720b68d000-7f720b88d000 ---p 00003000 08:07 18139                      /usr/local/lib/libgmpxx.so.4.2.1
7f720b88d000-7f720b88e000 r--p 00003000 08:07 18139                      /usr/local/lib/libgmpxx.so.4.2.1
7f720b88e000-7f720b88f000 rw-p 00004000 08:07 18139                      /usr/local/lib/libgmpxx.so.4.2.1
7f720b88f000-7f720b8ae000 r-xp 00000000 08:05 67                         /lib/ld-2.10.1.so
7f720ba89000-7f720ba8d000 rw-p 00000000 00:00 0 
7f720baa9000-7f720baad000 rw-p 00000000 00:00 0 
7f720baad000-7f720baae000 r--p 0001e000 08:05 67                         /lib/ld-2.10.1.so
7f720baae000-7f720baaf000 rw-p 0001f000 08:05 67                         /lib/ld-2.10.1.so
7fff960fe000-7fff96113000 rw-p 00000000 00:00 0                          [stack]
7fff96140000-7fff96141000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted

Am I doing something wrong, or is this a bug?

---

### Post by gmargo on 2010-05-18
Your "temp" variable has not been initialized.  Add "mpz_init(temp);" just after the declaration, and then it all works (tested on 8.04 Hardy.)

---

### Post by FRed_is_dead_7x on 2010-05-23
I thought it was something stupid. Thanks.

---

