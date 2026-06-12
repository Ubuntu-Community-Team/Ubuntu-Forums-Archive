---
title: "Virtual machine not saving files when I restart"
date: 2010-08-03
forum: General Help
---

### Post by dpatel304 on 2010-08-03
I'm running Arch Linux on a virtual machine and trying to save a file using Vi.  I save it using the :w command and am able to read it using the :r command just fine as long as I don't restart.  When I restart or shut down the virtual machine, all my data is lost.

Any help would greatly be appreciated, thanks in advance.

---

### Post by slooksterpsv on 2010-08-03
> **dpatel304 said:**
> I'm running Arch Linux on a virtual machine and trying to save a file using Vi.  I save it using the :w command and am able to read it using the :r command just fine as long as I don't restart.  When I restart or shut down the virtual machine, all my data is lost.

Any help would greatly be appreciated, thanks in advance.

What Virtualization software are you using, and are you opening a new file to write with:
vi filename.extension
or when you write the contents
:w filename.extension

---

### Post by dpatel304 on 2010-08-03
> **slooksterpsv said:**
> What Virtualization software are you using, and are you opening a new file to write with:
vi filename.extension
or when you write the contents
:w filename.extension

I'm using VirtaulBox.

I originally wasn't specifying an extension, but I just quickly tried it by giving the files a .vim extension, and still am not able to load it.

---

### Post by slooksterpsv on 2010-08-04
Sorry it took me so long, but my User CP wasn't showing thread replies for some reason. Anyways, are you using the snapshot feature? Can you create a file with pico/nano:
e.g.:
```

nano testfile.txt

```

Then type some text and press CTRL+o and enter to save, then ctrl+x, restart and see if the file is there.

Also where are you saving the files to, your home folder, or else where - give me the path. Also does the file start with a . in front so .tempfile or .textfile

---

### Post by dcstar on 2010-08-04
> **dpatel304 said:**
> **I'm running Arch Linux** on a virtual machine and trying to save a file using Vi.  I save it using the :w command and am able to read it using the :r command just fine as long as I don't restart.  When I restart or shut down the virtual machine, all my data is lost.

Any help would greatly be appreciated, thanks in advance.

And this fits into the **specific** purpose of this forum in what way?:
[I]
All your general support questions for **Ubuntu, Kubuntu, Edubuntu and Xubuntu**.[/I]

---

### Post by slooksterpsv on 2010-08-04
> **dcstar said:**
> And this fits into the **specific** purpose of this forum in what way?:
[I]
All your general support questions for **Ubuntu, Kubuntu, Edubuntu and Xubuntu**.[/I]

Can we get it moved to the Virtualization sub-forum then?

---

