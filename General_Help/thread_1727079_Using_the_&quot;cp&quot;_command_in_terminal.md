---
title: "Using the &quot;cp&quot; command in terminal"
date: 2011-04-12
forum: General Help
---

### Post by dragon1964m on 2011-04-12
I want to extract a working copy of a program from my laptop to my desktop. After searching around, I think I may be able to do this with the "cp" command in terminal. But, I am unsure what syntax I must use to do it.

Anyone with strong terminal-foo......can I do this and how?

---

### Post by matt_symes on 2011-04-12
Hi

If they are not networked up i would just copy the file onto a usb stick from the laptop and move the usb stick to the desktop and copy from that.

You can use nautilus to do this. No command line magic required.

Kind regards

---

### Post by Grenage on 2011-04-12
> **dragon1964m said:**
> I want to extract a working copy of a program from my laptop to my desktop. After searching around, I think I may be able to do this with the "cp" command in terminal. But, I am unsure what syntax I must use to do it.

Anyone with strong terminal-foo......can I do this and how?

Should you decide not to take the USB route, you could use scp:

```
scp */path/to/file* *remoteuser*@*remotehost*:/home/*remoteuser*/
```

For example:

```
scp /home/grenage/file1 bob@otherpc:/home/bob/
```
or:
```
scp /home/grenage/file1 bob@192.168.1.10:/home/bob/
```

---

### Post by matt_symes on 2011-04-12
Hi

As an addendum to Grenage's excellent reply above, i believe you will also have to ensure that openssh-server is installed on your dekstop for scp to work. (I am not 100% sure of this though).

```
sudo apt-get install openssh-server
```

Kind regards

---

### Post by Grenage on 2011-04-12
> **matt_symes said:**
> Hi

As an addendum to Grenage's excellent reply above, i believe you will also have to ensure that openssh-server is installed on your dekstop for scp to work. (I am not 100% sure of this though).

```
sudo apt-get install openssh-server
```

Kind regards

Ah touché, good catch!

---

