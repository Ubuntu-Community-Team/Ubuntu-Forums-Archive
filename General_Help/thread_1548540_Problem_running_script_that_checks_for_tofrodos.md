---
title: "Problem running script that checks for tofrodos"
date: 2010-08-08
forum: General Help
---

### Post by Rumpletumbler on 2010-08-08
I'm trying to run this script.   [http://hostsfile.mine.nu/downloads/updatehosts.sh.txt](http://hostsfile.mine.nu/downloads/updatehosts.sh.txt)

tofrodos is installed

I get the message &quot;tofrodos (which contains dos2unix) is missing&quot; when running the script.

ln -s fromdos dos2unix
ln -s todos unix2dos

didn't help  

I don't know if this is an issue since the above links were created.   [https://bugs.launchpad.net/ubuntu/+source/tofrodos/+bug/587973](https://bugs.launchpad.net/ubuntu/+source/tofrodos/+bug/587973)    

Anyone have this working in Lucid?

Nevermind.....got it working by changing dos2unix to fromdos in the script.

---

