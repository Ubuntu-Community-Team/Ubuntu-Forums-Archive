---
title: "ProFTPd User Based Permissions?"
date: 2009-10-04
forum: General Help
---

### Post by n0an on 2009-10-04
Hello,

I just got Ubuntu 8.04 on my server. I have installed and am running 4 ftps including the admin's. I want to have user-based permissions on folders. 

> How to install and configure FXP with proftpd?

> How do I make user-based permissions for the same folder? Like A and B both have different access to the same folder.

> Does proftpd have any multi-thread settings? I cannot utilize my full upload speed. It max out at 430 kbps or so in FTP to FTP transfers. 


Please explain in details as I have never done it before. 

Thanks,

n0an

---

### Post by Lars Noodén on 2009-10-04
Do you want there accounts to download **from** your computer or upload **to** it, or both?

If the answer includes upload **to** your computer, then SCP and SFTP should be used instead of FTP.  With FTP, the usernames and passwords are sent unencrypted over the net and eventually will be intercepted.  SCP and SFTP are part of the package OpenSSH and if you like a graphical interface to upload/download via SFTP, you have [Filezilla](http://filezilla-project.org/).  Even though it is advertised as an FTP client (that's the word most people are familiar with) it is easy to use for SFTP.  

If the answer is download only, then FTP is ok.

---

### Post by n0an on 2009-10-04
I want to know the permissions to add in the .conf file.

 <Directory ./abc/*>
<Limit>
AllowUser rootftp
...
...
<Limit>

I want to understand the permissions. Also, some directories I recently created have a lock icon on them in the GUI. It doesn't let the root account delete anything saying it's not the owner. How do I remove that?

---

