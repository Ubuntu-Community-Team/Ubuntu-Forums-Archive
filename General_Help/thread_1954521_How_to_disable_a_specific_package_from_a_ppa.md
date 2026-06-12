---
title: "How to disable a specific package from a ppa"
date: 2012-04-08
forum: General Help
---

### Post by Lucas Malor on 2012-04-08
I added [this ppa]("https://launchpad.net/%7Ejanvitus/+archive/ppa") to have latest amule updates. The fact is I'm not insterested in the other packages, but the Update Manager autodownload and selects them for the install. I must deselect them every time I update ubuntu packages. How can I disable them?

---

### Post by dandnsmith on 2012-04-08
I suggest you go back to that link, and read down until you find (step 4) the ref to /etc/apt/sources.list.
Edit this to delete the line(s) corresponding to the source(s), and then save it.
Now, when you update the packages, you should have just the ones you want.
This won't remove anything already installed.

---

### Post by Lucas Malor on 2012-04-08
I do not want to remove the entire repository, I want only to filter out all but one package (amule) of that PPA. 
Furthermore in /etc/apt/sources.list there's no manually added repository.

---

