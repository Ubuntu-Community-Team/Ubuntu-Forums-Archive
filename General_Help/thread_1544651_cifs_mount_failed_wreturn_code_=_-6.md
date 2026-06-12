---
title: ": cifs_mount failed w/return code = -6"
date: 2010-08-02
forum: General Help
---

### Post by KLStringer on 2010-08-02
I'm trying to mount a samba share from one Ubuntu server to another Ubuntu server and keep getting:

: cifs_mount failed w/return code = -6

I've searched cifs error codes on google and can't find anything about what it means. Anyone know what it means or has a link to a cifs error codes sheet?

Thanks in advance

---

### Post by Muttley99 on 2010-08-02
You could testparm your config file! 
Or better still use NFS if your not serving to a windows machine.
try findsmb on the client to see if the share is available.

---

### Post by KLStringer on 2010-08-02
It's being shared in a Windows environment and I know both shares are there because I can get to them from my XP PC. I'm consolidating recordings from a temp backup storage server that was used while we got the new permanent server up and running, now I need to get all the recordings moved over to the new server but keep getting that error when I try to mount the share. 

Thanks for the suggestion.

---

### Post by KLStringer on 2010-08-02
Ha, I got it working, seams that error code -6 means that the share path syntax isn't right I was trying to mount //%servername%/mnt/recordings/recordings while that is the path to the share the samba share path is only //%servername%/recordings/

---

### Post by anurag.awasthi on 2012-01-09
Hi Dear,
 
Could you please update me from where I can get the list of CIFS error code with their description. Please help on this query.
 
Thanks in advance.
 
chhers,

---

