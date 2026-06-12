---
title: "Menu editing in Gnome changes KDE menu?!"
date: 2006-05-24
forum: General Help
---

### Post by Caligula on 2006-05-24
Alright, this is weird...
When I delete something from the Gnome menu, it disappears from the KDE menu as well...
I'm going to check if it's happenning the other way round...

Is there any way around it?
At the moment I've got all the KDE apps in Gnome and all the Gnome apps in KDE... it's a mess...

thanks,
josh](*,) :-D 

P.S. another question popped into my head with those smilies... why is this site not entirely supporting khtml?!

---

### Post by Caligula on 2006-05-24
hmmmm....
it's not happening the other way roung, which means they can eventually coexist, but it's going to be an absolute nightmare...

And now one asks the question, if it's possible, and it's not the same menu file or something, the why does the Alacarte editor delete from the KDE menu?!

should I file a bug?

and, is there an easy way to do it?
](*,) :confused: :D

---

### Post by Sef on 2006-05-24
> When I delete something from the Gnome menu, it disappears from the KDE menu as well...
I'm going to check if it's happenning the other way round...

It sounds like that you installed Ubuntu then Kubuntu (or vice-versa), so you have a choice of which desktop to boot into.  Since they are sharing the same partition, then what affects one will affect the other.

> Is there any way around it?

You would need to install them on two separate partitions.

---

### Post by kko1 on 2006-05-25
Hello.

[QUOTE=Caligula]When I delete something from the Gnome menu, it disappears from the KDE menu as well...
Is there any way around it?[/QUOTE]

The question of the KDE and Gnome menus affecting each other has come up quite a lot of times. Often, too, the suggestion to "install them on separate partitions and dual boot" is offered as a "solution". This  isn't really necessary, and, I believe, not what many would want.

[SIZE="1"]Now, if you want to dual boot, please do - I am in no way opposed to that. If you don't want to dual boot, there are other options. ;)

Granted, the co-existence of different desktop environments, and the resulting tidyness of the menus in each, leaves a bit to be desired. Also, some people do like to keep all their programs in a combined menu, and some like to separate them completely. Currently, the option to choose between these isn't as flexible / usable as it could be.[/SIZE]


_Now, here's how it works:_

The menus are based on *.desktop* -files that reside (as I understand) in a number of directories, most notably /usr/share/applications. KDE and Gnome both respect the *OnlyShowIn=* (and probably also *NotShowIn=*) -settings, which can be added to any of these files. These can read for instance *OnlyShowIn=GNOME* or *OnlyShowIn=KDE*.

There is a standard for desktop entries in here: [http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html). How far do KDE and Gnome adhere to this standard (i.e. whether they fulfill it yet), I can't tell.

A forum search on "how to keep kde and gnome menus separate" turns up quite a lot of threads, many of them are relevant to this topic. As a disclaimer, I have to say that I am not currently using Gnome, so I haven't tested and can not vouch for any of the methods working, but from what I gather, they more or less do what they're supposed to.

- If you only want to change (hide) a few items, you can edit them manually, which is easy to do.

- Second, a lot of the threads provide scripts that will _try_ to add a "OnlyShowIn=KDE" -entry to all KDE-applications' .desktop files at once, or similarly for Gnome. These scripts have inherent _risks_ in them (if there's a mistake in the script or simply a typing error), but with the files-to-be-modified _backed up_, you should be able to restore the system to what it was before. These two threads should get you started:
[http://www.ubuntuforums.org/showthread.php?t=123969](http://www.ubuntuforums.org/showthread.php?t=123969)
[http://www.ubuntuforums.org/showthread.php?t=59455](http://www.ubuntuforums.org/showthread.php?t=59455)

- Third, there is a package that is maintained by a fellow who doesn't like that the other desktop's programs are simply hidden. It is a KDE improvement package called "K Menu Gnome", which aims to simply organise the KDE menu better, and to move Gnome items to a separate folder in the menu. (I don't know what effect it has on Gnome.) If you want to try it, you can get it here: [http://www.kde-look.org/content/show.php?content=31031](http://www.kde-look.org/content/show.php?content=31031)


Hope this helps, and as always, *please do post back and tell if (and preferably how) you've managed to do what you wanted to.* ;) Specifically, if you try the K Menu Gnome package, it would be nice to know how it worked for you.

kko

---

### Post by Caligula on 2006-05-25
> The menus are based on .desktop -files that reside (as I understand) in a number of directories, most notably /usr/share/applications. KDE and Gnome both respect the OnlyShowIn= (and probably also NotShowIn=) -settings, which can be added to any of these files. These can read for instance OnlyShowIn=GNOME or OnlyShowIn=KDE.

Thanks, adding a OnlyShowIN=KDE/Gnome shouldn't be too complicated, I don't mind doing that...

But which file is it? which file do I need to edit?

---

### Post by kko1 on 2006-05-26
Hi!

[QUOTE=Caligula]Thanks, adding a OnlyShowIN=KDE/Gnome shouldn't be too complicated, I don't mind doing that...

But which file is it? which file do I need to edit?[/QUOTE]

Take a look at */usr/share/applications* and */usr/share/applications/kde*, and you'll probably find what you are looking for. There's a *.desktop* -file (somewhere) for every menu entry. The entry for Totem, for instance, is called *totem.desktop*.

kko

PS. "Synaptic" is a good example, if you have it installed. It has two .desktop -entries, "synaptic.desktop" and "synaptic-kde.desktop". The first has a "NotShowIn=KDE" and the other has a "OnlyShowIn=KDE", so it is placed _exactly_ where the developer intended it to be, both in KDE and Gnome. :cool:

---

### Post by Caligula on 2006-05-26
okay, it wirked perfectly, I actually used one of the scripts...

Now I just need to edit the menu in KDE, that doesn't affect the gnome menu, does it? it's only the KDE menu file...(?)
That's what I read, anyway...

---

