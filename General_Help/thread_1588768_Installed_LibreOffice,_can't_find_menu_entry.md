---
title: "Installed LibreOffice, can't find menu entry"
date: 2010-10-05
forum: General Help
---

### Post by Rocket J Squirrel on 2010-10-05
I uninstalled OpenOffice using Software Center and installed LibreOffice from the PPA using the instructions on this page:

[http://www.mydailytechtips.com/2010/10/how-to-install-libreoffice-in-ubuntu.html](http://www.mydailytechtips.com/2010/10/how-to-install-libreoffice-in-ubuntu.html)

I can't find any way to launch it. Applications > Office used to have OpenOffice Writer in it. Now there are no menu items for LibreOffice any darn place.

---

### Post by Rocket J Squirrel on 2010-10-05
Nevermind -- this worked:

[http://www.ubuntugeek.com/how-to-install-libreoffice-in-ubuntu-using-deb-packages.htm](http://www.ubuntugeek.com/how-to-install-libreoffice-in-ubuntu-using-deb-packages.htm)

had to install the Java Runtime Environment, as shown here:

[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

Now I gots me LibreOffice. My only question is whether it's set up for automatic updates.

---

### Post by scouser73 on 2010-10-05
I never had any updates when I was using OpenOffice and as LibreOffice is a fork of that, I'd be of the same opinion.

---

### Post by earthmeLon on 2010-11-29
> **Rocket J Squirrel said:**
> Nevermind -- this worked:

[http://www.ubuntugeek.com/how-to-install-libreoffice-in-ubuntu-using-deb-packages.htm](http://www.ubuntugeek.com/how-to-install-libreoffice-in-ubuntu-using-deb-packages.htm)

had to install the Java Runtime Environment, as shown here:

[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

Now I gots me LibreOffice. My only question is whether it's set up for automatic updates.

To get the latest updates, add their PPA:
```

echo 'deb http://download.tuxfamily.org/gericom/libreoffice /' | sudo tee -a /etc/apt/sources.list
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 890E7A26
sudo apt-get update
sudo apt-get install libreoffice3*

```

Also, your first link doesn't resolve.  What did you do to get your menus working?

---

### Post by DevHead on 2011-01-03
Yes, how did you get the menus to show up?

Found the link:
[http://www.ubuntugeek.com/how-to-install-libreoffice-in-ubuntu-using-deb-packages.html](http://www.ubuntugeek.com/how-to-install-libreoffice-in-ubuntu-using-deb-packages.html)

---

