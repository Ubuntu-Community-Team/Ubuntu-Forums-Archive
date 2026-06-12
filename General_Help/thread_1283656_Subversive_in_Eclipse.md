---
title: "Subversive in Eclipse"
date: 2009-10-05
forum: General Help
---

### Post by pmains on 2009-10-05
Running 32-bit Jaunty, I had no luck getting Subclipse installed. For some reason, I kept getting an error indicating that there were no updates to be found at [http://subclipse.tigris.org/update_1.4.x](http://subclipse.tigris.org/update_1.4.x). Oh, well.

So, I next tried the instructions for installing subversive on Ubuntu [from this nileshk.com]("http://74.125.95.132/search?q=cache:yoLwEPUJtIoJ:www.nileshk.com/svn_in_eclipse_subversive_and_svnkit_for_subversion_1_6+nilesh+subversive&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a"). (I'm linking a google cache version, because the site seems to be down for the moment, although it was running this morning.) I installed the 3 recommended plugins from the 2 recommended sources, and reloaded Eclipse. No way to open an SVN perspective under Window > Open Perspective > Other ...

The sources are [http://download.eclipse.org/technology/subversive/0.7/update-site/](http://download.eclipse.org/technology/subversive/0.7/update-site/) and [http://www.polarion.org/projects/subversive/download/eclipse/2.0/update-site/](http://www.polarion.org/projects/subversive/download/eclipse/2.0/update-site/).

I tried adding "-Djava.library.path=/usr/lib/jni" to eclipse.ini.
I made sure the "subversion" package (which should include javahl) was installed.
I installed the Sun Java 6 SDK.
I went back and added as many plugins as I could from the 2 aforementioned sources, reloaded, etc. but still no dice.

So, one thing that jumps out at me is that, under Eclipse SDK > /usr/lib/eclipse > Eclipse Project SDK 3.2.2.[long char string], there is a plugin that has an error. None of the SVN plugins have errors, but this one has to do with JUnit and may be somehow related. Under status, 'Plug-in "org.eclipse.jdt.junit4.runtime" version "0.0.0" referenced by this feature is missing.' I made sure that junit (and, of course eclipse-jdt) were already installed, so I don't know what this error is about.

But, meanwhile, I still have the following Subversion SVN plugins installed:
[LIST]
[*]Connectors 2.2.1.[long char string]
[*]JDT Ignore Extensions
[*]Team Provider Localization
[*]Team Provider Sources
[*]Team Provider UI Capabilites
[*]Team Provider
[/LIST]
as well as SVNKit 1.3.0 Implementation installed. But no way to access them.

So, I'm pretty much stumped. Any help would be appreciated.

---

### Post by pmains on 2009-10-05
Also, I tried removing eclipse using "sudo apt-get purge eclipse". I got a message indicating that eclipse* would be removed. But, when I went to reinstall eclipse, no download was required (so not purged, I guess?) and the problems I had before were still there.

---

### Post by pmains on 2009-10-05
Also, the eclipse.ini change was suggested on [this dude's blog]("http://stuffikeepforgettinghowtodo.blogspot.com/2009/05/subversive-eclipse-on-jaunty-ubuntu.html").

He also suggested installing the libsvn-java package. Which I did. Didn't solve the problem, but seems like it couldn't have hurt.

---

### Post by pmains on 2009-10-08
I gave up and installed the latest Eclipse (Galileo) from eclipse.org. Subclipse installed the first time using [http://subclipse.tigris.org/update_1.6.x](http://subclipse.tigris.org/update_1.6.x) (1.6.x currently being the most recent) as the source address.:(

---

