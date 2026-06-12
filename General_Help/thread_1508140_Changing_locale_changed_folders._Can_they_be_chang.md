---
title: "Changing locale changed folders. Can they be changed back?"
date: 2010-06-12
forum: General Help
---

### Post by copb.phoenix on 2010-06-12
[http://lh5.ggpht.com/_Ed77Ix-72A0/TBPLPmBzzaI/AAAAAAAAA2Y/ZcuXwGMBgNc/uf.png](http://lh5.ggpht.com/_Ed77Ix-72A0/TBPLPmBzzaI/AAAAAAAAA2Y/ZcuXwGMBgNc/uf.png)

^ A picasa web snapshot of the problem. 

The short version is: My girlfriend's Taiwanese, I'm English, and, while I don't mind leaving such things localized while she's using my laptop, I cannot read her language any better than she can read my handwriting.


*Is there any way to change the pointers back to the English folders?* 


She told me that when she had first loaded it, it had a dialog to ask if she wanted things that way, but she clicked through it without really paying attention. Even just a way to get that dialog back would be greatly appreciated.

---

### Post by copb.phoenix on 2010-06-15
It's been a couple days... Anyone?

---

### Post by dcstar on 2010-06-15
> **copb.phoenix said:**
> 
........
The short version is: My girlfriend's Taiwanese, I'm English, and, while I don't mind leaving such things localized while she's using my laptop, I cannot read her language any better than she can read my handwriting.

*Is there any way to change the pointers back to the English folders?* 
........

Huh?, do you expect Ubuntu to **translate** words in one language to another language?

The names are the names, if you want them in a different language then you will have to manually change them.

---

### Post by copb.phoenix on 2010-06-15
I'm not that lazy, heavens. But, I'd deeply like to change my default pointers back to the English folders. Right now, they point to the Traditional Chinese ones. For example; Let's say I download a file in Firefox. It doesn't go into my Downloads folder; it goes into the Chinese equivalent, &#19979;&#36617;. I'd like to change all of the pointers back to English folders. It's not as easy as "rename them"; the actual pointers have clearly been changed. If you didn't check the snapshot, the English folders never budged an inch, they just aren't being used for some odd reason.

I knew this one was hard to explain... I'm not sure how to better put this across, but feel free to ask questions.

---

### Post by LequinhoTso on 2011-02-17
My situation:

I live in Brazil but like my system in English. I wanted GnuCash to be in Portuguese though, and read that I needed to change my *locale*. So I proceeded to install the portuguese package through System>Admin>Language and after I selected the language I wanted the Window turned grayish, and the ´loading´ cursor appeared whenever I hovered over it. But I was impatient and it was taking too long, so I restarted my system normally.

*Note 1) I don't know if it was right for me to just restart even when it looked like the process was still running.

Lucky me, my login and everything else was now translated into Portuguese without problems. Then I had that windows asking me if I wanted to update the folders, and I said YES. Only a few minutes later I realized that that was, in my opinion, very intrusive, since the paths would become different then what I was used to.

To change back:
A)Went through System>Admin>Language, selected English and reboot.**Didn't work** Because even with the Panels in English (and the date, hour and names of the programs...), the Folders remained translated.

B)Deleted Portuguese through System>Admin>Language, reboot. **Didn't work** Because Everything was like scenario A, and the difference was that according to System>Admin>Language, the Portuguese-pack was uninstalled already.

C)I realized things were very messed up - if I right-click and program (names already in english) I was presented the option in Portuguese. Also, the login still showed me the option to log in Portuguese.

D)Cleaned old and unused files on the system, through Ubuntu Tweak, insanely kept running *locale* and *locale -a* to convince myself that everything was en_US.utf8 (and it was!)

At this point I started freaking out about - "Oh God, can I restore it to an earlier point? Will I have to reinstall Ubuntu?!" And what I told myself the most was: "Now I know it&#347; true - Linux great advantage - full control over the system is it's major disadvantage, especially when on the hands of a stupid user! (I started using Ubuntu one week ago, so I am very very newbie at this time)"

Note 2) During all of this, I was not able to press the "Apply System-Wide" for English on Text tab inside Syst>Admin>Language. I clicked there several times but it was as if that led to no action at all - maybe what the system was thinking was - *´this is the only language available, as far as I can see, so there is no use choosing Apply System-Wide´*. But I knew there were still some traces of Portuguese!

**E) Running *locale* again I noticed this line: *"LANGUAGE=en_US:[B]pt_BR**:en"* and I didn't know a way to change it manually. So I decided to install again, reboot and etc. Again on a Portuguese log, I went to Languages and from there I put pt_BR down below at the end of the list on Language and chose English on both tabs as primary and applied system-wide. 

Reboot...

And with almost everything in English (there were still remains of Portuguese, like the right-click options, some descriptions, and the Folders) I finally uninstalled the Portuguese-pack.

After reboot and login, I was asked if I wanted to update my Folders, I said Yes, and I'm back to English folders.[/B]


*I think that what happened was a bad uninstall process (and I wonder if it had to do with Note 1 above), so installing again the language-pack made it possible to press "Apply system-Wide", and that was one way of forcing the system to really apply English to everything.

Now, I still have the Portuguese Folders, which I just grabbed the files and moved them to the English one and later deleted, since they were no more the official ones, and the Login screen is still in Portuguese, and it is still showing Portuguese as an option.


I'm working on that now.

Hope this long story helps someone, somehow.

---

### Post by LequinhoTso on 2011-02-17
[UPDATE] Ok, after posting here I went through a system cleanup using UbuntuTweak to clean old and unused Packages, Caches and Configs.

After that I did a reboot: **Log in language = English, but there is still Portuguese option.** (I checked locale and Syst>Adm>Languages and Portuguese does not exist anymore... I still don't know where else to look.)

Logging in Portuguese/English, apparently the same.

---

