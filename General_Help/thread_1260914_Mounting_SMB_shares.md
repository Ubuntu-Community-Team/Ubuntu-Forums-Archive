---
title: "Mounting SMB shares?"
date: 2009-09-08
forum: General Help
---

### Post by Jungle-Cat on 2009-09-08
Hey all,
So I´ve just used netboot to install a base Ubuntu system and then used apt to install xubuntu-desktop. Also installed samba, fusesmb and other networking related tools (Though not related to smb)

Now, I can´t mount any shares. In windows I just go \\hostname\share, and I believe that last time I used Ubuntu Nautilus supported this by going smb:\\hostname\share. 

Now, in Xubuntu I´m a bit stuck. I´ve tried using mount -t smbfs -o etc... but it says the mount point is invalid.

I simply want to mount \\hostname\share in ~smb (/home/user/smb/), which I believe I can then access by Thunar etc or simply cd /home/user/smb/share ?

Simply advise any additional info required and I´d be glad to indulge :)

Thanks

Edit: So I've had a look through synaptic... consequently removed fusesmb seeing as I saw i don't need it since I have samba and libsmbclient. I don't intend to host any shares on this machine, hence should I maybe only have fusesmb and not samba?

---

