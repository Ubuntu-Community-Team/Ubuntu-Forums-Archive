---
title: "Gnome install for 11.10 Problems"
date: 2011-12-22
forum: General Help
---

### Post by njooni91 on 2011-12-22
Hi all, I'm new to Ubuntu and I'm experiencing some problems.
So I installed Gnome by typing the following into the terminal:

sudo apt-get install gnome-tweak-tool
sudo add-apt-repository ppa:ferramroberto/gnome3
sudo apt-get update
sudo apt-get install gnome-shell-extensions-user-theme

and then I restarted my computer, because my laptop doesn't do the alt-F2 (because I would have to change my BIOS to accept the F2 as a function button rather than a decrease lighting button). Anyway After I restart I go to Shell Extensions and find that the page is empty. I looked it up on the forum and found that using a classic Gnome may be the problem, but I have absolutely no idea whether or not I am using a classic gnome. At any rate could anyone help me. I am currently using a G42 HP laptop with a Intel Graphics Media Accelerator (GMA) HD Graphics. Many thanks.

---

### Post by kurt18947 on 2011-12-23
Hi

Excuse me if you already know this/have done this.  I've seen reference to that ppa but have never used it.  The first thing I wonder is which UI are you selecting when you log on?  When 11.10 starts you should have a list of users.  To the right of the user name(s) is a star or gear looking thing.  When you click on that you should get a list of available UIs.  Default would be Ubuntu (Unity) and Ubuntu 2D.  If you successfully installed gnome-shell you should also see Gnome.  If you installed gnome-session-fallback you would also see Gnome classic & Gnome classic-no effects.

If you log in using gnome,  you should be running gnome 3 aka gnome shell.  You should now be able to install extensions then enable them in 'advanced settings'.  If you haven't done so, you should take a look at [http://extensions.gnome.org](http://extensions.gnome.org).  There are 8 pages of extensions there last time I checked and the installation is about the coolest I've seen.  You need java running - the site uses javascript - and you simply click the 'on' button to install the extension.  You may or may not need to go to 'advanced settings' to enable the desired extension.  Webup8 also has useful extensions installed via apt-get in a terminal.  [http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html](http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html)

---

### Post by njooni91 on 2011-12-23
Thank you I wasn't aware of the star button on the login screen. It's all good now, thanks again

---

### Post by BC59 on 2011-12-23
To install Gnome-shell you have to run:

```
sudo apt-get install gnome-shell
```

---

