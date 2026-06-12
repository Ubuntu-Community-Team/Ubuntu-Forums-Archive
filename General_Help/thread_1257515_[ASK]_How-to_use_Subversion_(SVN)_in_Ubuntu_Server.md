---
title: "[ASK] How-to use Subversion (SVN) in Ubuntu Server 9.04 ?"
date: 2009-09-03
forum: General Help
---

### Post by ularlaut on 2009-09-03
Hi all,

I required an assistance on how to use Subversion program in my Ubuntu Server 9.04, which is going to be use with my Apache2 Web-server.

I already installed the Subversion in the server with :

```

      #sudo apt-get install subversion

```And when I try to run them to check if its already run or not, I got reply like : 

```

   root@ubuntu-server:~# svn status
   svn: warning: '.' is not a working copy

```The manual that came with the programs does not have much help.

Could somebody help me with this ?

Thank you very much for the kind attention.

regards,

---

### Post by XCan on 2009-09-04
Did you checkout the project first? Sounds like you just typed "svn st" in a random dir. You need to be in the checked-out project's dir.

---

