---
title: "KDE Daemon requests wallet password because of kaddressbook"
date: 2009-08-16
forum: General Help
---

### Post by sleeping on 2009-08-16
If I add a "Network" addressbook in Kontact, every time I log in or log out of KDE, I get a prompt that KDE Daemon requests access to kdewallet, no matter if Kontact is running or not. If I remove the network address book from Kontact's list, it no longer asks for the password upon login, but I don't have access to the address book either.

Is there a way to use a network address book in Kontact without having KDE Daemon ask me for a password on every login? I'm ok with Kontact asking the wallet password when I start it, obviously. Why is KDE Daemon accessing my Kontact's address books?

---

### Post by sigixv on 2009-08-16
Not a frequent KDE user here, but couldn't it be that you have an automatic mail checker configured? It might automatically load your addresbooks for automatic processing of the mail afterwards, based on the senders mail address.

Just wildly guessing here.

---

### Post by sleeping on 2009-08-16
> **sigixv said:**
> Not a frequent KDE user here, but couldn't it be that you have an automatic mail checker configured? It might automatically load your addresbooks for automatic processing of the mail afterwards, based on the senders mail address.

Just wildly guessing here.

I do indeed have Kontact set to automatically check the mail. However, when KDE Daemon asks for the password, Kontact isn't running, so it can't be (or at least it shouldn't be) trying to check the mail.

Plus, if I don't provide the password and hit cancel, I get a second prompt for the password to the remote file for addresses, not for any one of my mail accounts.

---

### Post by sigixv on 2009-08-16
I didn't mean kontact itself by an automatic mail checker. You said you get prompted as soon as you log in to kde, so i presume you have configured a mail-checker that notifies you of new mail without having kontact open. This application is probably set to launch at login and to be hidden until the arrival of new mail. In my experience all kde stuff is quite integrated so it might be possible that a mail-checker loads stuff from your basic mail application.

However, i do find it strange if there would be a mail checker running, that it doesnt request kwallet for login & password of your mail accounts but it does do so for an addressbook...

---

### Post by AlmaTlust on 2009-08-24
You might have set your network address file as standard in kaddressbook. Then it is marked in the KDE settings and might get checked for its availability when logging in...

---

