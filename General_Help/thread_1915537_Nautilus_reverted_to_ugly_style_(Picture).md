---
title: "Nautilus reverted to ugly style? (Picture)"
date: 2012-01-26
forum: General Help
---

### Post by mace2 on 2012-01-26
Hi, I have a fresh install of Ubuntu 11.10. I'm not sure what happened but Nautilus looks awful, and no icons are showing.

I have 11.10 on another computer and it looks fine. I tried rebooting after seeing another thread but it didn't help.

What should I do? Thanks!

Pic: 

[IMG]http://i.imgur.com/fvt0m.png[/IMG]

---

### Post by ajgreeny on 2012-01-26
Are both machines running 11.10?  Your picture looks typical of nautilus in 11.10 as far as I can remember, as I gave up on that, and unity, and went back to 10.04.

I agree with you that it's ugly, but I think you are stuck with it if you want 11.10, though there may be ways to change it somehow, perhaps in gconf-editor, even though that has now almost lost any of the power it had in gnome2.

---

### Post by shevin on 2012-01-26
I have ubnuntu 11.10 64bit

it happened to me too ! after I did last nightupdates , however after re-starting, everything went back to normal

---

### Post by mace2 on 2012-01-26
> **shevin said:**
> I have ubnuntu 11.10 64bit

it happened to me too ! after I did last nightupdates , however after re-starting, everything went back to normal

Ah weird. Restarting didn't work for me unfortunately.

Little bump, hoping someone has a solution. :popcorn:

---

### Post by MG&amp;TL on 2012-01-26
That's unthemed gtk3. I don't know why it's doing that though.

You could try one of:

Installing gnome-tweak tool and setting the icon theme/gtk theme to  the ubuntu ones

Resetting unity.

---

### Post by mace2 on 2012-01-30
Update on this, I noticed that it looks like it should when I do a sudo nautilus. Could this be a permissions problem? What can I do?

I tried the gnome-tweak but that did not seem to work exactly. I now have some basic icons in Nautilus but it's not the default Ubuntu theme, Ambiance or Radiance or whatever.

Thanks.

---

### Post by Cheesemill on 2012-01-30
> **mace2 said:**
> I noticed that it looks like it should when I do a sudo nautilus

That's your problem. You should never use sudo with graphical apps because it can break things. You should always use gksudo instead. See here fore more details:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

By using sudo you've most probably changed the nautilus configuration files in your home folder to be owned by root instead of your normal user.

You should be able to fix this by doing:
```
sudo chown -R user:user /home/user
```replacing all instances of user in the above command with your actual username.

---

### Post by mace2 on 2012-01-31
> **Cheesemill said:**
> That's your problem. You should never use sudo with graphical apps because it can break things. You should always use gksudo instead. See here fore more details:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

By using sudo you've most probably changed the nautilus configuration files in your home folder to be owned by root instead of your normal user.

You should be able to fix this by doing:
```
sudo chown -R user:user /home/user
```replacing all instances of user in the above command with your actual username.

Thanks! This worked perfectly. Kudos!

---

