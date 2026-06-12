---
title: "Lightscribe software"
date: 2010-12-16
forum: General Help
---

### Post by jpaulb on 2010-12-16
I would like to label a about 100 CDs and like to use Lightscribe or similar.

Is there any lightscribe software available?

edit

[http://www.lightscribe.com/downloadSection/index.aspx]("http://www.lightscribe.com/downloadSection/index.aspx")

Has lightscribe software for Linux that works the first time.For me that is quite a surprise, since I feel I am becoming more computer illiterate each day.):P

Thanks

---

### Post by JOHNNYG713 on 2010-12-16
Remember Google is your friend ! [http://www.ubuntugeek.com/installing-lightscribe-simple-labeler.html](http://www.ubuntugeek.com/installing-lightscribe-simple-labeler.html)

---

### Post by tgalati4 on 2010-12-16
Pack of sharpies and a retired ball player.

---

### Post by jpaulb on 2010-12-16
> **JOHNNYG713 said:**
> Remember Google is your friend ! [http://www.ubuntugeek.com/installing-lightscribe-simple-labeler.html](http://www.ubuntugeek.com/installing-lightscribe-simple-labeler.html)

thanks

---

### Post by jpaulb on 2010-12-16
If I can get this to run on an AMD 64

---

### Post by fballem on 2011-01-05
> **jpaulb said:**
> If I can get this to run on an AMD 64

This might help (works on my 64-bit system):

LightScribe is used to label LightScribe discs.

- obtain the software from: [[[http://www.lightscribe.com/downloadSection/linux/index.aspx|LightScribe](http://www.lightscribe.com/downloadSection/linux/index.aspx|LightScribe) website.]]

**32-bit Linux**
- install the software. There are two components. The core software must be installed first, then the Application.

**64-bit Linux** (This needs to be installed using the following commands in a Terminal). **The version numbers will need to be changed** to match the actual download files. The first two commands will install the LightScribe software. The last command will resolve issues with referencing a required library.

```
sudo dpkg -i --force architecture lightscribe-1.18.19.1-linux-2.6-intel.deb
sudo dpkg -i --force architecture lightscribeApplications-1.18.15.1-linux-2.6-intel.deb
sudo ldconfig
```

**Set the label so that it will print darker**: 
```
sudo /usr/lib/lightscribe/elcu.sh
```

Once installed, then a menu option can be created to use the software.

[LIST=1]
[*]Right-click on Applications and select Edit Menu from the context menu.
[*]Click on Accessories, which is where the lightscribe menu item will be placed.
[*]Click the New Item button, and enter the following information into the fields:
[LIST=2]
[*]Ensure that Type is set to Application.
[*]Name may be anything. I use LightScribe Labeler.
[*]Command is: /opt/lightscribeApplications/SimpleLabeler/SimpleLabeler (the browse button may be used to locate the application, which is in the /opt/lightscribeApplications/SimpleLabeler folder.
[*]Comment may be anything. I use Writes a label on Lightscribe-enabled discs
[*]Click on the icon and browse to /opt/lightscribeApplications/SimpleLabeler/content/images folder. Once browsed, a list of suitable icons appears. Select one.
[*]Click on the Close button, which will complete the application.[/LIST]
[/LIST]
To use, select the launcher from Applications > Accessories > LightScribe Labeler (or whatever was put in the Name field.

---

