---
title: "Squid Optimization Question"
date: 2010-06-14
forum: General Help
---

### Post by jondavidf on 2010-06-14
I am trying to make sure that I have Squid configured for the fastest speed possible.  Are the changes I made below beneficial?  Are there any other changes that I should make?

About my setup - I have set up a server that shares files with Samba and proxies with Squid for about 50 users.  The "server" is just a rather cheap desktop that I installed Ubuntu Server 10.04 on.  That is the only operating system installed and the only apps that I added were Samba and Squid.  So the only things that should be running on the server are Ubuntu Server 10.04, Squid, and Samba. The specs of the server are:

Intel Core 2 Quad 2.5 Ghz
4GB DDR3 Ram
500GB Internal Drive (for OS and Squid only)

I am under the assumption that Samba and Ubuntu Server take little CPU/RAM/Hard Drive space to run. With that assumption I made the following changes to the Squid.conf file.

   [FONT=&quot]http_port 8080[/FONT]
  [FONT=&quot]cache_mem 1024 MB (to give 1GB of RAM for cache)
[/FONT]  [FONT=&quot]maximum_object_size_in_memory 4096 KB (4MB to allow larger objects to be stored)[/FONT]
 [FONT=&quot]memory_replacement_policy heap GDSF (updated due to suggestion by another user)[/FONT]
 [FONT=&quot]cache_replacement_policy heap LFUDA[/FONT][FONT=&quot] (updated due to suggestion by another user)[/FONT]
 [FONT=&quot]cache_dir ufs /var/spool/squid 102400 16 256 (to give 100GB of the 500GB Drive for Squid to use)
[/FONT]    [FONT=&quot]visible_hostname Ubuntu-Server[/FONT]
  
[FONT=&quot] All other settings are set to their default settings.
[/FONT]

---

### Post by jondavidf on 2010-06-14
Was just looking at another person's conf file.  Looks like most of their numbers were lower.  I'm not sure if that's better or not.  Also, I saw this code that I did not change in mine.  Do you think I should change the default size of the IP Cache?

ipcache_size 4096

---

### Post by fuzzyk.k on 2010-09-24
you should take a look at this for squid optimization its old but it works

[http://blog.last.fm/2007/08/30/squid-optimization-guide]("http://blog.last.fm/2007/08/30/squid-optimization-guide")

Also the speed of your hard disk matters 
hope i helped

---

