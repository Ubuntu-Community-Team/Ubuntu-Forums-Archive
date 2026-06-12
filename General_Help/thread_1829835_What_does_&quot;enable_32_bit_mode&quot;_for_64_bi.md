---
title: "What does &quot;enable 32 bit mode&quot; for 64 bit OS mean?"
date: 2011-08-20
forum: General Help
---

### Post by Asoka2 on 2011-08-20
I'm posting here first because I am new to Ubuntu, so please advise if there is a more appropriate forum. An application (AccuRev) I am installing on a 64 bit Ubuntu laptop is calling for me to verify that my 64 bit kernel has its "32 bit mode enabled". Can anyone tell me what such a mode on a 64 bit OS is? I thought all binaries ran for whatever target platform (32/64 bit) they were compiled for. It is also calling for glibc to be installed, and I understand that it goes by different name 'libc6', so I was thinking (assuming the name change is true) of simply creating a link glibc->libc6 to trick the app into using the libc6 file, but I don't know where they are located. The files I found with the libc6 in their names had longer names, and I don't know which one was the desired file. So am I just not savvy to the naming convention, or is my idea of creating a link just wrong? Thnx

---

### Post by 3Miro on 2011-08-20
All modern AMD and Intel CPUs can switch between 64 and 32-bit mode (with 64-bit OS). This means that you can run 32-bit apps on 64-bit OS (this holds for both Linux and Windows, not sure about Mac).

The Ubuntu kernel is properly configured for 32/64-bit compatibility.

However, applications do need system libraries compiled for their architecture. This many applications would require whole bunch of 32-bit libraries.

Open Synaptic Package Manager (in System -> Admin if you are using Gnome interface) and then look for
```
ia32-libs
```
Install the package (it will install a whole bunch of stuff) and then you should be able to run your app.

---

### Post by Asoka2 on 2011-08-21
> **3Miro said:**
> All modern AMD and Intel CPUs can switch between 64 and 32-bit mode (with 64-bit OS). This means that you can run 32-bit apps on 64-bit OS (this holds for both Linux and Windows, not sure about Mac).

The Ubuntu kernel is properly configured for 32/64-bit compatibility.

However, applications do need system libraries compiled for their architecture. This many applications would require whole bunch of 32-bit libraries.

Open Synaptic Package Manager (in System -> Admin if you are using Gnome interface) and then look for
```
ia32-libs
```Install the package (it will install a whole bunch of stuff) and then you should be able to run your app.

Found ia32-libs, thnx 3Miro.

---

### Post by 3Miro on 2011-08-21
If that solves your problem, please mark the thread as [Solved], it helps us keep track.

---

