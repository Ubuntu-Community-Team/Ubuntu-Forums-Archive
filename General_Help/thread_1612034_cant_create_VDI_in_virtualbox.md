---
title: "cant create VDI in virtualbox"
date: 2010-11-02
forum: General Help
---

### Post by eival on 2010-11-02
this is for Ubuntu 10.4

i cant create a VDI or anything else beyond that point without root access, however if i open virtualbox with sudo privileges from the terminal(which ive already went through), once i go to open it normally from the launcher in the Applications list those changes arent there.

here is the error i get

```
Failed to create the hard disk storage test.vdi.
Could not create the directory
'/home/marcus/.VirtualBox/HardDisks' (VERR_ACCESS_DENIED).

Details
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: VirtualBox
Interface: IVirtualBox {3f36e024-7fed-4f20-a02c-9158a82b44e6}

```


in 8.04 we use to have an option in the System tab for applying access to non root users, but in 10.4 the only similar option is User Groups, an the only options that seem similar to this issue is "mount user space file systems" and "use virtualbox virtualization solutions" neither of which have any effect.

is there a new way to apply non root users with root access in 10.4?

---

### Post by Barriehie on 2010-11-02
> **eival said:**
> this is for Ubuntu 10.4

i cant create a VDI or anything else beyond that point without root access, however if i open virtualbox with sudo privileges from the terminal(which ive already went through), once i go to open it normally from the launcher in the Applications list those changes arent there.

here is the error i get

```
Failed to create the hard disk storage test.vdi.
Could not create the directory
'/home/marcus/.VirtualBox/HardDisks' (VERR_ACCESS_DENIED).

Details
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: VirtualBox
Interface: IVirtualBox {3f36e024-7fed-4f20-a02c-9158a82b44e6}

```


in 8.04 we use to have an option in the System tab for applying access to non root users, but in 10.4 the only similar option is User Groups, an the only options that seem similar to this issue is "mount user space file systems" and "use virtualbox virtualization solutions" neither of which have any effect.

is there a new way to apply non root users with root access in 10.4?

So you've added your user to the group that manages virtualbox? i.e. ```

gksu users-admin
```

---

