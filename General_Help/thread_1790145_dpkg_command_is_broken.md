---
title: "dpkg command is broken"
date: 2011-06-24
forum: General Help
---

### Post by sropensrc on 2011-06-24
Hi,

My dpkg command is corrupted.  When I run command "dpkg -s packagename" I'd get error, "dpkg: /lib/libc.so.6: version `GLIBC_2.8' not found (required by dpkg)". This is a production system so I have to be careful in resolving it. I'm concerned that other packages may be broken due to the missing libc.

The server is running release 8.04, hardy.  Does anyone know how to fix this problem?    

Thank You

---

### Post by FormatSeize on 2011-06-24
> **sropensrc said:**
> Hi,
 
My dpkg command is corrupted. When I run command "dpkg -s packagename" I'd get error, "dpkg: /lib/libc.so.6: version `GLIBC_2.8' not found (required by dpkg)". This is a production system so I have to be careful in resolving it. I'm concerned that other packages may be broken due to the missing libc.
 
The server is running release 8.04, hardy. Does anyone know how to fix this problem? 

First, I will say that you really should update to 10.04, which is also another LTS. 
 
It is looking for a dependency that is not there. dpkg is looking for a library version that is later than the one that Hardy has. Hardy shipped with Glibc version 2.7. For whatever reason, your dpkg wants Glibc version 2.8. If I had to guess, I would say that (somehow) dpkg was updated, but not your C libraries. I'm not sure how that would happen, but an updated dpkg would look for the newer C libraries that the original didn't need. 
 
So you can try:
-Get GlibC version 2.8 from the repositories so that you satisfy dpkg's dependency
-Update the system to the most recent LTS, which will have the needed version of GlibC, and will also prevent a whole host of other problems
-Build Glibc yourself, then run dpkg (not highly recommended)
-Build the package without using dpkg (not highly recommended)

---

### Post by idoitprone on 2011-06-24
> **FormatSeize said:**
> First, I will say that you really should update to 10.04, which is also another LTS. 
 
It is looking for a dependency that is not there. dpkg is looking for a library version that is later than the one that Hardy has. Hardy shipped with Glibc version 2.7. For whatever reason, your dpkg wants Glibc version 2.8. If I had to guess, I would say that (somehow) dpkg was updated, but not your C libraries. I'm not sure how that would happen, but an updated dpkg would look for the newer C libraries that the original didn't need. 

ummm, he is running a server... i think it is still supported until 2013. unless he is an idoit like me and install a desktop edition for server
> 
 
So you can try:
-Get GlibC version 2.8 from the repositories so that you satisfy dpkg's dependency
-Update the system to the most recent LTS, which will have the needed version of GlibC, and will also prevent a whole host of other problems
-Build Glibc yourself, then run dpkg (not highly recommended)
-Build the package without using dpkg (not highly recommended)whatever he said, except upgrading. 

First I will figure out how to reinstall dpkg to the proper version.

Second, try to safely forge or swap out libc long enough to reinstall libc and dpkg to the proper hardy version.

---

### Post by sropensrc on 2011-06-24
I was working on installing netbackup client. Netbackup client needs xinetd, libc6-i386, and ia32-libs. I think I broke it when I removed libc6 on hardy and reinstalled with libc6-i386_2.11.1-0ubuntu7.8_amd64.deb from a lucid server. 

I'll carefully try your suggestions. 

Under the current state, if the server is rebooted will it have problems coming up?

Thank You for your help.

---

### Post by idoitprone on 2011-06-24
> **sropensrc said:**
> I was working on installing netbackup client. Netbackup client needs xinetd, libc6-i386, and ia32-libs. I think I broke it when I removed libc6 on hardy and reinstalled with libc6-i386_2.11.1-0ubuntu7.8_amd64.deb from a lucid server. 

I'll carefully try your suggestions. 

Under the current state, if the server is rebooted will it have problems coming up?

Thank You for your help.

that is something i will do. lol. Next time, will you want to destroy your system try not to destroy the package manager with it or else you end up alot of pain.

---

