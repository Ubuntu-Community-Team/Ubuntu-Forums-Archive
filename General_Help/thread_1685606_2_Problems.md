---
title: "2 Problems"
date: 2011-02-10
forum: General Help
---

### Post by hadaro on 2011-02-10
Hey guys :) please help me.

A) I can't write in "my" language at any program, I used the SCIM thingy and it doesn't work..
and beside that, I have problem with it because I can't use it for every program.

B) I can't open the Synaptic Package Manager,
when I try I get this message:

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by uRock on 2011-02-11
To first fix your package manager problem go into your menus to Applications> Accessories> Terminal, then copy and paste the following command, which should get Synaptic working right. ```
sudo dpkg --configure -a
```

As for the language issue, what language are you trying to use?

Regards,
uRock

---

### Post by hadaro on 2011-02-11
> **uRock said:**
> To first fix your package manager problem go into your menus to Applications> Accessories> Terminal, then copy and paste the following command, which should get Synaptic working right. ```
sudo dpkg --configure -a
```As for the language issue, what language are you trying to use?

Regards,
uRock

Thanks! :)
I am trying to use hebrew

---

### Post by uRock on 2011-02-11
I am not familiar with the Hebrew language, but I was able to find some documentation that may be helpful with getting it working correctly for you. [https://help.ubuntu.com/community/HebrewLocalizationHowto](https://help.ubuntu.com/community/HebrewLocalizationHowto)

---

### Post by hadaro on 2011-02-11
> **uRock said:**
> I am not familiar with the Hebrew language, but I was able to find some documentation that may be helpful with getting it working correctly for you. [https://help.ubuntu.com/community/HebrewLocalizationHowto](https://help.ubuntu.com/community/HebrewLocalizationHowto)

Thank you.
I am having a problem tho.

I copy and pasted this to the terminal:
> sudo apt-get install culmus xfonts-efont-unicode xfonts-efont-unicode-ib xfonts-intl-european msttcorefonts

And than I get this message:
> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What can I do?

---

### Post by uRock on 2011-02-11
Have you run the command I posted earlier? If yes, then do you have Synaptic Package Manager or the Ubuntu Software Center applications open?

---

### Post by hadaro on 2011-02-11
> **uRock said:**
> Have you run the command I posted earlier? If yes, then do you have Synaptic Package Manager or the Ubuntu Software Center applications open?

What do you mean open?
I can now open both of them.

---

### Post by drewsus on 2011-02-11
He means do you have them open. If you have either Synaptic Package Manager or Ubuntu Software Centre open, then if you try to install something in terminal you get the very error you posted. 
Close whichever you have open and try again.

---

### Post by hadaro on 2011-02-11
> **drewsus said:**
> He means do you have them open. If you have either Synaptic Package Manager or Ubuntu Software Centre open, then if you try to install something in terminal you get the very error you posted. 
Close whichever you have open and try again.

Oh, thanks for translating :P lol.
no I don't have them open.

---

### Post by drewsus on 2011-02-11
I am pretty sure you do/did when you ran that command.
That is the **exact** error you get when you run an install command in terminal with one of those two applications open. 

Please *insure* that they are closed and then run this command in terminal again: 
```
sudo apt-get install culmus xfonts-efont-unicode xfonts-efont-unicode-ib xfonts-intl-european msttcorefonts 
```

If you get the same error again, **don't close anything and take a screen shot** and attach it here or upload it to [www.imgur.com](www.imgur.com) and share the link to the image please

---

### Post by hadaro on 2011-02-11
> **drewsus said:**
> I am pretty sure you do/did when you ran that command.
That is the **exact** error you get when you run an install command in terminal with one of those two applications open. 

Please *insure* that they are closed and then run this command in terminal again: 
```
sudo apt-get install culmus xfonts-efont-unicode xfonts-efont-unicode-ib xfonts-intl-european msttcorefonts 
```If you get the same error again, **don't close anything and take a screen shot** and attach it here or upload it to [www.imgur.com]("http://www.imgur.com") and share the link to the image please

Hey it works.. I assumed I had it closed because I tried some other stuff and they worked :P but ok im good :)

Sorry for being too much new here, but I don't understand what to do next.. what I don't understand is in **bold**:
> Navigate to "System"-->"Administration"-->"Language Support". Mark "Hebrew" as your desired language, and choose to "Apply" the changes. This will install neccessary locale data as well as do any configuration needed to put the new locale into effect. **Aft****er you finish it's recommended you log out and re log in to GNOME to have ****the new locale settings take effect. **

Hmm... GNOME?

---

### Post by drewsus on 2011-02-11
Gnome is the desktop environment.
[http://www.gnome.org/](http://www.gnome.org/)
It is an integral part of Ubuntu. 
It is basically saying logout of your Ubuntu session and log back in.

---

### Post by hadaro on 2011-02-11
> **drewsus said:**
> Gnome is the desktop environment.
[http://www.gnome.org/](http://www.gnome.org/)
It is an integral part of Ubuntu. 
It is basically saying logout of your Ubuntu session and log back in.

I tried :( it didn't work.

---

