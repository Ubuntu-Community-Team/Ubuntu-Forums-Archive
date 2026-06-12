---
title: "backup-manager can't access ReadyNAS"
date: 2012-02-06
forum: General Help
---

### Post by panorack on 2012-02-06
I can't get backup-manager to use the 'backup' share on my ReadyNas. The problem seems to be the spaces used by the nas box for its shares' addresses. 

When mounted the address is shown in Nautilus as 'backup on nas-xx-xx-xx'. I have altered the target address in backup-manager to /'home/username/.gvfs/backup on nas-xx-xx-xx' but get an error message that the file doesn't exist.

I have managed to work around these spaces when using a terminal by putting the address in "" but that doesn't work for backup-manager, neither does using underscore or hyphens.

The app works perfectly when using the default target location of /var/archives so the problem has to be accessing the nas box. Can anyone offer any ideas.

Many thanks for taking the time to read this and for any suggestions you can offer.

panorack

---

### Post by Rafterman414 on 2012-02-06
Try typing in this for the target

/home/username/.gvfs/backup\ on\ nas-xx-xx-xx

The \ should tell it that there is a space in the filename in the terminal but I am not sure how the backup-manger handles spaces

---

### Post by panorack on 2012-02-06
Thanks for the reply. It didn't work with backup-manager but it's good to know how to deal with spaces when working in a terminal. 

Thanks.

---

