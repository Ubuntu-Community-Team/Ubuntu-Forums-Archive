---
title: "Problems with apt and packages after update"
date: 2012-03-26
forum: General Help
---

### Post by JazzPotato on 2012-03-26
Hi forum, 
 I recently updated my system, and after logging on today to do some work, I found out that Bluefish (A html editor) had been uninstalled :O But it was ok because my favourite IDE was still installed. So I went to listen to Banshee whilst I coded and oh no! :O Banshee has been uninstalled! So I went to the software centre to re-install it and It refuses to install any package with the error "There seems to be a programming error in aptdaemon."
 This is damn confusing. And I refuse to believe that the developers, although they seem to lack common sense, would make a programming error in aptdaemon. There is also a scary-lookong red stop sign in my notification area, which says "An error occured, please run package manager to see whats wrong"
Thanks, 
Live long and prosper,
Gary

---

### Post by MG&amp;TL on 2012-03-26
Okay, we need some debugging output. Run:

```
sudo apt-get update && sudo apt-get upgrade
```

in a terminal (so we can guess at what's wrong with apt)

And:

```
software-center
```

so we can see what precisely is the matter with aptdaemon, and, by extension, software-centre.

Thanks. :)

---

### Post by JazzPotato on 2012-03-26
The first one says no packages newly upgraded, 0 newly installed, 0 to remove blah blah,
And the second one says:
```
2012-03-26 19:24:56,104 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
```

---

### Post by MG&amp;TL on 2012-03-26
Okay, which version of Ubuntu? (the output was not very helpful, I'm afraid).

There's quite a few open bugs on "programming error"...so could be a lot of things.

---

