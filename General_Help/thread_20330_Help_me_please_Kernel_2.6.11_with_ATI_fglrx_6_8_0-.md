---
title: "Help me please Kernel 2.6.11 with ATI fglrx_6_8_0-8.10.19-1.i386.rpm"
date: 2005-03-16
forum: General Help
---

### Post by hamlo on 2005-03-16
While i compile the driver module for kernel 2.6.11 i see:

ATI module generator V 2.0
==========================
initializing...
build_date =&#1095;&#1060;&#1058; &#1085;&#1041;&#1058; 15 22:08:08 PST 2005
uname -a =Linux darkstar 2.6.11 #3 Tue Mar 15 21:52:11 PST 2005 i686 unknown unknown GNU/Linux
uname -s =Linux
uname -m =i686
uname -r =2.6.11
uname -v =#3 Tue Mar 15 21:52:11 PST 2005
uid=0(root) gid=0(root) groups=0(root),1(bin),2(daemon),3(sys),4(adm),6(disk),10(wheel),11(floppy)
.
drwxr-xr-x  100 root root 10360 2005-03-15 21:46 /usr/include
.
total 2
drwxr-xr-x   2 root root  128 2005-03-15 21:46 ATI
lrwxrwxrwx   1 root root   12 2004-12-11 01:36 linux -> linux-2.4.27
drwxr-xr-x  15 root root  616 2004-12-11 01:37 linux-2.4.27
drwxr-xr-x  19 root root 1352 2005-03-15 21:52 linux-2.6.x
drwxr-xr-x   7 root root  168 2003-10-28 22:08 rpm
drwxr-xr-x   2 root root  176 2004-09-16 16:11 speakup-2.4.27
.
file /lib/modules/2.6.11/build/include/linux/agp_backend.h says: AGP=1
file /proc/kallsyms says: SMP=1
assuming default: MODVERSIONS=0
.
CC=gcc
cc_version=3.3.4
found major but not minor version match for gcc and the ip-library
ls -l ./libfglrx_ip.a
lrwxrwxrwx  1 root root 20 2005-03-15 22:08 ./libfglrx_ip.a -> ./libfglrx_ip.a.GCC3
.
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
def_vma_api_version=-DFGL_LINUX253P1_VMA_API
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.11/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-2.6.x'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function `agp_find_supported_device':
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:6526: warning: unused variable `cap_ptr'
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function `__fgl_agp_init':
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:7611: warning: `pm_register' is deprecated (declared at include/linux/pm.h:106)
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function `__fgl_agp_cleanup':
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:7621: warning: `pm_unregister_all' is deprecated (declared at include/linux/pm.h:116)
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:6507: warning: `agp_check_supported_device' defined but not used
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_putminor':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:509: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:511: warning: `inter_module_unregister' is deprecated (declared at include/linux/module.h:574)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_register':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:531: warning: `inter_module_register' is deprecated (declared at include/linux/module.h:573)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:562: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_get_vm_phys_addr':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1673: warning: passing arg 1 of `pmd_offset' from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `do_vm_shm_nopage':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2203: warning: passing arg 1 of `pmd_offset' from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_vm_phys_addr_str':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2573: warning: passing arg 1 of `pmd_offset' from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2661: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_vm_map':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2722: warning: implicit declaration of function `remap_page_range'
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2875: error: parse error before '*' token
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2875: warning: type defaults to `int' in declaration of `drm_agp_module_stub'
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2875: warning: data definition has no type or storage class
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agpgart_available':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3017: error: `drm_agp_t' undeclared (first use in this function)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3017: error: (Each undeclared identifier is reported only once
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3017: error: for each function it appears in.)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3017: error: parse error before ')' token
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3038: error: request for member `free_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3040: error: request for member `free_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3043: error: request for member `allocate_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3045: error: request for member `allocate_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3048: error: request for member `bind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3050: error: request for member `bind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3053: error: request for member `unbind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3055: error: request for member `unbind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3058: error: request for member `enable' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3060: error: request for member `enable' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3063: error: request for member `acquire' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3065: error: request for member `acquire' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3068: error: request for member `release' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3070: error: request for member `release' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3073: error: request for member `copy_info' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3075: error: request for member `copy_info' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_uninit':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3146: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_free_memory':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3179: error: request for member `free_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3180: error: request for member `free_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_allocate_memory':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3189: error: request for member `allocate_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3190: error: request for member `allocate_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_bind_memory':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3200: error: request for member `bind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3201: error: request for member `bind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_unbind_memory':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3211: error: request for member `unbind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3212: error: request for member `unbind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_enable':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3222: error: request for member `enable' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3224: error: request for member `enable' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_acquire':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3270: error: request for member `acquire' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3271: error: request for member `acquire' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_release':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3281: error: request for member `release' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3282: error: request for member `release' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_copy_info':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3295: error: request for member `copy_info' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3302: error: request for member `copy_info' in something not a structure or union
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.x'
make: *** [kmod_build] Error 2
build failed with return value 2 

What is wrong...

---

### Post by pagefault on 2005-03-16
The current module is not compatible with the 2.6.11 kernel. You need to apply patches. I have not done this myself (still using 2.6.10) but you can find the info you need here.

[http://www.rage3d.com/board/showthread.php?t=33806492](http://www.rage3d.com/board/showthread.php?t=33806492)

---

