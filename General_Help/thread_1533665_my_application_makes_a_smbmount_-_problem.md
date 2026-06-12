---
title: "my application makes a smbmount - problem"
date: 2010-07-18
forum: General Help
---

### Post by ilantal on 2010-07-18
I have an application which makes an on the fly connection to a couple of servers. The command I used was
smbmount //192.168.1.100/mydb /home/ilan/ilanMnt -o user=ilan,pass=****

Note that I went to my own home directory to avoid sudo problems with /mnt.
I could be an ordinary user and not the root.
The command "mount" always wanted "sudo mount", so I avoided it. Smbmount worked with no problems. It seems that something has changed in 10.04 since it now tells me Operation not permitted.
If I run it with sudo, it will work - but I don't want sudo inside my application.
I am guessing that someone plugged the "Security hole" and this is the reason for my troubles. If this be the case, what is the best way to reach my server on the fly?

Thanks,
Ilan

---

