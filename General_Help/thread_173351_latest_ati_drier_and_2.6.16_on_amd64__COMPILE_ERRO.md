---
title: "latest ati drier and 2.6.16 on amd64  COMPILE ERROR"
date: 2006-05-10
forum: General Help
---

### Post by flapane on 2006-05-10
I ca't manage to compile fglrx module, as I get tons of errors. Any guess?

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating 
kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.16-flap/build 
SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-2.6.16.14'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function '__fgl_agp_init':
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:8175: warning: 'pm_register' 
is deprecated (declared at include/linux/pm_legacy.h:16)
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function 
'__fgl_agp_cleanup':
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:8185: warning: 
'pm_unregister_all' is deprecated (declared at include/linux/pm_legacy.h:26)
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:6079: warning: 
'ati_gart_base' defined but not used
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
In file included from 
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:162:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:274:5: warning: 
"FIREGL_VMA_INFO" is not defined
In file included from /lib/modules/fglrx/build_mod/2.6.x/drm_proc.h:41,
                 from 
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:333:
/lib/modules/fglrx/build_mod/2.6.x/drmP.h:561:5: warning: "__HAVE_VBL_IRQ" 
is not defined
/lib/modules/fglrx/build_mod/2.6.x/drmP.h:664:5: warning: "__HAVE_VBL_IRQ" 
is not defined
/lib/modules/fglrx/build_mod/2.6.x/drmP.h:936:5: warning: "__HAVE_SG" is not 
defined
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:407:5: warning: 
"FIREGL_VMA_INFO" is not defined
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:426:5: warning: 
"FIREGL_VMA_INFO" is not defined
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function 
'firegl_stub_putminor':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:581: warning: 
'inter_module_put' is deprecated (declared at include/linux/module.h:575)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:583: warning: 
'inter_module_unregister' is deprecated (declared at 
include/linux/module.h:572)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function 
'firegl_stub_register':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:603: warning: 
'inter_module_register' is deprecated (declared at 
include/linux/module.h:571)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:634: warning: 
'inter_module_put' is deprecated (declared at include/linux/module.h:575)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function 
'firegl_put_user_ptr':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1317: warning: cast from 
pointer to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1317: warning: cast from 
pointer to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1317: warning: cast from 
pointer to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1317: warning: cast from 
pointer to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function 
'__ke_no_iommu':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2356: error: 'no_iommu' 
undeclared (first use in this function)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2356: error: (Each 
undeclared identifier is reported only once
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2356: error: for each 
function it appears in.)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function 
'__ke_unregister_ioctl32_conversion':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2533: warning: 'return' 
with a value, in function returning void
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3592: warning: 
initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3593: warning: 
initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3594: warning: 
initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3595: warning: 
initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3596: warning: 
initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3597: warning: 
initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3598: warning: 
initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3599: warning: 
initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3601: warning: 
initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3611: warning: function 
declaration isn't a prototype
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function 
'test_inter_module_interface':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3677: warning: 
'inter_module_put' is deprecated (declared at include/linux/module.h:575)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3683: warning: 
'inter_module_put' is deprecated (declared at include/linux/module.h:575)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function 
'__ke_agp_allocate_memory_phys_list':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3941: warning: passing 
argument 3 of 'im_fglrx_agp_stub->allocate_memory_phys_list' makes integer 
from pointer without a cast
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function 
'__ke_agp_bind_memory':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3980: warning: passing 
argument 1 of 'im_fglrx_agp_stub->bind_memory' from incompatible pointer 
type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function 
'__ke_agp_unbind_memory':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3993: warning: passing 
argument 1 of 'im_fglrx_agp_stub->unbind_memory' from incompatible pointer 
type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function 
'__ke_smp_call_function':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:4222: warning: statement 
with no effect
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.16.14'
make: *** [kmod_build] Error 2
build failed with return value 2
[Error] Kernel Module : Failed to compile kernel module - please consult 
readme.

---

