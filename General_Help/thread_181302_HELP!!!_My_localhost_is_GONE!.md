---
title: "HELP!!! My localhost is GONE!"
date: 2006-05-24
forum: General Help
---

### Post by Isoss on 2006-05-24
I was installing some stuff with synaptic ( note softwares and dictionaries ) and have downloaded firefox 1.5. After I'm done, I opened my [http://localhost](http://localhost) and a page called : CAUDIUM The other fish! appeard. My index is doesn't appear at all. the address is still [http://localhost](http://localhost) but I can't like open [http://localhost/phpmyadmin](http://localhost/phpmyadmin) or [http://localhost/mywebsite/index.php](http://localhost/mywebsite/index.php) .. instead, it downloads the index.php file with the firefox download manager! I read that page 4 times and didn't understand a thing or how to fix this! ... please help!! I have a lotta work on my websites and if i'd spend a day on this it'll be bad!

This is the page: 
[IMG]http://nourelalam.org/Isos/Screenshot.png[/IMG]

---

### Post by Isoss on 2006-05-24
Alright, I opened synaptic and found that there is a broken file. update manager told me that software index is broken and that I'd better run apt-get -f install and I did. then I open [http://localhost](http://localhost) and that page is gone and the index is back. but when I tried to open one of my website folders it asked me to download the file or open it in the browser. and in both situations it downloads, whether I select save or open ... 
I also noticed something! that folders with the index.html work but the ones with the index.php gives that download prompt. and when I save the file it saves it as something like 8ssm1276.phtml instead of index.php.

Any clues?

---

### Post by adamkane on 2006-05-24
Which web server are you installing? Give more details about what you did.

I believe, that you need to re-install your web server.

---

### Post by Isoss on 2006-05-24
I am not installing a webserver. it's already installed and I have been using it for 2 months. but today, as I mentioned previously, was installing some softwares that, as far as I know, have nothing to do with the webserver .. may something was installed by mistake.

I have apache2 ... but since you have asked which webserver! I'd like you to tell me what else is there? I don't know any other webserver but IIS back in windows and apache! ... just curious since you have asked implying! ... and maybe I can reinstall the webserver and change it with something better for mysql and php work.

Thanks

---

### Post by adamkane on 2006-05-24
[SIZE=2]Please try one of these:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```
[/SIZE]

---

### Post by Isoss on 2006-05-24
ok .. but don't I have to uninstall the server first?
I am installing some stuff with synaptic so I can't use terminal at the moment. but just to make sure cuz I tried uninstalling the server once and didn't work cuz it has dependencies as far as I remember. do I have to remove before running the commands that you gave me? or it'll just update the whole thing? and if I have to remove, is there a way to uninstall or remove the apache2 without having it nagging that it has dependencies? 

I have php4 and I am a breezy user. will it be better if I keep php4 or it's ok ( and better ) to install php5? and if php5 is installable, will I have to remove php5? or it'll just be updated?

---

### Post by adamkane on 2006-05-24
You may install the one you prefer. I've installed PHP4, and then I installed PHP5, and everything was OK.

---

### Post by ifokkema on 2006-05-25
Hi,

You're problem is that you've now got caudium installed, which is a webserver. Judging from you're story, you had apache2 and you were installing software. Caudium got somehow installed, bound to your 127.0.0.1 IP address and is now serving as your webserver, pushing apache2 to the side.

You probably can read in error in /var/log/apache2/error.log that it couldn't bind to your 127.0.0.1:80 ip address.

Anyway, get rid of caudium and you're done. Although you might have installed some software that needs caudium. If that's the case, you need to run caudium on a different port than apache2.

Hope this helps you out,

Ivo

---

### Post by adamkane on 2006-05-25
I didn't find helpful info about Caudium with Google, so I assumed that you don't need Caudium. Please tell us about the applications you installed.

---

### Post by Isoss on 2006-05-25
[QUOTE=ifokkema]Hi,

You're problem is that you've now got caudium installed, which is a webserver. Judging from you're story, you had apache2 and you were installing software. Caudium got somehow installed, bound to your 127.0.0.1 IP address and is now serving as your webserver, pushing apache2 to the side.

You probably can read in error in /var/log/apache2/error.log that it couldn't bind to your 127.0.0.1:80 ip address.

Anyway, get rid of caudium and you're done. Although you might have installed some software that needs caudium. If that's the case, you need to run caudium on a different port than apache2.

Hope this helps you out,

Ivo[/QUOTE]



Thanks a lot. anyway, I did notice it's because of some software that was installed "somehow" ... like these dependencies with which some programs can't be installed without. so I searched synaptic for caudium and found it installed.  uninstalled it and then rebooted and it kept appearing. anyway, I continued working with some stuff and then, don't know what happened ... I entered the recovery mode then rebooed again and ubuntu just won't start as Gnome or as anything but as recovery ... so I had to reinstall ubuntu ... 

anybody knows what happeden? I thought recovery is something like safe mode in windows. maybe it is, but when I rebooted it just seemed to boot into it again although I chose the fisrt choice at the dual boot.

I don't want this to just pass like this ... it's really bad when I had all my programs installed and then I had to reinstall again. its really painful or a hard worker and a student like me :( 
so I hope I can find an answer for this and advices so I can avoid such a thing again. I also have leanrd something ... when I am installing a lotta packages, I must make sure that nothing was selected by default from the list as a dependency package. I mean like something I am not sure of ...

Thank you guys.

---

### Post by ifokkema on 2006-05-25
[QUOTE=Isoss]Thanks a lot. anyway, I did notice it's because of some software that was installed "somehow" ... like these dependencies with which some programs can't be installed without. so I searched synaptic for caudium and found it installed.  uninstalled it and then rebooted and it kept appearing. anyway, I continued working with some stuff and then, don't know what happened ... I entered the recovery mode then rebooed again and ubuntu just won't start as Gnome or as anything but as recovery ... so I had to reinstall ubuntu ... 

anybody knows what happeden? I thought recovery is something like safe mode in windows. maybe it is, but when I rebooted it just seemed to boot into it again although I chose the fisrt choice at the dual boot.

I don't want this to just pass like this ... it's really bad when I had all my programs installed and then I had to reinstall again. its really painful or a hard worker and a student like me :( 
so I hope I can find an answer for this and advices so I can avoid such a thing again. I also have leanrd something ... when I am installing a lotta packages, I must make sure that nothing was selected by default from the list as a dependency package. I mean like something I am not sure of ...[/QUOTE]

Hmm... not sure what you uninstalled, but apparently something important. I assume Ubuntu would tell you what went wrong during the boot. It can drop back to recovery mode if something serious happens.

You can get some information about packages that require caudium by running:
```
apt-cache showpkg caudium
```

Maybe a name pops up that you recognize.

I always use the command line to install / uninstall packages and I always clearly examine additional packages that get installed. If it ever happens again, however, I would try to keep caudium from starting up by using rcconf or try and configure caudium to bind to a different port. Not really a solution, but it would work for you.

Good luck on your new install!

Ivo

---

### Post by rickc on 2006-05-25
Does Ubuntu plan on coming with apache or 2 installed, or is to Overkill for the distro disk?

---

### Post by adamkane on 2006-05-27
It would be too insecure to come pre-installed with any servers.

---

