---
title: "Thunderbird email doesn't require password to use offline storage"
date: 2010-07-26
forum: General Help
---

### Post by Zorgoth on 2010-07-26
Is there a way to make Mozilla Thunderbird not allow anyone to view my offline storage without my password and to make it so whatever data it does store on my computer is encrypted with my password?  Or is there another client that will do this better?  I don't like the idea that anyone could waltz into my office and read my old emails.

---

### Post by prodigy_ on 2010-07-26
Try [this HOWTO](http://www.ehow.com/how_2272845_set-master-password-mozilla-thunderbird.html).

---

### Post by Zorgoth on 2010-07-26
That did not help; if you hit cancel, you will still be able to view my old emails.  Thanks though.  What I would really like to do would be to encrypt my old emails using my email password.

---

### Post by prodigy_ on 2010-07-26
You can use [TrueCrypt](https://help.ubuntu.com/community/TrueCrypt) to encrypt your Thunderbird profile. Additionally you can move the profile to a dedicated partition (using Thunderbird profile manager) and encrypt the whole partition.

---

### Post by Zorgoth on 2010-07-28
My whole hard drive is already encrypted; this is a company computer and I have to do that anyway.  I want to encrypt the profile in a way so that my past emails are only accessible by Thunderbird (or some other email client), and only when I am logged in to my email - basically I want to encrypt it with my email password - is there any way I can get this kind of functionality?

---

### Post by prodigy_ on 2010-07-28
If your files are already encrypted, why would you want to encrypt them twice? And when you're away from your desk, you can just lock Gnome with Ctrl+Alt+L.

---

