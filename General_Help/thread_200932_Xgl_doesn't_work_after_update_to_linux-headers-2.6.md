---
title: "Xgl doesn't work after update to linux-headers-2.6.15-25"
date: 2006-06-21
forum: General Help
---

### Post by jaywhy13 on 2006-06-21
I did an update tonight and now Xgl doesn't work
I had to reinstall the ATI drivers, after setting the symlink in /usr/src/ to point to the new linux-headers.

I have gone back through most of the tutorials and am now running low on suggestions.

What worked for me, was creating a .Xsession file that starts Xgl, hence making ur default session Xgl-ified. Xorg confirmed unchanged. Funny thing is, when I check ps -e | grep, I find that both compiz and Xgl are running. But I don't get the normal effects that u get wit Xgl. 

Open 2 ideas... anyone.

I think my fglrx installation had errors though... here is the /usr/share/fglrx/fglrx-install.log file:

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.15-25-386/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-25-386'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function &#8216;__fgl_agp_init&#8217;:
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:8175: warning: &#8216;pm_register&#8217; is deprecated (declared at include/linux/pm_legacy.h:16)
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function &#8216;__fgl_agp_cleanup&#8217;:
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:8185: warning: &#8216;pm_unregister_all&#8217; is deprecated (declared at include/linux/pm_legacy.h:26)
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:6079: warning: &#8216;ati_gart_base&#8217; defined but not used
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
In file included from /lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:162:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:274:5: warning: "FIREGL_VMA_INFO" is not defined
In file included from /lib/modules/fglrx/build_mod/2.6.x/drm_proc.h:41,
                 from /lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:333:
/lib/modules/fglrx/build_mod/2.6.x/drmP.h:561:5: warning: "__HAVE_VBL_IRQ" is not defined
/lib/modules/fglrx/build_mod/2.6.x/drmP.h:664:5: warning: "__HAVE_VBL_IRQ" is not defined
/lib/modules/fglrx/build_mod/2.6.x/drmP.h:936:5: warning: "__HAVE_SG" is not defined
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:407:5: warning: "FIREGL_VMA_INFO" is not defined
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:426:5: warning: "FIREGL_VMA_INFO" is not defined
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function &#8216;firegl_stub_putminor&#8217;:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:581: warning: &#8216;inter_module_put&#8217; is deprecated (declared at include/linux/module.h:575)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:583: warning: &#8216;inter_module_unregister&#8217; is deprecated (declared at include/linux/module.h:572)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function &#8216;firegl_stub_register&#8217;:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:603: warning: &#8216;inter_module_register&#8217; is deprecated (declared at include/linux/module.h:571)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:634: warning: &#8216;inter_module_put&#8217; is deprecated (declared at include/linux/module.h:575)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3592: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3593: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3594: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3595: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3596: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3597: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3598: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3599: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3601: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3611: warning: function declaration isn&#8217;t a prototype
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function &#8216;test_inter_module_interface&#8217;:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3677: warning: &#8216;inter_module_put&#8217; is deprecated (declared at include/linux/module.h:575)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3683: warning: &#8216;inter_module_put&#8217; is deprecated (declared at include/linux/module.h:575)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function &#8216;__ke_agp_allocate_memory_phys_list&#8217;:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3941: warning: passing argument 3 of &#8216;im_fglrx_agp_stub->allocate_memory_phys_list&#8217; makes integer from pointer without a cast
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function &#8216;__ke_agp_bind_memory&#8217;:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3980: warning: passing argument 1 of &#8216;im_fglrx_agp_stub->bind_memory&#8217; from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function &#8216;__ke_agp_unbind_memory&#8217;:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3993: warning: passing argument 1 of &#8216;im_fglrx_agp_stub->unbind_memory&#8217; from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function &#8216;__ke_smp_call_function&#8217;:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:4222: warning: statement with no effect
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2256: warning: &#8216;deferred_flush&#8217; defined but not used
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC4.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC4
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25-386'
build succeeded with return value 0
 compiling fglrx_agp.ko module
make -C /lib/modules/2.6.15-25-386/build SUBDIRS=/lib/modules/fglrx/build_mod/firegl_agpgart modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-25-386'
  CC [M]  /lib/modules/fglrx/build_mod/firegl_agpgart/backend.o
