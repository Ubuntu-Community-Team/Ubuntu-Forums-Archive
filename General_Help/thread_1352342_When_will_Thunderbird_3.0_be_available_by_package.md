---
title: "When will Thunderbird 3.0 be available by package?"
date: 2009-12-11
forum: General Help
---

### Post by Stuart P. Bentley on 2009-12-11
Now that Thunderbird 3.0 has gone live, how long until I can get it from the official package repo via Synaptic?

---

### Post by lykwydchykyn on 2009-12-11
In keeping with standard Ubuntu release policies, I'd say April when Lucid comes out.  That's assuming it doesn't have any show-stopper bugs that keep it from being in Lucid.

If you need it sooner, you can add a ppa and get it that way:

[http://pacoros.wordpress.com/2009/12/08/install-thunderbird-3-in-ubuntu-9-10-karmic/](http://pacoros.wordpress.com/2009/12/08/install-thunderbird-3-in-ubuntu-9-10-karmic/)

---

### Post by scouser73 on 2009-12-11
> **Stuart P. Bentley said:**
> Now that Thunderbird 3.0 has gone live, how long until I can get it from the official package repo via Synaptic?

More than likely it will appear when Lucid Lynx is available, if you want to install in independently of Synaptic Pachakage Manager then please follow my instructions.

Download the **.tar/bz2** file from

[[COLOR="Red"]**Mozilla Messaging: Thunderbird 3**[/COLOR]]("http://en-gb.www.mozillamessaging.com/en-GB/thunderbird/")

**1** - Extract the **.tar/bz2** file

**2** - Enter **gksudo nautilus** in terminal

**3** - Go to the folder **/opt**

**4** - Copy & paste the Thunderbird file that you extracted to **/opt**

**5 -** Enter these commands into **Terminal** > **sudo -i**

*Enter your password if asked.*

> **cd /opt**
> **chown -R username filename**

[COLOR="Red"]**Obviously the username refers to you, and the filename to the file**[/COLOR]

**6** - Go to **System > Preferences > Main Menu**

**7** - In Main Menu, click on **New Item**

**8** - In the **Name** field enter **Mozilla Thunderbird Mail/News**

**9** - In the **Command** field enter **/opt/thunderbird/thunderbird**

**10** - In the **Comment** field enter **Mozilla Thunderbird Mail/News**

[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)

---

### Post by Scott M. Sanders on 2009-12-11
Why does Ubuntu wait so long to release Mozilla stuff, meanwhile my Fedora and Windows boxes are already updated? 

I setup Firefox 3.5 in /opt when it came out and using /opt/firefox ever since. I hate to do that though...

---

### Post by lykwydchykyn on 2009-12-11
> **Scott M. Sanders said:**
> Why does Ubuntu wait so long to release Mozilla stuff, meanwhile my Fedora and Windows boxes are already updated? 

I setup Firefox 3.5 in /opt when it came out and using /opt/firefox ever since. I hate to do that though...

They typically release the latest version of an app when the release comes out, and keep it until the next release.

On Windows you don't have package management, so you go to the website, download and install it.  You can do the same on Ubuntu if you don't care about package management.

---

### Post by Rodney9 on 2009-12-11
> **scouser73 said:**
> More than likely it will appear when Lucid Lynx is available, if you want to install in independently of Synaptic Pachakage Manager then please follow my instructions.

Download the **.tar/bz2** file from

[[COLOR="Red"]**Mozilla Messaging: Thunderbird 3**[/COLOR]]("http://en-gb.www.mozillamessaging.com/en-GB/thunderbird/")

**1** - Extract the **.tar/bz2** file

**2** - Enter **gksudo nautilus** in terminal

**3** - Go to the folder **/opt**

**4** - Copy & paste the Thunderbird file that you extracted to **/opt**

**5 -** Enter these commands into **Terminal** 

*Enter your password if asked.*




[COLOR="Red"]**Obviously the username refers to you, and the filename to the file**[/COLOR]

**6** - Go to **System > Preferences > Main Menu**

**7** - In Main Menu, click on **New Item**

**8** - In the **Name** field enter **Mozilla Thunderbird Mail/News**

**9** - In the **Command** field enter **/opt/thunderbird/thunderbird**

**10** - In the **Comment** field enter **Mozilla Thunderbird Mail/News**

[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)

I don't have a /opt directory on it's own , I have one under var and etc.

---

### Post by Stuart P. Bentley on 2010-01-15
> **lykwydchykyn said:**
> They typically release the latest version of an app when the release comes out, and keep it until the next release.

On Windows you don't have package management, so you go to the website, download and install it.  You can do the same on Ubuntu if you don't care about package management.

Well, many apps like Chrome come in a downloadable deb package file (and Chrome even adds its own PPA for updating).

---

### Post by wojox on 2010-01-15
You can add the ppa's here: [http://wojox.homelinux.net/?p=33](http://wojox.homelinux.net/?p=33)

---

