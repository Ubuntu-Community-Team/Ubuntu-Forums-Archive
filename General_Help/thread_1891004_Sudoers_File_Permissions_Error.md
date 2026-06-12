---
title: "Sudoers File Permissions Error"
date: 2011-12-04
forum: General Help
---

### Post by eXtaticus on 2011-12-04
Recently, when I've been trying to use any "sudo" commands in the Terminal, it's been rejecting me and coming up with this error:

sudo: /etc/sudoers is mode 0666, should be 0440
sudo: no valid sudoers sources found, quitting

And then putting me back to the ordinary command line. This is urgent, as it renders in particular the "sudo apt-get" and "sudo -i" commands totally invalid; I can't install apps from the command line. I have absolutely no idea what caused this, neither do I have any idea how to fix it (probably something to do with chmod, but when I try that, it rejects me) - so any help would be greatly appreciated.

Thanks!

---

### Post by efflandt on 2011-12-04
Easiest way to fix it would be from install CD or bootable iso on USB.  But when you **sudo chmod** it from there, you need to begin with the path to your mounted internal hard drive before the etc/sudoers.

---

### Post by fdrake on 2011-12-04
> **eXtaticus said:**
> Recently, when I've been trying to use any "sudo" commands in the Terminal, it's been rejecting me and coming up with this error:

sudo: /etc/sudoers is mode 0666, should be 0440
sudo: no valid sudoers sources found, quitting

And then putting me back to the ordinary command line. This is urgent, as it renders in particular the "sudo apt-get" and "sudo -i" commands totally invalid; I can't install apps from the command line. I have absolutely no idea what caused this, neither do I have any idea how to fix it (probably something to do with chmod, but when I try that, it rejects me) - so any help would be greatly appreciated.

Thanks!
boot the os in  recovery mode(at boot time keep the shift key pressed untill u see the grub menu, press again shift to see the recovery menu) and from  there select shell prompt as root user:
once u login do :
```

chmod 440 /etc/sudoers
reboot now

```

---

### Post by eXtaticus on 2011-12-06
> **efflandt said:**
> Easiest way to fix it would be from install CD or bootable iso on USB.  But when you **sudo chmod** it from there, you need to begin with the path to your mounted internal hard drive before the etc/sudoers.

How do I do that?

EDIT: Forget it, I'm moving to Mint.

---

