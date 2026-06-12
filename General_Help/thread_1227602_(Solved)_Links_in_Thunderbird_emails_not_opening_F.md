---
title: "(Solved) Links in Thunderbird emails not opening Firefox 3.5"
date: 2009-07-30
forum: General Help
---

### Post by harecanada on 2009-07-30
I found this solution on Kubuntu Forums by [COLOR="Red"]robfish[/COLOR]
	
Re: Unable to get email links in Thunderbird to open Firefox

This comes from robfish in Kubuntu Forms
I use a different method:-

A problem with Thunderbird was its apparent inability to open links in Firefox. This problem has been solved!
Solution: When in Thunderbird, do the following:
Edit->
preferences->
Select the "Advance" tab->
Select the Config Editor at the bottom of the window.

When in the "Config Editor" :
Right Click->
New->
String->
Name: network.protocol-handler.app.ftp ; Value: /path/to/firefox(whatever your path and firefox version is. Mine looks like this: /usr/bin/firefox-3.5)

Again:

Right Click->
New->
String->
Name: network.protocol-handler.app.http ; Value: /path/to/firefox

And once more:

Right Click->
New->
String->
Name: network.protocol-handler.app.https ; Value: /path/to/firefox

Of course, set the /path/to/firefox as the location of Firefox (in most cases /usr/bin/firefox). This should configure Thunderbird to open all links in a Firefox window (or Tab if Firefox is already running).

(I also, did this - harecanada)	
Also, make sure Web Browser Default is pointing to the right browser:System>Preferences>Preferred Applications>Internet>Web Browser(It should say  Custom and below where it says Command it should have the correct path. Mine says; /usr/bin/firefox-3.5 )
*Note: If you are unsure of the path to Fire Fox, in a terminal type whereis firefox-3.5 (or whatever version your using)

---

### Post by quixote on 2009-07-31
Thanks for posting this.  Useful to know.

---

