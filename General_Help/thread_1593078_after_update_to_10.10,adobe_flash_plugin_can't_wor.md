---
title: "after update to 10.10,adobe flash plugin can't work at all"
date: 2010-10-11
forum: General Help
---

### Post by benjiaminlam on 2010-10-11
i've installed plugin many times but it still didn't work with any brower:confused:

ps:i'm on 32bits

---

### Post by dino99 on 2010-10-11
goto synaptic and remove/purge then reinstall flashplugin-installer

---

### Post by benjiaminlam on 2010-10-11
i did just like you said ,however ,it still can't work

---

### Post by sendblink23 on 2010-10-11
I know this is extreme measures.... but can you try a fresh install - during installing click the option to install all the codecs & you will be very happy (not needing to do anything extra) - but that is only if you have internet connection available

---

### Post by Dougie187 on 2010-10-11
Why don't you check your browser?

What browser are you using. Also, if you navigate to

```
about:plugins
```

in the address bar of your browser of interest, check there to see if flash (shockwave) is listed at all and/or enabled. If not there are more manual ways of checking as well.

---

### Post by benjiaminlam on 2010-10-11
> **Dougie187 said:**
> Why don't you check your browser?

What browser are you using. Also, if you navigate to

```
about:plugins
```in the address bar of your browser of interest, check there to see if flash (shockwave) is listed at all and/or enabled. If not there are more manual ways of checking as well.
i checked my bowers .the shockwave is on.:(

---

### Post by Dougie187 on 2010-10-11
> **benjiaminlam said:**
> i checked my bowers .the shockwave is on.:(

What browser are you using?

Have you tried other browsers? and what websites have you tried visiting?

When I first installed my computer (even with a fresh install, using google chrome) I had to manually enable the plugin in my browser because it wasn't enabled by default.

---

### Post by benjiaminlam on 2010-10-11
> **Dougie187 said:**
> What browser are you using?

Have you tried other browsers? and what websites have you tried visiting?

When I first installed my computer (even with a fresh install, using google chrome) I had to manually enable the plugin in my browser because it wasn't enabled by default.
i use firefox and visit some flash game website

---

### Post by Dougie187 on 2010-10-11
Ok, in a terminal (Applications->Accessories->Terminal)

try typing this and post whatever comes out

```
ls -l /usr/lib/mozilla/plugins/*flash*
```

It's kind of odd that it says it's installed and enabled in your browser but it's not working.

Also try going to the actual flash website

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

it should tell you if you have a version installed or not as well.

---

### Post by Vaphell on 2010-10-11
try that, it should do the dirty work for you
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by TheAnachron on 2010-10-11
If you are using NoScript make sure the site has permission.
To do so, click on the NS icon and choose "Temporary allow xxx".

---

### Post by Starter1961 on 2010-10-11
> **benjiaminlam said:**
> i use firefox and visit some flash game website

Hi, I had the same problem.  I went to "***Synaptic Package Manager***", selected the "***_flashplugin-installer_***" (showed as *uninstalled*) and checked the "_***Mark for Complete Removal***_" option.  I did the same thing for the "***_adobe-flashplugin_***."  Since I had "***_gnash_***" installed on my system, I repeated the procedure for all gnash files as well.  After I "**completely**" removed both packages of flash as well as the gnash, I reinstalled the new "***_adobe-falshplugin_***" and everything started working.

Good luck

---

### Post by Mozai on 2010-10-13
Once I removed gnash and restarted firefox, it worked for me.
I was surprised, since I didn't have gnash installed in 10.04.  For some reason Ubuntu thought to install it during my upgrade to 10.10... but gnash+firefox wasn't working for ANY flash <object> tags, not even the super simple ones I'd made myself using OpenOffice Presentation.

---

### Post by DarkBattM14 on 2010-10-16
> **Starter1961 said:**
> Hi, I had the same problem.  I went to "***Synaptic Package Manager***", selected the "***_flashplugin-installer_***" (showed as *uninstalled*) and checked the "_***Mark for Complete Removal***_" option.  I did the same thing for the "***_adobe-flashplugin_***."  Since I had "***_gnash_***" installed on my system, I repeated the procedure for all gnash files as well.  After I "**completely**" removed both packages of flash as well as the gnash, I reinstalled the new "***_adobe-falshplugin_***" and everything started working.

Good luck

That was the solution!!!! THNX!!!! :popcorn::popcorn:

---

