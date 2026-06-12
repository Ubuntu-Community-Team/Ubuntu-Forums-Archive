---
title: "Stop VSFTPD daemon from loading at boot"
date: 2010-06-09
forum: General Help
---

### Post by RFrenette on 2010-06-09
I installed VSFTPD via: sudo gedit /etc/vsftpd.conf

I can start/stop using the following:
sudo /etc/init.d/vsftpd start 
sudo /etc/init.d/vsftpd stop

By default, the *daemon * loads at boot but I don't want/need it to. I executed the following command thinking it would stop it from loading at boot:
sudo update-rc.d -f vsftp remove

However, after I rebooted I executed the following:
netstat -an --tcp

and saw it had loaded again:
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN 

Can anyone tell me how to stop the VSFTPD *daemon* from loading at boot?

Thanks.

---

### Post by dcstar on 2010-06-09
> **RFrenette said:**
> I installed VSFTPD via: sudo gedit /etc/vsftpd.conf

I can start/stop using the following:
sudo /etc/init.d/vsftpd start 
sudo /etc/init.d/vsftpd stop

By default, the *daemon * loads at boot but I don't want/need it to. I executed the following command thinking it would stop it from loading at boot:
sudo update-rc.d -f vsftp remove

However, after I rebooted I executed the following:
netstat -an --tcp

and saw it had loaded again:
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN 

Can anyone tell me how to stop the VSFTPD *daemon* from loading at boot?

Thanks.

Look in the relevant /etc/rcN.d folders and manually delete the S link that starts it.

---

### Post by RFrenette on 2010-06-09
Thanks for the reply, David.

I executed the following command:
ls -al /etc/rc*

and found the following:

/etc/rc0.d:
lrwxrwxrwx   1 root root    16 2010-06-08 19:31 K20vsftpd -> ../init.d/vsftpd
/etc/rc1.d:
lrwxrwxrwx   1 root root    16 2010-06-08 19:31 K20vsftpd -> ../init.d/vsftpd
/etc/rc2.d:
lrwxrwxrwx   1 root root    16 2010-06-08 19:31 S20vsftpd -> ../init.d/vsftpd
/etc/rc3.d:
lrwxrwxrwx   1 root root    16 2010-06-08 19:31 S20vsftpd -> ../init.d/vsftpd
/etc/rc4.d:
lrwxrwxrwx   1 root root    16 2010-06-08 19:31 S20vsftpd -> ../init.d/vsftpd
/etc/rc5.d:
lrwxrwxrwx   1 root root    16 2010-06-08 19:31 S20vsftpd -> ../init.d/vsftpd
/etc/rc6.d:
lrwxrwxrwx   1 root root    16 2010-06-08 19:31 K20vsftpd -> ../init.d/vsftpd

Per your reply, I'm wondering if I need to delete all of the S20vsftpd -> ../init.d/vsftpd entries listed in all the /etc/rcN.d dirs listed above.

Also, what about the K20vsftpdentries?

Thanks again.

---