In file included from /lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrapper.h:31,
                 from /lib/modules/fglrx/build_mod/firegl_agpgart/backend.c:30:
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.h:176:5: warning: "LINUX_VERSION_CODE" is not defined
/lib/modules/fglrx/build_mod/firegl_agpgart/backend.c: In function &#8216;agp_backend_initialize&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/backend.c:191: warning: passing argument 1 of &#8216;bridge->driver->agp_destroy_page&#8217; makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/firegl_agpgart/backend.c: In function &#8216;agp_backend_cleanup&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/backend.c:216: warning: passing argument 1 of &#8216;__ke_phys_to_virt&#8217; makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/firegl_agpgart/backend.c:216: warning: passing argument 1 of &#8216;bridge->driver->agp_destroy_page&#8217; makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/firegl_agpgart/backend.c: At top level:
/lib/modules/fglrx/build_mod/firegl_agpgart/backend.c:294: warning: &#8216;agp_init&#8217; defined but not used
  CC [M]  /lib/modules/fglrx/build_mod/firegl_agpgart/generic.o
In file included from /lib/modules/fglrx/build_mod/firegl_agpgart/agp.h:32,
                 from /lib/modules/fglrx/build_mod/firegl_agpgart/generic.c:43:
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_agp.h:759:1: warning: "PCI_DEVICE_ID_INTEL_ICH7_1" redefined
In file included from include/linux/pci.h:26,
                 from /lib/modules/fglrx/build_mod/firegl_agpgart/generic.c:34:
include/linux/pci_ids.h:2076:1: warning: this is the location of the previous definition
  CC [M]  /lib/modules/fglrx/build_mod/firegl_agpgart/isoch.o
In file included from /lib/modules/fglrx/build_mod/firegl_agpgart/agp.h:32,
                 from /lib/modules/fglrx/build_mod/firegl_agpgart/isoch.c:10:
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_agp.h:759:1: warning: "PCI_DEVICE_ID_INTEL_ICH7_1" redefined
In file included from include/linux/pci.h:26,
                 from /lib/modules/fglrx/build_mod/firegl_agpgart/isoch.c:6:
include/linux/pci_ids.h:2076:1: warning: this is the location of the previous definition
  CC [M]  /lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.o
In file included from /lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrapper.h:31,
                 from /lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:14:
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.h:176:5: warning: "LINUX_VERSION_CODE" is not defined
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function &#8216;intel_i810_cleanup&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:158: warning: passing argument 1 of &#8216;__ke_iounmap&#8217; discards qualifiers from pointer target type
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function &#8216;i8xx_alloc_pages&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:189: warning: &#8216;page&#8217; is used uninitialized in this function
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function &#8216;intel_i810_free_by_type&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:348: warning: passing argument 1 of &#8216;__ke_phys_to_virt&#8217; makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:348: warning: passing argument 1 of &#8216;i8xx_destroy_pages&#8217; makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:351: warning: passing argument 1 of &#8216;__ke_phys_to_virt&#8217; makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:351: warning: passing argument 1 of &#8216;agp_bridge->driver->agp_destroy_page&#8217; makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:354: warning: implicit declaration of function &#8216;kfree&#8217;
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function &#8216;intel_i830_cleanup&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:564: warning: passing argument 1 of &#8216;__ke_iounmap&#8217; discards qualifiers from pointer target type
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function &#8216;intel_i915_cleanup&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:670: warning: passing argument 1 of &#8216;__ke_iounmap&#8217; discards qualifiers from pointer target type
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:671: warning: passing argument 1 of &#8216;__ke_iounmap&#8217; discards qualifiers from pointer target type
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function &#8216;find_i830&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1526: warning: assignment from incompatible pointer type
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1528: warning: assignment from incompatible pointer type
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function &#8216;agp_intel_probe&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1697: warning: implicit declaration of function &#8216;pci_assign_resource&#8217;
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function &#8216;agp_intel_remove&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1734: warning: passing argument 1 of &#8216;__ke_pci_get_drvdata&#8217; from incompatible pointer type
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function &#8216;agp_intel_resume&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1742: warning: passing argument 1 of &#8216;__ke_pci_get_drvdata&#8217; from incompatible pointer type
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1744:5: warning: "__ke_LINUX_VERSION_CODE" is not defined
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: At top level:
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1814: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1815: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function &#8216;fgl_agp_intel_init&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1827: warning: passing argument 1 of &#8216;__fgl_pci_module_init&#8217; from incompatible pointer type
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function &#8216;fgl_agp_intel_cleanup&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1834: warning: passing argument 1 of &#8216;__fgl_pci_unregister_driver&#8217; from incompatible pointer type
  CC [M]  /lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.o
