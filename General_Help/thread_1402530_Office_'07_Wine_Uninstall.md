---
title: "Office '07 Wine Uninstall"
date: 2010-02-09
forum: General Help
---

### Post by MisterEwok on 2010-02-09
I was checking out wine, and installed ms office 2007 in it. But I ended up deciding (for the Windows programs that I needed to use, and the context in which I need them) to just install XP in a VirtualBox machine and use all my Windows programs there (not very many).

So, I uninstalled wine and I did all of this that is recommended in the wine faq (to completely remove everything):

rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

However, I now have an annoying issue. Microsoft office programs are the default opener of office documents. And since the programs no longer exist, this causes a problem. How can I remove the option to "Open With Microsoft Office ..." so that OpenOffice is the default?

Thanks,
ewok

---

### Post by warfacegod on 2010-02-09
Perhpas the most straight forward way would be to right click the file and select "Open with..."

---

### Post by MisterEwok on 2010-02-09
Right. I just wanted the option gone, or at least not default, so that I don't always have to right click every document I want to open.

---

### Post by warfacegod on 2010-02-09
Right click file> select properties> Open with tab

---

### Post by MisterEwok on 2010-02-09
Thank you. That worked. Mostly...

But there's still the same issue when opening attachments from e-mails in evolution. And in that case there's no properties button in the right-click menu.

---

### Post by warfacegod on 2010-02-09
> **MisterEwok said:**
> Thank you. That worked. Mostly...

But there's still the same issue when opening attachments from e-mails in evolution. And in that case there's no properties button in the right-click menu.

I'd say look around in the Evolution properties.

Just for kicks try:

```
sudo apt-get purge wine
```

And go to Synaptic and make sure all the wine packages are gone.

---

### Post by MisterEwok on 2010-02-09
Sweet. The purge wine line did the trick.
Thanks a lot.

---

### Post by warfacegod on 2010-02-09
Glad to help. I take it the Wine FAQ doesn't mention purging it? That sounds like a serious omission to me. Probably want to mark this as Solved under Thread Tools.

---

