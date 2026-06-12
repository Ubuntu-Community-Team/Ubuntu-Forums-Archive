---
title: "Gnome Do &quot;docky&quot; interface missing?"
date: 2010-10-11
forum: General Help
---

### Post by Calixte on 2010-10-11
Hello,

I love Gnome Do, particularly it's "docky" interface. However, after installing Ubuntu 10.10 I realized that the "Docky" theme was not available anymore. I cecked the Gnome Do website but it seems that docky is still supported. Am I missing something?

Thanks in advance,
Calixte


PS: I don't want to install Docky. The dock is OK, but I like the Gnome Do commands to be integrated with it.

---

### Post by nothingspecial on 2010-10-11
They are seperate packages now.

---

### Post by ean5533 on 2010-10-11
To clarify (and confirm) what nothingspecial has said, GNOME-Do and Docky are now completely separate projects. If you want GNOME-Do and Docky both running, you'll have to install them and run them both.

---

### Post by Calixte on 2010-10-11
How can I have [this]("http://do.davebsd.com/wiki/Docky#Working_With_Do_in_Docky") then? By installing them both?
[http://do.davebsd.com/wiki/Docky#Working_With_Do_in_Docky](http://do.davebsd.com/wiki/Docky#Working_With_Do_in_Docky)

---

### Post by ean5533 on 2010-10-11
> **Calixte said:**
> How can I have [this]("http://do.davebsd.com/wiki/Docky#Working_With_Do_in_Docky") then? By installing them both?
[http://do.davebsd.com/wiki/Docky#Working_With_Do_in_Docky](http://do.davebsd.com/wiki/Docky#Working_With_Do_in_Docky)

As far as I know, the developers of GNOME-Do and Docky (mostly the same people) have not finished adding the ability to integrate the two programs like what you see. They targeted it for the 2.0 series, but I don't think they ever added it (I could be mistaken).

To the best of my knowledge, if you really want to have what you've shown in the screenshot above, you'll need to use an old version of GNOME-Do. I do not know off-hand where to find old versions.

---

### Post by justplainjon on 2010-10-11
I had the same situation after updating to 10.10 in that previously I had Gnome Do with Docky enabled as a theme.

The Gnome Do included in 10.10 is 0.8.3.1, and I must have been using something older.  Docky is not a theme for Do anymore, it's a completely separate project.
 
Anyway, I installed Docky from the repository and I'm using that now as a launcher.  Doesn't have nearly the extensive list of docklets that I remember, but it's clean, fast, and works as advertised!

The biggest difference is that super-space would previously launch a Do query field right in the Docky space, and it now shows in the middle of the screen, no biggie.

---

### Post by rrob on 2010-10-12
I remove new version (sudo aptitude remove gnome-do) and download previous version with docky [http://ftp.cvut.cz/ubuntu/pool/universe/g/gnome-do/gnome-do_0.8.3.1+dfsg-1ubuntu1_i386.deb](http://ftp.cvut.cz/ubuntu/pool/universe/g/gnome-do/gnome-do_0.8.3.1+dfsg-1ubuntu1_i386.deb) , plugins [http://ftp.cvut.cz/ubuntu/pool/universe/g/gnome-do-plugins/gnome-do-plugins_0.8.2.1+dfsg-2ubuntu1_all.deb](http://ftp.cvut.cz/ubuntu/pool/universe/g/gnome-do-plugins/gnome-do-plugins_0.8.2.1+dfsg-2ubuntu1_all.deb) and docklets [http://ftp.cvut.cz/ubuntu/pool/universe/g/gnome-do-docklets/gnome-do-docklets_0.8.2-2_all.deb](http://ftp.cvut.cz/ubuntu/pool/universe/g/gnome-do-docklets/gnome-do-docklets_0.8.2-2_all.deb) and now Im happy user of working gnome-do+docky .)

UPDATE (2010-12)

[B]Tutorial how to remove gnome-do without docky and install version 8.3.1 with docky.
[/B]
```

#remove current version of gnome-do
sudo apt-get remove gnome-do

#download version 8.3.1
wget http://ftp.cvut.cz/ubuntu/pool/universe/g/gnome-do/gnome-do_0.8.3.1+dfsg-1ubuntu1_i386.deb
wget http://ftp.cvut.cz/ubuntu/pool/universe/g/gnome-do-plugins/gnome-do-plugins_0.8.2.1+dfsg-2ubuntu1_all.deb
wget http://ftp.cvut.cz/ubuntu/pool/universe/g/gnome-do-docklets/gnome-do-docklets_0.8.2-2_all.deb

#install downloaded files
sudo dpkg -i gnome-do_0.8.3.1+dfsg-1ubuntu1_i386.deb
sudo dpkg -i gnome-do-plugins_0.8.2.1+dfsg-2ubuntu1_all.deb
sudo dpkg -i gnome-do-docklets_0.8.2-2_all.deb

#if you dont have aptitude, install it, else jump to next step
sudo apt-get update ; sudo apt-get install aptitude

#command system to hold this version of gnome-do
sudo aptitude hold gnome-do

```

---

### Post by lumbricus on 2010-10-12
Integration of Do in Docky is planned for Docky 2.2:
[https://bugs.launchpad.net/docky/+bug/446049](https://bugs.launchpad.net/docky/+bug/446049)

---

### Post by FeraTech on 2010-10-12
Unfortuneatly the new "Docky" package is missing the work space switcher which makes it pretty useless as a bottom task bar.

---

### Post by nothingspecial on 2010-10-13
I hope the don`t intergrate it, or at least, leave the option to run gnome-do without docky.

I`ve nothing against docky itself, it`s just I`ve always used gnome-do to avoid having panels and docks and what have you.

---

### Post by scicode on 2010-10-24
Aaah, just reading up on this, very disappointing development. I have no problem of the two separating ... if they would keep the docky interface for do until docky and do can talk to each other. Sorry but this sucks!

---

### Post by ubuntakias on 2010-11-02
> **rrob said:**
> I remove new version (sudo aptitude remove gnome-do) and download previous version with docky [http://ftp.cvut.cz/ubuntu/pool/universe/g/gnome-do/gnome-do_0.8.3.1+dfsg-1ubuntu1_i386.deb](http://ftp.cvut.cz/ubuntu/pool/universe/g/gnome-do/gnome-do_0.8.3.1+dfsg-1ubuntu1_i386.deb) , plugins [http://ftp.cvut.cz/ubuntu/pool/universe/g/gnome-do-plugins/gnome-do-plugins_0.8.2.1+dfsg-2ubuntu1_all.deb](http://ftp.cvut.cz/ubuntu/pool/universe/g/gnome-do-plugins/gnome-do-plugins_0.8.2.1+dfsg-2ubuntu1_all.deb) and docklets [http://ftp.cvut.cz/ubuntu/pool/universe/g/gnome-do-docklets/gnome-do-docklets_0.8.2-2_all.deb](http://ftp.cvut.cz/ubuntu/pool/universe/g/gnome-do-docklets/gnome-do-docklets_0.8.2-2_all.deb) and now Im happy user of working gnome-do+docky .)

Thanks!!That was exactly what I was looking for.
Hope the integration will come soon.

---

### Post by rrob on 2010-12-18
> **ubuntakias said:**
> Thanks!!That was exactly what I was looking for.
Hope the integration will come soon.

I forget mention, use this command after installing to disable upgrades of gnome-do and hold it in this version 8.3.1.

```
sudo aptitude hold gnome-do
```

[B]Tutorial how to remove gnome-do without docky and install version 8.3.1 with docky.
[/B]
```

#remove current version of gnome-do
sudo apt-get remove gnome-do

#download version 8.3.1
wget http://ftp.cvut.cz/ubuntu/pool/universe/g/gnome-do/gnome-do_0.8.3.1+dfsg-1ubuntu1_i386.deb
wget http://ftp.cvut.cz/ubuntu/pool/universe/g/gnome-do-plugins/gnome-do-plugins_0.8.2.1+dfsg-2ubuntu1_all.deb
wget http://ftp.cvut.cz/ubuntu/pool/universe/g/gnome-do-docklets/gnome-do-docklets_0.8.2-2_all.deb

#install downloaded files
sudo dpkg -i gnome-do_0.8.3.1+dfsg-1ubuntu1_i386.deb
sudo dpkg -i gnome-do-plugins_0.8.2.1+dfsg-2ubuntu1_all.deb
sudo dpkg -i gnome-do-docklets_0.8.2-2_all.deb

#if you dont have aptitude, install it, else jump to next step
sudo apt-get update ; sudo apt-get install aptitude

#command system to hold this version of gnome-do
sudo aptitude hold gnome-do




```

---

