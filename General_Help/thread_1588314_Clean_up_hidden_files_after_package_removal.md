---
title: "Clean up hidden files after package removal"
date: 2010-10-04
forum: General Help
---

### Post by dodo3773 on 2010-10-04
I have noticed that after I uninstall a package from my system the hidden files in my home directory are still there. For example I used to have an application called proxychains installed. But then after I uninstalled it with the Ubuntu Software Center there was still a .proxychains folder in my home folder. Is there a way to remove all these files? Also are they stored anywhere else except home? I ask because I would like to clean up my system and I am O.K. with reconfiguring my applications if I do decide to install them at a later date.

---

### Post by seanarickymurphy on 2010-10-04
Tryed "sudo apt-get autoremove" in Terminal? or "sudo apt-get autoclean" "Sudo apt-get clean"?

---

### Post by bodhi.zazen on 2010-10-04
> **seanarickymurphy said:**
> Tryed "sudo apt-get autoremove" in  Terminal? or "sudo apt-get autoclean" "Sudo apt-get clean"?

That only works for system files.

> **dodo3773 said:**
> I have noticed that after I uninstall a package from my system the hidden files in my home directory are still there. For example I used to have an application called proxychains installed. But then after I uninstalled it with the Ubuntu Software Center there was still a .proxychains folder in my home folder. Is there a way to remove all these files? Also are they stored anywhere else except home? I ask because I would like to clean up my system and I am O.K. with reconfiguring my applications if I do decide to install them at a later date.

For files in your home directory you can safely ignore them, or remove them manually, or use a tool such as bleachbit. Take care with tools such as bleachbit that you do not remove too much =)

---

### Post by northrup on 2010-10-04
```
sudo apt-get clean
```

That gets rid of any package files left over.

The stuff in the home directory is safe to delete if you don't plan on re-installing the software.  Just make sure there's nothing in there that you want to keep.

---

### Post by cgroza on 2010-10-04
Those are left behind just in the case you will install the package again , you settings will not be lost.

---

### Post by tgm4883 on 2010-10-04
Perhaps this would help

```
apt-get purge packagename
```

---

### Post by dodo3773 on 2010-10-04
> **tgm4883 said:**
> Perhaps this would help

```
apt-get purge packagename
```

Alright, so I tried 

sudo apt-get clean
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get purge proxychains
          It said that proxychains was not installed so I installed it again and ran sudo apt-get purge proxychains again and even after running all these commands the folder is still there. I checked out bleachbit and it looked like just all the same commands we just tried.

---

### Post by scouser73 on 2010-10-05
I use Bleachbit, as bodhi.zazen mentioned, you should give that a go.

---

### Post by dodo3773 on 2010-10-05
> **scouser73 said:**
> I use Bleachbit, as bodhi.zazen mentioned, you should give that a go.
Is it the .DS_Store option or something under Deep scan? I have tried a lot of the other options with no luck.

---

### Post by tgm4883 on 2010-10-05
It's going to be on a per application basis whether it removes the folder in your home dir or not. A lot of application don't delete things from /home

---

### Post by dodo3773 on 2010-10-05
> **tgm4883 said:**
> It's going to be on a per application basis whether it removes the folder in your home dir or not. A lot of application don't delete things from /home

I guess that it's just something that I will have to do manually for now. I think that really is the answer (for now). Just like bodhi.zazen said I will just have to clean it up myself. Thanks for all the quick replies. Marking this thread as solved for now.

---

