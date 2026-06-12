---
title: "held broken packages when trying to activate nvidia drivers"
date: 2009-11-19
forum: General Help
---

### Post by Irishpolyglot on 2009-11-19
After having some problems booting into Ubuntu and [needing to remove the xorg.conf file]("http://ubuntuforums.org/showthread.php?t=1324329"), I finally decide that pixelly movies is not good enough and in the hardware drivers, I selected the latest nvidia driver 190 that was working for me previously and "Activate" and get this error:
> SystemError: E:Unable to correct problems, you have held broken packages. 
I ran both ```
sudo apt-get install -f
```
and
```
sudo dpkg --configure -a
```
But this doesn't help.

I'm in 64 bit Ubuntu on a Dell XPS M1730

---

### Post by arnab_das on 2009-11-19
see if this helps:

[http://thoughtsndreams.wordpress.com/2009/10/23/installing-nvidia-drivers-in-ubuntu/](http://thoughtsndreams.wordpress.com/2009/10/23/installing-nvidia-drivers-in-ubuntu/)

---

### Post by Irishpolyglot on 2009-11-21
That's done it!! :D
Many thanks :)

---

### Post by Scott O'Nanski on 2009-12-30
That blog has been deleted.

Could you repost the solution?

---

### Post by anthonie on 2010-01-19
> **Scott O'Nanski said:**
> That blog has been deleted.

Could you repost the solution?

Idem
Looking for a solution but it seems difficult to find.
Tries the webarchive but the owner of the former blog had a robot.txt file on the server, preventing the webarchive to archive the page... Nice...

---

### Post by plucky on 2010-01-19
> **Scott O'Nanski said:**
> That blog has been deleted.

Could you repost the solution?

Could it be [this?](http://exploreubuntu.wordpress.com/2009/10/23/installing-nvidia-drivers-in-ubuntu/)

Also probably out of date.Use **System > Administration > Hardware Drivers** to install the Nvidia drivers.


Good Luck

---

### Post by arnab_das on 2010-03-25
> **plucky said:**
> Could it be [this?](http://exploreubuntu.wordpress.com/2009/10/23/installing-nvidia-drivers-in-ubuntu/)

Also probably out of date.Use **System > Administration > Hardware Drivers** to install the Nvidia drivers.


Good Luck

thanks for reposting. and as u said, right now its far better to install it via System >Administration > hardware drivers.

i had to rename that blog, the name was so irrelevant. :) in case u come across any links on my blog kindly replace "www.thoughtsndreams.wordpress.com" with "www.exploreubuntu.wordpress.com". the rest portion of the link remains the same (i have simply exported my blog).

---

