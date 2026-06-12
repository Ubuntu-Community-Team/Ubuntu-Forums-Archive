---
title: "Samba smb.cong/file permissions"
date: 2010-12-28
forum: General Help
---

### Post by galileo005 on 2010-12-28
I've got an ubuntu server setup, and I've mapped a network drive on my laptop(Vista) to to it. I use it as a web server to test out local websites and php code. 
Everything works fine except I have to use the chmod -R on each folder I create to allow file permissions to save, upload etc. I cannot use the security tab in the properties menu remotely from my laptop. 

The user I use on the server is andy, i.e. andy@server:~$ and in the security tab I see in the Group or Username box:
Everyone
andy (Unix Group\andy)
andy (ANDY\andy)

ANDY is also in my network folder along with ANDY-LAPTOP, both in the work group HOME.

I'm assuming it's something to do with my smb.conf file which is in /etc/samba/ (is that where it should be?)

Here is what is in my smb.conf file that is not commented out:

[global]
    netbios name = andy
    workgroup = HOME
    security = user
    null passwords = true
    wins support = yes
    
[MyFiles]
    path = /var/www/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0777
    directory mask = 0777

The /var/www/ folder is what my server folder on my laptop is mapped to.
I want to be able to give Everyone full control from my laptop. Is there something I'm missing or doing wrong?
Cheers for the help.

---

