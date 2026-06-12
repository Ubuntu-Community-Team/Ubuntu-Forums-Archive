---
title: "How to backup 'Private Directory'?"
date: 2011-04-13
forum: General Help
---

### Post by IamAcoconut on 2011-04-13
After an upgrade gone wrong my 9.10/10.4 is unbootable and I see no way to fix it. 

I can't mount the directory now (LiveCD or chroot), it probably has something to do with the breakage and/or pre-existing ecryptfs issues, as I have both login and mount passphrases. 

And it's all on one partition too, so before reinstalling I have to back up.

[LIST]
[*]How can I back up the encrypted directory?
[*]And can I transplant it to a fresh Ubuntu installation?
[/LIST]

*cp* complains about symlinks, returning 'not permitted', is this normal?

**ETA**: Now that I look at it from LiveCD .ecryptfs and Private appear as broken symlinks (what do they link to anyway??), but when I tried to copy them while chrooting, they were both accessible directories (though still couldn't mount or copy) - I don't get it.

---

### Post by IamAcoconut on 2011-04-15
Bump.
No way to extract data after system breaks down?

---

### Post by IamAcoconut on 2011-04-18
Simple, you have to look for something like /home/user/.ecryptfs/user/.Private
Also backup the wrapped passphrase if you hadn't unwrapped and written it down before.

After all I managed to decrypt the data from another LiveCD, maybe the newer ecryptfs made it easier, or you just have to keep trying.

---

