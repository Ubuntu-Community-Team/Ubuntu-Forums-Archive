---
title: "[SOLVED] Update Manager isn't recognizing downloads?"
date: 2006-02-25
forum: General Help
---

### Post by RavenOfOdin on 2006-02-25
I've had about 10 downloads stuck on my Update Manager, totaling 3.2MB, for about a day now. Every time I try to download them it says "Could not apply changes! Fix broken packages first."

No package, however, is broken. This is corroborated by a check of all installed packages in the Synaptic Package Manager.

And when I take all but the most inconsequential packages out (ie: tar, unzip) it reloads with everything checked, meaning I must install everything else. It seems to be a dependency or linking problem to me, but I have no idea beyond that and I'd really like a second opinion.

The packages down there are as follows:

gnupg (0.2.10-4ubuntu0.1)
libgnutls11 (1.0.16-13.1ubuntu1.1)
libgnutls11-dev (1.0.16-13.1ubuntu1.1)
libtasn1-2 (0.2.10-4ubuntu0.1)
libtasn1-2-dev (0.2.10-4ubuntu0.1)
libungif4g (4.1.3-2ubuntu0.1)
openssh-client (1:4.1p1-7ubuntu4.1)
ssh-askpass-gnome (1:4.1p1-7ubuntu4.1)
tar (1.15.1-2ubuntu0.1)
unzip (5.52-3ubuntu2.2)

Is there any way I can fix this?

---

### Post by dcstar on 2006-02-25
[QUOTE=RavenOfOdin]I've had about 10 downloads stuck on my Update Manager, totaling 3.2MB, for about a day now. Every time I try to download them it says "Could not apply changes! Fix broken packages first."

No package, however, is broken. This is corroborated by a check of all installed packages in the Synaptic Package Manager.
.....[/QUOTE]
So "Edit-Fix Broken Packages", then "Apply" doesn't do anything?

---

### Post by RavenOfOdin on 2006-02-25
No, it doesn't - because "Apply" is grayed out. And strangely enough, so is "Mark for Upgrade" in the right-click menu.

:confused:

---

### Post by RavenOfOdin on 2006-03-02
And now two more packages have shown up (irssi) and (ubuntu-docs) - the latter of which I could swear I installed already.

Someone please help. This is getting to be very annoying.

---

### Post by carlosqueso on 2006-03-02
Try firing up a terminal and running ```
sudo apt-get update
sudo apt-get install -f
```  If it gives you an error, post it here.

---

### Post by yanik on 2006-03-02
open a terminal and type the following:

sudo apt-get update
sudo apt-get -f install  (say yes if it wants to install something)
sudo apt-get dist-upgrade  (say yes if it wants to install something)

---

### Post by folki on 2006-03-02
sudo apt-get install -f 
would search for missing dependencies to resolve that. If not, do 
sudo apt-get 
to examine the problem.

---

### Post by RavenOfOdin on 2006-03-02
Holy crap, I don't believe it.

dist-upgrade actually worked! :)

Now I can quit looking at the circle icon in my notification manager. 
Thanks for the input, guys.

---

