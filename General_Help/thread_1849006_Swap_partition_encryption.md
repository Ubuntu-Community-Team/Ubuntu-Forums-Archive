---
title: "Swap partition encryption"
date: 2011-09-23
forum: General Help
---

### Post by riph72 on 2011-09-23
Hello all,

I've searched for answers on this, but can't seem to find anything conclusive, so...

When using the "encrypt home folder" option (i.e. ecryptfs), is it necessary to take further measures to encrypt the swap partition, with 10.04 and onwards, or is it automatic?  I specify the version because I understand the answer might have changed from 9.10/10.04 onwards?

Regards,
Richard.

---

### Post by chazinams on 2011-09-23
As I understand it in order to encrypt the swap you need to do whole disk encryption. Using 11.04 and previous you need the alternate-CD to set this up. But far as I've heard beginning with 11.10 you will be able to do whole disk encryption with the default Live CD.

The Home encryption setup only encrypts home. All the other stuff, like Temp and Swap are not encrypted.

---

### Post by bodhi.zazen on 2011-09-23
You can encrypt swap with ecryptfs, but it is not set up by default when you encrypt your home directory.

---

### Post by patryk77 on 2011-09-23
One alternative would be to disable the swap partition and use a swap file instead (~/.swap)

Though that would require some hacking, as you would have to run swapon on login, once the partition is mounted unencrypted, and may not be ideal for multi-user environments.

[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

---

### Post by riph72 on 2011-09-24
> **bodhi.zazen said:**
> You can encrypt swap with ecryptfs, but it is not set up by default when you encrypt your home directory.

Would I be right in thinking I need to use:

ecryptfs-setup-swap

...to do this?  I did read some web pages that implied this was done by default with later versions of Ubuntu - I guess from the fact I can still hibernate, this is bad information?

Seeing as encrypted swap seems quite important, why isn't it done by default?  Is it purely because of the hibernation issue?

Regards,
Richard.

---

### Post by bodhi.zazen on 2011-09-24
> **riph72 said:**
> Would I be right in thinking I need to use:

ecryptfs-setup-swap

...to do this?  I did read some web pages that implied this was done by default with later versions of Ubuntu - I guess from the fact I can still hibernate, this is bad information?

Seeing as encrypted swap seems quite important, why isn't it done by default?  Is it purely because of the hibernation issue?

Regards,
Richard.

See [http://manpages.ubuntu.com/manpages/natty/man1/ecryptfs-setup-swap.1.html](http://manpages.ubuntu.com/manpages/natty/man1/ecryptfs-setup-swap.1.html) for details

---

### Post by riph72 on 2011-09-24
> **bodhi.zazen said:**
> See [http://manpages.ubuntu.com/manpages/natty/man1/ecryptfs-setup-swap.1.html](http://manpages.ubuntu.com/manpages/natty/man1/ecryptfs-setup-swap.1.html) for details

I looked at this link, ended up reading an interview with Dustin Kirkland, who states:

***Slo-Tech**: What about swap partition?*
 ***Dustin Kirkland**: Encrypting swap is critically important for *any* system where encryption of any kind is performed -- not just eCryptfs.*
 *If  you use the Ubuntu CD installer to setup your system with an Encrypted  Home Directory, your swap space will automatically be encrypted for you,  using dmcrypt and a randomly generated key at boot time. This keeps you  from being prompted for a passphrase at boot time, however, it will  break hibernation support (suspend is unaffected).*
 *Personally, I  just don't use swap space at all. If I'm swapping to disk, then  performance is really suffering, and I add more RAM to my system :-) *



If this is right, great, but my hibernation works... perhaps this was resolved in 10.04 ?  I did read somewhere that it was a "known issue", so perhaps a fix was planned?


That interview was in Jan 2010 by the way.

---

### Post by Paddy Landau on 2011-10-15
I recently installed 11.04, and specified an encrypted home file on installation.

The swap partition was automatically encrypted.

Hibernation works.

---

### Post by riph72 on 2011-10-15
> **Paddy Landau said:**
> I recently installed 11.04, and specified an encrypted home file on installation.

The swap partition was automatically encrypted.

Hibernation works.

Are you sure swap is encrypted, how are you checking?  Perhaps it's been sorted for 11.04 then.

I actually contacted Dustin Kirkland about this, he gave me instructions to check if swap was encrypted, and said if hibernation worked then it almost certainly wasn't.  But that was for 10.04...

---

### Post by Paddy Landau on 2011-10-15
> **riph72 said:**
> Are you sure swap is encrypted, how are you checking?

[LIST=1]
[*] Look at your swap partition with gparted. It shows as an unknown file system.
[*]Look at your swap partition with Disk Utility. It also shows it as unknown, but in the Partition Type it shows it as a Linux swap.
[*]Look at your file /etc/fstab. It loads the swap partition using /dev/mapper/cryptswap1.
[/LIST]

---

### Post by riph72 on 2011-10-15
> **Paddy Landau said:**
> [LIST=1]
[*] Look at your swap partition with gparted. It shows as an unknown file system.
[*]Look at your swap partition with Disk Utility. It also shows it as unknown, but in the Partition Type it shows it as a Linux swap.
[*]Look at your file /etc/fstab. It loads the swap partition using /dev/mapper/cryptswap1.
[/LIST]

Fair enough, mine is like that now, but wasn't prior to making the required change for swap, despite having an encrypted home folder.

I'm guessing that there's been a change between 10.04 and 11.04++ then...

Regards,
Richard.

---

### Post by Paddy Landau on 2011-10-15
> **riph72 said:**
> I'm guessing that there's been a change between 10.04 and 11.04++ then...
It must have been. My 10.04 had a normal swap partition.

---

