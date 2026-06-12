---
title: "Question: How to activate update on local repository?"
date: 2010-10-09
forum: General Help
---

### Post by website.reader3 on 2010-10-09
My system is Ubuntu 10.04 lucid desktop on amd64 linux.

I built a mirror repository for the Ubuntu lucid and maverick editions and was able to point the sources.list under /etc/apt to the local server (nginx) hosting the files.

The apt package manager sees the files just fine.

However under the System->Administration->Software Sources menu, the Updates tab has a top section under Ubuntu updates.  Unfortunately all these boxes are grayed out indicating that it doesn't believe the updates are valid or from a valid location?

I did install a trusted key into the apt-key and it lists this key among the other two Ubuntu keys.

When running the CLI command apt-get update, there seems to be no problem?

root@athlon:/etc/apt# apt-get update
Hit [http://server](http://server) lucid Release.gpg
Ign [http://server/](http://server/) lucid/main Translation-en_US
Ign [http://server/](http://server/) lucid/restricted Translation-en_US
Ign [http://server/](http://server/) lucid/universe Translation-en_US
Ign [http://server/](http://server/) lucid/multiverse Translation-en_US
Hit [http://server](http://server) lucid-updates Release.gpg
Ign [http://server/](http://server/) lucid-updates/restricted Translation-en_US
Hit [http://server](http://server) lucid-security Release.gpg
Ign [http://server/](http://server/) lucid-security/restricted Translation-en_US
Hit [http://server](http://server) lucid Release
Hit [http://server](http://server) lucid-updates Release
Hit [http://server](http://server) lucid-security Release
Hit [http://server](http://server) lucid/main Packages          
Hit [http://server](http://server) lucid/restricted Packages    
Hit [http://server](http://server) lucid/universe Packages
Hit [http://server](http://server) lucid/multiverse Packages
Hit [http://server](http://server) lucid/main Sources
Hit [http://server](http://server) lucid/restricted Sources     
Hit [http://server](http://server) lucid/universe Sources       
Hit [http://server](http://server) lucid/multiverse Sources     
Hit [http://server](http://server) lucid-updates/restricted Packages
Hit [http://server](http://server) lucid-security/restricted Packages
Reading package lists... Done

However to get the update check to work, the grayed out boxes are going to have to be fixed.

Any ideas on how to do this?

Do I need the language translations to work?  Does the Ign mean ignored?

Randall

---

