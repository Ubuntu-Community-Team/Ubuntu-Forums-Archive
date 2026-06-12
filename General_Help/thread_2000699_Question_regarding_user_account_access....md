---
title: "Question regarding user account access..."
date: 2012-06-10
forum: General Help
---

### Post by Baldrick_NZ on 2012-06-10
Hi all,

My wife and I are using 12.04 on a laptop with different user profiles. I hold the admin rights, she is a standard user.

We dual boot with Vista. Whenever she wants to access files from her own Vista profile, in Ubuntu, it always asks for my password (admin) to allow the Vista drive to mount.

Is there anyway that we could either override the password issue altogether, or have it so she can enter her login password, and have her keychain remember it?

I've also noted that if she is logged on, and has access to the Vista profile, that I can't mount the same Vista partition on my Ubuntu user profile. Can this be changed?

Any help would be greatly appreciated!

---

### Post by wilee-nilee on 2012-06-10
> **Baldrick_NZ said:**
> Hi all,

My wife and I are using 12.04 on a laptop with different user profiles. I hold the admin rights, she is a standard user.

We dual boot with Vista. Whenever she wants to access files from her own Vista profile, in Ubuntu, it always asks for my password (admin) to allow the Vista drive to mount.

Is there anyway that we could either override the password issue altogether, or have it so she can enter her login password, and have her keychain remember it?

I've also noted that if she is logged on, and has access to the Vista profile, that I can't mount the same Vista partition on my Ubuntu user profile. Can this be changed?

Any help would be greatly appreciated!

Not sure of a fix, but why would she not have admin, that is the stock user setup.

---

### Post by Baldrick_NZ on 2012-06-10
Found the answer here, for any else whose interested.

Post #3, worked a treat.

[http://ubuntuforums.org/showthread.php?t=1988698&highlight=automount+drives](http://ubuntuforums.org/showthread.php?t=1988698&highlight=automount+drives)

---

### Post by rk0r on 2012-06-10
Depending what install you have going i would partition your HDD 

* ubuntu
*windows
*share


You can store any documents on the share partition and access them on both ubuntu and windows. 

:)

---

### Post by zombifier25 on 2012-06-10
> **Baldrick_NZ said:**
> Found the answer here, for any else whose interested.

Post #3, worked a treat.

[http://ubuntuforums.org/showthread.php?t=1988698&highlight=automount+drives](http://ubuntuforums.org/showthread.php?t=1988698&highlight=automount+drives)

There's an easier (and much cleaner) way to do this though, and it works with any partitions. Open /usr/share/polkit-1/actions/org.freedesktop.udisks.policy then go to this section:
```

<action id="org.freedesktop.udisks.filesystem-mount-system-internal">

```
Then modify this part of that section:
```

    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>

```
to
```

    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>**yes**</allow_active>
    </defaults>

```

---

