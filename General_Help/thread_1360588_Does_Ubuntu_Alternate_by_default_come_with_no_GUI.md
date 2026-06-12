---
title: "Does Ubuntu Alternate by default come with no GUI?"
date: 2009-12-21
forum: General Help
---

### Post by ftp on 2009-12-21
Thanks for clicking in this thread and take a look at this low level question.:P

I have two Ubuntu Alternate installed in my VMware Workstation as virtual machines, and they both come up with no GUI after installing. I just wonder if it by default comes with no GUI?

Thanks you!

---

### Post by muteXe on 2009-12-21
Are they definately alternate installs and not server installs?
Was the install text-based?

---

### Post by RodGer GR on 2009-12-21
I installed once Ubuntu Hardy Heron on a friends computer because there was some ram problems. The installation procedure was text based and there was no option for a live session but the installed system had a GUI like any other typical ubuntu desktop system. Only the server edition comes without GUI by default.

Why did you choose the alternate and not the standard cd?

---

### Post by ftp on 2009-12-21
Thanks for your replies.

> **muteXe said:**
> Are they definately alternate installs and not server installs?
Was the install text-based?
Yes, I'm sure they are alternate installs and not server installs. And that was text-based.

> **RodGer GR said:**
> I installed once Ubuntu Hardy Heron on a friends computer because there was some ram problems. The installation procedure was text based and there was no option for a live session but the installed system had a GUI like any other typical ubuntu desktop system. Only the server edition comes without GUI by default.

Why did you choose the alternate and not the standard cd?
Are you sure only the server edition comes without GUI by default? I have installed Ubuntu 9.10 Karmic Koala both 32bit and 64bit, after installation they are all text-based. Are there any difference betwen Hardy Heron and Karmic Koala for the Alternate edition?

Actually I do installed standard cd, but I also wanted to install alternate editions for some testing purpose.

---

### Post by ftp on 2009-12-21
I'm now starting install Ubuntu 9.10 Alternate on a physical box to see if this is the case. Once I'm done I will update on this.:)

---

### Post by slakkie on 2009-12-21
You can install a GUI-less Ubuntu with the alternate CD but you can also install a desktop machine with the alternate CD.

In case you do not have a GUI, simply install one:

```

# Get a list of all the -desktop packages ubuntu ships with
aptitude search tu-desktop 
# And install one of the choices
sudo aptitude install ubuntu-desktop 

```

---

### Post by ftp on 2009-12-21
> **slakkie said:**
> You can install a GUI-less Ubuntu with the alternate CD but you can also install a desktop machine with the alternate CD.

In case you do not have a GUI, simply install one:

```

# Get a list of all the -desktop packages ubuntu ships with
aptitude search tu-desktop 
# And install one of the choices
sudo aptitude install ubuntu-desktop 

```


Thanks for your suggestion, I'm now installing ubuntu-desktop. :)

---

