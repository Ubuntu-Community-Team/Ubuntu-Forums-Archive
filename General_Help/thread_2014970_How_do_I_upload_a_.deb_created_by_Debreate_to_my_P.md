---
title: "How do I upload a .deb created by Debreate to my PPA?"
date: 2012-07-02
forum: General Help
---

### Post by alenn on 2012-07-02
I made a program using Qt Creator, and I made a package (.deb) using Debreate. Now I want to know how to upload this on PPA. I already created PPA on launchpad.

---

### Post by Cheesehead on 2012-07-02
You don't.

You upload the source (not the binary), and Launchpad's PPA service builds the package for you.

---

### Post by alenn on 2012-07-03
I have multiple files of source code, how to package it so I can upload it on PPA

---

### Post by alenn on 2012-07-03
bump

---

### Post by Cheesehead on 2012-07-03
First, you convert your raw source code files into a *Debian source package*. That's different from a normal Debian (binary) package, so don't get confused by the similar names!

A great explanation of Debian source packages is at [http://wiki.debian.org/SourcePackage#The_definition_of_a_source_package](http://wiki.debian.org/SourcePackage#The_definition_of_a_source_package)

You use the Debian tools to create those three files in the source package.
Most version control systems have add-on tools that will create the source package for you. Bazaar, for example, will even upload to Launchpad for you.

Once you have a source package, [https://help.launchpad.net/Packaging/PPA/Uploading](https://help.launchpad.net/Packaging/PPA/Uploading) shows you how to upload it to Launchpad.

I know it seems weirdly complex. It's not, really. The standards and formats exist so that packages get maintained in a uniform way (so anyone can maintain it when you get bored), and so the packages all get built in a uniform way.

If you're building for yourself, you don't need to invest that upfront time to follow the standards. But if you want to distribute using a PPA, Launchpad requires it. In the long run, if you plan on supporting this package for a few years, doing it right will make your maintenance much faster and easier.

---

### Post by alenn on 2012-07-03
I looked at Bazaar, and found interesanting command: bzr dh-make. but that command don't work even I followed all instructions on their page. Plz can you guide me how to solve this, I'm getting crazy

---

### Post by alenn on 2012-07-04
bump

---

### Post by Cheesehead on 2012-07-06
Well, describe in detail how your project's files are structured, and how you create a deb file now...

Really, what you seem to need is a plain old packaging tutorial (like [http://wiki.debian.org/IntroDebianPackaging](http://wiki.debian.org/IntroDebianPackaging) ). Once you understand the basic requirements and concepts, you can adapt them to your specific needs.

---

