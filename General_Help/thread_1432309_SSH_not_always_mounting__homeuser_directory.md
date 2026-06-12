---
title: "SSH not always mounting  /home/user directory"
date: 2010-03-17
forum: General Help
---

### Post by vladoportos on 2010-03-17
Heya all,

I have a little problem, more annoyance than anything.

I have my standard ubuntu server installation 
with encrypted disks and it mounts your /home/user dir 
as you log in and decrypt it( standard as it was during installation )

after a while, when I installed couple of things I noticed when 
I log in through ssh it wont mount my partition ( my /home/user )
it mount some standard /home/user directory and look like its ok,
but I miss all my files and settings and everything what I would normally have 
in my /home/user directory... so I try log in with another session 
and lord behold it is working just fine... all my files are back !

funny is that I have two sessions open through ssh, the same user name, the same ssh key 
and two different /home/user ( even though /home/user match the name I'm logged in with on both sessions )
I have no idea why this is happening at all, there is nothing suspicious in logs anywhere...

I believe it might have something to do with my recent installation of zoneminder or zabbix... not sure

any idea or similar experience ?

---

