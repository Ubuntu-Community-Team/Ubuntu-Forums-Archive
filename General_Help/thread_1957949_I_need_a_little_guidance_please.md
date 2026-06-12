---
title: "I need a little guidance please"
date: 2012-04-13
forum: General Help
---

### Post by blueguns on 2012-04-13
A few months ago, I upgraded to 11.10 from 11.04 on my old Dell Power Edge 400.
 I'm using the dual boot system because I need XP to update my Garmin and like to play backgammon online.Every other function has migrated to Ubuntu.

With 11.04 my computer was superman. Everything from boot up to opening Libre Office documents was incredibly fast.

 When 11.10 came out, I decided it had to be better so I installed it.

 For my box, that was a huge mistake. Everything slowed to almost a crawl. It is like running Win 3.1 on an old 486 chip.:icon_frown:

I found and downloaded 11.04 to my flash drive and want to re-install it.
 I know people have had problems with the "downgrade" but they are trying to install it over 11.10.

 I have copied my home folder to a disc to save my work.

 What I need to know is, how should I format and partition the current linux space to wipe 11.10 entirely so I can start afresh.

 I don't pretend to "know" linux and just consider myself a happy user.

 I am really appreciative of you folks being here and always willing to help.

 Also, hats off to the people that run and administer this group. I know it can be a thankless job, so THANKS.

---

### Post by JRV on 2012-04-13
The 12.04 LTS version will be released at the end of the month. If I were you I would wait until it is released, then backup your data, and do a fresh install of 12.04.

---

### Post by blueguns on 2012-04-13
> **JRV said:**
> The 12.04 LTS version will be released at the end of the month. If I were you I would wait until it is released, then backup your data, and do a fresh install of 12.04.

 Thanks for the update.

 Am I wrong in thinking that 11.10 just requires more resources than did 11.04, and am I the only one that's experienced this?

 What are the 12.04 beta testers saying about it?

Thanks again.

---

### Post by abyrne on 2012-04-13
> Am I wrong in thinking that 11.10 just requires more resources than did 11.04, and am I the only one that's experienced this?
Possibly. If 3D Visual FX were enabled on the new Unity interface that came with 11.10, then yes, that is probably the source of your slowdown.  

> What are the 12.04 beta testers saying about it?
I guess I could consider myself a beta tester. It's coming along nicely, and if you're not crazy about the new Unity interface, this version makes it much easier to switch back to GNOME Classic. Performance improvements are there, too.

Personally, I prefer Lubuntu. Mostly because I like to revive old machines, but also because I'll take cleanliness, speed, and stability over 3D effects any day.

Oh, and definitely do a clean install. Distribution upgrades are notoriously buggy.

---

### Post by Hungry Man on 2012-04-13
I don't know about specific performance improvements but 12.04 starts up and shuts down very quickly for me compared to Windows 7 and 11.10. There are definitely performance improvements that I'm noticing.

---

### Post by blueguns on 2012-04-13
[QUOTE=abyrne;11841418]Possibly. If 3D Visual FX were enabled on the new Unity interface that came with 11.10, then yes, that is probably the source of your slowdown.  


How can I find that out and disable it if needed?

Thanks.

---

### Post by blackangelpr on 2012-04-14
> **blueguns said:**
> [QUOTE=abyrne;11841418]Possibly. If 3D Visual FX were enabled on the new Unity interface that came with 11.10, then yes, that is probably the source of your slowdown.  


How can I find that out and disable it if needed?

Thanks.

if i do not miss understood then here is your answer:

instead of ubuntu session choose Ubuntu2d instead and if you did not install compiz you should not be using any 3d FX now..):P

---

### Post by blueguns on 2012-04-14
> **blackangelpr said:**
> [QUOTE=blueguns;11842286]

if i do not miss understood then here is your answer:

instead of ubuntu session choose Ubuntu2d instead and if you did not install compiz you should not be using any 3d FX now..):P

 Thanks mucho.

 If I can figure out how to save my home folder, I'm going to migrate to Lubuntu.

 I think that will meet my needs.

---

### Post by Spyderkid on 2012-04-14
basically in short, you can't "downgrade", you can only re-install an older version of Ubuntu.

If you want superspeed use ubuntu 10.04 it was the best for speed and stability

You can wait for ubuntu 12.04 which will be super stable, but may not be that fast, seeing as it uses a unity derivative.

---

### Post by blueguns on 2012-04-14
basically in short, you can't "downgrade", you can only re-install an older version of Ubuntu.

[I]If you want superspeed use ubuntu 10.04 it was the best for speed and stability

You can wait for ubuntu 12.04 which will be super stable, but may not be that fast, seeing as it uses a unity derivative.[/I]
__________________

Thanks. That I understand.

 My problem is that I want to migrate to Lubuntu 12.04 but I don't know how to save all of my home folder with it's hidden files. It's like 2 gigs worth of data. I really don't want to lose all my work.

 I don't know enough about adding a separate partition to park it in. I'm thinking I could burn it to a DVD and add it back to the new install.

I'm also a little confused how to wipe the existing distro to make room for the new one.

 Maybe I should have posted this in the complete newbie forum. I'm feeling pretty Forest Gumpish right now.

 Thanks everyone for your suggestions.
 As we say here in Texas, Ahh preciate ya.

---

### Post by 2F4U on 2012-04-14
The hidden folders in your home directory usually contain configuration information that belongs to your current desktop environment(s). So, if you are going to install Lubuntu, you wouldn't need this information since you install a different desktop environment.

> I'm also a little confused how to wipe the existing distro to make room for the new one.

When the installation comes to the partitioning screen, select "Something else" and just select the existing partitions to use for the new installation. You should at least format the root partition, but its up to you if you want to format the home partition.

---

### Post by blueguns on 2012-04-16
> **2F4U said:**
> The hidden folders in your home directory usually contain configuration information that belongs to your current desktop environment(s). So, if you are going to install Lubuntu, you wouldn't need this information since you install a different desktop environment.



When the installation comes to the partitioning screen, select "Something else" and just select the existing partitions to use for the new installation. You should at least format the root partition, but its up to you if you want to format the home partition.



 Thank you everyone. 

I really wish I had more time to devote toward learning more about this fantastic OS.

---

### Post by abyrne on 2012-04-16
I might be too late, but you really don't need to reinstall Ubuntu/Lubuntu! Lubuntu can easily be installed in your current Ubuntu installation by running
```
sudo apt-get install lubuntu-desktop
```
then you can logout, click the small ubuntu logo next to your name in the login screen, and then select Lubuntu (or LXDE, can't remember which).

---

