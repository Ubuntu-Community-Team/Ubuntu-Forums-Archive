---
title: "Choosing profiles when starting Firefox 3.6"
date: 2010-01-22
forum: General Help
---

### Post by feedmecereal on 2010-01-22
How do I get the new Firefox 3.6 to let me chose between different profiles when I start it? With Firefox 3.5 I could do that with the command:
```
/usr/bin/firefox -p -no-remote
```
But that doesn't seem to work anymore.

---

### Post by quixote on 2010-01-23
you can run "firefox --profilemanager"

That brings up the profiles to choose from.  To make it permanent, I thought the command was "firefox -p *profilename*". (I.e. for the desktop icon or menu link, that would be the actual command under Properties.)  But if -p isn't working, then ...???

---

### Post by Brandon Williams on 2010-01-23
To start with a specific profile, use 'firefox -P profile-name -no-remote'. If you always want to be allowed to select interactively, use 'firefox -ProfileManager -no-remote'.

The -no-remote flag is only required if you want to be able to run firefox windows for multiple profiles at the same time. If you don't use that flag, then it will open in a currently running instance if there is one, ignoring any command-line options related to profiles.

---

### Post by feedmecereal on 2010-01-23
Well, this is a little embarrassing. It turns out that I was clicking on an icon with the command firefox**-3.5** -p -no-remote. :oops:

I was just able in install Firefox 3.6 again and it works just fine. Thanks for your help anyway.

---

