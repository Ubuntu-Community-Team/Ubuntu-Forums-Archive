---
title: "Difficulties sharing folders using samba"
date: 2011-02-21
forum: General Help
---

### Post by lone_wolfII on 2011-02-21
I attempted to share my ~/Videos folder using the Folder Sharing dialog when right-clicking a folder in Nautilus. 
It started to install but failed partially spitting out some error that I didn't bother to read/write down. 
It asked me to restart which I did. But now when reattempting to share the folder, I get given the following message:

'net usershare' returned error 255: net usershare add: cannot create tmp file /var/lib/samba/usershares/:tmp0BRWpm

I've looked around for a thread for this particular error, but I can't find anything specific to the "cannot create tmp file" issue. 

I'm assuming it's some folder permission issue. I tried uninstalling and reinstalling samba from the Ubuntu Software Center. 

Any ideas?

Thanks.

---

### Post by flipNasty on 2011-07-27
I'm having this problem, as well... I've tried setting the permissions of /var/lib/samba/usershares/ to 755 and 777, with no luck... not really sure where to go from there, since fixing screwy permissions usually does it...

---

### Post by Kira_Belka on 2011-07-27
Hi guys.. how about smb.conf?

---

