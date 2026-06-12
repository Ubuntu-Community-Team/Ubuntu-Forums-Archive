---
title: "Replacing the (irritating) pre-loaded &quot;Yahoo!&quot; browser on a Dell mini 10?"
date: 2009-07-17
forum: General Help
---

### Post by whipsaw on 2009-07-17
Hi,

I'm a new user (have used Macs forever), and have just received a Dell mini 10. I want to replace the Yahoo (Firefox) browser with a plain Firefox browser, but can't figure out a simple way to do so.

Any help would be greatly appreciated!

---

### Post by vinutux on 2009-07-17
> **whipsaw said:**
> Hi,

I'm a new user (have used Macs forever), and have just received a Dell mini 10. I want to replace the Yahoo (Firefox) browser with a plain Firefox browser, but can't figure out a simple way to do so.

Any help would be greatly appreciated!

**[COLOR="DarkGreen"][http://www.ubuntumini.com/2009/06/install-firefox-35.html]("http://www.ubuntumini.com/2009/06/install-firefox-35.html")[/COLOR]**

---

### Post by Brandon Williams on 2009-07-18
The version of firefox installed in Dellbuntu isn't a "Yahoo" browser, it just has a few Yahoo related settings. Something about these changes means that they can't use regular firefox branding, and just call it "Web Browser" instead.

You can easily make the Yahoo stuff go away. IIRC, there's a Yahoo toolbar and the default search engine is Yahoo. In the menu, go to 'View -> Toolbars' and there should be a box to uncheck to make the Yahoo toolbar go away. Next, go to 'Tools -> Addons' and disable any Yahoo-related addons. And finally, in the search bar, click the down-arrow next to the Yahoo logo and select 'Manage Search Engines', then move Google (or whichever one you prefer) up to the top to make it the default. I think that's everything ... I'm working from a memory that's 6 weeks old, though.

As for the browser branding, go [here](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/) and download the version of firefox-3.0-branding that matches the current browser version on your machine (it's 3.0.11 on mine). Extract the package, and move it's content to the appropriate /usr/lib/ directory. Here's an example:
```
$ mkdir firefox-3.0-branding
$ dpkg -x firefox-3.0-branding_3.0.11+build2+nobinonly-0ubuntu0.8.10.1_i386.deb firefox-3.0-branding
$ cd firefox-3.0-branding/
$ sudo find -type f -exec cp {} /{} \;
cp: cannot create regular file `/./usr/share/doc/firefox-3.0-branding/changelog.Debian.gz': No such file or directory
cp: cannot create regular file `/./usr/share/doc/firefox-3.0-branding/copyright': No such file or directory
```
The two error messages result from the fact that there is no /usr/share/doc/firefox-3.0-branding/ directory, but they can easily be ignored.

---

