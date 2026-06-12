---
title: "GPG/PGP keys: some advice, please"
date: 2010-03-25
forum: General Help
---

### Post by Muscovy on 2010-03-25
I recently generated a GPG key for managing a PPA. While stumbling thought building packages, I realised I had set an expiry on my key.

Is setting an expiry dangerous for any services I would use?

---

### Post by km0r3 on 2010-03-26
> **Muscovy said:**
> I recently generated a GPG key for managing a PPA. While stumbling thought building packages, I realised I had set an expiry on my key.

Is setting an expiry dangerous for any services I would use?

What do you define as *dangerous* in this case? Loosing your credentials?

AFAIK you can edit the expiry date, as long as you know your password to your PGP key.
If you're using the PGP in order to communicate with Launchpad then setting no expiry date would be recommended, but you can have multiple keys assigned to your Launchpad User Account.

Hope this helps. :)

---

