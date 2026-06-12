---
title: "Trouble upgrading to Firefox 3.6 in Karmic"
date: 2010-01-22
forum: General Help
---

### Post by zookrider on 2010-01-22
I am attempting to upgrade from Firefox 3.5.7 to Firefox 3.6 in Karmic Koala. I used the following commands:

> sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
> sudo apt-get update
> sudo apt-get upgrade

All commands seemed to execute flawlessly with no errors, the only problem after restarting both my computer and Firefox, a quick click on "About Firefox" shows that I'm still running 3.5.7

I followed the instructions from [this site]("http://www.ubuntugeek.com/how-to-install-firefox-3-6-in-ubuntu-karmicjauntyintrepidhardy.html") to the letter. Help please...

---

### Post by Ahriman on 2010-01-22
what about the explicit:
```
sudo apt-get install firefox-3.6
```
did that not work either?

---

### Post by zookrider on 2010-01-22
> **Ahriman said:**
> what about the explicit:
```
sudo apt-get install firefox-3.6
```
did that not work either?

I tried that, it said:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.


Hence you see my problem, the CLI tells me that I have 3.6, yet when I open it the program itself tells me that it is 3.5.7

---

### Post by polki@mac.com on 2010-01-22
Does starting it in the terminal with "firefox-3.6" work?

---

### Post by zookrider on 2010-01-22
> **polki@mac.com said:**
> Does starting it in the terminal with "firefox-3.6" work?

No such luck.

> michael@michael-laptop:~$ firefox-3.6
firefox-3.6: command not found

---

### Post by rob1408 on 2010-01-22
You could try installing it via Ubuntuzilla.

[http://sourceforge.net/projects/ubuntuzilla/files/](http://sourceforge.net/projects/ubuntuzilla/files/)

then running this command through the terminal:

ubuntuzilla.py

Follow the onscreen instructions and you should end up with Firefox 3.6.

---

### Post by kansasnoob on 2010-01-22
I always use Ubuntuzilla:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

And I just wrote some notes for someone else:

[http://ubuntuforums.org/showpost.php?p=8705493&postcount=6](http://ubuntuforums.org/showpost.php?p=8705493&postcount=6)

---

### Post by kansasnoob on 2010-01-22
> **rob1408 said:**
> You could try installing it via Ubuntuzilla.

[http://sourceforge.net/projects/ubuntuzilla/files/](http://sourceforge.net/projects/ubuntuzilla/files/)

then running this command through the terminal:

ubuntuzilla.py

Follow the onscreen instructions and you should end up with Firefox 3.6.

Have you checked out the new Ubuntuzilla PPA?

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation)

---

### Post by zookrider on 2010-01-22
> **rob1408 said:**
> You could try installing it via Ubuntuzilla.

[http://sourceforge.net/projects/ubuntuzilla/files/](http://sourceforge.net/projects/ubuntuzilla/files/)

then running this command through the terminal:

ubuntuzilla.py

Follow the onscreen instructions and you should end up with Firefox 3.6.

OK, when I follow [their instructions]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation") I get the following:

> michael@michael-laptop:~$ deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found


---

### Post by rob1408 on 2010-01-22
You should be able to just download the deb and choose 'open with Gdebi package installer' (if you're using Firefox).  This will install the deb (no need for the terminal just yet).  When the installation is complete, open up the terminal and type 'ubuntuzilla.py'.

---

### Post by zookrider on 2010-01-22
> **kansasnoob said:**
> I always use Ubuntuzilla:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

And I just wrote some notes for someone else:

[http://ubuntuforums.org/showpost.php?p=8705493&postcount=6](http://ubuntuforums.org/showpost.php?p=8705493&postcount=6)

You good sir have solved my problem. Thank you.

---

### Post by ktucker on 2010-01-22
What worked for me was to uninstall all firefox entries via Synaptic and then install only firefox (version to be installed: 3.6.1~hg20100122...)

This also installed firefox-branding and ubufox.

---

### Post by ktucker on 2010-01-23
My quick fix above did not work for long. Next day, Firefox would only work if I deleted the contents of my profile folder or started Firefox with 'firefox -P' and added a new profile. So, there is something in the profile directory which causes the following behaviour:

1. Delete contents of my profile directory and type 'firefox':

The following line appears twice:
(firefox-bin:5146): GLib-WARNING **: g_set_prgname() called multiple times
and Firefox starts and I can use it.

2. Close Firefox and try again ('firefox'):

The following line appears once:
(firefox-bin:5336): GLib-WARNING **: g_set_prgname() called multiple times
but Firefox does not start.

Go back to step 1 - but lose all your settings etc.

So it might not be 'solved' completely, and can someone test on Lucid?

K

---

### Post by nanotube on 2010-01-23
> **ktucker said:**
> My quick fix above did not work for long. Next day, Firefox would only work if I deleted the contents of my profile folder or started Firefox with 'firefox -P' and added a new profile. So, there is something in the profile directory which causes the following behaviour:

1. Delete contents of my profile directory and type 'firefox':

The following line appears twice:
(firefox-bin:5146): GLib-WARNING **: g_set_prgname() called multiple times
and Firefox starts and I can use it.

2. Close Firefox and try again ('firefox'):

The following line appears once:
(firefox-bin:5336): GLib-WARNING **: g_set_prgname() called multiple times
but Firefox does not start.

Go back to step 1 - but lose all your settings etc.

So it might not be 'solved' completely, and can someone test on Lucid?

K

you're using the nightly build from the daily ppa. if you want stability, use the mozilla release af 3.6. 

one convenient way to get the official mozilla release is the ubuntuzilla ppa ([http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net))

---

### Post by Arkitekt on 2010-02-26
I was having the same problem, turns out it is two different issues.

After some trial and error, I have discovered that the reason 3.6 won't start up is due to greasemonkey. The reason it is causing a problem with 3.6 is because greasemonkey seems to not auto-update when a new version comes out, most of us have pre-3.6 versions. I myself had a version from January of 2009. Looks like in 0.8.3 greasemonkey added a 3.6 compatibility flag. Updating manually from the add-ons website to 0.8.20100211.5 fixed this issue for me. 

I fixed my GLib warnings by downgrading libglib2.0-0 and libglib2.0-data to 2.22.1-0ubuntu1, the newest one from karmic-updates (2.22.3-0ubuntu1) seems to be unstable. For those wondering how to do this, in synaptic highlight the package and under the package menu on the toolbar select force version (CTRL-E).

Hope this solves this for everyone.

---

