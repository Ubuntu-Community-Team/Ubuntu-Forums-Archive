---
title: "Chrome Crashing"
date: 2011-07-22
forum: General Help
---

### Post by ajack38 on 2011-07-22
When I try to open Chrome it doesn't load.

I went into a terminal and typed:chromium-browser
This started to open chrome again but this time it came up with details about what is failing. This is what came after I typed in "chromium-browser".

```
ashley@Home-Studio:~$ chromium-browser
[3701:3701:5980343201:ERROR:process_singleton_linux.cc(240)] readlink(/home/ashley/.config/chromium/SingletonLock) failed: Invalid argument
[3701:3701:5980343337:ERROR:process_singleton_linux.cc(240)] readlink(/home/ashley/.config/chromium/SingletonLock) failed: Invalid argument
[3701:3701:5980343359:ERROR:process_singleton_linux.cc(264)] Failed to create /home/ashley/.config/chromium/SingletonLock: File exists
[3701:3701:5980343406:ERROR:process_singleton_linux.cc(240)] readlink(/home/ashley/.config/chromium/SingletonLock) failed: Invalid argument
[3701:3701:5980343431:ERROR:browser_main.cc(1444)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption.

```

Does anyone know how to fix this? Is there a Terminal code that I could Invoke to Reset/Reconfigure these files?

Thanks in Advance.

---

