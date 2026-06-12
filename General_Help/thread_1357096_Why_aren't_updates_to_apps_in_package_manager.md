---
title: "Why aren't updates to apps in package manager?"
date: 2009-12-16
forum: General Help
---

### Post by Pingster on 2009-12-16
There are updates, now, for five programs, each of which I got through Synaptic Package Manager; but the updates aren't shown in Synaptic, only the old versions.  Why don't the sources get updated regularly?

---

### Post by Tclarkie on 2009-12-16
go into preferences and set the updates you want to be able to see

---

### Post by 3rdalbum on 2009-12-16
> **Pingster said:**
> There are updates, now, for five programs, each of which I got through Synaptic Package Manager; but the updates aren't shown in Synaptic, only the old versions.  Why don't the sources get updated regularly?

Ubuntu is a "stable software" distribution. The only time there are program updates is when there's a security issue or a critical bugfix, and only when the software is in "main".

Remember, Ubuntu is an enterprise distribution. The last thing they want is a system administrator applying updates across a network, and the next morning having frustrated users complaining that the feature they use has moved.

You can get new software updates by looking for a "PPA" (Personal Package Archive repository) to add to your Software Sources that contains later versions of the software.

---

### Post by Pingster on 2009-12-16
> go into preferences and set the updates you want to be able to see     I assume you mean the **Always prefer the highest version** option.  I have that selected.

> Ubuntu is a "stable software" distribution. The only time there are program updates is when there's a security issue or a critical bugfix, and only when the software is in "main".

Remember, Ubuntu is an enterprise distribution. The last thing they want is a system administrator applying updates across a network, and the next morning having frustrated users complaining that the feature they use has moved.

You can get new software updates by looking for a "PPA" (Personal Package Archive repository) to add to your Software Sources that contains later versions of the software.I was afraid of that.  I'll have to look into getting PPAs for some of the programs I have.

---

### Post by dcstar on 2009-12-17
> **Pingster said:**
> There are updates, now, for five programs, each of which I got through Synaptic Package Manager; but the updates aren't shown in Synaptic, only the old versions.  Why don't the sources get updated regularly?

If you want newer versions select the Backports repository option and newer packages for the next Ubuntu release may become available for your release.

---

### Post by Pingster on 2009-12-17
> **dcstar said:**
> If you want newer versions select the Backports repository option and newer packages for the next Ubuntu release may become available for your release.
Thanks.  I found an update to another program that way.

---

