---
title: "Cant figure out how to install tar.gz"
date: 2010-11-26
forum: General Help
---

### Post by jadms85 on 2010-11-26
I have been trying every method of installing tar.gz(apache download) i have looked through a million how tos and maybe im missing something.I have build essential al that couldnt figure it out so i tried through terminal no luck there either---Terminal-- when i enter tar xfvz and filename i get a no such file or directory error am i supposed to mkdir or something i have tried extracting files through virtual means with extraction software but i downloaded sypatic etc and i get lost there can anyone shead soem light on how to install tar .gz files

---

### Post by Swagman on 2010-11-26
Did you cd to the dir where the Tar is ?

---

### Post by jadms85 on 2010-11-26
no i had a feeling that is where i was going wrong could you explain how to and what that process actually does.

---

### Post by dino99 on 2010-11-26
with synaptic, install alien & gdebi

then goto your tar.gz folder and:

sudo alien -k filename.tar.gz

(replace filename by its real name of course)

you get a deb file, doubleclick on it for installation

---

### Post by gandaran on 2010-11-26
> **dino99 said:**
> with synaptic, install alien & gdebi

then goto your tar.gz folder and:

sudo alien -k filename.tar.gz

(replace filename by its real name of course)

you get a deb file, doubleclick on it for installation
you must mean install 'checkinstall' not alien, alien is for converting RPM packages to .DEB, checkinstall is for building .deb packages from source code

---

### Post by dino99 on 2010-11-26
> **gandaran said:**
> you must mean install 'checkinstall' not alien, alien is for converting RPM packages to .DEB, checkinstall is for building .deb packages from source code

just try then you will know :)

---

### Post by nss0000 on 2010-11-26
Twenty years ago tar.gz was important, but no longer.  People would keep entire norebooks filled with the  ARCAENA of tar.gz usage and all its variants.  It was like taking PhD candidacy exams every time you had to use the syntax !!  Brain-death was immediate for many, and they returned as babbling idiots to M$. 

No longer. Since it's too hard to learn howto use, and Ubuntu will make available automagically any software that's worth installing in Ubuntus unfailing judgment you no longer need to worry. 

So save your tender braincells and ignore such **stone-age** felons as tar.gz !

---

### Post by gandaran on 2010-11-26
> **dino99 said:**
> just try then you will know :)

prove it! have you tried it? where did you read alien builds .deb's out of tar packages, nonsense!

---

### Post by dino99 on 2010-11-26
> **gandaran said:**
> prove it! have you tried it? where did you read alien builds .deb's out of tar packages, nonsense!

yes sometimes i use it and that perfectly work, point. Learn your lesson kid.

---

### Post by jadms85 on 2010-11-26
I have check install and gdebi but i do not know how to use synaptic interface i search apache and it gives me a huge list of file names with gdebi and checkinstall to i just sudo the other commands

---

### Post by dino99 on 2010-11-26
> **jadms85 said:**
> I have check install and gdebi but i do not know how to use synaptic interface i search apache and it gives me a huge list of file names with gdebi and checkinstall to i just sudo the other commands

--> system admin synaptic

---

### Post by gandaran on 2010-11-26
> **jadms85 said:**
> I have check install and gdebi but i do not know how to use synaptic interface i search apache and it gives me a huge list of file names with gdebi and checkinstall to i just sudo the other commands
if it's apache you want to install then just mark the 'apache2' package in synaptic for install and click the apply button.

---

### Post by jadms85 on 2010-11-26
ok i did that now how do i find apache??

---

### Post by gandaran on 2010-11-26
> **jadms85 said:**
> ok i did that now how do i find apache??
you mean how do you run apache? apache is just a server it doesn't have an interface gui, post a new thread on how to start apache (I don't know how to) I think you should read the apache tutorial and learn first, google it, theres a lot of information about apache.

---

### Post by BeachBuddah on 2010-11-26
Hi - been following this thread - it's nice to find an alternative to the traditional tar.gz install process...but

I ran the sudo -k alien command on the terminal for my own tar.gz file (libre office) and got this output:

libo-3.3.0-linux-x86-install-rpm-en-us_1-1_all.deb generated

but when I navigated to the folder with the tar.gz file, there was no deb pkg to be seen - any ideas on how to find it?

---

### Post by mc4man on 2010-11-26
> any ideas on how to find it?
Do a search
It's best to create a folder to do build  in, then it will be obvious.
Alien can build .debs directly from archived sources though I'd be a bit careful with it's use. ( actually not sure what the 'value' is here, for the most part a waste of time

---

### Post by BeachBuddah on 2010-11-26
> Do a search

mcman ty for the reply - I'm truly new to Ubuntu and Linux...how do I do a search?

OK - skip that, I found the search fn.  But strangely enough, while the Ubuntu Software Center says that Libre Office is installed, I can't find it - search function or no.  I'm just a bit baffled here.  Any suggestions will be greatly appreciated.

---

### Post by mc4man on 2010-11-26
> Any suggestions will be greatly appreciated.

Well first remove that 'package' you built, (probably installed basically a bunch of folders/files to /.
(I wouldn't bother with alien, it may have some value with something, for sources that actually need to be compiled - don't waste your time.

You'd be better off trying  a pre-built Libre Office deb set - please read here
[http://ubuntuforums.org/showthread.php?t=1585017&highlight=Libre+Office](http://ubuntuforums.org/showthread.php?t=1585017&highlight=Libre+Office)

---

### Post by BeachBuddah on 2010-11-28
OK - tyvm mcman - done and done - I have my LO installed.  I appreciate the help.

---

### Post by bearcat7 on 2011-01-10
Alien worked perfect for me

Thx for info

Using Ubuntu10.10

---

