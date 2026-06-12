---
title: "https web login page never appears"
date: 2009-12-30
forum: General Help
---

### Post by bala150985 on 2009-12-30
Hi 

I installed ubuntu 9.04 and installed VMware on it, and I was able to open the [https://127.0.0.1:8333](https://127.0.0.1:8333) happily it asked for the user name and password and it worked out,

Now when I tried to access that same link the login box does not appear,  I went to edit>preferences> and tried to delete the certificate and readded it, still I don't see the login page.  However if I give [http://127.0.0.1:8222](http://127.0.0.1:8222) the login page appears and I am able to log in.  Can some one tell me how to fix this.

bala@ubuntu:~$ netstat -ant
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:902             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:8333            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:8307          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:8222            0.0.0.0:*               LISTEN     
tcp6       0      0 127.0.0.1:8005          :::*                    LISTEN     
tcp6       0      0 :::8009                 :::*                    LISTEN     
tcp6       0      0 :::8308                 :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
bala@ubuntu:~$ 



Thanks a lot in advance.

---

### Post by dcstar on 2009-12-30
> **bala150985 said:**
> Hi 

I installed ubuntu 9.04 and installed VMware on it, and I was able to open the [https://127.0.0.1:8333](https://127.0.0.1:8333) happily it asked for the user name and password and it worked out,

Now when I tried to access that same link the login box does not appear,  I went to edit>preferences> and tried to delete the certificate and readded it, still I don't see the login page.  However if I give [http://127.0.0.1:8222](http://127.0.0.1:8222) the login page appears and I am able to log in.  Can some one tell me how to fix this.

bala@ubuntu:~$ netstat -ant
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:902             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:8333            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:8307          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:8222            0.0.0.0:*               LISTEN     
tcp6       0      0 127.0.0.1:8005          :::*                    LISTEN     
tcp6       0      0 :::8009                 :::*                    LISTEN     
tcp6       0      0 :::8308                 :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
bala@ubuntu:~$ 



Thanks a lot in advance.

Look in the Virtualization forum for all VM issues.

---

### Post by john newbuntu on 2009-12-30
Did you make any changes to the configuration of sites?  Are your certificates ok.  Did it expire?  Check apache logs.  It usually is good at pointing these problems out.

---

