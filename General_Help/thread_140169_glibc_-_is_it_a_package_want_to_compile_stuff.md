---
title: "glibc - is it a package? want to compile stuff"
date: 2006-03-05
forum: General Help
---

### Post by halfvolle melk on 2006-03-05
Hi,

I want to try Linux From Scratch. The compiler got stuck half way the 3rd package (which, on a sidenote, happens to be glibc). Maybe because I did something stupid, or the host system doesn't have glibc itself?

I've installed "build-essential", also gawk, bison and maybe some other stuff that was needed, but do I have glibc? Synaptic only finds "glibc-doc" and I found a tutorial that says:'get the sources and compile it'. I thougt glibc was essential for compiling. Can anyone explain?

edit: Host system is Ubuntu server + some of the stuff binutils and so on depend on

---

### Post by Xian on 2006-03-05
[QUOTE=halfvolle melk]I thougt glibc was essential for compiling. Can anyone explain?[/QUOTE]

Goes by a different name....

```
$ sudo apt-cache policy libc6
libc6:
  Installed: 2.3.6-0ubuntu8
  Candidate: 2.3.6-0ubuntu8
  Version table:
 *** 2.3.6-0ubuntu8 0
        500 http://us.archive.ubuntu.com dapper/main Packages
        100 /var/lib/dpkg/status
```

---

### Post by halfvolle melk on 2006-03-05
Thanks for your reply,

Olny a second ago I tried 'sudo apt-get install llibc6' (on my desktop) telling me I already had the newest version. 'apt-cache'? policy? Oh well, I'll man those up. libc6 it is then, thanks again!

---

