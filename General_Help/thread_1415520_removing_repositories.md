---
title: "removing repositories"
date: 2010-02-24
forum: General Help
---

### Post by ionray on 2010-02-24
Hey,
I've been trying to get a program working.  I have narrowed it down to where I have to remove something I got from the repository.  I cant find any information on how to remove using google ( is there sudo I can use in the terminal?).

Thanks,
Ryan

---

### Post by Ozymandias_117 on 2010-02-24
If you're referring to removing a package you installed, you can use "sudo apt-get remove *packagename*" or, if you want to also get rid of configuration files, use purge instead of replace

---

### Post by 3rdalbum on 2010-02-24
> **ionray said:**
> Hey,
I've been trying to get a program working.  I have narrowed it down to where I have to remove something I got from the repository.  I cant find any information on how to remove using google ( is there sudo I can use in the terminal?).

Thanks,
Ryan

Why, won't Synaptic Package Manager let you remove it?

---

### Post by lavinog on 2010-02-24
Can you give us some more details?  Did you install the package with synaptic, software center, or with the command line?

---

### Post by ionray on 2010-02-24
I used the command line to get and install the package which i thought it was screwing up a program im trying to install so i used "sudo apt-get remove [I]packagename" to remove it.  But i still have the same problem as i did before.  So thanks so much for all your help i thought it would have been a bit harder to get rid of them :S.
[/I]

---

