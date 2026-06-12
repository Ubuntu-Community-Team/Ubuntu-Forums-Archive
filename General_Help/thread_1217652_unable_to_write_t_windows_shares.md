---
title: "unable to write t windows shares"
date: 2009-07-19
forum: General Help
---

### Post by bowens44 on 2009-07-19
I am having a problem writing to windows shares on my network.

Up until recently everything worked fine.

I mount the shares at boot in fstab:

//192.168.5.3/MP3 /media/music cifs credentials=/root/.smbcredentials,_netdev,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.5.3/Photos /media/photos cifs noperm,credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.5.3/data /media/data cifs noperm,credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0


I am able to copy files from these shares to my linux box without issue.
When I try to write to the shares the files begin to copy and then I get an error that says :

error writing to file, resource temporarily unavailable. Occasionally I'll get an error that says 'broken pipe'

Any idea what is causing this? How do I trouble shoot it?

I am running ubuntu 9.04 and attempting to copy to share on a box that has windows xp.

---

