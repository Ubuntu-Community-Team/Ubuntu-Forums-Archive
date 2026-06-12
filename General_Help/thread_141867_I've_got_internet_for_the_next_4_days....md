---
title: "I've got internet for the next 4 days..."
date: 2006-03-09
forum: General Help
---

### Post by Xecuter on 2006-03-09
...so name EVERYTHING you think I should download and install.

Write it like this:
- Name of product
- Installation method
- Description of the product


For instance, I'd like the ATI graphic drivers. And a Python IDLE.

Name it all, I can uninstall it later if I have no use of it.

---

### Post by justleen on 2006-03-09
[QUOTE=Xecuter]...so name EVERYTHING you think I should download and install.

Write it like this:
- Name of product
- Installation method
- Description of the product


For instance, I'd like the ATI graphic drivers. And a Python IDLE.

Name it all, I can uninstall it later if I have no use of it.[/QUOTE]


errr... A life?



Start with Automatix ([http://ubuntuforums.org/showthread.php?t=138405&highlight=10+packages)](http://ubuntuforums.org/showthread.php?t=138405&highlight=10+packages)), i'd say, and then check this post:
[http://ubuntuforums.org/showthread.php?t=35208&highlight=10+packages](http://ubuntuforums.org/showthread.php?t=35208&highlight=10+packages)

---

### Post by dbott67 on 2006-03-09
For a terminal, I like tilda.  Eye candy 'gdesklets'.  Pure WOW factor '3ddesktop'.  For light-weight system info 'conky'.  Read my post here for details and screenshots.  They can be installed through synaptic:

[http://www.ubuntuforums.org/showpost.php?p=392855&postcount=19](http://www.ubuntuforums.org/showpost.php?p=392855&postcount=19)

This thread has a bunch of cool apps that people have posted about:

[http://www.ubuntuforums.org/showthread.php?t=61805](http://www.ubuntuforums.org/showthread.php?t=61805)

Have fun!

-Dave

---

### Post by meborc on 2006-03-09
-nethack
-sudo ap-get install nethack
-my favourite game :mrgreen:

---

### Post by Xecuter on 2006-03-09
Thanks everybody! Keep 'em comin'!

I'm getting this error: 

W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: Følgende signaturer kunne ikke verifiseres fordi den offentlige nøkkelen ikke er tilgjengelig: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release: Følgende signaturer kunne ikke verifiseres fordi den offentlige nøkkelen ikke er tilgjengelig: NO_PUBKEY E8DDB29170188C3B

---

### Post by justleen on 2006-03-09
[QUOTE=Xecuter]Thanks everybody! Keep 'em comin'!

I'm getting this error: 

W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: Følgende signaturer kunne ikke verifiseres fordi den offentlige nøkkelen ikke er tilgjengelig: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release: Følgende signaturer kunne ikke verifiseres fordi den offentlige nøkkelen ikke er tilgjengelig: NO_PUBKEY E8DDB29170188C3B[/QUOTE]


you need to get a public gpg key.. try this:
 $ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys E8DDB29170188C3B
 $ gpg --armor --export E8DDB29170188C3BF | apt-key add -
 $ apt-get update

---

### Post by Xecuter on 2006-03-09
Doesn't work...

---

### Post by dbott67 on 2006-03-09
It could just be something with your repos.  Read this post and update your sources.list file as indicated.

[http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

-Dave

---

### Post by Xecuter on 2006-03-10
I'm getting a lot more errors with that source.list.

---

### Post by dbott67 on 2006-03-10
Try this [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Fill in the form and create your own.

-Dave

---

### Post by nocturn on 2006-03-10
Clear your sources list (empty), make a backup first.

Now do an apt-get update

Copy the old one back (or one you downloaded).

apt-get upgrade again

That should fix it.

---

### Post by Xecuter on 2006-03-10
[QUOTE=dbott67]Try this [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Fill in the form and create your own.

-Dave[/QUOTE]

Thanks. I got some errors but I've fixed it! I'm starting to get the hang of this. ;)

But anyways... 

List some more if you guys have some! :D

---

### Post by MerZo on 2006-03-10
Maybe offtopic, but why do you want to install software, and why wont you have Internet in 4 days? Vacation?

Don't really see the point. :-)

---

### Post by DavidW2 on 2006-03-10
Xecuter,

You should look at this thread for ideas..

[http://www.ubuntuforums.org/showthread.php?t=35208](http://www.ubuntuforums.org/showthread.php?t=35208)

Page 11 has a summation of the previous posts.

---

### Post by Xecuter on 2006-03-11
[QUOTE=MerZo]Maybe offtopic, but why do you want to install software, and why wont you have Internet in 4 days? Vacation?

Don't really see the point. :-)[/QUOTE]

Well I go to school in the city, and I don't have internet there. But now I've got winter holydays and I'va taken my computer home where I have internet.

---

### Post by Zyphrexi on 2006-03-11
crossfire, client and server
use synaptic and search for crossfire
you can run a server locally and cheat to your hearts content!
(or don't cheat, and get 0wn3D)

oh and make sure you get the map editor.
(I like making demon houses... demons rule)

also... dragon monks are the best characters, but fireborns make the best priests. (just remember that for when you play)

---

