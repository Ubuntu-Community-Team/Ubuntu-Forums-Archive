---
title: "Can't install from the new Getdeb."
date: 2009-11-18
forum: General Help
---

### Post by Marlonsm on 2009-11-18
Always I try to install something from the new Getdeb site I get this error:
"Firefox doesn't know how to open this address, because the protocol (apt) isn't associated with any program."
I'm using Kubuntu 9.10 and I've already added their repository and the key, but it's still not working. I couldn't find any solution so far.

Is there something I can do?

---

### Post by Marlonsm on 2009-11-19
Bump.

---

### Post by MonoDeem on 2009-11-19
```
sudo apt-get install apturl

```

---

### Post by Marlonsm on 2009-11-19
Nope, didn't work. I already had the "apturl-kde" package, and the "apturl" (for Gnome) also didn't work.

I also tried this guide:
```
You need AptURL protocol support registered in your web browser to be able to use allmyapps.

== Procedure for Firefox ==

Type in &#8220;about:config&#8221; in the location bar.

Right click, select New &#8211;> String
Type in &#8220;network.protocol-handler.app.apt&#8221; in the name of string,
and type in &#8220;/usr/bin/apturl&#8221; in the value.

One more right click, select New &#8211;> String
Type in &#8220;network.protocol-handler.app.apt+http&#8221; in the name of string,
and type in &#8220;/usr/bin/apturl&#8221; in the value.
```

---

### Post by scouser73 on 2009-11-19
Download the actual software and then install it that way.  I know it's not ideal but you can do that and hopefully someone will provide a more useful answer for you.

---

### Post by Marlonsm on 2009-11-20
> **scouser73 said:**
> Download the actual software and then install it that way.  I know it's not ideal but you can do that and hopefully someone will provide a more useful answer for you.

The problem is that they don't have a download link for 9.10 any more, just for 9.04 and before.

The only option I have is to go to the application's homepage and download it from there, but usually they only have the source, so I'd have to compile it myself.

---

### Post by Marlonsm on 2009-11-21
One last bump...

BTW, I tried in Konqueror and in Epiphany and it's also not working there.

---

### Post by Rob_H on 2009-12-07
Don't know of a real fix, but here's a workaround: Once you get the protocol error message, dismiss the message box. Then right-click on the empty browser window and select "View Page Source" (or equivalent). You should see a META tag in the HTML that reveals the URL it was trying to load. For example, here's the META tag for Songbird:

```
<META http-equiv="refresh" content="0;URL=apt:songbird?refresh=yes">
```

The URL in this case is "apt:songbird". Pass this to apturl-kde in a terminal like so:

```
apturl-kde apt:songbird
```

You should be in business now. It's an ugly hack, but it worked for me.

---

### Post by stinkeye on 2009-12-08
Don't know how you do it in firefox but in Opera I had to associate apturl to the apt protocol.
Try this link [*[COLOR="DarkRed"]https://help.ubuntu.com/community/AptURL[/COLOR]*]("https://help.ubuntu.com/community/AptURL")

---

### Post by RobotJox on 2009-12-11
well, for me, apturl is working but I can't update existing packages from getdeb. 

For instance if I try to install devede 3.15 I get the message that "devede is already installed" although I have only devede 3.14 installed?!

---

### Post by mkvnmtr on 2009-12-11
I believe I enabled the get deb repository and can now install through my package manager.

---

### Post by abadr on 2009-12-15
Adding the repository worked for me. Here's howto:
[http://www.getdeb.net/updates/Ubuntu/all#how_to_install](http://www.getdeb.net/updates/Ubuntu/all#how_to_install)

---

### Post by luigi_mb on 2009-12-15
> **Marlonsm said:**
> Always I try to install something from the new Getdeb site I get this error:
"Firefox doesn't know how to open this address, because the protocol (apt) isn't associated with any program."
I'm using Kubuntu 9.10 and I've already added their repository and the key, but it's still not working. I couldn't find any solution so far.

Is there something I can do?

Yes, read

[http://www.getdeb.net/updates/Ubuntu/all#how_to_install](http://www.getdeb.net/updates/Ubuntu/all#how_to_install)

In other words, download and install the "getdeb" package. Then you can install the applications offered at the GeDeb site.


/luigi

---

### Post by dugh on 2010-01-21
That is pretty ridiculous.

---

### Post by dmanhog on 2010-02-21
I can't get installs to work from getdeb.net with Konqueror or Firefox but it does seem to work using Chromium.  I suppose it's of little concern since you can install them through the package manager once the repo is installed but a simple click off of the web page is a nice touch that Kubuntu seems to be missing out on.  At least it does work with Chromium.  If it works there must be a way to get Konqueror and Firefox working:confused:.  That's as far as I'm going with it as I'm happy I have something that works.  I just wanted it out there that there is a browser that is working in Kubuntu with getdeb out of the box.  Maybe someone can use that to help fix the issue or just do like me and use Chromium when you go to getdeb.net  Kubuntu 9.10 has been outstanding btw and this is the only issue I have had to deal with, very nice.

---

