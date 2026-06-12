---
title: "Mozplugger preventing silverlight 3.0 (2.99) to work"
date: 2010-03-03
forum: General Help
---

### Post by nelio2k on 2010-03-03
I downloaded the latest mono 3.0 preview from [http://www.go-mono.com/moonlight/prerelease.aspx](http://www.go-mono.com/moonlight/prerelease.aspx) in hope of watching the Olympics.

The firefox extension installed worked fine and the add-on was installed successfully. However, whe logging on to the page to watch the Olympics, such as this page: [http://www.nbcolympics.com/video/assetid=168fcf14-1b5e-48d0-8644-3535911574a0.html#left+with+lasting+impressions](http://www.nbcolympics.com/video/assetid=168fcf14-1b5e-48d0-8644-3535911574a0.html#left+with+lasting+impressions) , the silverlight plug-in did not load.

I found out the problem is that mozplugger is loading an older version of my silverlight, as shown below from my "```
about:plugins
```" command in my FF. 


```
Silverlight Plug-In

    File name: mozplugger.so
    3.0.40818.0

MIME Type 	Description 	Suffixes 	Enabled
application/x-silverlight 	Novell Moonlight 	xaml 	Yes
application/x-silverlight-2 	Novell Moonlight 		Yes
```

Once I've removed the mozplugger using ```
sudo apt-get remove mozplugger
```, the latest silverlight 3.0 is loaded successfully and the videos work. 

**How am I supposed to make mozplugger such that it will forget the existance of an older version of x-silverlight? It is not located anywhere in my /etc/mozpluggerrc.**

I've referred to the site here: [http://plugindoc.mozdev.org/faqs/uninstall.html](http://plugindoc.mozdev.org/faqs/uninstall.html) that tells me to remove the actual file, which is mozplugger.so in my case. I don't think that is a good idea, but I found out anyway that I have multiple mozplugger.so files...

```
$ locate mozplugger.so
/usr/lib/firefox/plugins/mozplugger.so
/usr/lib/mozilla/plugins/mozplugger.so
/usr/lib/xulrunner-addons/plugins/mozplugger.so

```

Moving them to another location to emulate removing them does not solve the problem.

Anyone have any ideas?

---

