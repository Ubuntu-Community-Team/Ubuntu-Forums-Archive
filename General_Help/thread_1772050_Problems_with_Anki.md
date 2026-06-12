---
title: "Problems with Anki"
date: 2011-05-31
forum: General Help
---

### Post by jameswm on 2011-05-31
Sorry if this is in the wrong place.. I made an account long ago, but never used Ubuntu til now. x.x

I finished installation and downloaded updates, went to the Software Center and downloaded Anki. However, when I try to download a language flash-card pack (or whatever it is) I get an error saying the "File is corrupt or not in the Anki database." It says this for any download

---

### Post by Krovas on 2011-06-12
*Bump*

Same here. It's too bad; Anki looks like an incredible tool.

EDIT: Go to Anki's page and install the latest version (1.2.8). Worked for me, anyway.

---

### Post by HunterDX77M on 2011-08-06
I hope I am not too late to help you. I had this same exact problem. Here is the solution that worked for me:
1) Open up the terminal
2) Type these three commands in:

```

sudo apt-get install anki
sudo apt-get remove anki
sudo dpkg -i anki_1.2.8-1_all.deb

```It seems weird installing it and then removing it, but you need the libraries installed before you can install the current version. Also, make sure you don't purge with the second command so that it works as intended. Hope this helps!):P

---

### Post by fandez on 2012-07-21
Thank you guys!
This worked for me, and maybe it's a bit cleaner. 
I needed to install a missing library before installing Anki, so the steps that worked for me where the following:

Download latest version ([http://anki.googlecode.com/files/anki_1.2.11-1_all.deb](http://anki.googlecode.com/files/anki_1.2.11-1_all.deb))

Open a terminal, go where you downloaded Anki and then launch:

sudo apt-get install python-sqlalchemy
sudo dpkg -i anki_1.2.8-1_all.deb

That's it! I hope I help someone :)

---

