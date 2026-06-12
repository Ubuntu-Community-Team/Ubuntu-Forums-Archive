---
title: "Problem installing Eclipse, missing libservlet2.4-java_5.0.30-12_all.deb"
date: 2011-08-14
forum: General Help
---

### Post by aqui_c on 2011-08-14
Hi All!
I'm trying to install Eclipse, everything goes OK until i get the following error:

```
Err http://br.archive.ubuntu.com/ubuntu/ natty/universe libservlet2.4-java all 5.0.30-12
  404  Not Found
Imposible obtener http://br.archive.ubuntu.com/ubuntu/pool/universe/libs/libservlet2.4-java/libservlet2.4-java_5.0.30-12_all.deb  404  Not Found
```

I tried with the ```
--fix-missing
``` option, but it seems that it's a dependency missing in the repositories or something. 
Anyone has a clue on how to solve it?

---

### Post by gandaran on 2011-08-14
run 
```
sudo apt-get update
```
and paste the output

---

### Post by aqui_c on 2011-08-14
```
Ign http://linux.dropbox.com natty InRelease
Ign http://extras.ubuntu.com natty InRelease
Ign http://security.ubuntu.com natty-security InRelease
Ign http://archive.canonical.com natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Ign http://ar.archive.ubuntu.com natty InRelease
Ign http://ar.archive.ubuntu.com natty-updates InRelease
Ign http://ar.archive.ubuntu.com natty-backports InRelease
Obj http://linux.dropbox.com natty Release.gpg
Obj http://security.ubuntu.com natty-security Release.gpg
Obj http://archive.canonical.com natty Release.gpg
Obj http://ppa.launchpad.net natty Release.gpg
Obj http://ar.archive.ubuntu.com natty Release.gpg
Obj http://linux.dropbox.com natty Release
Obj http://archive.canonical.com natty Release
Obj http://security.ubuntu.com natty-security Release
Obj http://ar.archive.ubuntu.com natty-updates Release.gpg
Obj http://linux.dropbox.com natty/main i386 Packages
Obj http://security.ubuntu.com natty-security/main Sources
Obj http://ar.archive.ubuntu.com natty-backports Release.gpg
Ign http://linux.dropbox.com natty/main TranslationIndex
Obj http://security.ubuntu.com natty-security/restricted Sources
Obj http://security.ubuntu.com natty-security/universe Sources
Obj http://security.ubuntu.com natty-security/multiverse Sources
Obj http://security.ubuntu.com natty-security/main i386 Packages
Obj http://security.ubuntu.com natty-security/restricted i386 Packages
Obj http://ar.archive.ubuntu.com natty Release
Des:1 http://extras.ubuntu.com natty Release.gpg [72 B]
Obj http://security.ubuntu.com natty-security/universe i386 Packages
Obj http://security.ubuntu.com natty-security/multiverse i386 Packages
Ign http://security.ubuntu.com natty-security/main TranslationIndex
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Ign http://security.ubuntu.com natty-security/universe TranslationIndex
Obj http://ar.archive.ubuntu.com natty-updates Release
Obj http://ppa.launchpad.net natty Release
Obj http://extras.ubuntu.com natty Release
Obj http://archive.canonical.com natty/partner Sources
Obj http://archive.canonical.com natty/partner i386 Packages
Ign http://archive.canonical.com natty/partner TranslationIndex
Obj http://ppa.launchpad.net natty/main Sources
Obj http://extras.ubuntu.com natty/main Sources
Obj http://ppa.launchpad.net natty/main i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Obj http://extras.ubuntu.com natty/main i386 Packages
Ign http://extras.ubuntu.com natty/main TranslationIndex
Obj http://ar.archive.ubuntu.com natty-backports Release
Des:2 http://ar.archive.ubuntu.com natty/main Sources [862 kB]
Ign http://linux.dropbox.com natty/main Translation-es_AR
Ign http://security.ubuntu.com natty-security/main Translation-es_AR
Ign http://linux.dropbox.com natty/main Translation-es
Ign http://security.ubuntu.com natty-security/main Translation-es
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-es_AR
Ign http://security.ubuntu.com natty-security/multiverse Translation-es
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-es_AR
Ign http://linux.dropbox.com natty/main Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-es
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-es_AR
Ign http://security.ubuntu.com natty-security/universe Translation-es
Ign http://security.ubuntu.com natty-security/universe Translation-en
Des:3 http://ar.archive.ubuntu.com natty/restricted Sources [4.104 B]
Ign http://archive.canonical.com natty/partner Translation-es_AR
Des:4 http://ar.archive.ubuntu.com natty/universe Sources [4.380 kB]
Ign http://ppa.launchpad.net natty/main Translation-es_AR
Ign http://archive.canonical.com natty/partner Translation-es
Ign http://archive.canonical.com natty/partner Translation-en
Ign http://ppa.launchpad.net natty/main Translation-es
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://extras.ubuntu.com natty/main Translation-es_AR
Ign http://extras.ubuntu.com natty/main Translation-es
Ign http://extras.ubuntu.com natty/main Translation-en
Obj http://ar.archive.ubuntu.com natty/multiverse Sources
Des:5 http://ar.archive.ubuntu.com natty/main i386 Packages [1.550 kB]
Des:6 http://ar.archive.ubuntu.com natty/restricted i386 Packages [8.986 B]
Des:7 http://ar.archive.ubuntu.com natty/universe i386 Packages [6.021 kB]
Obj http://ar.archive.ubuntu.com natty/multiverse i386 Packages
Ign http://ar.archive.ubuntu.com natty/main TranslationIndex
Ign http://ar.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://ar.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://ar.archive.ubuntu.com natty/universe TranslationIndex
Des:8 http://ar.archive.ubuntu.com natty-updates/main Sources [98,6 kB]
Des:9 http://ar.archive.ubuntu.com natty-updates/restricted Sources [14 B]
Des:10 http://ar.archive.ubuntu.com natty-updates/universe Sources [22,6 kB]
Obj http://ar.archive.ubuntu.com natty-updates/multiverse Sources
Des:11 http://ar.archive.ubuntu.com natty-updates/main i386 Packages [287 kB]
Des:12 http://ar.archive.ubuntu.com natty-updates/restricted i386 Packages [14 B]
Des:13 http://ar.archive.ubuntu.com natty-updates/universe i386 Packages [82,0 kB]
Obj http://ar.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://ar.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://ar.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://ar.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://ar.archive.ubuntu.com natty-updates/universe TranslationIndex
Obj http://ar.archive.ubuntu.com natty-backports/main Sources
Obj http://ar.archive.ubuntu.com natty-backports/restricted Sources
Obj http://ar.archive.ubuntu.com natty-backports/universe Sources
Obj http://ar.archive.ubuntu.com natty-backports/multiverse Sources
Obj http://ar.archive.ubuntu.com natty-backports/main i386 Packages
Obj http://ar.archive.ubuntu.com natty-backports/restricted i386 Packages
Obj http://ar.archive.ubuntu.com natty-backports/universe i386 Packages
Obj http://ar.archive.ubuntu.com natty-backports/multiverse i386 Packages
Ign http://ar.archive.ubuntu.com natty-backports/main TranslationIndex
Ign http://ar.archive.ubuntu.com natty-backports/multiverse TranslationIndex
Ign http://ar.archive.ubuntu.com natty-backports/restricted TranslationIndex
Ign http://ar.archive.ubuntu.com natty-backports/universe TranslationIndex
Des:14 http://ar.archive.ubuntu.com natty/main Translation-es [675 kB]
Obj http://ar.archive.ubuntu.com natty/multiverse Translation-es
Des:15 http://ar.archive.ubuntu.com natty/restricted Translation-es [2.542 B]
Des:16 http://ar.archive.ubuntu.com natty/universe Translation-es [1.277 kB]
Ign http://ar.archive.ubuntu.com natty/main Translation-es_AR
Ign http://ar.archive.ubuntu.com natty/main Translation-en
Ign http://ar.archive.ubuntu.com natty/multiverse Translation-es_AR
Ign http://ar.archive.ubuntu.com natty/multiverse Translation-en
Ign http://ar.archive.ubuntu.com natty/restricted Translation-es_AR
Ign http://ar.archive.ubuntu.com natty/restricted Translation-en
Ign http://ar.archive.ubuntu.com natty/universe Translation-es_AR
Ign http://ar.archive.ubuntu.com natty/universe Translation-en
Ign http://ar.archive.ubuntu.com natty-updates/main Translation-es_AR
Ign http://ar.archive.ubuntu.com natty-updates/main Translation-es
Ign http://ar.archive.ubuntu.com natty-updates/main Translation-en
Ign http://ar.archive.ubuntu.com natty-updates/multiverse Translation-es_AR
Ign http://ar.archive.ubuntu.com natty-updates/multiverse Translation-es
Ign http://ar.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://ar.archive.ubuntu.com natty-updates/restricted Translation-es_AR
Ign http://ar.archive.ubuntu.com natty-updates/restricted Translation-es
Ign http://ar.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://ar.archive.ubuntu.com natty-updates/universe Translation-es_AR
Ign http://ar.archive.ubuntu.com natty-updates/universe Translation-es
Ign http://ar.archive.ubuntu.com natty-updates/universe Translation-en
Ign http://ar.archive.ubuntu.com natty-backports/main Translation-es_AR
Ign http://ar.archive.ubuntu.com natty-backports/main Translation-es
Ign http://ar.archive.ubuntu.com natty-backports/main Translation-en
Ign http://ar.archive.ubuntu.com natty-backports/multiverse Translation-es_AR
Ign http://ar.archive.ubuntu.com natty-backports/multiverse Translation-es
Ign http://ar.archive.ubuntu.com natty-backports/multiverse Translation-en
Ign http://ar.archive.ubuntu.com natty-backports/restricted Translation-es_AR
Ign http://ar.archive.ubuntu.com natty-backports/restricted Translation-es
Ign http://ar.archive.ubuntu.com natty-backports/restricted Translation-en
Ign http://ar.archive.ubuntu.com natty-backports/universe Translation-es_AR
Ign http://ar.archive.ubuntu.com natty-backports/universe Translation-es
Ign http://ar.archive.ubuntu.com natty-backports/universe Translation-en
Descargados 15,3 MB en 21min. 42seg. (11,7 kB/s)
Leyendo lista de paquetes...
```

---

