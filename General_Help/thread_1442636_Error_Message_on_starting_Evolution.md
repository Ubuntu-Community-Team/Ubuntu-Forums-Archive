---
title: "Error Message on starting Evolution"
date: 2010-03-30
forum: General Help
---

### Post by herrgottlschnitzer on 2010-03-30
I am a new user to Ubuntu 9.04  I have tried to get EVOLUTION working. I get the Error Message:
Error while Generating Message List, so I can not get started with this program. Also Error while refreshing Folder appears.:(

---

### Post by ajgreeny on 2010-03-30
Sounds as if your mail folder(s) are not being read properly, or are perhaps corrupted in some way.  Have you imported mail from somewhere else to the evolution application you are now trying to use?

---

### Post by byStanderone on 2010-03-30
...haven't encountered any prob with evo in karmic, may i know what distro you are using?

---

### Post by byStanderone on 2010-03-30
....sorry, did'nt notice that you are in jaunty, ajgreeny has a point.

---

### Post by theDaveTheRave on 2010-03-30
herrgottlschnitzer,

I had this problem when I changed desktops.

If you previously used evolution you should be able to copy across the old files that fill the < /.evolution/mail/local > folder and then things should work as planned.

Otherwise if it is a clean install there must be some other problem somewhere?


can you start evolution as root??

```

gksudo evolution

```

if so it is probably going to be easiest to copy over the root contents of < .evolution/mail/local > into your home directory location, change the read / write permisions, then start evolution again....

I would use a file manager for this, as I can never remember the CLI for doing it all in one go ;)

hope that helps a little...

David

---

### Post by herrgottlschnitzer on 2010-03-31
> **ajgreeny said:**
> Sounds as if your mail folder(s) are not being read properly, or are perhaps corrupted in some way.  Have you imported mail from somewhere else to the evolution application you are now trying to use?
No, I have not imported anything to Evoluton. The Message list remains blank. The only other things is that the program indicates that there are 2 unread messages. This is true becauseI can see my Hotmail messages using Firefox. H.

---

### Post by herrgottlschnitzer on 2010-03-31
> **byStanderone said:**
> ...haven't encountered any prob with evo in karmic, may i know what distro you are using?
The Distro is whatever came with the Ubuntu 9.04 package. H

---

### Post by theDaveTheRave on 2010-04-01
herrgottlschnitzer,

maybe the thing to do is to remove evolution using synaptic, the re-install.

You may find that you selecting the it for straight re-installation may work, but if not perform the 2 separately.

The other altenative is to use another email client, have a hunt to what is available, and make your choice.

David

---

### Post by herrgottlschnitzer on 2010-04-02
> **herrgottlschnitzer said:**
> The Distro is whatever came with the Ubuntu 9.04 package. H
The distribution of Evolution that I am trying to use is 2.26.1

---

### Post by herrgottlschnitzer on 2010-04-02
> **byStanderone said:**
> ...haven't encountered any prob with evo in karmic, may i know what distro you are using?
I am using Distribution 2.26.1 of Evolution. I have filled out the Setup Assistant and the screen then changes to the Message List display but I am not asked for a password as the documentation says  should happen. Then if I restart Evolution again and Select Edit   Preferences  I see that some of the info that I previously typed into this file in the Home Directory  has been changed or deleted. For example if I had typed in for incoming mail server configuration [http://www.hotmail.com](http://www.hotmail.com) I then find that only http remains. The [www.hotmail.com]("http://www.hotmail.com") has been deleted.

---

### Post by herrgottlschnitzer on 2010-04-03
> **herrgottlschnitzer said:**
> I am using Distribution 2.26.1 of Evolution. I have filled out the Setup Assistant and the screen then changes to the Message List display but I am not asked for a password as the documentation says should happen. Then if I restart Evolution again and Select Edit Preferences I see that some of the info that I previously typed into this file in the Home Directory has been changed or deleted. For example if I had typed in for incoming mail server configuration [http://www.hotmail.com](http://www.hotmail.com) I then find that only http remains. The [www.hotmail.com]("http://www.hotmail.com") has been deleted.
 
 
I still have not solved the problem of getting Evoution 2.26.1 to work. Can you offer any further help. I really need to get this program working. H.

---

### Post by dcstar on 2010-04-03
> **herrgottlschnitzer said:**
> I still have not solved the problem of getting Evoution 2.26.1 to work. Can you offer any further help. I really need to get this program working. H.

Exit Evolution, rename the hidden .evolution folder and start Evolution again.

---

