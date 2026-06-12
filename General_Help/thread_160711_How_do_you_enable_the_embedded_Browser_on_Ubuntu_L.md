---
title: "How do you enable the embedded Browser on Ubuntu Linux?"
date: 2006-04-15
forum: General Help
---

### Post by Phillipus on 2006-04-15
Hi,

(That should say "How do you enable the embedded Browser in **Eclipse **on Ubuntu Linux?").

I have installed Ubuntu 5.10 and eclipse-SDK-3.1.2-linux-gtk from the Eclipse downloads site.  I have also installed Sun's JDK 1.5_06 using make-jpkg and dpkg.    Eclipse and Java now work fine but I cannot get the Embedded Browser (Gecko Mozilla) in Eclipse working.  I have installed Mozilla (using Synaptic Package Manager) and launch Eclipse with the following script:

#!/bin/sh
export MOZILLA_FIVE_HOME=/usr/lib/mozilla
export LD_LIBRARY_PATH=$MOZILLA_FIVE_HOME:$LD_LIBRARY_PATH
/home/phillipus/eclipse/eclipse

But this does not work either.

Any help please!

Cheeers,

PB

---

### Post by Phillipus on 2006-04-15
:) 

I find the solution:

I noticed that the error message in the Eclipse Browser View mentioned not being able to find libstdc++5 so I installed that in Synaptic.

It works now.  So why would that be so?

---

### Post by rfruth on 2006-04-15
I've heard of Eclipse but I use and prefer Firefox so no idea here.

---

### Post by krismatth3 on 2006-04-15
Eclipse is an IDE, [http://eclipse.org/](http://eclipse.org/) . It is not a web browser, so preferring Firefox over Eclipse.. doesn't make sense.

I suspect the reason that you needed lidstdc++5 is that certain versions of Gecko (the renderer behind Firefox and Mozilla) require it. I know Firefox 1.5.0.2 from mozilla.com does.

---

### Post by Phillipus on 2006-04-15
Eclipse is indeed an IDE.  I now have the procedure sorted for running it all nicely in Ubuntu should anyone else need to know:

1.	Install Java 1.5 by whatever voodoo is necessary
2.	Install the &#8220;mozilla-browser&#8221; package via Synaptic
3.	Install the &#8220;libstdc++5&#8221; package via Synaptic if it is not already installed
4.	Install Eclipse from the Eclipse web-site (just untar it)
5.	Add the line &#8220;export MOZILLA_FIVE_HOME=/usr/lib/mozilla&#8221; to the end of the file: /etc/environment (&#8220;sudo gedit /etc/environment&#8221; in Ubuntu)
6.	Hoorah!  This works for all Eclipse RCP apps now.


8)

---

