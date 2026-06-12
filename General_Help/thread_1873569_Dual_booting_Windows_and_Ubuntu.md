---
title: "Dual booting Windows and Ubuntu"
date: 2011-11-01
forum: General Help
---

### Post by murdockpt on 2011-11-01
Partially doing this for a change of scenery, but also looking, with being in school now, to get rid of all the distractions i find in Windows.

So heres what I'm hoping to do...

1)Leave my windows partition (120 gb partition)
2)Leave my Media partition (games are stored here, torrents get dumped here, and documents id like not to lose. (80gb partition)
3)Install Ubuntu on the 30gbs left. (30gb)

Now way back it used to be so simple as pickign a partition and installing ubuntu on it. This has changed I think.

I know need to set aside the root folder, swap and the boot one. 

So i have 30gbs set aside for ubuntu and Im in windows. how do i partition this up.

also going to go ahead and ask how to set up the boot stuff for it.

I rmemeber when this was alot easier. Or ive just forgotten how to use my computer properly.

also: no spellcheck for me. too lAZY.

---

### Post by murdockpt on 2011-11-01
i obviously know how to set up partitions, im just looking for numbers on how big each should be.

might also go ahead and just ask how to set up the root. apparently its not working in ins current state, which entirely blows my mind.

and yeah, just need some assistance on the booting thing.

edit: 4gb of ram. 30 gbs set aside for the ubuntu install.

---

### Post by oldfred on 2011-11-01
No need for separate /boot. With only 30GB you may not want a separate /home. I normally suggest 10-20GB for / (root), 2GB or the size of RAM for swap, and the rest /home. If most of your data is in the shared NTFS partition then a separate /home is not really required.

---

### Post by murdockpt on 2011-11-01
so during the install, when it asks for the boot location, it would be the same location as the main install?

and still set aside 8bg for swap?

also, how do i go about setting up a dual boot scenario?

---

### Post by oldfred on 2011-11-01
Do not mix up the /boot partition or folder in / (root) and the small part of grub2's boot loader that has to be installed to the MBR or sda. All MBR(msdos) based systems have to have a boot loader in the MBR of the drive which is just the first sector before any partitions.

If you have 8GB of RAM you would only need swap if you were to hibernate. Otherwise 2GB is plenty, and some get by without any. Some say it boots a bit faster with some swap as it has to error out if not swap found. System boots fast enough for most users that hibernation in Ubuntu does not speed up booting much and often adds complexity.

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

