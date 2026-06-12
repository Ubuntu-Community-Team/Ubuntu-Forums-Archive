---
title: "Custom Named Public/Private Key Not Working"
date: 2012-09-12
forum: General Help
---

### Post by Xplorer4x4 on 2012-09-12
I run Kubuntu but I suspect this applies to all variants of Ubuntu so I chose that prefix.

I need to set up keys for multiple server so I want to use custom name files for my keys. For example, trying to set up keys for my local NAS I do:
> xplorer4x4@xplorer4x4-MS-7673:~/.ssh$ ssh-keygen -t rsa
Generating public/private rsa key pair.                                                                                                                                                     
Enter file in which to save the key (/home/xplorer4x4/.ssh/id_rsa):wdlive
Enter passphrase (empty for no passphrase):                                                                                                                                                 
Enter same passphrase again:                                                                                                                                                                
Your identification has been saved in wdlive.                                                                                                                                               
Your public key has been saved in wdlive.pub.                                                                                                                                               
The key fingerprint is:                                                                                                                                                   
80:{EDITED}8d:ef xplorer4x4@xplorer4x4-MS-7673                                                                                                               
The key's randomart image is:
{EDITED}
[email]xplorer4x4@xplorer4x4-MS-7673:~/.ssh[/email]$ ssh-copy-id -i ~/.ssh/wdlive.pub root@192.168.1.160
root@192.168.1.160's password: 
Now try logging into the machine, with "ssh 'root@192.168.1.160'", and check in:
  ~/.ssh/authorized_keys
to make sure we haven't added extra keys that you weren't expecting.

When I check ~/.ssh/authorized_keys on the NAS, I see my key is listed, but I still get a password prompt. I guess I need to do something special in this case?

EDIT: Solved. Minuets after returning to google I found that I needed to add
```
Host *
IdentityFile ~/.ssh/wdlive.pub
```
to my ~/.ssh/config file. If you need to add other keys just add another line that says:
IdentityFile ~/.ssh/configsomekeyfile.pub

---

