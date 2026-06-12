---
title: "I can't get rid of unity ?"
date: 2012-03-05
forum: General Help
---

### Post by garyed on 2012-03-05
I've read about getting rid of unit so much my eyes are bleeding.
I've been using Ubuntu for about 4 years now & this is by far the most frustrating thing I've come across. All I want to do is to get classic gnome back. I've got to where I can choose it logging in but I do automatic login & it always takes me straight to the unity desktop. I've got all my computers with auto login for different family members & I need to get them all to boot classic gnome. There has got to be a simple way to do this.
Can anyone tell me how? 

I'm using 11.10

---

### Post by An Sanct on 2012-03-05
use the "log out" command and then select "Gnome Classic" or "Ubuntu Classic" as the desktop from the choice list.

I hope this will keep the preferred desktop settings ;)

PS. I love unity .... khm ...

---

### Post by Frogs Hair on 2012-03-05
See this following link if you are using 11.10 , but fall back is not quite like Gnome 2.. Instead  of right clicking the panel to add items use Alt + Right Click. [http://ubuntuforums.org/showthread.php?t=1859960](http://ubuntuforums.org/showthread.php?t=1859960)

---

### Post by ajgreeny on 2012-03-05
You might like to investigate cinnamon DE; it's in its early development at the moment, and I've never seen it, but it is supposed to be just like gnome 2 (classic gnome as we knew it) but built on gnome-3 and gtk3 libraries etc etc.
[https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable](https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable)

---

### Post by garyed on 2012-03-05
I've been through all those steps in the first two replies & I can get gnome classic instead of unity but when I auto login it always goes back to unity.

---

### Post by LinuxFan999 on 2012-03-05
You could also try KDE, XFCE, and LXDE.

---

### Post by HiImTye on 2012-03-05
```
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-classic
```
should fix your problem

---

### Post by garyed on 2012-03-05
> **HiImTye said:**
> ```
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-classic
```
should fix your problem

Thank you very, that did the trick.

Now how can I run that command for other users on my computer?

---

### Post by HiImTye on 2012-03-05
that sets the *default* so you shouldn't need to do that, they will just select gnome-classic (no effects) at the login screen and they should enter a gnome-fallback session
after all, only one user logs in at boot up right?

---

### Post by 73ckn797 on 2012-03-05
Look here: [http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html](http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html)

---

### Post by HiImTye on 2012-03-05
> **73ckn797 said:**
> Look here: [http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html](http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html)
those are all unnecessary as he has a working linux installation right now, no need to subject him to possible problems down the road

---

### Post by garyed on 2012-03-05
> **HiImTye said:**
> that sets the *default* so you shouldn't need to do that, they will just select gnome-classic (no effects) at the login screen and they should enter a gnome-fallback session
after all, only one user logs in at boot up right?

That's true about just one user auto logs in but I want the other users to also default to gnome-classic so they don't have to change the desktop selection when they log in.

---

### Post by garyed on 2012-03-05
> **73ckn797 said:**
> Look here: [http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html](http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html)

Thanks for the idea but I'd rather not get that involved in deleting unity since I can get gnome classic working.

---

### Post by HiImTye on 2012-03-05
> **garyed said:**
> That's true about just one user auto logs in but I want the other users to also default to gnome-classic so they don't have to change the desktop selection when they log in.
they should only need to change the selection one time and then that selection will be remembered for subsequent logins

---

### Post by garyed on 2012-03-05
> **HiImTye said:**
> they should only need to change the selection one time and then that selection will be remembered for subsequent logins

That works O.K. too.

Thanks again

---

