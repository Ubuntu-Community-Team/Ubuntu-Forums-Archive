---
title: "Encrypting swap with unknown key's"
date: 2009-12-21
forum: General Help
---

### Post by Dad1985 on 2009-12-21
I want to encrypt my swap partition in a way that encryption is done on the flyu at boot, and I never want to know the key.  When I try and use things like cryptsetup, it always asks me for a key at boot and when I dont provide it one it just doesn't load the swap, which is expected. I don't want a key, I want it to randomly generate a long key and trash it at each restart, can this be done?

---

### Post by hugmenot on 2009-12-21
But since your swap is probably not your only encrypted partition, you would have to enter a key anyhow (for the permanent storage), wouldn&#8217;t you? What&#8217;s the point?

---

### Post by Dad1985 on 2009-12-21
> **hugmenot said:**
> But since your swap is probably not your only encrypted partition, you would have to enter a key anyhow (for the permanent storage), wouldn’t you? What’s the point?

My / and /home, etc can be unencrypted, Though id like my swap and /tmp to be encrypted, and id like to never know the key.  Never knowing the key allow me to never be coerced into giving it and in certain jurisdictions like that in the UK, failure to give up an encrypted key means 5 years in prison.  if you never knew the key, then they certainly cannot ask you for it.

im not claiming I have anything to hide as I dont, id just like to learn how to do this, as I know it to be possible.

---

