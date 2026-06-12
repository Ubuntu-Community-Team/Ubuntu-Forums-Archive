---
title: "Transfer settings from thunderbird in Breezy to Dapper?"
date: 2006-05-03
forum: General Help
---

### Post by MrJavalava on 2006-05-03
Hi.

Trying to transfer the accounts and settings I have in Breezy to Dapper (or Kubuntu 6.06) so I won't have to setup everything again. The thing is that it isn't going very well. :-k 

The import option only cares about other mailprograms already exsisting in dapper (which I don't have). It cannot import settings or emails from a directory. THIS IS annoying. ](*,)  

Plus I have another problem, the mozilla thunderbird will not install properly for some reason, so there is no icon in the menu for mozilla thunderbird...

Any clue?

---

### Post by ajgreeny on 2006-05-03
Can't help with the installation problem, apart from suggesting you try a complete uninstall and reinstallation to see what happens.

As for the transfer of all your settings, it is very easy.
In your home folder there will be a subfolder (hidden, so make sure you set your file manager to show hidden files) called .mozilla-thunderbird.  In that folder there is a file called xxxxxxxx.default.  Copy that folder to your new dapper .mozilla-thunderbird hidden folder, then change the profiles.ini file to point to this copied over profile.  Now when you open thunderbird it should oprn with all your old mailboxes and mail messages, and account information.

Good luck.

---

### Post by MrJavalava on 2006-05-03
[QUOTE=ajgreeny]Can't help with the installation problem, apart from suggesting you try a complete uninstall and reinstallation to see what happens.

As for the transfer of all your settings, it is very easy.
In your home folder there will be a subfolder (hidden, so make sure you set your file manager to show hidden files) called .mozilla-thunderbird.  In that folder there is a file called xxxxxxxx.default.  Copy that folder to your new dapper .mozilla-thunderbird hidden folder, then change the profiles.ini file to point to this copied over profile.  Now when you open thunderbird it should oprn with all your old mailboxes and mail messages, and account information.

Good luck.[/QUOTE]

Yeah, I knew all that with the hideen .mozilla-thunderbird directory.. Just had a hard time making it work. I did the whole uinstall of both mozilla firefox and thunderbird, and reinstalled it. Suddenly everything worked. :KS

---

