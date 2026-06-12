---
title: "Libgtk1.2 Woes"
date: 2010-10-24
forum: General Help
---

### Post by Piro24 on 2010-10-24
Hello all.

I'm trying to get epsxe to work. Naturally, it didn't. This is the output from the command line.

```

patrick@GW-LPTP:~/Downloads/epsxe160lin$ ./epsxe
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
patrick@GW-LPTP:~/Downloads/epsxe160lin$ sudo apt-get install libgtk1.2-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk1.2-common is already the newest version.

```

As you can see, I tried installing libgtk1.2-common in order to resolve the issue, but that didn't help. Any ideas? Is there perhaps a way that I could find and point out to epsxe where to find libgtk-1.2.so.0? 

Thanks in advance to anyone who helps. I'm running XUbuntu 10.04, but that shouldnt be the issue...

---

### Post by Piro24 on 2010-10-24
Shameless Bump.

---

### Post by WorMzy on 2010-10-24
You'll need to install [libgtk1.2]("http://packages.ubuntu.com/jaunty/amd64/libgtk1.2/filelist"), not libgtk1.2-common. However, this package is only available on Jaunty, Hardy, and Dapper. Since you were able to install libgtk1.2-common, I assume you must be using one of these anyway.

---

### Post by Piro24 on 2010-10-24
> **WorMzy said:**
> You'll need to install [libgtk1.2]("http://packages.ubuntu.com/jaunty/amd64/libgtk1.2/filelist"), not libgtk1.2-common. However, this package is only available on Jaunty, Hardy, and Dapper. Since you were able to install libgtk1.2-common, I assume you must be using one of these anyway.

Nope, I'm using 10.04 (Lucid Lynx, I believe). Trying to install libgtk1.2 gives me this

```

Error: Dependency is not satisfiable: libglib1.2ldbl (>= 1.2.10-18)

```.

Am I out of luck here?

---

### Post by WorMzy on 2010-10-24
I'm guessing that you're manually downloading and installing these packages? Well, libglib1.2ldbl is [also in the repos]("http://packages.ubuntu.com/jaunty/libglib1.2ldbl").

---

### Post by Piro24 on 2010-10-24
> **WorMzy said:**
> I'm guessing that you're manually downloading and installing these packages? Well, libglib1.2ldbl is [also in the repos]("http://packages.ubuntu.com/jaunty/libglib1.2ldbl").

I was actually able to install that one, but my problem persists :/.

Same error message as before...

This is frustrating.

---

