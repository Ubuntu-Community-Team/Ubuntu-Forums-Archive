---
title: "wget download using password + user problem"
date: 2010-05-14
forum: General Help
---

### Post by vzhen on 2010-05-14
Hi

I want to download something from oracle.com. It required to login before i can download.

and i use below command but not working. it just download the link.

#wget --http-user=USER --http-password=PASSWORD [http://download.oracle.com/xxx/xxxx/xxxx](http://download.oracle.com/xxx/xxxx/xxxx)


Any idea?

---

### Post by TeoBigusGeekus on 2010-05-14
Try
```
wget --user=USER --password='PASSWORD' http://download.oracle.com/xxx/xxxx/xxxx/NAMEOFFILE.EXTENSIONOFFILE
```

---

### Post by vzhen on 2010-05-14
Not working aslo

Can u try it for me ?

[http://download.oracle.com/otn/linux/ias/101202/as_linux_x86_ids_101202_disk1.cpio](http://download.oracle.com/otn/linux/ias/101202/as_linux_x86_ids_101202_disk1.cpio)

---

### Post by TeoBigusGeekus on 2010-05-14
It worked mate...
Do you get any error messages? Also, where do you look for the file after executing the command?

---

### Post by vzhen on 2010-05-14
I dont get any error,  it connected and saving to otnlogin.jsp?......
The downloaded file saving at home dir

The file size actually is 600mb plus but i get otnlogin.jsp? which mean the login page link.

Actually, i no problem using browser (chromium)to download. but 600mb i cannot resume. 

```
wget --user=MYUSERNAME --password='MYPASSWORD' [http://download.oracle.com/otn/linux/ias/101202/as_linux_x86_ids_101202_disk1.cpio](http://download.oracle.com/otn/linux/ias/101202/as_linux_x86_ids_101202_disk1.cpio)



100%[======================================>] 4,087       13.8K/s   in 0.3s    

2010-05-14 18:55:07 (13.8 KB/s) - `otnLogin.jsp?remoteIp=121.123.136.158&globalId=&redirectUrl=http:%2F%2Fdownload-llnw.oracle.com:80%2Fotn%2Flinux%2Fias%2F101202%2Fas_linux_x86_ids_101202_disk1.cpio' saved [4087/4087]
```

---

