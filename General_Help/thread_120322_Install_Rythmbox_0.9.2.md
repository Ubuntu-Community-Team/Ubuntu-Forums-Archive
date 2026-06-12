---
title: "Install Rythmbox 0.9.2?"
date: 2006-01-21
forum: General Help
---

### Post by furu on 2006-01-21
I see that there is a newer release of the Rythmbox:
[http://www.gnome.org/projects/rhythmbox/](http://www.gnome.org/projects/rhythmbox/)

This release can be used as a daap client.

My problem as a new Ubuntu and Linux user:
How do I install Rythmbox 0.9.2 onto Ubuntu?

I have downloaded the latest .gz file, but I don't know what to do next.

So, if anyone could give me a guido of how to do this...?

/Stig

---

### Post by veloct on 2006-01-21
You have 3 choices here:

1. Wait for it to be packaged for Ubuntu and available in one of the repos.
2. Try to find a *.deb for it and install it that way (chances that it won't work are high, dependencies, etc..).
3. Compile it from source yourself. You can do that for anything in linux (make sure you have compiled or install all dependencies yourself). This is not very easy for a newb, but you can try it. You'll need a few files first. Build-essentials and checkinstall (if you use check install it will install it and create a *.deb file you can use elsewhere and you'll be able to remove the program easily also), you can sudo apt-get install these from the repos. You'll have to untar the file into a folder, then you'll have to use the command line to do the following from the folder you extracted the file into.
```
./configure
make
sudo checkinstall 
```

Hope that helps some, I know it's not very detailed but that's the basics of it.  You can do a search on the wiki or here in the forums as I'm sure there is a wiki entry or howto with much more detail.  Good luck

---

