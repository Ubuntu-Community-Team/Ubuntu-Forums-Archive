---
title: "Linux Memory Management - inexplicable behavior"
date: 2012-07-23
forum: General Help
---

### Post by meber on 2012-07-23
Hello, 
during the execution of my self-developed application (C++/OpenGL 3D terrain visualization, embedded, current Ubuntu kernel) I observe the following inexplicable behavior: the viewer spins around -> the application hangs frequently (the rotation speed has no effect) - the application hangs on an OpenGL call (glDrawElements() of a triangle strip with texture coordinates) - interesting and for me inexplicable is the output of the used/allocated memory - "top": VIRT (~215m) and RES (~190m) are nearly constant during the execution time (vary by ~ 5m), but the SHR-memory increases during the execution from ~40m to ~120m, the application runs until a SHR-memory of ~120m -> the application hangs, subsequently the SHR-memory is decreased to ~40m and the applications runs again until the next hang (SHR-memory ~40m) and so on. During the described execution time no new data is loaded, all data is already cached.
 
What is the reason for the app-hang? Why is allocated SHR memory increased/decreased continuously - there is enough free memory available during the entire execution time? What can I do - so that the application is running without the described hangs?
 
Thanks for your advice and help
Markus

---

