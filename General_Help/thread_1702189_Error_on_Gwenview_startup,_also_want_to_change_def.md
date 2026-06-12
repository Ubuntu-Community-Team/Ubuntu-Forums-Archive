---
title: "Error on Gwenview startup, also want to change default view."
date: 2011-03-07
forum: General Help
---

### Post by Rytron on 2011-03-07
Hi.

I get an error on Gwenview startup. I also want to change default view from '[COLOR="Indigo"]View[/COLOR]' to '[COLOR="Navy"]Browse[/COLOR]'.

Thanks.

---

### Post by Verbeck on 2011-03-07
if you open it from the menu/launcher it should open in 'browse' mode.. but it looks like it's trying to open a file..

try running it without all the extra options in the menu entry 
/(not sure whether -caption/%c works from gnome)

---

### Post by Rytron on 2011-03-08
Hello Verbeck.

Ah yes. In the menu launcher, it has the description [COLOR="Indigo"]gwenview %U -caption "%c" %i[/COLOR]
BTW, what exactly does **%U -caption "%c" %i** mean?

When I launch it via terminal it starts on '[COLOR="Red"]Start Page[/COLOR]', I get this:

```
$ gwenview

progname=<unknown>; RGBA=on
"/usr/bin/gwenview(21017)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/gwenview(21017)" Soprano: "QLocalSocket::connectToServer: Invalid name"
"/usr/bin/gwenview(21017)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/gwenview(21017)" Soprano: "QLocalSocket::connectToServer: Invalid name"
"/usr/bin/gwenview(21017)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/gwenview(21017)" Soprano: "QLocalSocket::connectToServer: Invalid name"
"/usr/bin/gwenview(21017)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/gwenview(21017)" Soprano: "QLocalSocket::connectToServer: Invalid name"
"/usr/bin/gwenview(21017)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/gwenview(21017)" Soprano: "QLocalSocket::connectToServer: Invalid name"
gwenview(21017)/kdeui (kdelibs): Attempt to use QAction "edit_redo" with KXMLGUIFactory! 
gwenview(21017)/kdeui (kdelibs): Attempt to use QAction "edit_undo" with KXMLGUIFactory! 
"/usr/bin/gwenview(21017)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/gwenview(21017)" Soprano: "QLocalSocket::connectToServer: Invalid name"

```

---

### Post by Verbeck on 2011-03-08
%U means to open  urls/files (would be replaced with the actual file name when used in file associations)
-caption %c uses the name used in the 'name' field of the launcher in the application's title bar.  (caption)
%i uses the icon from the 'icon' field of the launcher entry
*a brief overview can be found [highlight][here]("http://docs.kde.org/stable/en/kdebase-workspace/kmenuedit/quickstart.html")[/highlight] or [highlight][here]("http://library.gnome.org/devel/integration-guide/stable/desktop-files.html.en#commandline") [/highlight]

and nepomuk is something used in kde to handle metadata
so i wouldn't worry too much about that error
more info > [http://nepomuk.kde.org/](http://nepomuk.kde.org/)

edit/ it opens  'Start page' for me too and since it shows the recent folders i mistook it for browse mode :oops: )

---

### Post by Rytron on 2011-03-08
I liked Gwenview for viewing photos until now. What are your other favorite programs to view pictures?

---

### Post by Verbeck on 2011-03-08
i used ristretto when i was running xfce
its quite simple compared to gwenview so the functionality differs somewhat

---

### Post by Rytron on 2011-03-09
> **Verbeck said:**
> i used ristretto when i was running xfce
its quite simple compared to gwenview so the functionality differs somewhat

Yes, Ristretto is very good.

---

