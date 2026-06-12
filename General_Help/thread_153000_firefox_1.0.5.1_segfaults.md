---
title: "firefox 1.0.5.1 segfaults"
date: 2006-03-31
forum: General Help
---

### Post by dashnak on 2006-03-31
Hi, I'm having a problem with firefox 1.5.0.1...
I installed it some 2 months ago from the repositories of a guy that built the package for breezy and everything worked perfectly, I was just ecstatic with joy, jejeje...
Yesterday I upgraded open office to 2.0.1 from the repositories that appear in a thread in this forum, I did it because I was trying to fix some really weird bug in 2 beta, but in the end, the bug was still there even in the new version of Impress so I unistalled it and reinstalled 2 beta...
The problem was that then my sister logged to her account and realized that when she opened firefox, and she typed something in the search bar and pressed enter, or wrote an url and pressed enter, or if she tried to browse one of the urls from her history or practically tried to do anything with it, firefox would segfault... And now I just discovered that when opening thundebird the exact same thing happens...
Now, it only happens in her account, or in a new account I made just to try and see if it would happen again.... It NEVER happens in my account...
I already tried changing her theme, deleting her ~/.mozilla, and reconfiguring fontconfig... And nothing seems to do the trick...
Does anyone have any ideas?
Thanks

---

### Post by dcstar on 2006-03-31
[QUOTE=dashnak]Hi, I'm having a problem with firefox 1.5.0.1...
I installed it some 2 months ago from the repositories of a guy that built the package for breezy and everything worked perfectly, I was just ecstatic with joy, jejeje...
Yesterday I upgraded open office to 2.0.1 from the repositories that appear in a thread in this forum, I did it because I was trying to fix some really weird bug in 2 beta, but in the end, the bug was still there even in the new version of Impress so I unistalled it and reinstalled 2 beta...
The problem was that then my sister logged to her account and realized that when she opened firefox, and she typed something in the search bar and pressed enter, or wrote an url and pressed enter, or if she tried to browse one of the urls from her history or practically tried to do anything with it, firefox would segfault... And now I just discovered that when opening thundebird the exact same thing happens...
Now, it only happens in her account, or in a new account I made just to try and see if it would happen again.... It NEVER happens in my account...
I already tried changing her theme, deleting her ~/.mozilla, and reconfiguring fontconfig... And nothing seems to do the trick...
Does anyone have any ideas?
Thanks[/QUOTE]
Yes, chances are the new accounts are trying to run the "old" Firefox binary.

You will probably have to modify the launch icons to point to the new version of Firefox you installed.

---

### Post by dashnak on 2006-03-31
There are no "old" binaries, as far as I know, firefox 1.5.0.1 replaced the other version. Furthermore, launching firefox in her account and going to "about" says that it is version 1.5.0.1...
Also, and I don't know if this is relevant or not, if I right-click the launcher icon in the top bar and select "properties", gnome-panel crashes miserably....

---

### Post by Barrakketh on 2006-03-31
Installing Firefox in Breezy is asking for trouble...there's a reason why the devs have refused to backport the Dapper packages (1.5.0.1) to Breezy.  There are a lot of applications that depend on Firefox/Seamonkey/Gecko, and all of those packages that you use would need to be rebuilt and tested to make sure things don't break.

These packages, among others, depend on Firefox/Seamonkey:

espresso-frontend-gtk
firefox-gnome-support
gnome-app-install
libnss3
openoffice.org2
yelp
xsane
librsvg2-bin

---

### Post by dashnak on 2006-03-31
Yeah, I know that, but I decided I'd jump the gun and if everything broke, well, I'd just uninstall...
But it worked, it worked perfectly fine until the day before yesterday....
I guess the weird bug in Oo.org could then be traced back to this, but, firefox had never stopped working before that....

---

### Post by dashnak on 2006-04-01
*bump*

---

### Post by dcstar on 2006-04-01
[QUOTE=Barrakketh]Installing Firefox in Breezy is asking for trouble...there's a reason why the devs have refused to backport the Dapper packages (1.5.0.1) to Breezy.  There are a lot of applications that depend on Firefox/Seamonkey/Gecko, and all of those packages that you use would need to be rebuilt and tested to make sure things don't break.
.......[/QUOTE]
Rubbish, **installing** FF 1.5 does nothing to the existing dependencies if it is done according to the instructions available in these forums (and other places).

Removing FF 1.0.7 **will** cause problems, which is why it is also stated quite clearly not to do such a thing.

Many people - including myself - have installed FF 1.5 on our Breezy systems with few issues whatsoever.

---

### Post by dashnak on 2006-04-03
So, should I just reinstall 1.0.7?
Even though my account doesn't show any problems whatsoever?

---

