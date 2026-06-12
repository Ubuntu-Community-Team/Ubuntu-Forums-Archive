---
title: "Exporting firefox configuration and passwords"
date: 2010-07-09
forum: General Help
---

### Post by Ceiber Boy on 2010-07-09
I'm installing ubuntu on a second machine and I would like to transfer all my bookmarks passwords etc from firefox on my original machine to firefox on my second maxhine, is their an easy way of ding this, copy a specific file or something? Or di I have to go down the root of having to install another program to do this for me?

Thanks for your help.

Just to make things clear my original machine has ubuntu 9.10 and my new machine will have 10.04

---

### Post by Gibbs on 2010-07-09
> **Ceiber Boy said:**
> I'm installing ubuntu on a second machine and I would like to transfer all my bookmarks passwords etc from firefox on my original machine to firefox on my second maxhine, is their an easy way of ding this, copy a specific file or something? Or di I have to go down the root of having to install another program to do this for me?

Thanks for your help.

Just to make things clear my original machine has ubuntu 9.10 and my new machine will have 10.04

Go to ~./.mozilla/firefox and store profile.ini and the profile directories you want (they look like **3h7lx50k.default**). Then when you install your new copy create a backup directory, move everthing there and then copy the stored files over.

*I can't guarantee that will work* - i've only done it for Thunderbird - but if you come across any problems you should be able to sort them out by editing files.

Edit: Take a look at [http://kb.mozillazine.org/Profile_backup](http://kb.mozillazine.org/Profile_backup)

---

### Post by mike555 on 2010-07-09
You could click "bookmarks > organize bookmarks > Import & backup > Export html ... 
  then to list your add-ons install the add-on ' extension list dumper " .then click on it and preferences and make a list .

---

### Post by lovinglinux on 2010-07-09
You can copy the ~/.mozilla/firefox folder from one machine to the new one.

I recommend using [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109/) to make regular backups of your profile.

Firefox also has an extension, called [Fire Sync](https://addons.mozilla.org/en-US/firefox/addon/10868/), that will become a default feature on Firefox 4.  It allows to sync settings, passwords, bookmarks, history and tabs. It doesn't sync extensions tho.

---

