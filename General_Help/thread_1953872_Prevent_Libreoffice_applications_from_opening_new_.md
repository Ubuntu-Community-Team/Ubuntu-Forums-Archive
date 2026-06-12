---
title: "Prevent Libreoffice applications from opening new icon on launcher?"
date: 2012-04-07
forum: General Help
---

### Post by ryanmichaelmcclure on 2012-04-07
Every time that I open an application of LibreOffice that is on my launcher, the document opens as its own separate icon. Here's an example:

[IMG]http://i41.tinypic.com/kd2001.png[/IMG]

(Note: the placement of the document icon is not default-I moved it to that spot so it would be easier to see)

I clicked on Writer, and it opened a new icon for the document. Oddly enough, if I have 2 or more documents open, they all stay in that one new icon. 

Also, it's a little strange that the document icon is blurry, almost as if it is using a smaller .png than the application launcher.

So, does anyone know how to make documents open within the application icon? Or, does it normally open in the application icon and I'm just experiencing a bug?

---

### Post by 3rdalbum on 2012-04-07
When I click on Writer, it does not open a new icon. It just uses the existing icon. This is the default Libreoffice Writer button that ships with Ubuntu 11.10.

Incidentally, how did you change the Launcher so it doesn't have the boxes around the icons? I'd like to know because it looks nice and different; but also if it's a patched Launcher it might have a bug in how it handles windows and icons.

Can you also confirm for me how you created the Libreoffice button on the Launcher? I've occasionally run into problems with certain ways of creating Launcher buttons that result in windows not appearing in the parent button.

---

### Post by ryanmichaelmcclure on 2012-04-07
> **3rdalbum said:**
> When I click on Writer, it does not open a new icon. It just uses the existing icon. This is the default Libreoffice Writer button that ships with Ubuntu 11.10.

Incidentally, how did you change the Launcher so it doesn't have the boxes around the icons? I'd like to know because it looks nice and different; but also if it's a patched Launcher it might have a bug in how it handles windows and icons.

Can you also confirm for me how you created the Libreoffice button on the Launcher? I've occasionally run into problems with certain ways of creating Launcher buttons that result in windows not appearing in the parent button.

I actually have the default Unity; I messed with the .pngs of the Launcher to hide the boxes. :) Here's a link to a page to help you remove the boxes.

[http://www.omgubuntu.co.uk/2011/12/how-to-customise-unity-like-never-before/](http://www.omgubuntu.co.uk/2011/12/how-to-customise-unity-like-never-before/)

(Don't use the rotated plugin by the way...it's so buggy :P)

I simply went into the dash menu and dragged the LibreOffice icon down onto the Launcher.

---

### Post by ryanmichaelmcclure on 2012-04-07
I reinstalled LibreOffice and now every application works for opening within it EXCEPT for Writer..the one that I actually use. :( 

That, and the Math file is missing from the dash launcher, but the .desktop file exists within "/usr/share/applications" and running "libreoffice --math" from terminal works fine. 

Help!!

Edit: libreoffice --writer yields Writer opening with a small icon and as its own independent icon per document.

---

