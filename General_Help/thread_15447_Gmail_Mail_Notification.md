---
title: "Gmail Mail Notification"
date: 2005-02-14
forum: General Help
---

### Post by csindone on 2005-02-14
I have searched the posts and I found some people are using Mail Notification for Unbuntu and Gmail. I have tried all the panel alers and even gdesklets but nothing works for Gmail.

[http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)

Only problem is I am a newbie and am not sure how to install it. I downloaded the source distribution and extracted the contents, I followed the install instructions but it didn't work.

Can someone help

---

### Post by piedamaro on 2005-02-14
Mail-notification works well. The easiest thing to do is to install a precompiled package for mail-notification (.deb)
You can find it at the same place where you downloaded the source :)

---

### Post by scoon on 2005-02-14
Hey there, 

In a terminal try this: 
apt-cache search notification$

the deb package is called mail-notification.  I use it everyday.


scoon

---

### Post by csindone on 2005-02-14
[QUOTE=piedamaro]Mail-notification works well. The easiest thing to do is to install a precompiled package for mail-notification (.deb)
You can find it at the same place where you downloaded the source :)[/QUOTE]
 I can download the (.deb), but how do I install it?

---

### Post by piedamaro on 2005-02-14
put the .deb in your home dir. Then open a terminal and type:
sudo dpkg -i <packagename.deb>

substitute <packagename.deb> with the real package name, you can type the first 2 or 3 letters and then hit tab for autocompletion.

scoon, I searched through apt, but I couldn't foind mail-notification, I've compiled and installed it with checkinstall :)
Did you add any extra repository?

---

### Post by scoon on 2005-02-14
Hey there, 

