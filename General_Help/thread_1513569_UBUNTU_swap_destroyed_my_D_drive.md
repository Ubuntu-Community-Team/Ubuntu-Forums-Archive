---
title: "UBUNTU swap destroyed my D drive"
date: 2010-06-19
forum: General Help
---

### Post by dcstewie on 2010-06-19
Hi,

I had C and D drives on Vista. I then created E and installed UBUNTU on it. During installation I've specified D as UBUNTU swap drive. I can't access the D drive any more from windows Vista. Are my files on D deleted? Can I recover them?

Thanks

---

### Post by lesny on 2010-06-19
Partition was formated as swap partition, so it will be hard to recover some filesm i suppose.

---

### Post by gdonwallace on 2010-06-19
If any files where on that drive when you formatted it for swap, and they are / were windows files, they will be gone.:(

Much like formatting a drive to reinstall a OS, formatting a part of the drive (i.e. partition) as swap, Linux will wipe whatever data is on that drive and format it to be used as swap.  The other issue is that each OS will set a flag on the formatted partition / drive so that it knows what that drive is being used for and if it can access that drive.  Windows cannot read or access a partition formatted for swap, so it will see it as unformatted or inaccessible.  

I am sad to say, but anything that was on that drive is most likely gone, now can't be read by Windows, or inaccessible to Linux.

---

