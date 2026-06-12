---
title: "undefined reference error when compiling"
date: 2010-09-09
forum: General Help
---

### Post by tdnghia89 on 2010-09-09
Hi, when i compile Borealis, this error come up:

```

/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `vtable for __cxxabiv1::__vmi_class_type_info@CXXABI_1.3'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `__cxa_begin_catch@CXXABI_1.3'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `operator delete[](void*)@GLIBCXX_3.4'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `operator new(unsigned int)@GLIBCXX_3.4'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `typeinfo for int@CXXABI_1.3'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `__cxa_pure_virtual@CXXABI_1.3'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `vtable for __cxxabiv1::__class_type_info@CXXABI_1.3'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `__cxa_guard_abort@CXXABI_1.3'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `__cxa_free_exception@CXXABI_1.3'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `__gxx_personality_v0@CXXABI_1.3'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `__cxa_guard_acquire@CXXABI_1.3'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `__cxa_throw@CXXABI_1.3'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `vtable for __cxxabiv1::__si_class_type_info@CXXABI_1.3'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `operator delete(void*)@GLIBCXX_3.4'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `__cxa_allocate_exception@CXXABI_1.3'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `operator new[](unsigned int)@GLIBCXX_3.4'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `__cxa_guard_release@CXXABI_1.3'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `__cxa_rethrow@CXXABI_1.3'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `__cxa_end_catch@CXXABI_1.3'
/home/nghiatran/external-packages/xerces/lib/libxerces-c.so: undefined reference to `vtable for __cxxabiv1::__enum_type_info@CXXABI_1.3'
collect2: ld returned 1 exit status

```I use GCC4.1.1, Xerces 2.7.0. 
I search around but cannot find the fix. Can somebody give some advice ? I really appreciate your help.

---

### Post by spjackson on 2010-09-09
Did you compile libxerces-c.so yourself?[FONT=monospace] It looks like it has been built with g++ 3.4.x
[/FONT]

---

