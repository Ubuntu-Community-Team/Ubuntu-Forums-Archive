---
title: "svn:// works but svn+ssh:// does not"
date: 2009-12-06
forum: General Help
---

### Post by Eugene_Bondarenko on 2009-12-06
Hello,
I've successfully set svn server and it runs fine. The server is set on my local comp where my root user is eugene. 
Then I tried creating another account. So I created unprivileged user "eugeneb" which belongs to "subversion" group and then created rsa keys to enable passwordless "ssh eugeneb@localhost". 
Passwordless ssh works fine. svn://eugeneb@localhost/project/ works fine too. However svn+ssh://eugeneb@localhost/project/ returns the following error
> 
No repository found in 'svn+ssh://eugeneb@localhost/project'
Finished

Also I tried connecting via command line and received the same result
> 
eugene@eugene-desktop:~$ svn co svn+ssh://localhost/project/ project --username eugeneb
svn: No repository found in 'svn+ssh://localhost/project'
eugene@eugene-desktop:~$ svn co svn://localhost/project/ project --username eugeneb
Checked out revision 3.
eugene@eugene-desktop:~$ 
eugene@eugene-desktop:~$ ssh eugeneb@localhost
Linux eugene-desktop 2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:00:22 UTC 2009 i686

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

Last login: Mon Dec  7 01:42:05 2009 from localhost
eugeneb@eugene-desktop:~$ 



Could you please share your thoughts about this.

---

### Post by Eugene_Bondarenko on 2009-12-07
up

---

### Post by Eugene_Bondarenko on 2009-12-08
The issue is no more. For some reason ssh+svn:// wanted to see full url
svn+ssh://eugeneb@localhost/home/svn/project/
while svn:// liked this url
svn://eugeneb@localhost/project/

---

