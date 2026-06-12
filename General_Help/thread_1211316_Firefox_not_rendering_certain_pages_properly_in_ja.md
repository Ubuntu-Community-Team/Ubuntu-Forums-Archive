---
title: "Firefox not rendering certain pages properly in jaunty 64 bit"
date: 2009-07-12
forum: General Help
---

### Post by sistarbliss on 2009-07-12
Recently something changed with my firefox browser and I'm not quite sure how to remedy the situation.  
[B]
Symptoms:  Some web pages not rendering properly[/B]

[LIST=1]
[*]Blogger Dashboard not displaying blogs I'm following in the left hand pane
[*]Blogger bar at the top of blogs not displaying text where it says "follow, flag" etc..
[*]Blogger text not displaying in post content areas.
[*]Some wordpress and php driven sites not displaying text at all
[/LIST]
**Things I've done in attempt to resolve issue:** 

[LIST=1]
[*]Disable all plugins
[*]Checked all preferences via view>preferences>dialogue to see if there was anything being blocked accidentally
[*]Reinstall Firefox
[*]Completely remove firefox from synaptic and then reinstall
[/LIST]
Has anyone else encountered this?  I have not gone to the depth of deleting everything from my directories after uninstalling the browser via synaptic.  

**Questions:**

[LIST=1]
[*]What would be the proper procedure to completely remove all firefox data as to start with a clean slate.  I don't want to screw something up.
[/LIST]
**Questionable things that may have caused this:**


[LIST=1]
[*]Installing fonts via synaptic (can't remember which packages).  I also dumped a slew of fonts in .fonts in my home dir.  This worked well for me in Hardy, but the fonts won't display in gimp or office programs via jaunty.  Not sure why this is.
[*]Updates?
[*]Corrupt Firefox profile? Not sure how to tell if profile has become corrupt
[*]A glitch with a plugin? Here are the plugins that I have installed:
[/LIST]
[INDENT]
[LIST]
[*]firebug
[*]firecolor color picker
[*]web developer
[*]fireftp
[*]xmarks
[*]delicious toolbar
[*]newsfox
[*]feedly
[/LIST]
Any help or suggestions would be greatly appreciated.
[/INDENT]

---

### Post by pytheas22 on 2009-07-12
I'm not sure what might have caused the problem, but you can refresh your Firefox profile by typing:
```

mv ~/.mozilla ~/mozilla-OLD
```

Then restart Firefox.

If this doesn't work and you want your old profile back, simply type:
```

mv ~/.mozilla-OLD ~/mozilla
```

---

### Post by sistarbliss on 2009-07-12
It must have something to do with my fonts.  I just went to edit>preferences>content>fonts&colors>advanced and unchecked the box "allow pages to choose their own fonts, instead of my selections above"  

The fonts are different, but at least I can see the text on the pages!!!  Thank you SO much for your response.  I have put your profile reset info in my notes as to have it for reference.

I've been dealing with this for over a week now and not been able to figure it out.  Just a little setting resolved things temporarily.  Whew!  

\\:D/

---

### Post by lovinglinux on 2009-07-12
I suggest you visit [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

> **pytheas22 said:**
> I'm not sure what might have caused the problem, but you can refresh your Firefox profile by typing:
```

mv ~/.mozilla ~/mozilla-OLD
```


See quote below:

> **[color=#CC0000]Note:[/color]** Several posts on these forums recommends moving, renaming or deleting **[COLOR="Sienna"]~/.mozilla[/COLOR]** folder to solve Firefox issues. While this will certainly remove any corrupted Firefox profiles and thus solve many common issues, you should consider that the **[COLOR="Sienna"]~/.mozilla[/COLOR]** folder is also the place where other Mozilla applications might store their profiles (Sunbird, etc), so removing this folder will also remove their settings. 

Firefox profiles are stored under **[COLOR="Sienna"]~/.mozilla/firefox[/COLOR]** or **[COLOR="Sienna"]~/.mozilla/firefox-x.y[/COLOR]** folders, where **[COLOR="Sienna"]x.y[/COLOR]** is the Firefox version. So if you need to remove a Firefox profile to fix a problem, then remove **[COLOR="Sienna"]~/.mozilla/firefox[/COLOR]** or **[COLOR="Sienna"]~/.mozilla/firefox-x.y[/COLOR]** not **[COLOR="Sienna"]~/.mozilla[/COLOR]**. 

Nevertheless, there also no reason to delete the entire profile if you can pinpoint the culprit inside it. Most common Firefox issues can be traced back to a single profile file. So, if you can avoid removing the entire profile, you wil be able to preserve other settings like extensions, themes, bookmarks, cookies and passwords.

---

### Post by sistarbliss on 2009-07-12
Thanks so much for the info/link.  I've also recently had issues with flash burying my processor, so this helps a bunch!

---

