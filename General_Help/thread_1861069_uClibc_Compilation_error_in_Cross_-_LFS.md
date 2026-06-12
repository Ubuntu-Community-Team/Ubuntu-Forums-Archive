---
title: "uClibc Compilation error in Cross - LFS"
date: 2011-10-15
forum: General Help
---

### Post by chinmaya_n on 2011-10-15
uClibc is giving the following error when **$ make** is done, in the process of Cross-LFS (Linux From Scratch). This is shown [here (click)]("http://cross-lfs.org/view/clfs-embedded/arm/cross-tools/uclibc.html").

```
clfs@chinmaya:/mnt/clfs/sources/uClibc-0.9.31$ patch -Np1 -i ../uClibc-0.9.31-configs-2.patch
patching file clfs/config.arm.big
patching file clfs/config.arm.little
patching file clfs/config.i386.little
patching file clfs/config.mips.big
patching file clfs/config.mips.little
patching file clfs/config.x86_64.little
clfs@chinmaya:/mnt/clfs/sources/uClibc-0.9.31$ cp -v clfs/config.${CLFS_ARCH}.${CLFS_ENDIAN} .config
`clfs/config.arm.little' -> `.config'
clfs@chinmaya:/mnt/clfs/sources/uClibc-0.9.31$ if [ "${CLFS_ABI}" == "aapcs" ] || [ "${CLFS_ABI}" == "aapcs-linux" ]; \
>   then sed -i s/CONFIG_ARM_OABI/CONFIG_ARM_EABI/g .config; fi
clfs@chinmaya:/mnt/clfs/sources/uClibc-0.9.31$ make oldconfig
  MKDIR include/config
  HOSTCC-o extra/config/conf.o
  GEN extra/config/zconf.tab.c
  GEN extra/config/lex.zconf.c
  GEN extra/config/zconf.hash.c
  HOSTCC-o extra/config/zconf.tab.o
  HOSTCC extra/config/conf
./.config:38:warning: override: reassigning to symbol CONFIG_ARM_EABI
*
* Restart config...
*
*
* Target Architecture Features and Options
*
Target ABI
  1. OABI (CONFIG_ARM_OABI) (NEW)
> 2. EABI (CONFIG_ARM_EABI)
choice[1-2?]: 2
Target Processor Type
> 1. Generic Arm (CONFIG_GENERIC_ARM)
  2. Arm 610 (CONFIG_ARM610)
  3. Arm 710 (CONFIG_ARM710)
  4. Arm 7TDMI (CONFIG_ARM7TDMI)
  5. Arm 720T (CONFIG_ARM720T)
  6. Arm 920T (CONFIG_ARM920T)
  7. Arm 922T (CONFIG_ARM922T)
  8. Arm 926T (CONFIG_ARM926T)
  9. Arm 10T (CONFIG_ARM10T)
  10. Arm 1136JF-S (CONFIG_ARM1136JF_S)
  11. Arm 1176JZ-S (CONFIG_ARM1176JZ_S)
  12. Arm 1176JZF-S (CONFIG_ARM1176JZF_S)
  13. Arm Cortex-M3 (CONFIG_ARM_CORTEX_M3)
  14. Arm Cortex-M1 (CONFIG_ARM_CORTEX_M1)
  15. Intel StrongArm SA-110 (CONFIG_ARM_SA110)
  16. Intel StrongArm SA-1100 (CONFIG_ARM_SA1100)
  17. Intel Xscale (CONFIG_ARM_XSCALE)
  18. Intel Xscale With WMMX PXA27x (CONFIG_ARM_IWMMXT)
choice[1-18?]: 1
*
* Using ELF file format
*
Target Processor Endianness
  1. Big Endian (ARCH_WANTS_BIG_ENDIAN)
> 2. Little Endian (ARCH_WANTS_LITTLE_ENDIAN)
choice[1-2?]: 2
Target CPU has a memory management unit (MMU) (ARCH_HAS_MMU) [Y/n/?] y
  Do you want to utilize the MMU? (ARCH_USE_MMU) [Y/n/?] y
Enable floating point number support (UCLIBC_HAS_FLOATS) [Y/n/?] y
  Target CPU has a floating point unit (FPU) (UCLIBC_HAS_FPU) [Y/n/?] y
  Enable full C99 math library support (DO_C99_MATH) [Y/n/?] y
  Enable XSI math extensions to the ISO C standard (bessel) (DO_XSI_MATH) [N/y/?] n
  Enable C99 Floating-point environment (UCLIBC_HAS_FENV) [Y/n/?] y
