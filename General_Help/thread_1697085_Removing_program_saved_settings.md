---
title: "Removing program saved settings"
date: 2011-02-28
forum: General Help
---

### Post by Mariane on 2011-02-28
I've had this problem before with firefox: too many pluggins and fiddling messed it up and no way to revert to a clean version. 

Now I'm having it with Audacity. 
```

sudo apt-get remove --purge audacity

``` 
does NOT remove some config files hidden who knows where. Proof is, when doing "open file" Audacity shows the directory from which I last opened a file. As it is not standard but a directory I created myself this shows Audacity has not been properly purged. 

And indeed, 
```

cd /
sudo find ./ -name audacity*

``` 

Finds loads of stuff which should have been purged but had not been removed. Most of them are of the type:
./usr/share/locale/it/LC_MESSAGES/audacity.mo
But there are others, too, one of which is bound to be the one telling audacity which directory was opened last. 

Did
```

cd /
sudo rm -rf audacity*

``` 
get rid of them? No. To get rid of them I had to go to the directories, one by one, and there do "sudo rm whatever". This took ages, and I didn't remove all the "audacity.mo" files, they look like something unimportant as long as I stick to English. 

It worked. The problem was that I had fiddled with the "export as mp3" settings, the resulting files didn't play, and I had no idea what the original default settings were. 

Please please please, teach me a command which is stronger than the "purge" above or tell me which files I should manually delete when I have that kind of problem. After all the whole point of typing:
```

sudo apt-get remove --purge something
sudo apt-get install samesomething

``` 
is to get a clean version with all the default settings, so there has got to be a way to do this... 

Mariane

---

### Post by runeh76 on 2011-02-28
Hi

I would love to know also this.
Sometimes i use ```
gksudo nautilus
``` to find leftover files after "remove" command


(have u tryed autoremove)?

---

### Post by peculiar penguin on 2011-02-28
> tell me which files I should manually delete when I have that kind of problem.**Always** start looking in your home directory. Settings are generally saved per  user so that different users can have different settings that don't  interfere with each other. This means the config files are going to be  located in each users' home directory, and not in a system location like  /usr or /etc (touching files there can be dangerous unless you really know what you're doing).

Most applications create a hidden directory (name starts with a dot ".", select View > Show Hidden Files in Nautilus or use ls -a on the command line to show them) for this.

I'm running 10.10 which comes with Audacity 1.3.12-beta, and in this case the config directory is named **.audacity-data** and located in my home directory as described above. Now guess what the file audacity.cfg in there does :p

---

### Post by Mariane on 2011-02-28
> **peculiar penguin said:**
> 
**Always** start looking in your home directory. 


Great info, thank you. As for autoremove I use it when it tells me "you can use autoremove to fix this", it had never occurred to me to use it without being prompted. :oops:

Mariane

---

