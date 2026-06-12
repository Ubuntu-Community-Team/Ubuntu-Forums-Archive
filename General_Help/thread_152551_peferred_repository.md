---
title: "peferred repository"
date: 2006-03-30
forum: General Help
---

### Post by rottame on 2006-03-30
Hi

I've created a local repository (http)  for sharing ubuntu updates with my brother, my sister and my second box
But if a package exist on both the local and the official repository, apt-get wants to download it from the official one
Is here a way to define a preferred repository?

thanks
Angelo

---

### Post by Sutekh on 2006-04-01
I don't think apt-get has a preference, but instead tries to install the latest version.  Could be wrong though, perhaps the package in your local repository isn't as new as the one in the official repository?

You could just comment out the official repositories from each PC's sources.list to allow the other PCs to use your local repository to do updates instead.  Laborious, but I don't know another way.  I have a local repository set up at home too, I use two different versions of the sources.list and just change them when I want to get stuff from the local repository or the official ones.

---

### Post by pdobrev on 2006-04-01
For the preferences you may want to edit (create) /etc/apt/preferences but for the exact syntax of the file you'll have to consult google. However, I think that for your situation it would be best to run apt cache (I'm not really sure if it's called this way) on your computer and this way if someone tries to download a package that does not exist on your computer, it will be downloaded on your computer and then sent to the user. If using this scheme, other users should have only your repository in sources.list.


Best,
Petar.

---

