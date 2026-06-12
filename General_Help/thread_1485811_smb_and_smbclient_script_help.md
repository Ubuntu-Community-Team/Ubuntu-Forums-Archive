---
title: "smb and smbclient script help"
date: 2010-05-17
forum: General Help
---

### Post by mcclunyboy on 2010-05-17
Hi,

I am trying to replace FTP with smbclient but would need help.

What do I script?

I have:
   ftp -n >> $OUTLOG << EOF2 

        open **[COLOR=red]IPADDRESS[/COLOR]** 
        user **[COLOR=red]USERNAME PASSWORD[/COLOR]** 
        cd $DIREXTERNAL 
        get $FILEEXTERNAL1 $OUTFILE1.bak1 
        get $FILEEXTERNAL2 $OUTFILE2.bak2 
        bye 
        EOF2 
  
any help is useful..

---

### Post by mcclunyboy on 2010-05-17
quick thought this should meet my requirements, i can't test at the minute so hoping someone has used theese commands in a script and let me know what they did..

smblcient //hostname/directory password -U username
put/get/cd
bye

---

