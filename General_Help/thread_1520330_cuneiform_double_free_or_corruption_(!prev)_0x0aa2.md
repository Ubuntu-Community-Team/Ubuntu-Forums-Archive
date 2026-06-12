---
title: "cuneiform: double free or corruption (!prev): 0x0aa204d0"
date: 2010-06-29
forum: General Help
---

### Post by xxlray on 2010-06-29
I run ubuntu in a parallels Virtual Machin on a macbook pro. When I use cuneiform 0.7.0 I get the following error:

```
$ cuneiform -l ger -f hocr -o "pg_0059.pdf.png.bmp.hocr" "pg_0059.pdf.png.bmp"Cuneiform for Linux 0.7.0
*** glibc detected *** cuneiform: double free or corruption (!prev): 0x0aa204d0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0x60a591]
/lib/tls/i686/cmov/libc.so.6(+0x6cde8)[0x60bde8]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0x60eecd]
/lib/tls/i686/cmov/libc.so.6(fclose+0x14a)[0x5faaaa]
/usr/lib/cuneiform/librfrmt.so(RFRMT_Formatter+0x209)[0xe06f79]
/usr/lib/cuneiform/libpuma.so(+0xb702)[0x298702]
/usr/lib/cuneiform/libpuma.so(PUMA_XFinalRecognition+0xf3)[0x299e63]
cuneiform[0x804a5e6]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x5b5bd6]
cuneiform[0x8049461]
======= Memory map: ========
00110000-00118000 r-xp 00000000 08:01 1327145    /usr/lib/cuneiform/librcorrkegl.so
00118000-00119000 r--p 00007000 08:01 1327145    /usr/lib/cuneiform/librcorrkegl.so
00119000-0011a000 rw-p 00008000 08:01 1327145    /usr/lib/cuneiform/librcorrkegl.so
0011a000-0015f000 rw-p 00000000 00:00 0 
0015f000-00176000 r-xp 00000000 08:01 1327149    /usr/lib/cuneiform/librimage.so
00176000-00177000 r--p 00016000 08:01 1327149    /usr/lib/cuneiform/librimage.so
00177000-00178000 rw-p 00017000 08:01 1327149    /usr/lib/cuneiform/librimage.so
00178000-00179000 rw-p 00000000 00:00 0 
00179000-00186000 r-xp 00000000 08:01 1327155    /usr/lib/cuneiform/librout.so
00186000-00187000 r--p 0000c000 08:01 1327155    /usr/lib/cuneiform/librout.so
00187000-0018a000 rw-p 0000d000 08:01 1327155    /usr/lib/cuneiform/librout.so
0018a000-0018b000 rw-p 00000000 00:00 0 
0018b000-00190000 r-xp 00000000 08:01 1327161    /usr/lib/cuneiform/librshelllines.so
00190000-00191000 r--p 00004000 08:01 1327161    /usr/lib/cuneiform/librshelllines.so
00191000-00192000 rw-p 00005000 08:01 1327161    /usr/lib/cuneiform/librshelllines.so
00192000-00193000 r-xp 00000000 08:01 1327128    /usr/lib/cuneiform/libcpu32.so
00193000-00194000 r--p 00000000 08:01 1327128    /usr/lib/cuneiform/libcpu32.so
00194000-00195000 rw-p 00001000 08:01 1327128    /usr/lib/cuneiform/libcpu32.so
00195000-001a0000 r-xp 00000000 08:01 1327133    /usr/lib/cuneiform/libexc.so
001a0000-001a1000 r--p 0000a000 08:01 1327133    /usr/lib/cuneiform/libexc.so
001a1000-001a2000 rw-p 0000b000 08:01 1327133    /usr/lib/cuneiform/libexc.so
001a2000-00222000 rw-p 00000000 00:00 0 
00224000-00231000 r-xp 00000000 08:01 1327127    /usr/lib/cuneiform/libcpage.so
00231000-00232000 r--p 0000c000 08:01 1327127    /usr/lib/cuneiform/libcpage.so
00232000-00233000 rw-p 0000d000 08:01 1327127    /usr/lib/cuneiform/libcpage.so
00233000-00236000 r-xp 00000000 08:01 1327158    /usr/lib/cuneiform/librreccom.so
00236000-00237000 r--p 00002000 08:01 1327158    /usr/lib/cuneiform/librreccom.so
00237000-00238000 rw-p 00003000 08:01 1327158    /usr/lib/cuneiform/librreccom.so
00238000-00239000 rw-p 00000000 00:00 0 
00239000-0024a000 r-xp 00000000 08:01 1327154    /usr/lib/cuneiform/librneg.so
0024a000-0024b000 r--p 00010000 08:01 1327154    /usr/lib/cuneiform/librneg.so
0024b000-0024c000 rw-p 00011000 08:01 1327154    /usr/lib/cuneiform/librneg.so
0024c000-00255000 r-xp 00000000 08:01 1327165    /usr/lib/cuneiform/libsmetric.so
00255000-00256000 r--p 00008000 08:01 1327165    /usr/lib/cuneiform/libsmetric.so
00256000-00257000 rw-p 00009000 08:01 1327165    /usr/lib/cuneiform/libsmetric.so
00257000-0025f000 r-xp 00000000 08:01 1327126    /usr/lib/cuneiform/libcline.so
0025f000-00260000 r--p 00007000 08:01 1327126    /usr/lib/cuneiform/libcline.so
00260000-00261000 rw-p 00008000 08:01 1327126    /usr/lib/cuneiform/libcline.so
00261000-0027f000 r-xp 00000000 08:01 1327143    /usr/lib/cuneiform/librbal.so
0027f000-00280000 r--p 0001d000 08:01 1327143    /usr/lib/cuneiform/librbal.so
00280000-00281000 rw-p 0001e000 08:01 1327143    /usr/lib/cuneiform/librbal.so
00281000-00282000 rw-p 00000000 00:00 0 
00282000-00288000 r-xp 00000000 08:01 1327142    /usr/lib/cuneiform/libr3532.so
00288000-00289000 r--p 00005000 08:01 1327142    /usr/lib/cuneiform/libr3532.so
00289000-0028a000 rw-p 00006000 08:01 1327142    /usr/lib/cuneiform/libr3532.so
0028a000-0028d000 rw-p 00000000 00:00 0 
0028d000-0029f000 r-xp 00000000 08:01 1327141    /usr/lib/cuneiform/libpuma.so
0029f000-002a0000 r--p 00012000 08:01 1327141    /usr/lib/cuneiform/libpuma.so
002a0000-002a2000 rw-p 00013000 08:01 1327141    /usr/lib/cuneiform/libpuma.so
002a2000-002b2000 rw-p 00000000 00:00 0 
002b2000-002bd000 r-xp 00000000 08:01 1327164    /usr/lib/cuneiform/librverline.so
002bd000-002be000 r--p 0000a000 08:01 1327164    /usr/lib/cuneiform/librverline.so
002be000-002bf000 rw-p 0000b000 08:01 1327164    /usr/lib/cuneiform/librverline.so
002bf000-00308000 rw-p 00000000 00:00 0 
00308000-00315000 r-xp 00000000 08:01 1327146    /usr/lib/cuneiform/librcutp.so
00315000-00316000 r--p 0000c000 08:01 1327146    /usr/lib/cuneiform/librcutp.so
00316000-00318000 rw-p 0000d000 08:01 1327146    /usr/lib/cuneiform/librcutp.so
00318000-00338000 rw-p 00000000 00:00 0 
00338000-0033d000 r-xp 00000000 08:01 1327122    /usr/lib/cuneiform/libccom.so
0033d000-0033e000 r--p 00004000 08:01 1327122    /usr/lib/cuneiform/libccom.so
0033e000-0033f000 rw-p 00005000 08:01 1327122    /usr/lib/cuneiform/libccom.so
0033f000-00342000 r-xp 00000000 08:01 1327167    /usr/lib/cuneiform/libwindummy.so
00342000-00343000 r--p 00002000 08:01 1327167    /usr/lib/cuneiform/libwindummy.so
00343000-00344000 rw-p 00003000 08:01 1327167    /usr/lib/cuneiform/libwindummy.so
00346000-0034e000 r-xp 00000000 08:01 1327156    /usr/lib/cuneiform/librpic.so
0034e000-0034f000 r--p 00007000 08:01 1327156    /usr/lib/cuneiform/librpic.so
0034f000-00350000 rw-p 00008000 08:01 1327156    /usr/lib/cuneiform/librpic.so
00350000-00354000 r-xp 00000000 08:01 1327137    /usr/lib/cuneiform/libloc32.so
00354000-00355000 r--p 00003000 08:01 1327137    /usr/lib/cuneiform/libloc32.so
00355000-00356000 rw-p 00004000 08:01 1327137    /usr/lib/cuneiform/libloc32.so
00356000-003bd000 rw-p 00000000 00:00 0 
003bd000-003c5000 r-xp 00000000 08:01 1327130    /usr/lib/cuneiform/libctb32.so
003c5000-003c6000 r--p 00007000 08:01 1327130    /usr/lib/cuneiform/libctb32.so
003c6000-003c7000 rw-p 00008000 08:01 1327130    /usr/lib/cuneiform/libctb32.so
003c7000-003d8000 rw-p 00000000 00:00 0 
003d9000-003e7000 r-xp 00000000 08:01 1327140    /usr/lib/cuneiform/libpass2.so
003e7000-003e8000 r--p 0000d000 08:01 1327140    /usr/lib/cuneiform/libpass2.so
003e8000-003e9000 rw-p 0000e000 08:01 1327140    /usr/lib/cuneiform/libpass2.so
003e9000-003ec000 rw-p 00000000 00:00 0 
003ec000-00404000 r-xp 00000000 08:01 1327135    /usr/lib/cuneiform/libleo32.so
00404000-00405000 r--p 00017000 08:01 1327135    /usr/lib/cuneiform/libleo32.so
00405000-00406000 rw-p 00018000 08:01 1327135    /usr/lib/cuneiform/libleo32.so
00406000-0040b000 rw-p 00000000 00:00 0 
0040b000-00414000 r-xp 00000000 08:01 1327132    /usr/lib/cuneiform/libevn32.soAborted
```My system infos:
```
$ cat /etc/issue
Ubuntu 10.04 LTS \n \l

$ uname -r
2.6.32-22-generic

$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
stepping    : 10
cpu MHz        : 2400.028
cache size    : 3072 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall lm constant_tsc up arch_perfmon aperfmperf pni ssse3 sse4_1 hypervisor lahf_lm
bogomips    : 4800.05
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management:

```

---

### Post by joako on 2011-03-26
I've installed Ubuntu 10.10 in VirtualBox on MacOS X Server 10.6.5 and I am seeing the same errors.... but it seems my OCR is running just fine.

# cuneiform --version
Cuneiform for Linux 0.7.0

Did you ever get anywhere with your errors?

---

### Post by xxlray on 2011-03-26
No - I simply gave up.

---

### Post by the_last_don on 2011-03-26
I foolowd [this one]("http://ubuntuforums.org/showthread.php?t=175050") and tried
export  MALLOC_CHECK_=0 

cuneiform executed with no core dumps, but it does not generate any text output :-(
any other  hint ?

---

