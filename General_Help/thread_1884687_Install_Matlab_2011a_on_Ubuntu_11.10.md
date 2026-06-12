---
title: "Install Matlab 2011a on Ubuntu 11.10"
date: 2011-11-21
forum: General Help
---

### Post by MirceaAN on 2011-11-21
Hello ppl,

I'm having some troubles launching Matlab on my Ubuntu 11.10 system.

I used the method explained on the Ubuntu Community ([https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)) end I managed to finish the installation and activation with no errors. But after that I can't start the program. I used the commands to create the launcher but when I press the icon in the Application window nothing happens.


Can anyone give me some informations pls. I don't want to go back to windows.

---

### Post by 3Miro on 2011-11-21
Lets first check to see if Matlab works at all. Open a Terminal (search for it in the Unity menu) and then go to:
```
cd /usr/local/MATLAB/R2011a/bin
```
then start it with
```
./matlab
```
Note that R2011a may be different depending on the version that you had.

Let me know if this starts or if you get some sort of an error.

---

### Post by San_SS! on 2011-11-21
What happens to me is that I can run Matlab from the terminal. But if I launch it from the dmenu (I'm using xmonad) it won't work.

I've been trying to figure out why without success.

---

### Post by MirceaAN on 2011-11-21
> **3Miro said:**
> Lets first check to see if Matlab works at all. Open a Terminal (search for it in the Unity menu) and then go to:
```
cd /usr/local/MATLAB/R2011a/bin
```
then start it with
```
./matlab
```
Note that R2011a may be different depending on the version that you had.

Let me know if this starts or if you get some sort of an error.

Perfect... Now starts from the code but not from unity..

---

### Post by Crazyboyy on 2012-01-31
Can any one help me through the installation of matlab 2011a in ubuntu 11.10

Actually I completed the installation and started the matlab but its crashed here is the dump file



------------------------------------------------------------------------
          std::terminate() detected at Wed Feb  1 01:39:09 2012
------------------------------------------------------------------------

Configuration:
  Crash Decoding  : Disabled
  Current Visual  : 0x23 (class 4, depth 24)
  Default Encoding: UTF-8
  GNU C Library   : 2.13 stable
  MATLAB License  : 161052
  MATLAB Root     : /usr/local/MATLAB/R2011a
  MATLAB Version  : 7.12.0.635 (R2011a)
  Operating System: Linux 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 i686
  Processor ID    : x86 Family 6 Model 5 Stepping 5, GenuineIntel
  Virtual Machine : Java 1.6.0_17-b04 with Sun Microsystems Inc. Java HotSpot(TM) Client VM mixed mode
  Window System   : The X.Org Foundation (11004000), display :0

Fault Count: 1



Abnormal termination:
std::terminate()

Register State (captured):
  EAX = 00000000  EBX = 00cd0b58
  ECX = 00000a0a  EDX = 0775aa10
  ESP = 0775a620  EBP = 0775a798
  ESI = 0775aba8  EDI = 00ce14bc

  EIP = 00cb14c9  EFL = 008b3979

   CS = 0775a748   DS = 00000000   SS = 00c481a0
   ES = 00000000   FS = 00000000   GS = 00c451f0


Stack Trace (captured):
[  0] 0x00cb1099 /usr/local/MATLAB/R2011a/bin/glnx86/../../bin/glnx86/libmwfl.so+00450713 fl::sysdep::linux::unwind_stack(void const**, unsigned int, unsigned int, fl::diag::thread_context const&)+000036
[  1] 0x00c6224a /usr/local/MATLAB/R2011a/bin/glnx86/../../bin/glnx86/libmwfl.so+00127562 fl::diag::stacktrace_base::capture(fl::diag::thread_context const&, unsigned int)+000180
[  2] 0x00c6c473 /usr/local/MATLAB/R2011a/bin/glnx86/../../bin/glnx86/libmwfl.so+00169075
[  3] 0x00c6c845 /usr/local/MATLAB/R2011a/bin/glnx86/../../bin/glnx86/libmwfl.so+00170053 fl::diag::terminate_log(char const*, fl::diag::thread_context const&, bool)+000115
[  4] 0x0044fa0f /usr/local/MATLAB/R2011a/bin/glnx86/../../bin/glnx86/libmwmcr.so+00375311 fl::diag::terminate_log(char const*, ucontext const*, bool)+000096
[  5] 0x0044c8a6 /usr/local/MATLAB/R2011a/bin/glnx86/../../bin/glnx86/libmwmcr.so+00362662
[  6] 0x0044e56e /usr/local/MATLAB/R2011a/bin/glnx86/../../bin/glnx86/libmwmcr.so+00370030
[  7] 0x0044f2db /usr/local/MATLAB/R2011a/bin/glnx86/../../bin/glnx86/libmwmcr.so+00373467
[  8] 0x005230a5 /usr/local/MATLAB/R2011a/bin/glnx86/../../sys/os/glnx86/libstdc++.so.6+00741541
[  9] 0x005230e2 /usr/local/MATLAB/R2011a/bin/glnx86/../../sys/os/glnx86/libstdc++.so.6+00741602
[ 10] 0x0052321a /usr/local/MATLAB/R2011a/bin/glnx86/../../sys/os/glnx86/libstdc++.so.6+00741914
[ 11] 0x00150681 /usr/local/MATLAB/R2011a/bin/glnx86/../../bin/glnx86/libmx.so+00263809
[ 12] 0x0015095f /usr/local/MATLAB/R2011a/bin/glnx86/../../bin/glnx86/libmx.so+00264543 mxErrMsgIdAndTxt(char const*, char const*, ...)+000043
[ 13] 0x001cf8c0 /usr/local/MATLAB/R2011a/bin/glnx86/../../bin/glnx86/libmwservices.so+00243904
[ 14] 0x001d157f /usr/local/MATLAB/R2011a/bin/glnx86/../../bin/glnx86/libmwservices.so+00251263 svGetPreferencesDirectory(bool)+000088
[ 15] 0x008cb2ce /usr/local/MATLAB/R2011a/bin/glnx86/libnativeservices.so+00004814 Java_com_mathworks_services_Prefs_nativeGetPreferencesDirectory+000035
[ 16] 0xb2361f4d /usr/local/MATLAB/R2011a/bin/glnx86/libnativeservices.so+2980675405
[ 17] 0xb235ae67 /usr/local/MATLAB/R2011a/bin/glnx86/libnativeservices.so+2980646503
[ 18] 0xb235ae67 /usr/local/MATLAB/R2011a/bin/glnx86/libnativeservices.so+2980646503
[ 19] 0xb235afcd /usr/local/MATLAB/R2011a/bin/glnx86/libnativeservices.so+2980646861
[ 20] 0xb23582cc /usr/local/MATLAB/R2011a/bin/glnx86/libnativeservices.so+2980635340
[ 21] 0xb456b740 /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/client/libjvm.so+02176832
[ 22] 0xb467f158 /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/client/libjvm.so+03305816
[ 23] 0xb456b59f /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/client/libjvm.so+02176415
[ 24] 0xb45482d6 /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/client/libjvm.so+02032342
[ 25] 0xb4547010 /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/client/libjvm.so+02027536
[ 26] 0xb4546358 /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/client/libjvm.so+02024280
[ 27] 0xb45e2006 /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/client/libjvm.so+02662406
[ 28] 0xb45e7aed /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/client/libjvm.so+02685677
[ 29] 0xb45c9ba2 /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/client/libjvm.so+02562978 JVM_FindClassFromClassLoader+000194
[ 30] 0x0221e246 /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/libjava.so+00045638 Java_java_lang_Class_forName0+000278
[ 31] 0xb2361f4d /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/libjava.so+2954161997
[ 32] 0xb235ae67 /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/libjava.so+2954133095
[ 33] 0xb235ae67 /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/libjava.so+2954133095
[ 34] 0xb235afcd /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/libjava.so+2954133453
[ 35] 0xb23582cc /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/libjava.so+2954121932
[ 36] 0xb456b740 /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/client/libjvm.so+02176832
[ 37] 0xb467f158 /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/client/libjvm.so+03305816
[ 38] 0xb456b59f /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/client/libjvm.so+02176415
[ 39] 0xb459b7a3 /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/client/libjvm.so+02373539
[ 40] 0xb458bcc0 /usr/local/MATLAB/R2011a/sys/java/jre/glnx86/jre/lib/i386/client/libjvm.so+02309312
[ 41] 0x00366aad /usr/local/MATLAB/R2011a/bin/glnx86/../../bin/glnx86/libmwjmi.so+00215725
[ 42] 0x003665d6 /usr/local/MATLAB/R2011a/bin/glnx86/../../bin/glnx86/libmwjmi.so+00214486
[ 43] 0x00352285 /usr/local/MATLAB/R2011a/bin/glnx86/../../bin/glnx86/libmwjmi.so+00131717 mljInit()+000025
[ 44] 0x00425c05 /usr/local/MATLAB/R2011a/bin/glnx86/../../bin/glnx86/libmwmcr.so+00203781
[ 45] 0x00419e6a /usr/local/MATLAB/R2011a/bin/glnx86/../../bin/glnx86/libmwmcr.so+00155242
[ 46] 0x0041a067 /usr/local/MATLAB/R2011a/bin/glnx86/../../bin/glnx86/libmwmcr.so+00155751
[ 47] 0x006d8d31                /lib/i386-linux-gnu/libpthread.so.0+00027953
[ 48] 0x007bf0ce                      /lib/i386-linux-gnu/libc.so.6+00860366 clone+000094



If this problem is reproducible, please submit a Service Request via:
    [http://www.mathworks.com/support/contact_us/](http://www.mathworks.com/support/contact_us/)

A technical support engineer might contact you with further information.

Thank you for your help.

---

