---
title: "linux binary dependency"
date: 2010-07-06
forum: General Help
---

### Post by mayapower on 2010-07-06
[FONT=Courier, Monospaced]Hi, 
 [/FONT][FONT=Courier, Monospaced]I am  writing a python package deployment tool for linux based 
 platforms. I have tried various existing tool sets but none of them is up to the mark and they have their  own issues.
 [/FONT]
[FONT=Courier, Monospaced]The  function that collects all the dependencies of python(*.so) 
 modules give me a huge list. 
 [/FONT]```

[FONT=Courier, Monospaced][U]/lib/libgcc_s.so.1
/lib/tls/i686/cmov/libc.so.6
/lib/tls/i686/cmov/libdl.so.2
/lib/tls/i686/cmov/libm.so.6
/lib/tls/i686/cmov/libpthread.so.0
/lib/tls/i686/cmov/librt.so.1
/lib/tls/i686/cmov/libutil.so.1
/usr/lib/libICE.so.6
/usr/lib/libSM.so.6
/usr/lib/libX11.so.6
/usr/lib/libXau.so.6
/usr/lib/libXcomposite.so.1
/usr/lib/libXcursor.so.1
/usr/lib/libXdamage.so.1
/usr/lib/libXdmcp.so.6
/usr/lib/libXext.so.6
/usr/lib/libXfixes.so.3
/usr/lib/libXi.so.6
/usr/lib/libXinerama.so.1
/usr/lib/libXrandr.so.2
/usr/lib/libXrender.so.1
/usr/lib/libatk-1.0.so.0
/usr/lib/libexpat.so.1
/usr/lib/libfontconfig.so.1
/usr/lib/libfreetype.so.6
/usr/lib/libgdk-x11-2.0.so.0
/usr/lib/libgdk_pixbuf-2.0.so.0
/usr/lib/libglib-2.0.so.0
/usr/lib/libgmodule-2.0.so.0
/usr/lib/libgobject-2.0.so.0
/usr/lib/libgthread-2.0.so.0
/usr/lib/libgtk-x11-2.0.so.0
/usr/lib/libpango-1.0.so.0
/usr/lib/libpangocairo-1.0.so.0
/usr/lib/libpangoft2-1.0.so.0
/usr/lib/libpcre.so.3
/usr/lib/libpng12.so.0
/usr/lib/libstdc++.so.6
/usr/lib/libxcb-xlib.so.0
/usr/lib/libxcb.so.1
/usr/lib/libz.so.1
/usr/local/lib/libcairo.so.2
/usr/local/lib/libpixman-1.so.0
/usr/local/lib/libpython2.6.so.1.0
/usr/local/lib/libwx_gtk2u-2.8.so.0
[/U][/FONT]

```[FONT=Courier, Monospaced]
 [/FONT]
[FONT=Courier, Monospaced]Is  it really necessary too include all these *.so file along with your package? 
 Special concern is *.so files in 'usr/lib' & 'lib/tls/i686'  directory. 
 It seems there is no specific definition of system wide dlls on linux platforms. Initially I did some tests by deploying a package using pyinstaller  on ubuntu hardy(glibc 2.7) and tried on karmic(glibc 2.11). The list of pulled out dlls is almost the same as mentioned above. The app is running fine. Later I removed all the  libX*.so from the package. Application is still running fine without any problem. One thing that I have noticed that when I have removed all the libX*.so from the package, the rendering of cairo fonts is  better compare to libX*.so of hardy and a slight performance improvement. 
 May be because of libX*.so on karmic are the latest ones and has  some improvements over libX of hardy. 
 [/FONT]
[FONT=Courier, Monospaced]This  is pretty confusing. It's been said that "deploy on older 
 and run on newer" for linux development. The binary's forward  backward compatibility is issue is behind this term. 
 [/FONT]
[FONT=Courier, Monospaced]How  do I sort out this issue? Is it OK to safely ignore all the libs in 'usr/lib' & 'lib/tls/i686' directory? 
 Another solution that comes in my mind is to deploy the python  package as a .deb file. What ever libs you are excluding from you app, add them in .deb installer. This will take care of installing the libs from the repository of distro if in case they are not present. 
 [/FONT]
[FONT=Courier, Monospaced]
[/FONT]
[FONT=Courier, Monospaced]Cheers 
 [/FONT]
[FONT=Courier, Monospaced]
[/FONT]
[FONT=Courier, Monospaced]Prashant[/FONT]

---

