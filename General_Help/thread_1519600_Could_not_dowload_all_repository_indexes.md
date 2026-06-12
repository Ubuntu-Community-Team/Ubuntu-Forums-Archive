---
title: "Could not dowload all repository indexes"
date: 2010-06-28
forum: General Help
---

### Post by kzarya on 2010-06-28
everytime i check for updates using the update manager i get this message "Could not dowload all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead."

I've just started using Ubuntu and loving it, pretty much a beginner. any help regarding the issue would be appreciated.
The message aint causing any problems with the working but i still like to have an error free computer :P thanks a lot

---

### Post by kzarya on 2010-06-30
Someone?? anyone?

---

### Post by mikewhatever on 2010-06-30
A repository may be down sometimes, it doesn't mean something is wrong with the computer. Think of it as an informative notification.;)

---

### Post by Ve5ahchoo8ah on 2010-08-15
I have same problem!
It says

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

is this for the same reason?!:confused:

---

### Post by Elfy on 2010-08-15
That ppa looks like a general sort of address - are you sure you got the right thing when you tried to add whatever ppa it was?

Normally they look like 

[http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu)

This is the one you have an issue with 

[http://ppa.launchpad.net/user/ppa-name/](http://ppa.launchpad.net/user/ppa-name/)

---

### Post by Ve5ahchoo8ah on 2010-08-15
sorry I don't know how to fix it! can you take a look at my sources.list which i have attached in the previous post? where should i correct?![U]
[/U]

---

### Post by kiridude on 2010-08-15
It looks like the particular server you were connecting to is down. Try administration > update manager > settings > ubuntu software tab > download from "other" > select best server.

---

### Post by Ve5ahchoo8ah on 2010-08-15
thanks [kiridude]("http://ubuntuforums.org/member.php?u=797142"),
I did as you said but it gave me the same error! 
when I uncheck everything in "Other software" tab, it works! should I do that?!

---

### Post by kiridude on 2010-08-15
sorry, did not read the thread carefully.

Uncheck them one by one to see which one is the problem one.

---

### Post by Elfy on 2010-08-15
> **samic130 said:**
> sorry I don't know how to fix it! can you take a look at my sources.list which i have attached in the previous post? where should i correct?![U]
[/U]

It's not in your sources list - likely it is in /etc/apt/sources.list.d /foo.lst

Check in Software Sources in the System Admin menu - find one that says 

[http://ppa.launchpad.net/user/ppa-name/](http://ppa.launchpad.net/user/ppa-name/)  and untick it and reload.

Again I say - go back to whatever you have tried to add as a repo and check the details - the address it gives does not appear to be a good ppa address.

---

### Post by Ve5ahchoo8ah on 2010-08-15
thanks [[COLOR=#D40000]**forestpiskie**[/COLOR]]("http://ubuntuforums.org/member.php?u=610428")
It works! that was the solution! thank you very much
:P
(sorry I can't mark the thread as solved!)

---

### Post by Elfy on 2010-08-15
No - I know you can't mark it solved as you hijacked it :p

Glad you are ok though.

---

