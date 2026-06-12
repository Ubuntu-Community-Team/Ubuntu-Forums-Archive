---
title: "How do I my own open source software for inclusion in the official Ubuntu distro ?"
date: 2009-07-29
forum: General Help
---

### Post by seemanta on 2009-07-29
Hi,

I have written an open source software which I feel would be good if made a part of the official Ubuntu distribution. 

But how do I go about it ? Do I first have to submit it to Debian and then Ubuntu will pick it up? Or is there a process to directly submit my package to the Ubuntu maintainers ?

Any help, pointers would be appreciated.

regards,
Seemanta

---

### Post by mikewhatever on 2009-07-29
Is your software available for testing? What is it? Where is it?

Sharing with the community before having it included is a good idea. Why do you think your software is useful?

---

### Post by pastalavista on 2009-07-29
The best way (I've heard) to get software considered for Ubuntu is to create an account with [Launchpad.net]("http://launchpad.net") and upload your code for evauation and "vetting". It is a very slow process but you can receive lots of input and collaboration.

---

### Post by seemanta on 2009-07-29
Hi,
Thanks for responding, all of you. My software is an open source tool to program AT89S52 microcontrollers. Yes, it is available for testing and already it is being hosted at sourceforge.net: [http://sourceforge.net/projects/gnuproload/](http://sourceforge.net/projects/gnuproload/)


The reason I feel it would be useful is because my software allows users with either the Sunrom or EzEE-downloader AT89S52 boards to migrate to Linux. Previously Sunrom boards and EzEE downloader boards were useful only on Windows. But with my software they can use their boards on Linux also.

Here is a link with more details on why I wrote this software.
([http://seemanta.net/myblog/?p=15](http://seemanta.net/myblog/?p=15)). This was a purely educational venture and I want others also to get benefited out of my software just as I have :-)

regards,
Seemanta

---

### Post by t0p on 2009-07-29
Another good move would be to put it up somewhere for download, so we can use y.our program and rave about it (if it's any good).  You get your program a user-base, which helps if you want it accepted by a distro.  Set up a PPA, so ubuntu users can install and update through the package manager.  Also put up the source code, so the coder community can scrutinize it.  Scrutiny is important in the community.

---

