---
title: "Few important questions abt Ubuntu..."
date: 2006-05-24
forum: General Help
---

### Post by elijahclarity on 2006-05-24
I have a few very importnt questions about Ubuntu. 

1. I've heard that Breezy users can't upgrade their systems to Gnome 2.14...and that it will only be possible when Dapper is out? Why? But I remember that Kubuntu breezy users could easily upgrade to KDE 3.5??

2. Why is it that some new packages take time to appear in Ubuntu repos? Like it was with Firefox 1.5 - people had to install it manually if I'm right. I think new versions of Amarok were promptly available in the repos. But why such prolonged delay with some packages?

Thats all...thanks:)

---

### Post by jsmidt on 2006-05-24
[QUOTE=elijahclarity]I have a few very importnt questions about Ubuntu. 

1. I've heard that Breezy users can't upgrade their systems to Gnome 2.14...and that it will only be possible when Dapper is out? Why? But I remember that Kubuntu breezy users could easily upgrade to KDE 3.5??
[/QUOTE]
Actually you should be able to upgrade from breezy to dapper right now obtaining gnome 2.14.  Make sure you change all the breezy's in /etc/apt/sources.list to dapper then  type:
[HTML]apt-get dist-upgrade[/HTML]

It maye be a problem if you don't type with the dist- in front of upgrade.

I will warn though that it could be a mistake to upgrade before Dapper is stable, but if you have to, like me :) , it hasn't been a completely terrible experience.  Most everything worked.
 
[/QUOTE]
2. Why is it that some new packages take time to appear in Ubuntu repos? Like it was with Firefox 1.5 - people had to install it manually if I'm right. I think new versions of Amarok were promptly available in the repos. But why such prolonged delay with some packages?

Thats all...thanks:)[/QUOTE]

The reason packages take time is you have to "debianize" them after they are released.(Put into .deb format)  That takes some work.  However it seems if you used the dapper repos firefox 1.5 didn't take to long to be there.

---

### Post by jsmidt on 2006-05-24
By the way, if you were wanting to still run breezy but get gnome 2.14 I think that is a mistake.  That really has the potential to screw things up.  But upgrading completely to Dapper shouldn't be too dangerous.  Again it hasn't for me and RC will be out tomarrow for heavens sake.

---