In file included from /lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrapper.h:31,
                 from /lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:6:
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.h:176:5: warning: "LINUX_VERSION_CODE" is not defined
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c: In function &#8216;agp_ali_probe&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:303: warning: passing argument 1 of &#8216;__ke_pci_find_capability&#8217; from incompatible pointer type
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:331: warning: passing argument 1 of &#8216;__ke_pci_read_config_byte&#8217; from incompatible pointer type
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:363: warning: passing argument 1 of &#8216;__ke_pci_read_config_dword&#8217; from incompatible pointer type
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:367: warning: passing argument 1 of &#8216;__ke_pci_set_drvdata&#8217; from incompatible pointer type
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c: In function &#8216;agp_ali_remove&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:373: warning: passing argument 1 of &#8216;__ke_pci_get_drvdata&#8217; from incompatible pointer type
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c: At top level:
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:396: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:397: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c: In function &#8216;fgl_agp_ali_init&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:403: warning: passing argument 1 of &#8216;__fgl_pci_module_init&#8217; from incompatible pointer type
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c: In function &#8216;fgl_agp_ali_cleanup&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:408: warning: passing argument 1 of &#8216;__fgl_pci_unregister_driver&#8217; from incompatible pointer type
  CC [M]  /lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.o
In file included from /lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c:113:
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_agp.h:759:1: warning: "PCI_DEVICE_ID_INTEL_ICH7_1" redefined
In file included from include/linux/pci.h:26,
                 from /lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c:74:
include/linux/pci_ids.h:2076:1: warning: this is the location of the previous definition
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c:171: error: static declaration of &#8216;errno&#8217; follows non-static declaration
include/linux/unistd.h:4: error: previous declaration of &#8216;errno&#8217; was here
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c: In function &#8216;__ke_phys_to_virt&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c:660: warning: passing argument 1 of &#8216;phys_to_virt&#8217; makes integer from pointer without a cast
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c:660: warning: return makes integer from pointer without a cast
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c: In function &#8216;__ke_verify_area&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c:1123: warning: implicit declaration of function &#8216;verify_area&#8217;
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c: In function &#8216;__ke_get_vm_phys_addr&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c:1362: warning: passing argument 1 of &#8216;pmd_offset&#8217; from incompatible pointer type
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c: In function &#8216;__ke_vm_phys_addr_str&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c:1818: warning: passing argument 1 of &#8216;pmd_offset&#8217; from incompatible pointer type
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c: In function &#8216;__ke_smp_call_function&#8217;:
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c:2252: warning: statement with no effect
make[2]: *** [/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.o] Error 1
make[1]: *** [_module_/lib/modules/fglrx/build_mod/firegl_agpgart] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25-386'
make: *** [default] Error 2
AGPGART module build failed with return value 2
duplicating results into driver repository...
done.
==============================
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel modules
done.

---

### Post by jaywhy13 on 2006-06-25
Has anyone gotten Xgl to work with ati, dapper and **linux-headers-2.6.15-25**?

---

### Post by joshrobinson on 2006-06-25
[QUOTE=jaywhy13]Has anyone gotten Xgl to work with ati, dapper and **linux-headers-2.6.15-25**?[/QUOTE]

works for me, although im using amd64 kernel.. so it is doable.. maybe try reinstalling your ati drivers, and reinstalling compiz and xgl.. its worth a shot

are you using the ati driver from the ati website? or the one in the repos?
i use the one in the repo's and it works fine for me.. the ati installer gives me problems here and there
also make sure you have build-essential and you picked the correct headers

---

### Post by jaywhy13 on 2006-06-26
[QUOTE=joshrobinson]works for me, although im using amd64 kernel.. so it is doable.. maybe try reinstalling your ati drivers, and reinstalling compiz and xgl.. its worth a shot

are you using the ati driver from the ati website? or the one in the repos?
i use the one in the repo's and it works fine for me.. the ati installer gives me problems here and there
also make sure you have build-essential and you picked the correct headers[/QUOTE]

Well... I got Xgl and compiz wont load... I get <defunct> for both of them AND my line in gdm.conf is 
GdmXserverTimeout=25,
I had it at 50 previously... both in /etc/gdm/gdm.conf and /etc/X11/gdm/gdm.conf. ANy suggestions?

---

### Post by den_ on 2006-08-02
Well, I don't think it is a kernel issue. I installed ubuntu (Dapper) as a second distro before about two weeks and xgl worked excellent with linux-686 (that is 2.6.15.24?). Then I installed 2.6.17.6 vanilla, becouse i wanted optimized kernel and main reason was actually that 2.6.15 doesn't work nice with smp on, and xgl worked further without problems.

Yesterday I wrote in root dir "rm -r * /source" =D>. Since then xgl doesn't work at all. Of course i had to reinstall ubuntu. Used the same procedure for xgl installation, than some others things and in short I have spent the whole day trying to set xgl stuff.

ANd yes, i have radeon x600 pro.

---

