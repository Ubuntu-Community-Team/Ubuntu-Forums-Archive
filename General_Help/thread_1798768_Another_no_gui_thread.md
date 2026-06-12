---
title: "Another no gui thread"
date: 2011-07-06
forum: General Help
---

### Post by irishbrian on 2011-07-06
As the title may explain, I find myself without a GUI. I had installed Ubuntu 11.04 64bit with no issues really. 
Ignoring the why, I then installed gnome3 for some extra desktop customisability. However, I found there were some issues with it, which I assumed were due to a conflict of interest between Unity and gnome3. So ... I uninstalled gnome3. Please stop facepalming.
So, when I reboot my system I now find I'm stuck at a terminal prompt. I can't reinstall the ubuntu-desktop as it says I need to update first. 
When trying to update it just keeps saying that it "Failed to fetch ..." all my packages. 
Help. Dear God help. :(

---

### Post by dragonfly41 on 2011-07-06
Perhaps retrace your last step of uninstalling gnome3?

[http://techhamlet.com/2011/05/how-to-install-gnome-3-on-ubuntu-11-04/](http://techhamlet.com/2011/05/how-to-install-gnome-3-on-ubuntu-11-04/)

---

### Post by irishbrian on 2011-07-06
thanks for the reply.

> sudo ppa-purge ppa:gnome3-team/gnome3

this has been done. So gnome3 is gone. But it took *something* with it, and I can't trace what exactly that something is.

because the apt-get update doesn't work, I couldn't even reinstall it if I wanted to.

Can I reinstall the GUI without having to do a completely fresh install?

---

### Post by wildmanne39 on 2011-07-07
Hi, it is better to wipe the partitions a do a fresh install I have helped people how have done what you done and it is better to reinstall, when you remove gnome3 it leaves gtk3 behind and it conflicts with gtk2.

---

### Post by Crempel on 2011-07-08
> **wildmanne39 said:**
> Hi, it is better to wipe the partitions a do a fresh install I have helped people how have done what you done and it is better to reinstall, when you remove gnome3 it leaves gtk3 behind and it conflicts with gtk2.

Hi, I also got gnome 3 installed, but unity works quite well, the only funny thing is that most open application windows have no control buttons and a few other minor issues. 

I would like to revert to gnome 2 w/o doing a clean install and I can afford to risk stuffing gnome altogether since I also got LXDE working very nicely. Can I remove the gtk3 "left overs"? If you think it is too risky just say "no" and I will forget about it.

Thank you very much in advance.:)

---

### Post by irishbrian on 2011-07-08
> **wildmanne39 said:**
> Hi, it is better to wipe the partitions a do a fresh install I have helped people how have done what you done and it is better to reinstall, when you remove gnome3 it leaves gtk3 behind and it conflicts with gtk2.

This is what I ended up doing. I couldn't figure a way around it, and with only the terminal I found it quite difficult to undo the "work" I had done. For some reason I also couldn't connect to the internet, which I believe was my major problem, as I couldn't update any of the packages again.

I could probably have connected somehow, but didn't have the time or patience to figure that out, I had stuff to do. :(

[quote= Crempel ]I would like to revert to gnome 2 w/o doing a clean install and I can  afford to risk stuffing gnome altogether since I also got LXDE working  very nicely. Can I remove the gtk3 "left overs"? If you think it is too  risky just say "no" and I will forget about it.[/quote]

From my experience, if you don't want to do a full reinstall, leave it alone. If you can't work around it, back everything up, thread carefully, and get the install cd cleaned and ready to go ...

---

### Post by wildmanne39 on 2011-07-08
> **Crempel said:**
> Hi, I also got gnome 3 installed, but unity works quite well, the only funny thing is that most open application windows have no control buttons and a few other minor issues. 

I would like to revert to gnome 2 w/o doing a clean install and I can afford to risk stuffing gnome altogether since I also got LXDE working very nicely. Can I remove the gtk3 "left overs"? If you think it is too risky just say "no" and I will forget about it.

Thank you very much in advance.:)
Hi, I personally would reinstall, but I have seen one person say that he used commands to remove gnome3 but he had problems afterwards and it took him days to sort it out, I helped by looking at some files and he had gtk3 still installed with gtk2 he manually removed the files and I think he got it to work, but he did not post how he removed the files and he said that it would have been easier to reinstall.

---

### Post by Crempel on 2011-07-09
> **wildmanne39 said:**
> Hi, I personally would reinstall, but I have seen one person say that he used commands to remove gnome3 but he had problems afterwards and it took him days to sort it out, I helped by looking at some files and he had gtk3 still installed with gtk2 he manually removed the files and I think he got it to work, but he did not post how he removed the files and he said that it would have been easier to reinstall.

Thank you wildmanne39, I'll do a reinstall.

---

