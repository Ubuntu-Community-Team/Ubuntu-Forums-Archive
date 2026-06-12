---
title: "SWAT - issues creating new users?"
date: 2010-03-24
forum: General Help
---

### Post by squalex on 2010-03-24
Hi,

I just installed swat on a ubuntu 9.10 and configured it.
I had a previous very simple samba config before.

So everything works fine with my old users (from the previous config) but won't work with new users...

I tried to add them through the password tab swat web based interface but they wouldn't show up on my smbusers file. So I tried *sudo gedit /etc/samba/smbusers* and added them manually. But I still can't access the shares with these new usernames...

I also tried *sudo smbpasswd -a newuser* but still the same...

And everything seems right in the smb.conf new users are there.

I'm new with all this, hope someone can help me.
Thanks!

---

