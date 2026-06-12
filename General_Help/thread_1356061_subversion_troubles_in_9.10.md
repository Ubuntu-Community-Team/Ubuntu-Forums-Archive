---
title: "subversion troubles in 9.10"
date: 2009-12-15
forum: General Help
---

### Post by Chocrates on 2009-12-15
I'm trying to import an existing project onto my home box with svn.
I'm running newest ubuntu, installed it a few days ago, and i did an apt-get install subversion which gave me svn verstion 1.6.5
when i run:
svn import svn+ssh://username@url.edu/path/to/svn -m 'initial import'

i get this error:
svn: Expected FS format between '1' and '3'; found format '4'

after some googleing this seems to be a problem for most people when they have a repository made in verstion 1.6.x and they are trying to check it out with a client that is still 1.5.x
my repository was made in 1.6.x 
i tried uninstalling svn then compiling subversion 1.6.6 and im still getting this error

also, another member of my group was able to check the repository out with svn version 1.6.x, so the repository is not broken 

does anybody have any ideas as to how i might be able to fix this?

thanks

---

