---
title: "gparted and gksu"
date: 2010-06-12
forum: General Help
---

### Post by DThurman on 2010-06-12
Ubuntu v10.4

I have installed the gparted package and I was not
able to launch it from the System->Administration
menu - the wheel spins and nothing happens.

I used a gnome terminal, and ran:
# gksu gparted
... and nothing is launched.

I then ran in the gnome terminal as:
# sudo gparted
<entered password>
and it spit out the text:
======================
libparted : 2.2
======================

and gparted gui launched.

The gparted icon's property shows for the
command textbox as:
gksu gparted

So... what is going on?

---

### Post by wilee-nilee on 2010-06-12
> **DThurman said:**
> Ubuntu v10.4

I have installed the gparted package and I was not
able to launch it from the System->Administration
menu - the wheel spins and nothing happens.

I used a gnome terminal, and ran:
# gksu gparted
... and nothing is launched.

I then ran in the gnome terminal as:
# sudo gparted
<entered password>
and it spit out the text:
======================
libparted : 2.2
======================

and gparted gui launched.

The gparted icon's property shows for the
command textbox as:
gksu gparted

So... what is going on?

Not sure you could just run ```
sudo apt-get purge gparted
``` Then install again. Here is a screenshot of the properties of the gparted launcher in the menu.
[ATTACH]160134[/ATTACH]

---

### Post by DThurman on 2010-06-12
Geez...  I stumbled on what caused it!

I just happened to look in my home directory
and I found this:

$HOME/.gksu.lock

So, I deleted that file, and now I can launch
my gparted from the System->Administration menu!

Sorry for the bother - but problem solved
(but why was it there to begin with!?!? :) )

---

### Post by wilee-nilee on 2010-06-12
> **DThurman said:**
> Geez...  I stumbled on what caused it!

I just happened to look in my home directory
and I found this:

$HOME/.gksu.lock

So, I deleted that file, and now I can launch
my gparted from the System->Administration menu!

Sorry for the bother - but problem solved
(but why was it there to begin with!?!? :) )

Not sure why but hey it's working now.

---

