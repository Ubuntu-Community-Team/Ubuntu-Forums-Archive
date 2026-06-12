---
title: "Will upgrading restore my lost packages?"
date: 2009-09-22
forum: General Help
---

### Post by arnab_das on 2009-09-22
I accidentally removed Compiz package (I dont use Compiz btw) by using the "sudo apt-get remove compiz" command from the terminal. I had learnt that this would free up extra space. I have also removed all the "Not Installed (residual config)" packs from the synaptic manager to free up some space. 

Are these likely to damage my system in any way? If yes, is it possible to restore them?

Will upgrading to Karmic Koala (when its released next month) restore all these lost packages?

Please help me out. Thanks for the replies in advance.

---

### Post by ks07 on 2009-09-22
> **arnab_das said:**
> I accidentally removed Compiz package (I dont use Compiz btw) by using the "sudo apt-get remove compiz" command from the terminal. I had learnt that this would free up extra space. I have also removed all the "Not Installed (residual config)" packs from the synaptic manager to free up some space. 

Are these likely to damage my system in any way? If yes, is it possible to restore them?

Will upgrading to Karmic Koala (when its released next month) restore all these lost packages?

Please help me out. Thanks for the replies in advance.
I always remove my 'residual config' packages (using purge, but it's the same process) and I haven't had any problems at all, so you should be fine. As for removing Compiz, if you don't use it then you should have no problems.

Depending on what you uninstalled, upgrading may reinstall some of the packages you deleted, if you deleted any that are installed by default. Ofc, you can always delete them again after upgrading.

---

### Post by CatKiller on 2009-09-22
> **arnab_das said:**
>  Are these likely to damage my system in any way?

No. The packages you purged weren't installed anyway (just the residual config files). One thing that would probably be sensible would be to re-install the *ubuntu-desktop* package before you upgrade to Karmic. That will pull in all the default applications again, and you should be fine without it in the meantime.

---

### Post by arnab_das on 2009-09-22
> **CatKiller said:**
> No. The packages you purged weren't installed anyway (just the residual config files). One thing that would probably be sensible would be to re-install the *ubuntu-desktop* package before you upgrade to Karmic. That will pull in all the default applications again, and you should be fine without it in the meantime.


could u plz tell me the way to do that? appreciate ur response.

---

### Post by CatKiller on 2009-09-22
> **arnab_das said:**
> could u plz tell me the way to do that?

When you're ready to upgrade to Karmic (you don't need to do it now if everything's working) just install the *ubuntu-desktop* package in Synaptic (or apt-get) the same as you would any other package. It's not a real package, it's a meta-package whose only function is to depend on everything that's included in the default install. Having this installed means that your Karmic install can also have everything that's included in the default install. I'm not specifically aware of any problems with upgrading without this package, but it's standard advice to help the upgrade process go smoothly.

Installing it will re-install Compiz and suchlike (since they're included in the default install) but you can remove them again after you've done the upgrade if you still don't want them.

I realise you said that you "accidentally" removed Compiz. If you want it back, you could re-install the *ubuntu-desktop* package now, and it would re-install all those bits again.

---

### Post by arnab_das on 2009-09-22
> **CatKiller said:**
> When you're ready to upgrade to Karmic (you don't need to do it now if everything's working) just install the *ubuntu-desktop* package in Synaptic (or apt-get) the same as you would any other package. It's not a real package, it's a meta-package whose only function is to depend on everything that's included in the default install. Having this installed means that your Karmic install can also have everything that's included in the default install. I'm not specifically aware of any problems with upgrading without this package, but it's standard advice to help the upgrade process go smoothly.

Installing it will re-install Compiz and suchlike (since they're included in the default install) but you can remove them again after you've done the upgrade if you still don't want them.

I realise you said that you "accidentally" removed Compiz. If you want it back, you could re-install the *ubuntu-desktop* package now, and it would re-install all those bits again.

thank you very very much. I'll tell u what i did. I went to Synaptic package manager, then searched "ubuntu-desktop". right clicked on ubuntu-desktop, and then selected "Mark recommended for installation" and then installed whatever missing apps there was. I guess this was the correct procedure. if not, plz let me know.

I love ubuntuforums! Now i always know where to seek help! :)

---

