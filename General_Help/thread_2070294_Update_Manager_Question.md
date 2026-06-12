---
title: "Update Manager Question"
date: 2012-10-12
forum: General Help
---

### Post by gregintexas on 2012-10-12
Hi;

I am using Ubuntu 12.04 LTS on my Samsung Chronos laptop. My upgrade manager is set to run each Friday. A couple of weeks ago, and today, Update Manager lists quite a few KDE related packages it wants to update. I do not use KDE. I decided at the outset I would try out Unity for a while, and it turned out that I liked it quite a bit.

Is KDE required in some way? The packages it wants to update do NOT appear in my list of installed packages. Why does it want to update KDE when KDE is not in use?

It also is attempting to update/install something called "Find obsolete NVidia Drivers". Why? The Chronos has an ATI card, not an NVidia (it also has a built in Intel card that I am not using). Why would Update Manager want to install this?

It's not a huge big deal, but it is annoying unchecking all those packages every time. I put enough "stuff" on my system without Ubuntu putting stuff on it that I am not going to use. Any idea why it would do this?

Thanks in advance;

G

---

### Post by zvacet on 2012-10-12
You probably installed some KDE application and that can be reason why you are getting KDE updates.
> The packages it wants to update do NOT appear in my list of installed packages.

I will not say that I don´t believe you but you can not update something you didn´t install.Try to run 

```
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages 
```

and you will get list of all installed packages.

---

### Post by gregintexas on 2012-10-12
I've listed my packages a number of different ways, but executed your command. Editing the file and listing all packages that begin with "k":

kbd                                                                             
kdelibs-bin                                                                     
kerneloops-daemon                                                               
keyboard-configuration                                                          
klibc-utils                                                                     
krb5-locales   

kdelibs-bin belongs to the KDE family, and maybe klibc-utils, but none of the other packages such as katepart, kde-runtime, and dozens of others are installed. That's why I'm asking. It doesn't make sense.

I used to use KDE back in the day, but started using (and liking) gnome on SLES10. I'm not planning on returning to KDE. Is Ubuntu trying to tell me something?

G

---

### Post by gregintexas on 2012-10-12
These libraries *may* belong to KDE as well ...

libkidletime4                                                                   
libklibc                                                                        
libkmediaplayer4                                                                
libknewstuff3-4                                                                 
libknotifyconfig4                                                               
libkpathsea5                                                                    
libkrb5-26-heimdal                                                              
libkrb5-3                                                                       
libkrb5support0

G

---

### Post by sandyd on 2012-10-12
If you install a KDE app (ex: Amarok), Ubuntu will pull in KDE libraries as dependencies.

As a result, you shouldn't be worried - unless you don't want any KDE-based app on your system, since only the libraries (not the kde desktop) is installed. ;) .

---

### Post by gregintexas on 2012-10-12
Maybe I'm not being clear. Update manager is attempting to "update" (I guess install)

kate-data
kdatepart
kde-runtime
kde-runtime-data
kdelibs-bin
kdelibs5-data
kdelibs5-plugin
kdemultimedia-kio-plugins
kdoctools
libkatepartinterfaces4
libkcddb4
libkcmutils
libkde3support4
libkdeclaritive5 (plasma)
libkdecore5
libkdesu5
liblkdeui5
libkdewebkit5
libkmediaplayer4
libknewstuff3-4
libknotifyconfig4
...
There are actually quite a few more. I have none of these presently installed. Why are they attempting to update?

G

ps ... I've actually been trying NOT to install KDE dependent apps as I did so in 10.04 LTS and never really used the stuff.

---

### Post by gregintexas on 2012-10-13
I'm facing the problem, yet again with this morning's updates. Anyone with an idea of where I could go to research the problem?

---

### Post by gregintexas on 2012-10-16
Bump.

---

### Post by jerrrys on 2012-10-16
Look in /usr/share/applications for KDE apps

---

