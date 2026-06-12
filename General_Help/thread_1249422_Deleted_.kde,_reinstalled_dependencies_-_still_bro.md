---
title: "Deleted .kde, reinstalled dependencies - still broken."
date: 2009-08-25
forum: General Help
---

### Post by fgysin on 2009-08-25
Hi

I was using Kopete on my Ubuntu 9.04 because I don't like Pidgin. I had some problems with my IM accounts with it and wanted to do a clean reinstall... After purging and reinstalling kopete my accounts were somehow still configured, so I figured they must be configured somewhere in the kwallet or another kde related package.
What I did next seemed like a good idea at the time, but probably was rather stupid: I purged kopete and deleted the .kde folder in my home.

My idea: When I reinstall kopete and all its kde dependencies, the .kde folder will be generated once again, and I can start from scrap with clean default preferences.

BUT:
After the reinstall of all kde depedencies and kopete, kopete still does not seem to work.
If I want to add an IM account the list of available IM protocols just appears to be empty. Furthermore when I open the config window inside kopete it is just blank with no content at all. What have I done?

Can someone help me? I'd really like to have my kopete back again running. What did I break when deleting the .kde folder? And how do I fix it? Stupid as I am I did not make a backup of the .kde folder before deleting it... :/

---

### Post by slakkie on 2009-08-25
find -H .kde -name kopete\*
.kde/share/apps/kopete
.kde/share/config/kopeterc


Think you could remove these files. 

And always make a backup if you intend to wipe stuff and you're not sure what you will delete. 

Removing your .kde dir is not that bad, you just lose all your settings.

Next time do this:

```

tar zcvf dot_kde.tgz .kde # Restore: tar zxvf dot_kde.tgz
rm -rf .kde
# or
mv .kde .kde.old

```

---

### Post by nikhilk on 2009-08-25
Have you logged out and logged in again after all the deleting, purging and reinstalling actions?

I believe the .kde folder should be created automatically when you start a new KDE session. See if logging out and back in resolves your problem.

---

### Post by fgysin on 2009-08-26
> **slakkie said:**
> Removing your .kde dir is not that bad, you just lose all your settings.
That's what I thought as well... But as it seems somethink broke with the deletion of .kde - even though the folder has been recreated after the reinstall of kopete, kopete does not work anymore.

I tried restarting the pc, it did not help.

Again: The .kde folder is here, kopete starts, but the list of available IM protocols is empty and the configure window is blank.


Strange enough today I encountered a very similar problem at work on my other machine:
I removed and reinstalled some kde packages (it was amarok this time), and suddenly kopete looses all my IM accounts and then the IM protocol list is empty and the configure window is blank.

I think it could be somehow related to what I did during the reinstallation of the kde packages (kopete/amarok respectively) - as far as I can see that is the only common thing between the two seperate cases of my kopete screwing up my IM accounts:
After typing *sudo apt-get remove kopete/amarok* I was told that some dependencies were no longer required and that I should run *sudo apt-get autoremove* to clear them. That is what I did and lotta packages were cleared...

Is it possible that this deleted some packages needed for a proper kopete functionality and that those packages are somehow not reinstalled even if I remove and reinstall kopete?

---

