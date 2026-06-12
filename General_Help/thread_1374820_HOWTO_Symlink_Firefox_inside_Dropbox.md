---
title: "HOWTO: Symlink Firefox inside Dropbox"
date: 2010-01-07
forum: General Help
---

### Post by KrazyPenguin on 2010-01-07
HOWTO: Symlink Firefox inside Dropbox

This is easy but I decided to post it.
This is great if you do a reinstall of your system or use multiple computers, since you can use all your firefox settings on each computer located in different locations.

Assuming that Dropbox is already installed on your computer:

first move your .mozilla directory to /home/username/Dropbox/

mv /home/joe/.mozilla /home/joe/Dropbox/.mozilla

Now create the symlink:
	ln -s /home/joe/Dropbox/.mozilla/ /home/joe/

It's that easy.

Now if you use another computer, you just install Dropbox on it and sign in.  Delete you /home/joe/.mozilla file and use the same symlink command we used above, and now you will have two computers using the same firefox settings.

This can be done with other files, and probably with your /home/joe directory if you want as well.  

Just a little example of cloud computing for beginners.
Thanks.

---