Check this out: [http://ubuntuguide.org/index.html#synaptic](http://ubuntuguide.org/index.html#synaptic)

That will help you with installing new software. 


scoon

---

### Post by ups on 2005-02-14
[QUOTE=csindone]I can download the (.deb), but how do I install it?[/QUOTE]
 You can install a deb file by doing this:
```
sudo dpkg -i <file-name>
```

However, there's no need for this. Synaptic already has it, search for mail-notification in synaptic and install from there.

---

### Post by csindone on 2005-02-14
[QUOTE=ups]You can install a deb file by doing this:
```
sudo dpkg -i <file-name>
```

However, there's no need for this. Synaptic already has it, search for mail-notification in synaptic and install from there.[/QUOTE]
 I did find it in Synaptic, but when I try and install it I get a warning window telling me it could not mark the package for installation or upgrade, and then there is a drop down list with uninstalled packages

---

### Post by ups on 2005-02-14
[QUOTE=csindone]I did find it in Synaptic, but when I try and install it I get a warning window telling me it could not mark the package for installation or upgrade, and then there is a drop down list with uninstalled packages[/QUOTE]
 weird, well can u install using the dpkg command?

---

### Post by csindone on 2005-02-14
[QUOTE=ups]weird, well can u install using the dpkg command?[/QUOTE]
 the dpkg -i command also showed missing dependies, but i have been messing around a lot with stuff, I have considered doing a clean install

---

### Post by csindone on 2005-02-15
I decide to start from scratch, and did the following:

1. Fresh install of Ubuntu and during installation I let it do the updates off the internet.

2. Added extra repositories as per Unofficial Ubuntu 4.10 guide

3. apt-get update and upgrades

4. ran Smart Update in Synaptic

did a search for mail-notification in Synaptic and it wasn't found
downloaded the .deb package and tired to install but to many errros

Any suggestions?

---

### Post by scoon on 2005-02-15
Hey there, 

Read this: [http://www.debian.org/doc/manuals/repository-howto/repository-howto.html#id2781524](http://www.debian.org/doc/manuals/repository-howto/repository-howto.html#id2781524)

And add the .deb you have to your own repo. 


scoon

---

### Post by csindone on 2005-02-15
[QUOTE=scoon]Hey there, 

Read this: [http://www.debian.org/doc/manuals/repository-howto/repository-howto.html#id2781524](http://www.debian.org/doc/manuals/repository-howto/repository-howto.html#id2781524)

And add the .deb you have to your own repo. 


scoon[/QUOTE]
 I tried following the article, I downloaded the .deb of the mail-notification file and put it in my home directory, then I altered the source.lists to add the location but all I got were errors, I tried switching the syntax around but no luck.

I think I am to much of a linux newbie for this

---

### Post by kresten on 2005-02-15
[QUOTE=csindone]I have searched the posts and I found some people are using Mail Notification for Unbuntu and Gmail. I have tried all the panel alers and even gdesklets but nothing works for Gmail.

[http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)

Only problem is I am a newbie and am not sure how to install it. I downloaded the source distribution and extracted the contents, I followed the install instructions but it didn't work.

Can someone help[/QUOTE]

Hi chech this firefox extension out it works great for me!!

 [http://www.nexgenmedia.net/extensions/](http://www.nexgenmedia.net/extensions/)

---

### Post by ups on 2005-02-15
[QUOTE=csindone]I decide to start from scratch, and did the following:

1. Fresh install of Ubuntu and during installation I let it do the updates off the internet.

2. Added extra repositories as per Unofficial Ubuntu 4.10 guide

3. apt-get update and upgrades

4. ran Smart Update in Synaptic

did a search for mail-notification in Synaptic and it wasn't found
downloaded the .deb package and tired to install but to many errros

Any suggestions?[/QUOTE]
 I assume u tried using dpkg -i... the errors were dependency errors? if so, you might need to install them, via synaptic. if its some other errors, can u paste them here?

---

### Post by piedamaro on 2005-02-15
[QUOTE=csindone]I think I am to much of a linux newbie for this[/QUOTE]
To install a package? Nooooo :) Don't worry, it's just a matter of dependencies. Post your error messages.

---

### Post by csindone on 2005-02-15
[QUOTE=piedamaro]To install a package? Nooooo :) Don't worry, it's just a matter of dependencies. Post your error messages.[/QUOTE]
 chris@ubuntu:~ $ sudo dpkg -i mail-notification_1.0-1_i386.deb
(Reading database ... 64043 files and directories currently installed.)
Preparing to replace mail-notification 1.0-1 (using mail-notification_1.0-1_i386.deb) ...
Unpacking replacement mail-notification ...
dpkg: dependency problems prevent configuration of mail-notification:
 mail-notification depends on libeel2-2 (>= 2.8.2); however:
  Version of libeel2-2 on system is 2.8.1-0ubuntu1.
 mail-notification depends on libgnutls11 (>= 1.0.16); however:
  Package libgnutls11 is not installed.
dpkg: error processing mail-notification (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mail-notification
chris@ubuntu:~ $

That is what I get, I tried to do a search and install the missing packages in synaptic, but that didn't work

---

### Post by Jad on 2005-02-15
hmm why anyone need Gmail mail notification while there is a gmail notifier extention for firefox?

---

### Post by ups on 2005-02-15
[QUOTE=Jad]hmm why anyone need Gmail mail notification while there is a gmail notifier extention for firefox?[/QUOTE]
 because the firefox extension requires u to keep firefox open, and look into firefox to see if the mail has arrived. If that be the case, I'll just keep my gmail tab open all the time (which I do when I have firefox open).

The mail-notification applet will notify u on the panel, so u dont have to specifically look into firefox for that. 

I like mail-notification applet, but it has always kept crashing on me for whatever reason (not just with ubuntu, but earlier with fedora as well).

---

### Post by macewan on 2005-02-15
wget http://savannah.nongnu.org/download/mailnotify/mail-notification-1.0.tar.gz
tar xzvf mail-no*.gz
cd mail-notification-1.0
./configure
make
sudo make install

---

### Post by csindone on 2005-02-15
actually I solved my mail-notification problems by upgrading Warty to Hoary. Hoary seems to run very well on my PC so far and mail-notification is preinstalled. Now if someone could only show me how to add a command so mail-notification plays a sound file when new mail arrives...

---

### Post by macewan on 2005-02-16
[QUOTE=csindone]actually I solved my mail-notification problems by upgrading Warty to Hoary. Hoary seems to run very well on my PC so far and mail-notification is preinstalled. Now if someone could only show me how to add a command so mail-notification plays a sound file when new mail arrives...[/QUOTE]
 Just keep in mind that upgrading to Hoary may break things elsewhere. Whereas [this](http://www.ubuntuforums.org/showpost.php?p=71404&postcount=20)  will not, plus it would seem to be quicker.

---

### Post by JakeSpeare on 2006-03-16
> sudo apt-get install gmail-notify 
installs a great little notifier.

No hazzle.

---

