---
title: "mozilla-mplayer package depends on firefox. Why?"
date: 2009-11-29
forum: General Help
---

### Post by pitris on 2009-11-29
Hello,
I'm using SeaMonkey and _NO_ Firefox at all. I'd like to use mozilla-mplayer plugin in my browser but when I install it, it tries to install Firefox as well. Why? I don't want any Firefox, but mozilla-mplayer plugin.
The same it is with adblock-plus and mozilla-noscript packages.

Thanks for any reasonable answer.

PS: I'm running Karmic.

---

### Post by 3rdalbum on 2009-11-29
Mozilla-mplayer's package requires:

firefox-3.0 OR seamonkey-browser OR epiphany-browser OR etc.

If you've installed Seamonkey through the repositories, then mozilla-mplayer's dependencies should be satisfied and it will not mark Firefox for installation.

If the version of Seamonkey that you are using has not been installed using the repositories, then Apt will try and install Firefox. You should either install Seamonkey from the repositories, or download the .Deb package from [http://packages.ubuntu.com](http://packages.ubuntu.com), extract the contents and put them in a relevant location to manually install it.

---

### Post by John Bean on 2009-11-29
Perhaps its down to false assumptions by the package author or maybe there are real dependencies on parts of the Firefox package that don't exist in Seamonkey and the dependency tree is insufficiently fine-grained to allow them to be isolated without installing the whole Firefox package.

Either way it doesn't seem to be a big deal unless space is seriously limited; nobody is forcing you to actually use the Firefox bits that get downloaded to satisfy the dependencies.

---

### Post by John Bean on 2009-11-29
> **3rdalbum said:**
> If the version of Seamonkey that you are using has not been installed using the repositories
A very good point, and one I missed. APT is outstanding at its job but it's not psychic... yet :-)

---

### Post by 3rdalbum on 2009-11-29
Actually now I'm being a smartalec, but you could create a basic stub Debian package that's called "seamonkey-browser", give it a high version number and install it; and then Apt will install the mozilla-mplayer package without bringing in Firefox.

---

### Post by pitris on 2009-11-29
> **3rdalbum said:**
> If the version of Seamonkey that you are using has not been installed using the repositories,
Ah ok, that's it. I'm running SM 2.0, which isn't it the repos, so that's why I downloaded it mozilla.org. And I didn't know that SM from repos can satisfy dependencies. Thanks for explaining.

---

