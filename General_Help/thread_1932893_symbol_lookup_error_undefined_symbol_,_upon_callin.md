---
title: "symbol lookup error: undefined symbol , upon calling C++ executable from matlab"
date: 2012-02-28
forum: General Help
---

### Post by swagatika on 2012-02-28
Although I faced this problem while using Matlab, I feel this is more an issue with linux:

Upon giving the following command from Matlab command prompt, I get this error:

>>[status, result] = system('./testGEA outDataTest1.txt')

status =

     127

result =

./testGEA: symbol lookup error:  /home/swagatika/softwares/qvision.0.8.0/lib/libqvision.so.0: undefined  symbol: _ZN12QApplication10commitDataER15QSessionManager

testGEA is an executable file compiled using Qvision library (link : [http://qvision.sourceforge.net/testGEA_8cpp.html](http://qvision.sourceforge.net/testGEA_8cpp.html))

I can successfully execute the command from Linux(ubuntu 10.10) terminal, but calling from Matlab fails.

I searched on internet and got to know that I am supposed to apply some commands and here is it:
ldd gives the following:

~/softwares/qvision.0.8.0/lib$ ldd libqvision.so.0
linux-gate.so.1 => (0x00363000)
libgsl.so.0 => /usr/lib/libgsl.so.0 (0x007b6000)
libgslcblas.so.0 => /usr/lib/libgslcblas.so.0 (0x001d0000)
libQtXml.so.4 => /usr/lib/libQtXml.so.4 (0x005cf000)
libQtOpenGL.so.4 => /usr/lib/libQtOpenGL.so.4 (0x00a0a000)
libQtGui.so.4 => /usr/lib/libQtGui.so.4 (0x00fa4000)
libQtCore.so.4 => /usr/lib/libQtCore.so.4 (0x061b1000)
libGLU.so.1 => /usr/lib/libGLU.so.1 (0x00110000)
libGL.so.1 => /usr/lib/mesa/libGL.so.1 (0x00203000)
libpthread.so.0 => /lib/libpthread.so.0 (0x00180000)
libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00c38000)
libm.so.6 => /lib/libm.so.6 (0x0019a000)
libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00256000)
libc.so.6 => /lib/libc.so.6 (0x00612000)
libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00272000)
libdl.so.2 => /lib/libdl.so.2 (0x001c0000)
libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00af6000)
libX11.so.6 => /usr/lib/libX11.so.6 (0x00364000)
libQtDBus.so.4 => /usr/lib/libQtDBus.so.4 (0x004c0000)
libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x002e9000)
libaudio.so.2 => /usr/lib/libaudio.so.2 (0x00319000)
libglib-2.0.so.0 => /lib/libglib-2.0.so.0 (0x00b00000)
libpng12.so.0 => /lib/libpng12.so.0 (0x00330000)
libz.so.1 => /lib/libz.so.1 (0x00481000)
libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x0053b000)
libSM.so.6 => /usr/lib/libSM.so.6 (0x001c4000)
libICE.so.6 => /usr/lib/libICE.so.6 (0x0057e000)
libXext.so.6 => /usr/lib/libXext.so.6 (0x00597000)
libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0x00355000)
librt.so.1 => /lib/librt.so.1 (0x0035a000)
libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00496000)
libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x0049a000)
libXxf86vm.so.1 => /usr/lib/libXxf86vm.so.1 (0x005a7000)
libdrm.so.2 => /lib/libdrm.so.2 (0x005ad000)
/lib/ld-linux.so.2 (0x004a2000)
libxcb.so.1 => /usr/lib/libxcb.so.1 (0x0076f000)
libexpat.so.1 => /lib/libexpat.so.1 (0x00789000)
libXt.so.6 => /usr/lib/libXt.so.6 (0x009a3000)
libXau.so.6 => /usr/lib/libXau.so.6 (0x005b7000)
libpcre.so.3 => /lib/libpcre.so.3 (0x00bcf000)
libuuid.so.1 => /lib/libuuid.so.1 (0x005bb000)
libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x005c0000)

I also used nm which gives U which means that the symbol is undefined.

$ nm -D /home/swagatika/softwares/qvision.0.8.0/lib/libqvision.so.0 | grep _ZN12QApplication10commitDataER15QSessionManager
U _ZN12QApplication10commitDataER15QSessionManager

I do not have much knowledge about the linux commands, so please give suggestions with details if possible...

Thanks

---