Linux kernel header location (KERNEL_HEADERS) [${CLFS}/usr/include] ${CLFS}/usr/include
#
# configuration written to ./.config
#
clfs@chinmaya:/mnt/clfs/sources/uClibc-0.9.31$ make
  MKDIR include/bits
  GEN include/bits/sysnum.h
  GEN include/bits/uClibc_config.h
  LN include/pthread.h
  LN include/semaphore.h
  LN include/bits/pthreadtypes.h
  LN include/fpu_control.h
  LN include/dl-osinfo.h
  LN include/hp-timing.h
  LN include/bits/atomic.h
  LN include/bits/byteswap-common.h
  LN include/bits/byteswap.h
  LN include/bits/cmathcalls.h
  LN include/bits/confname.h
  LN include/bits/dirent.h
  LN include/bits/dlfcn.h
  LN include/bits/elfclass.h
  LN include/bits/environments.h
  LN include/bits/errno.h
  LN include/bits/fenvinline.h
  LN include/bits/getopt.h
  LN include/bits/huge_valf.h
  LN include/bits/huge_vall.h
  LN include/bits/in.h
  LN include/bits/inf.h
  LN include/bits/initspin.h
  LN include/bits/ioctl-types.h
  LN include/bits/ioctls.h
  LN include/bits/ipc.h
  LN include/bits/kernel-features.h
  LN include/bits/kernel_sigaction.h
  LN include/bits/local_lim.h
  LN include/bits/locale.h
  LN include/bits/mathcalls.h
  LN include/bits/mathinline.h
  LN include/bits/mman-common.h
  LN include/bits/mman.h
  LN include/bits/mqueue.h
  LN include/bits/msq.h
  LN include/bits/nan.h
  LN include/bits/netdb.h
  LN include/bits/poll.h
  LN include/bits/posix1_lim.h
  LN include/bits/posix2_lim.h
  LN include/bits/posix_opt.h
  LN include/bits/resource.h
  LN include/bits/sched.h
  LN include/bits/select.h
  LN include/bits/sem.h
  LN include/bits/sigaction.h
  LN include/bits/sigcontext.h
  LN include/bits/siginfo.h
  LN include/bits/signum.h
  LN include/bits/sigset.h
  LN include/bits/sigstack.h
  LN include/bits/sigthread.h
  LN include/bits/sockaddr.h
  LN include/bits/socket.h
  LN include/bits/stat.h
  LN include/bits/statfs.h
  LN include/bits/statvfs.h
  LN include/bits/stdio.h
  LN include/bits/stdio_lim.h
  LN include/bits/syscalls-common.h
  LN include/bits/termios.h
  LN include/bits/time.h
  LN include/bits/types.h
  LN include/bits/typesizes.h
  LN include/bits/uClibc_charclass.h
  LN include/bits/uClibc_clk_tck.h
  LN include/bits/uClibc_ctype.h
  LN include/bits/uClibc_errno.h
  LN include/bits/uClibc_fpmax.h
  LN include/bits/uClibc_local_lim.h
  LN include/bits/uClibc_locale.h
  LN include/bits/uClibc_mutex.h
  LN include/bits/uClibc_page.h
  LN include/bits/uClibc_pthread.h
  LN include/bits/uClibc_stdio.h
  LN include/bits/uClibc_touplow.h
  LN include/bits/uClibc_uintmaxtostr.h
  LN include/bits/uClibc_uwchar.h
  LN include/bits/uClibc_va_copy.h
  LN include/bits/uio.h
  LN include/bits/ustat.h
  LN include/bits/utmp.h
  LN include/bits/utmpx.h
  LN include/bits/utsname.h
  LN include/bits/waitflags.h
  LN include/bits/waitstatus.h
  LN include/bits/wchar.h
  LN include/bits/xopen_lim.h
  LN include/bits/arm_asm.h
  LN include/bits/armsigctx.h
  LN include/bits/endian.h
  LN include/bits/fcntl.h
  LN include/bits/fenv.h
  LN include/bits/huge_val.h
  LN include/bits/kernel_stat.h
  LN include/bits/kernel_types.h
  LN include/bits/mathdef.h
  LN include/bits/setjmp.h
  LN include/bits/shm.h
  LN include/bits/sigcontextinfo.h
  LN include/bits/stackinfo.h
  LN include/bits/syscalls.h
  LN include/bits/uClibc_arch_features.h
  LN include/bits/wordsize.h
  LN include/sys/acct.h
  LN include/sys/epoll.h
  LN include/sys/inotify.h
  LN include/sys/prctl.h
  LN include/sys/ptrace.h
  LN include/sys/timerfd.h
  LN include/sys/elf.h
  LN include/sys/io.h
  LN include/sys/procfs.h
  LN include/sys/ucontext.h
  LN include/sys/user.h
  AS lib/crt1.o
  AS lib/Scrt1.o
  AS lib/crti.o
  AS lib/crtn.o
/tmp/ccrkwOvN.s: Assembler messages:
/tmp/ccrkwOvN.s: Error: .size expression for _init does not evaluate to a constant
/tmp/ccrkwOvN.s: Error: .size expression for _fini does not evaluate to a constant
make: *** [lib/crtn.o] Error 1
clfs@chinmaya:/mnt/clfs/sources/uClibc-0.9.31$  
```I 've seen this bug being resolved [here (click)]("http://manulix.wikidot.com/build-howto#toc11").
However it is for PowerPC but my requirement is on ARM. I could not know how to apply that patch in ARM as I don't know on which files that patch should be applied. And this patch is actually for **binutils 2.21.1**! 

Can anybody plz help me.. I has been a week that I could not resolve this issue. I tried in #cross-lfs channel but I could not get apt ideas.

Thanks,
Chinmaya

---

### Post by chinmaya_n on 2011-10-16
Bump!
Bump!
Bump!

---

### Post by chinmaya_n on 2011-10-19
Got the thing resolved as said in the patch by removing the lines
> .size   _init, .-_init
.size   _fini, .-_fini

from **uClibc-0.9.31/libc/sysdeps/linux/arm/crtn.S**

Thanks,
Chinmaya

---

