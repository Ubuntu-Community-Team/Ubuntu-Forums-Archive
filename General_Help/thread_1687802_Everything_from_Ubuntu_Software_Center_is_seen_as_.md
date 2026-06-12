---
title: "Everything from Ubuntu Software Center is seen as untrusted"
date: 2011-02-14
forum: General Help
---

### Post by ~Middle on 2011-02-14
Hello, i could really do with some help, basically every package is seen as untrusted and it is stopping me from upgrading or updating, and to install packages i have to do it from apt-get and say that i trust the source.

Would it be possible for someone to help me over TeamViewer?

Thanks a lot for any responses

---

### Post by zhogan85 on 2011-02-14
I had this same problem recently. To solve, go to synaptic, then settings -> repositories and then in ubuntu software as well as other software, make sure all the boxes are ticked and make sure whichever update boxes that you want are ticked. I think this should do it for you. I don't know how they came unticked on my system but this worked for me.

---

### Post by ~Middle on 2011-02-14
Thanks for your reply,

Basically it is impossible for me to install something from USC because if i do it says i need to do a partial upgrade, then i get a massive list of packages that aren't authorised:

[http://ubuntuforums.org/showthread.php?t=1687149](http://ubuntuforums.org/showthread.php?t=1687149)

I would really appreciate it if someone could TeamViewer with me to help me out!

Thanks a lot

---

### Post by wojox on 2011-02-14
What version are you using? Did you install the minimal .iso and build it yourself?

---

### Post by ~Middle on 2011-02-14
I am using Ubuntu 10.10 Maverick Meerkat, I think the reason that this has happened is this:

[http://ubuntuforums.org/showthread.php?t=1685440](http://ubuntuforums.org/showthread.php?t=1685440) (Look at the whole thread, sorry)

In addition my PC has frozen 5 times since this has happened, i do OC my system, but this is strange it looks software lated not hardware...

Thanks a lot

---

### Post by ~Middle on 2011-02-14
Bump, my PC froze again, but with optimised default settings for my hardware, so there is something wrong with the software...

---

### Post by wojox on 2011-02-15
I would do the partial upgrade. You removed 100 packages accidentally?

What worse could happen? :p 

Run from the terminal:

```
sudo apt-get update; sudo apt-get upgrade; sudo apt-get dist-upgrade
```

---

### Post by ~Middle on 2011-02-15
OK now, as soon as i log into my account my PC (or GFX card?) freezes, and i have no control over the machine...

Do you think that this is a hardware or software issue?

And how can i boot into text mode? Like how can i get the grub menu with memtest86+ etc on it?

Thanks a lot

---

### Post by ~Middle on 2011-02-15
OK, well that went horribly, i now can't boot into the DE as i get an error, like when gnome-desktop was uninstalled. 

I try to do 

apt-get upgrade

but get:

dpkg: error processing /var/cache/apt/archives/udev_164-3_amd64.deb

And a few more bits relating to that... what can i do?!

I think that i will lug my PC downstairs and give it a connection to the network so i can do apt-get update, but i am not hopeful. Any suggestions will be really really appreciated!

Thanks

---

### Post by ~Middle on 2011-02-15
I am being suggested that i should do a clean install, but i REALLY don't want to. Can anyoen else offer any advice?

Maybe ssh to my box and have a look?

---

