---
title: "Flash don't work after bad install?"
date: 2011-10-29
forum: General Help
---

### Post by LeetNeo on 2011-10-29
I used this to install Intel Drivers for graphics, but didn't work out.

[http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

So when I come on FireFox, I try to go on YouTube, there's no flash installed???

So I go into the Ubuntu Software Manager and try to install it there and gives me an error. I tried "Adobe Flash Plugin" for Firefox. Then it says Package Dependencies cannot be resolved.

Can anyone help me? I'm not too good with Linux anymore, my Terminal knowledge isn't the best, thanks.

-LeetNeo.

---

### Post by Gremlinzzz on 2011-10-29
> **LeetNeo said:**
> I used this to install Intel Drivers for graphics, but didn't work out.

[http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

So when I come on FireFox, I try to go on YouTube, there's no flash installed???

So I go into the Ubuntu Software Manager and try to install it there and gives me an error. I tried "Adobe Flash Plugin" for Firefox. Then it says Package Dependencies cannot be resolved.

Can anyone help me? I'm not too good with Linux anymore, my Terminal knowledge isn't the best, thanks.

-LeetNeo.

sudo apt-get install adobe-flashplugin

---

### Post by LeetNeo on 2011-10-29
> **Gremlinzzz said:**
> sudo apt-get install adobe-flashplugin

I guess this is an error?

"E: Package 'adobe-flashplugin' has no installation candidate"

-LeetNeo.

---

### Post by Gremlinzzz on 2011-10-29
make sure canonical is checked in software sources 

you may need this command not sure 
 sudo apt-get -f install

sudo apt-get install sun-java6-jre sun-java6-plugin

sudo apt-get install adobe-flashplugin

---

### Post by Gremlinzzz on 2011-10-29
> **LeetNeo said:**
> I guess this is an error?

"E: Package 'adobe-flashplugin' has no installation candidate"

-LeetNeo.

make sure canonical is checked in software sources

after sudo apt-get update

then  


sudo apt-get install sun-java6-jre sun-java6-plugin

sudo apt-get install adobe-flashplugin

---

### Post by LeetNeo on 2011-10-29
> **Gremlinzzz said:**
> make sure canonical is checked in software sources 

you may need this command not sure 
 sudo apt-get -f install

sudo apt-get install sun-java6-jre sun-java6-plugin

sudo apt-get install adobe-flashplugin

It gives me the same error even after I checked all these, should I reformat?

-LeetNeo.

---

### Post by Gremlinzzz on 2011-10-29
If you want :popcorn:

---

### Post by Gremlinzzz on 2011-10-29
this is what i meant by making sure these are checked,
for some reason there not by default.
[http://ubuntuforums.org/attachment.php?attachmentid=205785&stc=1&d=1319908677](http://ubuntuforums.org/attachment.php?attachmentid=205785&stc=1&d=1319908677)

---

### Post by garvinrick4 on 2011-10-29
Flash aid will remove all previous attempts to install and install anew.
Go to tools in Firefox and select add ons.
Type flash aid in search box and install.
Now stop and restart Firefox and in upper right hand corner is a red circle with f in middle
click on it and choose one of the 3 ways to install. Install it and now restart firefox
and should have Flash. Let me no if you are cool now.

---

### Post by LeetNeo on 2011-10-29
> **Gremlinzzz said:**
> this is what i meant by making sure these are checked,
for some reason there not by default.
[http://ubuntuforums.org/attachment.php?attachmentid=205785&stc=1&d=1319908677](http://ubuntuforums.org/attachment.php?attachmentid=205785&stc=1&d=1319908677)

Everything is checked, nothing working.

> **garvinrick4 said:**
> Flash aid will remove all previous attempts to install and install anew.
Go to tools in Firefox and select add ons.
Type flash aid in search box and install.
Now stop and restart Firefox and in upper right hand corner is a red circle with f in middle
click on it and choose one of the 3 ways to install. Install it and now restart firefox
and should have Flash. Let me no if you are cool now.

Tried it just now, nothin'.

I'm going to just reformat.

-LeetNeo.

---

