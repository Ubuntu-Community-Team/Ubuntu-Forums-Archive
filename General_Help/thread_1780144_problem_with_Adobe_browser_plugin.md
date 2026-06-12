---
title: "problem with Adobe browser plugin"
date: 2011-06-11
forum: General Help
---

### Post by parminides on 2011-06-11
My understanding is that when one installs Adobe Reader the browser plugin automatically gets added.

For some reason the Adobe browser plugin isn't working in Firefox on my Ubuntu 10.10 desktop. The plugin doesn't show up in Tools Add-ons or Tools -> Manage Content Plug-ins.

It works fine on my laptop with the same versions of Ubuntu, Adobe Reader (9.4.2-0maverick1), and firefox (3.6.17).

Starting firefox from a terminal yields messages that are probably illuminating to some:

```

$ LoadPlugin: failed to initialize shared library /opt/google/picasa/3.0/lib/npPicasa3.so [/opt/google/picasa/3.0/lib/npPicasa3.so: cannot open shared object file: Permission denied]
2.4+ kernel w/o ELF notes? -- report this
[COLOR="Red"]*** NSPlugin Viewer  *** ERROR: /opt/Adobe/Reader9/Browser/intellinux/nppdf.so: failed to map segment from shared object: Permission denied[/COLOR]

```

This message caused me to stumble onto the readme file, /opt/Adobe/Reader9/Browser/HowTo/ENU/Browser_Plugin_HowTo.txt, which encouraged me to run the script /opt/Adobe/Reader9/Browser/install_browser_plugin.

I ran it in the local mode, and it created the directory ~/.mozilla/plugins and the file nppdf.so in it. My spirits were high.

Alas, it didn't work, complaining that,

```

$ LoadPlugin: failed to initialize shared library /home/clarkb/.mozilla/plugins/nppdf.so [/home/clarkb/.mozilla/plugins/nppdf.so: wrong ELF class: ELFCLASS32]

```

and again,

```

*** NSPlugin Viewer  *** ERROR: /opt/Adobe/Reader9/Browser/intellinux/nppdf.so: failed to map segment from shared object: Permission denied

```

Next I removed the plugins directory I'd created, and, following an Internet hint, I tried the command:

```

nspluginwrapper -i /opt/Adobe/Reader9/Browser/intellinux/nppdf.so

```

This didn't work either, again complaining that it "failed to map segment..."

Any ideas about what's going on or how I can get the Adobe browser plugin to work? I'm almost sure that it worked not long ago.

---

### Post by linuxinstalledfromhdd on 2011-06-11
Slowly go down this list one by one and make sure you have everything installed on your system..

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

