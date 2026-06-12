---
title: "Help in customizing..."
date: 2010-03-06
forum: General Help
---

### Post by petedes5 on 2010-03-06
I want to use the feature that windows 7 advertises where you can "snap" two windows side by side like this: [http://www.microsoft.com/windows/windows-7/features/snap.aspx](http://www.microsoft.com/windows/windows-7/features/snap.aspx)

I'm sure compiz has a setting but i could not figure it out :confused:

---

### Post by stinkeye on 2010-03-06
[**_[COLOR="DarkRed"]Get Aero Snap in Ubuntu[/COLOR]_**]("http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg%21+Ubuntu%21%29")

---

### Post by petedes5 on 2010-03-06
Thanks for the link.

So... I tried it and it really isn't that great. The snap doesn't resize that well and it takes away form my "expose"

Any other ways?

Since, I'm here is there anything else cool I should know about compiz? Kind of a newb : )

---

### Post by stinkeye on 2010-03-06
Seeing as your interested in a snap feature you could have a look at a tiling plugin for compiz.

Add the repository for compiz
In terminal
```
sudo add-apt-repository ppa:compiz/ppa
```

Open synaptic package manager
click the reload button
search for *compiz-fusion-plugins-unsupported*
and install

After you have installed go to settings > repositories > other software
and untick the compiz ppa.
This is because if you update some of the  other packages it can have undesirable effects.

You should now have a tile plugin in CCSM > Window Management

---

