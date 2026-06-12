---
title: "Cannot acces a svn server from ssh, even using svn+ssh://"
date: 2011-03-14
forum: General Help
---

### Post by LucasQueiroz on 2011-03-14
Hello there. I have been trying to configure a svn server on a intranet. I use ssh between the computers. On one that it's IP is 192.168.1.86, and name sonic1 I already created the server. 

```
lucas@sonic1:~/svn/ProjetoCUDA/LJ/src$ pico sample.cu 
lucas@sonic1:~/svn/ProjetoCUDA/LJ/src$ svn commit
Sending        src/sample.cu
Transmitting file data .
Committed revision 11.
```

But when I'm one other PC, I try to use svn+ssh,

```

lucas@sonic3-desktop:~$ cd Codigos/
lucas@sonic3-desktop:~/Codigos$ svn co svn+ssh://192.168.1.86/home/lucas/svn/ProjetoCUDA
lucas@192.168.1.86's password: 
svn: No repository found in 'svn+ssh://192.168.1.86/home/lucas/svn/ProjetoCUDA'
lucas@sonic3-desktop:~/Codigos$ svn co svn+ssh://192.168.1.86/home/lucas/svn/ProjetoCUDA/LJ
lucas@192.168.1.86's password: 
svn: No repository found in 'svn+ssh://192.168.1.86/home/lucas/svn/ProjetoCUDA/LJ'
```

Any ideas how to configure this correctly?

Thanks in advance

---

