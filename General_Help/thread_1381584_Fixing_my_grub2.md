---
title: "Fixing my grub2"
date: 2010-01-14
forum: General Help
---

### Post by Jackzor on 2010-01-14
I'm not sure what I did but my grub menu has gone to looking ...Old.

I don't like it. When I first had ubuntu installed grub was very bland but still nice looking. It was just black with a white box outlined with white text inside.

Now it is a black background and the box is blue.

I can't stand it! Any ideas as to how to get it back to the way it was?

---

### Post by john newbuntu on 2010-01-14
My guess is that you got upgraded from Grub legacy to Grub2.  Here is an exhaustive documentation on how you can customize your splash image:

[https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot](https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot)

---

### Post by Jackzor on 2010-01-14
I already had grub2 though! Lol.

---

### Post by Jackzor on 2010-01-15
Okay. I think this is what I did. I followed the very first part of this:
[https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)
But I quit halfway through and I just want to undo it all
How could I do that?

---

### Post by ranch hand on 2010-01-15
You should be able to undo that by getting rid of the burg ppa and then running;
```

sudo grub-install /dev/sda

```
and;
```

sudo update-grub

```
the "sda" needs edited to meet your needs.

You should also check your grub files to make sure that they are clean.  Hopefully you backed them up before you started messing with burg.

My link in my sig will help you understand the new grub a little better and the second link is the best in depth info you  can get.

If things do not straighten out to where they were you ca nalways go to synaptic and remove grub-common and grub-pc and then reinstall them (do not reboot until you re-install unless you really like to chroot from the CD).

---

### Post by Jackzor on 2010-01-15
output for sudo update-grub

```
nicholas@nicholas-laptop:~$ sudo update-grub
Generating grub.cfg ...
No path or device is specified.
Try ``/usr/sbin/grub-probe --help'' for more information.
No path or device is specified.
Try ``/usr/sbin/grub-probe --help'' for more information.

```

EDIT:

This output is what was happening BEFORE you posted ranch hand

Just so you know

---

### Post by ranch hand on 2010-01-15
I think that you better try the install command first and then the update.

If that does not work I would really think about getting rid of grub and reinstalling unless you really know your way around in the grub files.

It looks to me like you really have some corruption there somewhere.  Was this a clean install of 9.10 or an update?

Edit

Is the /etc/grub.d.30_os-prober file enabled in permissions to be executable?

---

### Post by Jackzor on 2010-01-15
> **ranch hand said:**
> 
If things do not straighten out to where they were you ca nalways go to synaptic and remove grub-common and grub-pc and then reinstall them (do not reboot until you re-install unless you really like to chroot from the CD).

This fixed it for the most part. Thank you very much. I guess I should have thought about that before posting. Now all I have to do is get the resolution set back as it was. But I'll figure that out on my own. Thanks man!

---

### Post by ranch hand on 2010-01-15
Some of us kind of went nuts for grub2 after the initial shock at Karmic-testing A2 when it was dumped, as grub1.98, in our laps with no documentation.

It is a lot of fun to play with.  It seems cumbersome at first.  It is actually more agile and adaptable than grub0.97.

Right now I am trying to modify a theme for plymouth for an install of 10.04-testing.  Some folks play computer games.  I think the computer is a game.

In testing it is sometimes a real rough game.  Sometimes just kind of fun.

---

