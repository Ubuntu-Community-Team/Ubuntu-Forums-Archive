---
title: "Can Ubuntu software center install multiple software at a time yet?"
date: 2010-04-09
forum: General Help
---

### Post by Macfunky on 2010-04-09
Really love Ubuntu and want to upgrade to lucid when it comes out (currently using jaunty) as i have heard nothing but good about it. My problem is i did try karmic but one big thing that put me off was the Ubuntu software center and the fact that i could only install one piece of software at a time. This is very annoying as i use a lot of software. When i reinstall a system i like to be able to choose everything i use, install, sit back and have it done in one go. 

Also i'm wondering will lucid have synaptic? If not can i install it through the Ubuntu software center?

---

### Post by kellemes on 2010-04-09
> **Macfunky said:**
> If not can i install it through the Ubuntu software center?

Yes.
But you can also do from a terminal-window..
```
sudo apt-get install synaptic
```

---

### Post by aeiah on 2010-04-09
lucid beta has synaptic, but you can just install it through the software center if the final doesn't, or using 
```

sudo apt-get install synaptic

```
or
```

sudo aptitude install synaptic

```

i can't answer your software center question as i don't think ive used it or the add / remove software thing since ubuntu 5.10

---

### Post by arubislander on 2010-04-09
> **Macfunky said:**
> Really love Ubuntu and want to upgrade to lucid when it comes out (currently using jaunty) as i have heard nothing but good about it. My problem is i did try karmic but one big thing that put me off was the Ubuntu software center and the fact that i could only install one piece of software at a time. This is very annoying as i use a lot of software. When i reinstall a system i like to be able to choose everything i use, install, sit back and have it done in one go. 

Also i'm wondering will lucid have synaptic? If not can i install it through the Ubuntu software center?

What a lot of users seem not to notice is that Software Center does not require you to wait until the current installation is finished before installing the next piece of software... You can click install on one program and while it's downloading and / or installing you can select another to install, it will then be added to the queue.

But both Karmic and Lucid have synaptic installed I think.

---

### Post by lovinglinux on 2010-04-09
> **Macfunky said:**
> When i reinstall a system i like to be able to choose everything i use, install, sit back and have it done in one go.

Use [UMarks](http://lovinglinux.megabyet.net/?page_id=534) extension for Firefox. I developed it to do exactly that. You can install all your software at once after an clean install of Ubuntu. You can do that from command-line or from Synaptic, but with the extension is as simple as clicking a button. Additionally, you can keep different versions of your installation backups and search the installed packages on popular web sites.

---

