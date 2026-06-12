---
title: "SSD, Trim &amp; Full Disk Encryption"
date: 2012-08-19
forum: General Help
---

### Post by Ceiber Boy on 2012-08-19
I installed Ubuntu 12.04 using the alternate install image onto an 120GB SSD. during install i created a boot partition and a encrypted partition (Extended) containing the root file system and home directory.

Question:
As its an SSD i want to enable 'TRIM', with the possible complication of and extended encrypted partition is this still as simple as adding the 'TRIM' argument in the 'fstab' file or is their a further process i need to go through?

Thanks

If you feel that you require further information please ask.

---

### Post by Bobhuber on 2012-08-19
> **Ceiber Boy said:**
> I installed Ubuntu 12.04 using the alternate install image onto an 120GB SSD. during install i created a boot partition and a encrypted partition (Extended) containing the root file system and home directory.

Question:
As its an SSD i want to enable 'TRIM', with the possible complication of and extended encrypted partition is this still as simple as adding the 'TRIM' argument in the 'fstab' file or is their a further process i need to go through?

Thanks

If you feel that you require further information please ask.

[http://askubuntu.com/questions/162476/how-to-check-if-trim-is-working-for-an-encrypted-volume](http://askubuntu.com/questions/162476/how-to-check-if-trim-is-working-for-an-encrypted-volume)

---

### Post by kurci2 on 2012-08-19
I believe this should defenitely solve your problem =)

[http://worldsmostsecret.blogspot.com/2012/04/how-to-activate-trim-on-luks-encrypted.html](http://worldsmostsecret.blogspot.com/2012/04/how-to-activate-trim-on-luks-encrypted.html)

Works fine for me.

---

### Post by Ceiber Boy on 2012-08-20
> **kurci2 said:**
> I believe this should defenitely solve your problem =)

[http://worldsmostsecret.blogspot.com/2012/04/how-to-activate-trim-on-luks-encrypted.html](http://worldsmostsecret.blogspot.com/2012/04/how-to-activate-trim-on-luks-encrypted.html)

Works fine for me.Job done.
Thanks

---

### Post by kurci2 on 2012-08-20
My pleasure =)

---

