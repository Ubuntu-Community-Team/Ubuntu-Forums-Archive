---
title: "Installing packages"
date: 2006-05-23
forum: General Help
---

### Post by dyarza on 2006-05-23
Hi everybody,

I just installed the OS after a few tries.  I was getting a failure installing the base systems but it seems to be up now.

I am getting very strange behabiour and I am wondering if anybody has any input.  First, whwn I go to System->Administration->Networking, I was prompted for my admin password the first time but nothing seems to happen.  I get the same when I go to Applications->Add Applications.  There is a momentary pause with the waiting icon and then nothing.

I am trying to install a copiler so I can install things like rdesktop, which tells me I do not have a valid compiler.  I understand that this is not installed by default, and I have found instructions on these forums on how to do it but nothing seems to do anything.

I realize how broad this questions is but I am hoping someone can point me in the right direction.

Thanks,

David

---

### Post by halfvolle melk on 2006-05-23
Do you have only one user or did you also set up a root account? The password asked when doing stuff in "System -> Administration" is the password of the main user, not that of the root account. If you enter the wrong password nothing will happen, just as you discribed.

Oh, by the way, installing most things you need to compile stuff can be done like this: Applications -> Accessories -> Terminal. Once there, type this in the terminal:
```
sudo apt-get install build-essentail
```
The password asked here is also that of your normal/main user.

---

### Post by dyarza on 2006-05-23
Thanks,

Maybe it is along those lines.  I did create a root password, but it is the same as for my main user account.  Since I am the only one using this machine I did not think anything of it.

I tried to do the command you describe, but again, no results.

Thanks,

---

### Post by solstice on 2006-05-23
I have seen this problem before. I used to get this, I think when i was using kubuntu only, which was one of the reason i switched to ubuntu. I thought it may be a KDE issue rather than gnome.

What would happen would be something similar to what you were describing. At first my password would work fine and i could change settings, then, it would stop working. The password box would just dissapear and not bring up the configuration dialogs.

I saw something about reinstalling the language packages or something....and this did fix the issue temporarily. this was many months ago though, right at breezy's release so I cant remember the exact details.

---

### Post by dyarza on 2006-05-23
OK, so I have changed my password from that of the root.  Still the same thing.  I'm reinstalling everything.

---

