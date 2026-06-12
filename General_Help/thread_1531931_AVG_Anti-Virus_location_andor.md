---
title: "AVG Anti-Virus location and/or"
date: 2010-07-15
forum: General Help
---

### Post by BSG Fan on 2010-07-15
Okay, my Ubuntu is 9.10
When I had Windows in prehistoric times I used to have the free "AVG Anti-Virus".  Okay, Linux does not need antivirus but I see that there is software for Linux anyway.  I saw it today and I couldn't wait.
Lol, I supposed don't nee it but I downloaded.

Okay,
I did,  where, in what location exactly is the "AVG"?
I don't see it in any place around of its 80 mby.
Where it's?

the file I downloaded was this:
[B]AVG Anti-Virus Free Edition for Linux
(avg85flx-r812-a3371.i386.deb) 8.5.0812 deb April 29, 2010 80 MB[/B]

So, if it can not be seen... how I un-install it?

Please, help.

Thanks in advance

BSG Fan
;)

The file was in my "Home Folder" with its 80 megabytes.
I went there and is not more there.
What happened?
I am confused.

I don't know if this thread is for this section of questions.

---

### Post by cariboo on 2010-07-15
Downloads by default go to ~/Downloads unless you changed the default download location.

Seeing as installing files has nothing to do with security, Moved to General Help

---

### Post by BSG Fan on 2010-07-15
Thanks u, cariboo907.

Okay, I did a search.  
I went here:
**[http://www.linuxquestions.org/questions/ubuntu-63/cant-uninstall-avg-8-5-on-ubuntu-remix-9-04-a-744522/](http://www.linuxquestions.org/questions/ubuntu-63/cant-uninstall-avg-8-5-on-ubuntu-remix-9-04-a-744522/)**
and went here also:
**[http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)**

to verify if the file is still in my pc, and this was what happened:


I DID THIS FIRST:

#####@#####-desktop:~$ sudo apt-get remove --purge avg85flx

[sudo] password for #####: 

Reading package lists... Done

Building dependency tree       

Reading state information... Done

The following packages will be REMOVED:

  avg85flx*

0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.

After this operation, 112MB disk space will be freed.

Do you want to continue [Y/n]? y

(Reading database ... 149455 files and directories currently installed.)

Removing avg85flx ...

 * Stopping avgd                                                         [ ok ]

Uninstalling 'avgd' service initscripts...

Unregistering 'avgd' service ...

 Removing any system startup links for /etc/init.d/avgd ...

   /etc/rc0.d/K20avgd

   /etc/rc1.d/K20avgd

   /etc/rc2.d/S20avgd

   /etc/rc3.d/S20avgd

   /etc/rc4.d/S20avgd

   /etc/rc5.d/S20avgd

   /etc/rc6.d/K20avgd

Purging configuration files for avg85flx ...

dpkg - warning: while removing avg85flx, directory `/opt' not empty so not removed.

Processing triggers for man-db ...

#####@#####-desktop:~$ 



=========



AND AGAIN I DID THIS:



#####@#####-desktop:~$ sudo apt-get remove --purge avg85flx

Reading package lists... Done

Building dependency tree        

Reading state information... Done

Package avg85flx is not installed, so not removed

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

#####@#####-desktop:~$ 





============



Also I did:



#####@#####-desktop:~$ [Desktop Entry]

bash: [Desktop: command not found

#####@#####-desktop:~$ Name=AVG Antivirus

bash: Antivirus: command not found

#####@#####-desktop:~$ Comment=Antivirus

#####@#####-desktop:~$ Exec=gksudo avggui &

[1] 4791

#####@#####-desktop:~$ Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png

#####@#####-desktop:~$ Terminal=false

#####@#####-desktop:~$ Type=Application

#####@#####-desktop:~$ Categories=Application;System;bash: avggui: command not found

#####@#####-desktop:~$ Categories=Application;System;





=========


What that means?  That I never downloaded those 80 megabytes in my pc?
I saw the file there.
I am confused.

---

### Post by oldsoundguy on 2010-07-15
All that work for something  you can't use or do not need in Linux.

---

### Post by BSG Fan on 2010-07-15
> **oldsoundguy said:**
> All that work for something  you can't use or do not need in Linux.

Exactly, u are totally right.  
According all that wasted time it means that that file does not exist more in my pc, right?
I am a moron for use that software.

---

### Post by tgm4883 on 2010-07-15
> **oldsoundguy said:**
> All that work for something  you can't use or do not need in Linux.

Now that is debatable. What if he shares files with Windows machines? Or has a Fileserver for Windows machines. Someone has to protect those boxes.

---

### Post by oldsoundguy on 2010-07-15
> **tgm4883 said:**
> Now that is debatable. What if he shares files with Windows machines? Or has a Fileserver for Windows machines. Someone has to protect those boxes.

In reality, why?  Unless they are YOUR boxes, not your responsibility to protect the world's Windows computers from malware when the users won't listen to advice and protect their own!

It's alright to be a nice person, but really, where does the responsibility of protection lie?

---

### Post by tgm4883 on 2010-07-15
> **oldsoundguy said:**
> In reality, why?  Unless they are YOUR boxes, not your responsibility to protect the world's Windows computers from malware when the users won't listen to advice and protect their own!

It's alright to be a nice person, but really, where does the responsibility of protection lie?

Well I was half joking with that, but yes. Social responsibility is one reason. The responsibility of protections is laid upon the people technologically savvy enough to know about it. I tell people to secure their open wifi access points to, is it my job? No, but it's the right thing to do.

With that being said, while there are very few, there **_are_** linux threats.

---

### Post by lisati on 2010-07-15
Apologies if this seems a bit like the dreaded and frowned-upon "RTFM", but have you tried "man avg"?

---

