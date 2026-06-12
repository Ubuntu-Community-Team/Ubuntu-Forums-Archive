---
title: "Ubuntu Software Center does not use the default browser"
date: 2011-02-26
forum: General Help
---

### Post by StephGbzh on 2011-02-26
Hi,

I have Firefox and Chromium installed since last year on Ubuntu 10.10.
Firefox is and has always been my Default Browser.

Recently, the Ubuntu Software Center changed its mind on what to do when I click on the "website" link on software pages: it now opens the link in Chromium instead of Firefox.
I want it back to opening links in Firefox.

I suspect the last updates of Chromium to be responsible for this behavior.
When I remove Chromium from my Ubuntu, the links open in Firefox. Reinstalling Chromium leads back to links opening in Chromium.

The Ubuntu menu System > Preferences > Preferred Applications shows that the default browser is Firefox.
In Firefox, menu Tools > Preferences > Advanced > General > "Check now" tells me "Firefox is already set as your default browser".
In Chromium, Preferences > Basic > Default Browser confirms that : "Chromium is not currently your default browser".

I also changed the following setting from Chromium to Firefox (and restarted my computer) to not avail:
```
sudo update-alternatives --config x-www-browser
There are 2 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).

  Selection    Path                       Priority   Status
------------------------------------------------------------
  0            /usr/bin/chromium-browser   40        auto mode
  1            /usr/bin/chromium-browser   40        manual mode
* 2            /usr/bin/firefox            40        manual mode
```

tl;dr : Where can I set the browser used to open "Website" links in the Ubuntu Software Center ?

Thanks

---

### Post by StephGbzh on 2011-02-27
No one?

I also tried gksu > gnome-default-applications-properties in case the Software Center uses its root credentials to open links through root preferences.

The default browser for root is "sensible-browser".
That leads to the use of :
```
$BROWSER variable
/usr/bin/gnome-www-browser
/usr/bin/x-www-browser
/usr/bin/www-browser
```
each one being used if the preceding one fails.

Well, $BROWSER is undefined, gnome-www-browser and x-www-browser link to /usr/bin/firefox and www-browser links to Lynx.

Thus still no clue about why Ubuntu Software Center opens Chromium instead of Firefox...:confused:

---

### Post by StephGbzh on 2011-03-27
Solution found : see [http://ubuntuforums.org/showpost.php?p=10606797&postcount=4](http://ubuntuforums.org/showpost.php?p=10606797&postcount=4)

---

