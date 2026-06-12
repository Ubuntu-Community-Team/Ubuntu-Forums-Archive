---
title: "Xubuntu - Anyway to Integrate Apps?"
date: 2011-11-01
forum: General Help
---

### Post by cottfcfan on 2011-11-01
My Xubuntu desktop is now set up nicely apart from one thing.
Certain apps will not integrate, choosing their own fonts & theme.
Keepassx & luckybackup are the two i'm having a problem with.
I have installed a gtk2/3 theme so that isn't the problem.
Any ideas?

---

### Post by 2F4U on 2011-11-01
Maybe this is because keepassx uses the Qt library and not GTK?

---

### Post by cottfcfan on 2011-11-01
It is, but the silly thing is, I had it all integrated, when I was messing with Xubuntu on a seperate partition. Now I've wiped it and installed it as my main op. I have the issue. It has to be something I need to install, that I had installed before, but I don't know what.

---

### Post by cottfcfan on 2011-11-02
The only way ive found for complete integration of Apps is by installing "xubuntu-desktop" on a fresh install of Ubuntu, and then logging in to the xubuntu session.
It works well, but obviously takes up more space. I'm also hoping there's no conflict of gtk/xfce programs.

---

### Post by gsmanners on 2011-11-02
I don't know for sure, but there might be some theme integration going on in gtk3. If you have a theme that properly supports both gtk2 and gtk3 (like the default greybird) then I think that will at least get the menus in all your apps (include the qt4) to look the same.

---

### Post by cottfcfan on 2011-11-02
Hi gsmanners,
Thanks for your reply.
I thought of that, so am using ambiance blue a gtk2/3 theme.
To be honest it doesn't seem to matter what I use, unless I go down the route above, the problem persists.

---

### Post by gsmanners on 2011-11-02
I see. There's something in the Xubuntu session that integrates qt4 and gtk2/3. Interesting. I'll have to see what that's doing.

---

### Post by cottfcfan on 2011-11-02
Actually just installed Mint Xfce Debian on a separate partition and all qt apps integrate nicely there. The Mint Devs have obviously included whatever package is missing in Xubuntu.
I'll keep searching.

---

### Post by cottfcfan on 2011-11-05
OK. Ive finally figured this out.
The 2 apps that need installing from synaptic are:
libgnomeui-0 & libgnomeui-common.
Just wish they were included in the stock install, as I have spent about a week on this.
Anyway problem solved.

---

