---
title: "problem with Xorg 10.04 Lucid"
date: 2011-01-25
forum: General Help
---

### Post by srgreddy on 2011-01-25
Dear Linux community members

Recently we installed 30 64bit  Ubuntu 10.04 machines. We configured them using NIS and NFS. Among them  one made as Server and all other made as clients.The installation was  successful and every thing worked fine. We had over 60 users for this  unit. Last week I updated the Server but not the clients. After this  when I trying to login in the client, it able to login but the graphical  interface to mount the home directory of the corresponding user is not  working. By saying Graphical interface what I want to say is when we login in our  local machine a gnome secession will start. This is working fine. I  switched on the server. In the server we created around 60 users. When  we tried to login through the client machine, we can not see anything.  But the login id and password are correct. I checked this by login into  the local account of the client and I can switch over to any user by the  command 

su userid 
and then giving the password.

 After a long study, I understood that this is a xorg problem. My  operating system is Ubuntu 10.04 Lucid 64 BIT. My machine architecture  is HP Compaq 6005 pro MT PC with AMD phenom II processor.

Please see this thread. 
[http://ubuntuforums.org/showthread.php?t=1546501](http://ubuntuforums.org/showthread.php?t=1546501)
This thread showing a possible solution for the blank screen after login.
But mine problem is somewhat different than this.
I am able to login to client machine with local user but unable to do the same with the user mounted 
by nis/nfs. 
Was this information is sufficient.


Can you any of you help me in working it.

---

