---
title: "Wine: Failed to load opengl32"
date: 2012-02-22
forum: General Help
---

### Post by M@s on 2012-02-22
Hi!

I'm trying to launch a program through Wine, but I only get this message:

```
wine 'MPK MINI Editor.exe'
err:module:load_builtin_dll failed to load .so lib for builtin L"OPENGL32.dll": libGL.so.1: cannot open shared object file: No such file or directory
err:module:import_dll d Loading library OPENGL32.dll (which is needed by L"Z:\\home\\mats\\apps\\MPK MINI Editor .13\\MPK MINI Editor.exe") faile(error c000007a).
err:module:load_builtin_dll failed to load .so lib for builtin L"GLU32.dll": libGL.so.1: cannot open shared object file: No such file or directory
err:module:import_dll Loading library GLU32.dll (which is needed by L"Z:\\home\\mats\\apps\\MPK MINI Editor .13\\MPK MINI Editor.exe") failed (error c000007a).
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\mats\\apps\\MPK MINI Editor .13\\MPK MINI Editor.exe" failed, status c0000135

```

I'm using Ubuntu 11.10 64-bit on an Asus U36SD, and have done som tweaking for [Desktop Effects]("https://help.ubuntu.com/community/Asus_U36SD") to work:
> Create a new file /etc/modprobe.d/blacklist-nvidia.conf with the following content. (You need super user privileges. See here for help.

```
blacklist nouveau
blacklist nvidia
```
Remove nvidia drivers (otherwise it's libGL.so will used by default) by running the following command
```
sudo apt-get purge nvidia-current
```
Don't know if this could have something to do with the error?

---

