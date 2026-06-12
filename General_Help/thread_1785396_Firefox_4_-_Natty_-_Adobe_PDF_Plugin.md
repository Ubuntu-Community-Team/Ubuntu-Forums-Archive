---
title: "Firefox 4 - Natty - Adobe PDF Plugin"
date: 2011-06-18
forum: General Help
---

### Post by spieler8 on 2011-06-18
I am having problems with the Adobe PDF plugin to load and display PDFs within the browser.

This is a plain Natty-installation with Firefox 4. Adobe Reader 9 is installed with the deb package from the adobe - homepage.

The PDF seems to load when the file is actually stored on a webserver. But when the PDF is kind of dynamically generated, the file is not opened by the plugin but a file-save/open dialog appears.

Can someone reproduce this behaviour? To test, please go, for example, to 

[http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.110.6657&rank=1](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.110.6657&rank=1)

If you click the PDF button unter "cached", the PDF is not loaded within the browser on my system.
If you however click, for example the second link under "Downloads" everything works as should.

Things I tried that failed:
- completely removing Adobe Reader 9 and the plugin and try to use Reader 8 + plugin instead
- using Mozplugger/evince instead of the Adobe Reader 9 plugin

In all cases, the PDF under "cached" is not loaded within the browser.
As comparision, for example in Windows 7 using Adobe Reader X, everything works as should.

I am not sure which one is the culprit here, my suspicion is Firefox 4...

As said, can someone reproduce this behaviour?
Do you know of existing bugreports either in launchpad, firefox bugzilla etc?

---

### Post by mikeh2508 on 2011-06-20
Hi,

Being totally new to this - I am having exactly the same problem. Thought it was me but if others have the issue :D

---

### Post by spieler8 on 2011-06-23
Seems a bug has been filed recently 

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/799337](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/799337)

You might want to subscribe.

Still wondering wether its only us two. come on guys, really easy to check! :-)

---

### Post by lovinglinux on 2011-06-23
> **spieler8 said:**
> Still wondering wether its only us two. come on guys, really easy to check! :-)

Well, I guess lots of people don't use the Adobe plugin. I never liked it, even  when I was a Windows user. There are alternatives that don't require to install a 200+ Mb package. For instance, I use [gPDF]("https://addons.mozilla.org/en-US/firefox/addon/14814/") for Firefox, but you can use Evince or Okular with mozplugger plugin.

BTW, the days of Adobe plugin are over. Google Chrome already has a built-in reader and Mozilla is working on a Firefox version that will handle PDFs natively using HTML5, without the need for third-party plugins.

---

### Post by spieler8 on 2011-06-24
[quote=spieler8]
Things I tried that failed:
- using Mozplugger/evince instead of the Adobe Reader 9 plugin
[/quote]

[quote=spieler8]
Can someone reproduce this behaviour?
[/quote]

no offense, but did you actually read what I've written?

---

