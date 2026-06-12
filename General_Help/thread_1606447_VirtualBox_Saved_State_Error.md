---
title: "VirtualBox: Saved State Error"
date: 2010-10-26
forum: General Help
---

### Post by Sailor5 on 2010-10-26
Ahoy Sailors!

So I was trying to create a new saved state when suddenly Virtual Box broke, Upon starting it back up again I've gotten this error.```
Hard disk '/home/zack/.VirtualBox/Machines/TinyXP/Snapshots/{f6777506-37c2-4a23-b158-f18475ab6217}.vdi' with UUID {f6777506-37c2-4a23-b158-f18475ab6217} cannot be directly attached to the virtual machine 'TinyXP' ('/home/zack/.VirtualBox/Machines/TinyXP/TinyXP.xml') because it has 1 differencing child hard disks.
Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {99404f50-dd10-40d3-889b-dd2f79f1e95e}
```

What all this then?

Thanks Bye!

---

### Post by JohnSearle on 2011-01-22
> **Sailor5 said:**
> Ahoy Sailors!

So I was trying to create a new saved state when suddenly Virtual Box broke, Upon starting it back up again I've gotten this error.```
Hard disk '/home/zack/.VirtualBox/Machines/TinyXP/Snapshots/{f6777506-37c2-4a23-b158-f18475ab6217}.vdi' with UUID {f6777506-37c2-4a23-b158-f18475ab6217} cannot be directly attached to the virtual machine 'TinyXP' ('/home/zack/.VirtualBox/Machines/TinyXP/TinyXP.xml') because it has 1 differencing child hard disks.
Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {99404f50-dd10-40d3-889b-dd2f79f1e95e}
```

What all this then?

Thanks Bye!

Was this ever solved? I ran into the same problem.

---

### Post by CharlesA on 2011-01-22
I actually ran into that the other day. I was able to get around it by starting the VM back up, but it didn't restore to the previous state.

Basically it acted as if it was powered off.

---

### Post by JohnSearle on 2011-01-22
> **CharlesA said:**
> I actually ran into that the other day. I was able to get around it by starting the VM back up, but it didn't restore to the previous state.

Basically it acted as if it was powered off.

Thanks for the reply.

Yeah, I just did the same thing. I actually unmounted the whole volume and remounted it. Too bad I lost my state, I was in the middle of something that was processing for two days straight at that point.

---

