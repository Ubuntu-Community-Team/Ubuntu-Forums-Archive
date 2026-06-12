---
title: "Virtualbox users group"
date: 2010-01-06
forum: General Help
---

### Post by unclesamslair on 2010-01-06
I get this error when I try to start virtualbox

```

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```

I added myself to the vboxusers group and logged off and on and rebooted but it still gives me the same error. help?

---

### Post by jmate24 on 2010-01-06
reinstall vbox.

---

### Post by todak on 2010-01-06
Don't reinstall. Open the **Users and Groups** under **System >Administration**. Click on the key to give you root privileges for this program. Click on the user name you want to check and click the **Properties** button. Under **User Privileges** tab, scroll down and see if the **Use VirtualBox** box is checked.

---

### Post by unclesamslair on 2010-01-06
I went to add/remove and found out that apparently virtualbox wasn't installed. So I try to install.
```

Cannot install 'virtualbox-ose'

This application conflicts with other installed software. To install 'virtualbox-ose' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

```

so I got to synaptic and remove the virtualbox-ose package. same error.

---

### Post by dcstar on 2010-01-07
> **unclesamslair said:**
> I get this error when I try to start virtualbox
........


Look in the Virtualization forum, lots more VM stuff there.

---

