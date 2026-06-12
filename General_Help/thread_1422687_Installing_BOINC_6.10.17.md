---
title: "Installing BOINC 6.10.17"
date: 2010-03-05
forum: General Help
---

### Post by MC707 on 2010-03-05
Ok so I got the [BOINC 6.10.17 .dev package]("http://packages.debian.org/sid/amd64/boinc-client/download"), since the repositories are 2 years old (6.4.5). Then I double click the .dev package and get this error:

[[IMG]http://img46.imageshack.us/img46/9364/15002441.png[/IMG]](http://img46.imageshack.us/i/15002441.png/)
Error: Dependency is not satisfiable: libssl0.9.8 (>= 0.9.8k-1)

I searched for "libssl" in synaptic... but I didn't get any idea of what to do #-o

Thanks in advance

---

### Post by Intrepid Ibex on 2010-03-05
I don't have ubuntu anymore but one of this flags will (hopefully) work with dpkg in ignoring dependencies as I couldn't find any newer version of libssl for you:
--ignore-depends, -f, --nodeps
e.g.
```
dpkg -f boinc-client*deb
```
the "boinc-client*deb" part will search for all the files starting "boinc-client" and ending "deb" in that directory. You most likely have only that one file fulfilling those 'requirements' so it will be safe to use.

---

### Post by MC707 on 2010-03-05
Hey thanks for answering. Ok, so what I did was

```
mario@mario-desktop:~/Downloads$ sudo dpkg --ignore-depends=boinc-client_6.10.17+dfsg-3_amd64.deb -i boinc-client_6.10.17+dfsg-3_amd64.deb
[sudo] password for mario: 
(Reading database ... 267147 files and directories currently installed.)
Preparing to replace boinc-client 6.4.5+dfsg-2ubuntu2 (using boinc-client_6.10.17+dfsg-3_amd64.deb) ...
 * Stopping BOINC core client: boinc                                     [ OK ] 
Unpacking replacement boinc-client ...
dpkg: dependency problems prevent configuration of boinc-client:
 boinc-client depends on libssl0.9.8 (>= 0.9.8k-1); however:
  Version of libssl0.9.8 on system is 0.9.8g-16ubuntu3.1.
dpkg: error processing boinc-client (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Errors were encountered while processing:
 boinc-client
mario@mario-desktop:~/Downloads$

```

--nodeps seems to ```
unknown option --nodeps
```

Any idea of what I could do now...?

Regards

---

### Post by Intrepid Ibex on 2010-03-05
gosh... did you try with the -f?

**E:** Oh, didn't check out how many "beans" you had - wouldn't have had to explain the * part O_O.

**E2:** Wait a sec, just found this: [http://manpages.ubuntu.com/manpages/jaunty/man1/dpkg.1.html](http://manpages.ubuntu.com/manpages/jaunty/man1/dpkg.1.html)
```
--ignore-depends=package,...
              Ignore   dependency-checking   for   specified   packages
              (actually, checking is performed, but only warnings about
              conflicts are given, nothing else).
```

---

### Post by MC707 on 2010-03-05
Ayup.

```
mario@mario-desktop:~/Downloads$ dpkg -f boinc-client*deb
Package: boinc-client
Source: boinc
Version: 6.10.17+dfsg-3
Architecture: amd64
Maintainer: Debian BOINC Maintainers <pkg-boinc-devel@lists.alioth.debian.org>
Installed-Size: 985
Depends: libc6 (>= 2.2.5), libcurl3 (>= 7.16.2-1), libgcc1 (>= 1:4.1.1), libssl0.9.8 (>= 0.9.8k-1), libstdc++6 (>= 4.1.1), zlib1g (>= 1:1.1.4), debconf (>= 0.5) | debconf-2.0, python (>= 2.3), adduser, lsb-base (>= 3.0-6), ca-certificates
Recommends: schedtool
Suggests: boinc-app-seti, boinc-manager
Section: net
Priority: optional
Homepage: http://boinc.berkeley.edu/
Description: core client for the BOINC distributed computing infrastructure
 The Berkeley Open Infrastructure for Network Computing (BOINC) is a
 software platform for distributed computing: several initiatives of
 various scientific disciplines all compete for the idle time of
 desktop computers. The developers' web site at the University of
 Berkeley serves as a common portal to the otherwise independently run
 projects.
 .
 This package contains the BOINC core client program that is required
 to participate in any project that uses BOINC. A central server
 distributes work units and collects results via this client. When
 attaching a local machine to a project, this client will also
 dynamically download the projects application's program to be then
 wrapped by the BOINC core client.
mario@mario-desktop:~/Downloads$ 
```
Dunno what happened there though...

---

### Post by MC707 on 2010-03-05
> **Intrepid Ibex said:**
> gosh... did you try with the -f?

**E:** Oh, didn't check out how many "beans" you had - wouldn't have had to explain the * part O_O.
Its ok, other people that didn't know that probably would learn from it if they read this thread.

> **Intrepid Ibex said:**
> **E2:** Wait a sec, just found this: [http://manpages.ubuntu.com/manpages/jaunty/man1/dpkg.1.html](http://manpages.ubuntu.com/manpages/jaunty/man1/dpkg.1.html)
```
--ignore-depends=package,...
              Ignore   dependency-checking   for   specified   packages
              (actually, checking is performed, but only warnings about
              conflicts are given, nothing else).
```
That explains it...

---

### Post by dcstar on 2010-03-05
> **MC707 said:**
> Ok so I got the [BOINC 6.10.17 .dev package]("http://packages.debian.org/sid/amd64/boinc-client/download"), since the repositories are 2 years old (6.4.5).
.........

Then you go here, download (and try to install) the .deb and then download and install each other package that the install process tells **you** is a dependency:

[http://packages.ubuntu.com/lucid/boinc-client](http://packages.ubuntu.com/lucid/boinc-client)

---

### Post by MC707 on 2010-03-05
MUAHAHAHAHA FINALLY I INSTALLED 6.10.17!!1

Whew I had to get that outtah my chest. Thanks fellas, I got it working thanks to y'all. I am going to explain how to do the installation, just for the sake of other unfortunate souls like me that had to tinker with pretty much everything to get the app installed. I have to note this phrase that kinda opened my eyes (and the latter two files to download in this mini-guide I have made down in this post) [QUOTE=dcstar]"then download and install each other package that the install process tells you is a dependency"[/QUOTE]

Disclosure: I do not make myself responsible to damage to your hardware or software, even if I had direct responsibility (lol). This was done on a quad core intel PC, with Ubuntu 9.10 Karmic with all updates installed.

Explaining the exact process I did would be a bit tedious to both write and read, so I am just going to do things straight fast. Ok, first uninstall the previous BOINC installation if you had one. Then, download the following files:
*[client]("http://mirrors.kernel.org/ubuntu/pool/universe/b/boinc/boinc-client_6.10.17+dfsg-2ubuntu2_amd64.deb") (3)
*[manager]("http://mirrors.kernel.org/ubuntu/pool/universe/b/boinc/boinc-manager_6.10.17+dfsg-2ubuntu2_amd64.deb") (4)
*[libssl0.9.8  (>= 0.9.8k-1)]("http://mirrors.kernel.org/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8k-7ubuntu6_amd64.deb") (NEW dependency that client asks for) (1)
*[libsqlite3-0  (>= 3.6.21) ]("http://mirrors.kernel.org/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8k-7ubuntu6_amd64.deb") (NEW dependency that manager asks for) (2)

Next, install the latter two files, then the client, then the manager. Then, ****ing enjoy crunching for science!

Now as the above quote said, you might need the latter files or not, or you might need even more dependency files than those. If so, go to the respective page for [_client_]("http://packages.ubuntu.com/lucid/boinc-client") and [_manager_]("http://packages.ubuntu.com/lucid/boinc-manager") and download the dependency in that page that the .deb file for client and manager asks for, and install those first.

Hehehe now I'm finally gonna crunch with my GPU >:D

Regards

---

### Post by dcstar on 2010-03-05
> **MC707 said:**
> MUAHAHAHAHA FINALLY I INSTALLED 6.10.17!!1
........
Now as the above quote said, you might need the latter files or not, or you might need even more dependency files than those. If so, go to the respective page for [_client_]("http://packages.ubuntu.com/lucid/boinc-client") and [_manager_]("http://packages.ubuntu.com/lucid/boinc-manager") and download the dependency in that page that the .deb file for client and manager asks for, and install those first.

Hehehe now I'm finally gonna crunch with my GPU >:D


You don't need to install the Manager to run the new client, I only run the new client on my 9.04 system because the new Manager has too many unresolvable dependencies for this version.

---

### Post by MC707 on 2010-03-08
> **dcstar said:**
> You don't need to install the Manager to run the new client, I only run the new client on my 9.04 system because the new Manager has too many unresolvable dependencies for this version.

Strange, I only had one unresolvable dependency (for the manager). Still, I like to keep my stuff as updated as possible.

---

### Post by size_XXM on 2010-03-10
> **MC707 said:**
> 
*[libssl0.9.8  (>= 0.9.8k-1)]("http://mirrors.kernel.org/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8k-7ubuntu6_amd64.deb") (NEW dependency that client asks for) (1)
*[libsqlite3-0  (>= 3.6.21) ]("http://mirrors.kernel.org/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8k-7ubuntu6_amd64.deb") (NEW dependency that manager asks for) (2)
Those two links are the same! Where did you get the libsqlite package? I can't see it on that repository.

---

