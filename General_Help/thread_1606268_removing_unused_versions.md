---
title: "removing unused versions"
date: 2010-10-26
forum: General Help
---

### Post by Anil babu on 2010-10-26
how to remove
2.6.32-21  
2.6.32.24 from list OSs

---

### Post by lukeiamyourfather on 2010-10-26
Basically just ignore them. GRUB used to be relatively easy to edit but the "list" format has changed which makes it less friendly to edit and they (whoever made the list utility) suggest not to edit it. I wish the "startup manager" had a feature to rename or remove items but it doesn't. If anyone else knows of another utility I'd be interested too.

---

### Post by gwu777 on 2010-10-26
> **Anil babu said:**
> how to remove
2.6.32-21  
2.6.32.24 from list OSs

Because this bug me too this is how I do it. It works for me although I am not sure it is the best recommanded option.

1. I open nautilus as sudo:
```
sudo nautilus
```
2. Browse to system > boot
3. From there, remove all the files which do not have the latest kernel number - the one you want to keep. I personnaly move them to a "Old Kernel" folder just in case...
4. Update grub
```
sudo update-grub 
```

Be careful to remove only the unwanted file, ie the one with the old kernel number, otherwise your system will not boot.

I usually keep as well the memtest files.

Hope this helps.

---

### Post by Boondoklife on 2010-10-26
You can do this with Ubuntu Tweak I believe, check it out [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Quackers on 2010-10-26
> **Boondoklife said:**
> You can do this with Ubuntu Tweak I believe, check it out [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

That's how I clean my old kernels. I do leave a spare one though, for emergency use :-)

---

### Post by oldos2er on 2010-10-26
Use the package manager, which will automatically update grub for you. ```
sudo apt-get remove linux-image-2.6.32-21-generic linux-image-2.6.32-24-generic
```

---

### Post by gwu777 on 2010-10-26
> **Boondoklife said:**
> You can do this with Ubuntu Tweak I believe, check it out [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

I did give it a try and it is really cool and clean. i would advise it over my previous answer! :)

---

