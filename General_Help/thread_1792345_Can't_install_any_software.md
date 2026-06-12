---
title: "Can't install any software"
date: 2011-06-28
forum: General Help
---

### Post by anton706 on 2011-06-28
I have a problem,suddenly I cant install any software and even I cant open synaptic when i try them it gives me an error the error is in the image.
Please help me fix that.

---

### Post by amjjawad on 2011-06-28
> **anton706 said:**
> I have a problem,suddenly I cant install any software and even I cant open synaptic when i try them it gives me an error the error is in the image.
Please help me fix that.

From Terminal:

```
sudo apt-get clean

sudo apt-get update

```

In case of error message, please post the output.

Also, you can try one thing before that. From Synaptic, go to:

Settings > Repositories > Download from > Click on the drop list arrows and choose  "Other ..." then Click on "Select Best Server". At the end, **Choose Server** and don't forget to Click "Reload" when you're done.

---

### Post by anton706 on 2011-06-28
It didn't help.Also I cant even open synaptic when I try I get this error and then it closes synaptic.

---

### Post by amjjawad on 2011-06-28
> **anton706 said:**
> It didn't help.Also I cant even open synaptic when I try I get this error and then it closes synaptic.

What is the output of:

```
sudo apt-get update

```

??

---

### Post by anton706 on 2011-06-28
E: Type 'launchpad.net/tiheum/equinox/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/tiheum-equinox-natty.list
E: The list of sources could not be read.

---

### Post by mcduck on 2011-06-28
> **anton706 said:**
> E: Type 'launchpad.net/tiheum/equinox/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/tiheum-equinox-natty.list
E: The list of sources could not be read.

Well, that error pretty much explains what's the problem.

The */etc/apt/sources.list.d/tiheum-equinox-natty.list* -file has a line in it that doesn't belong there. Fix the file or remove it and run "sudo apt-get update" again and things will start working again.

---

### Post by beew on 2011-06-28
In the terminal type

```
 
sudo rm /etc/apt/sources.list.d/tiheum-equinox-natty.list
sudo apt-get update 
```Basically  the file tiheum-equinox-natty.list is corrupted and has become unreadable and the first  command above gets rid of it.

---

### Post by anton706 on 2011-06-28
Thank you,it worked.

---

