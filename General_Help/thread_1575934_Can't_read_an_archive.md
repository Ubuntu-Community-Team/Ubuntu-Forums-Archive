---
title: "Can't read an archive"
date: 2010-09-16
forum: General Help
---

### Post by bel3atar on 2010-09-16
Hi, I retrieved this [http://www.emsimarrakech.ma/mise_a_niveau.rar](http://www.emsimarrakech.ma/mise_a_niveau.rar) from my schools' website, but I just couldn't open it in Ubuntu:
When I extract it, there's n output files
When I open it with the archiver, I see the files, but they're unreadable using evince
When I'm on windows, it just works...

If someone could help I would be happy....

---

### Post by oldos2er on 2010-09-16
Ubuntu doesn't come with rar support enabled, you need to install it. ```
sudo apt-get update && sudo apt-get install rar unrar
```

---

### Post by bel3atar on 2010-09-16
I've unrar-free installed, it should do it huh?

---

### Post by F104G on 2010-09-23
Hello people.  Sorry, not a solution but a similar problem.  I was searching for an answer when I saw this thread.  Followed the suggestions but with no luck.  
I have been using Ubuntu for a few months now, but have never been able to get anything to extract.  Looking in the Installed Programmes list it tells me I have the following installed:  
7zip    
Archive Manager    
Unarchiver for.rar files

If I double-click on a .rar file it opens and shows me the files within.  I can click on them all and choose Extract, it asks me where to? and I choose Desktop.  It then does it's thing and says all files were extracted... but they're not there.  If I extract the entire folder it puts a folder with that name on the desktop but it's empty.  Am I doing something wrong?
I can drop it onto a USB stick and extract it with the Mac, but I'd like to be able to get Ubuntu to do it for me :)
After reading this post I tried the suggestions here but got the following:

[I]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B81A3FBA47394CE
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  akonadi-server: Depends: libqt4-dbus (>= 4:4.6.0~rc1-1ubuntu1) but it is not going to be installed
                  Depends: libqt4-sql-mysql but it is not going to be installed
  kdelibs-bin: Depends: libqt4-dbus (>= 4:4.6.2) but it is not going to be installed
               Depends: libqt4-xml (>= 4:4.6.2) but it is not going to be installed
  kdelibs5: Depends: libphonon4 (>= 4:4.6.2) but it is not going to be installed
            Depends: libqt4-dbus (>= 4:4.6.2) but it is not going to be installed[/I]

       [it goes on and on for a while]

  [I]soprano-daemon: Depends: libqt4-dbus (>= 4:4.6.1) but it is not going to be installed
                  Depends: libqt4-network (>= 4:4.6.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
[/I]
So, I tried apt-get -f install and this is what I got:

[I]
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
daedalus@daedalus-laptop:~$
[/I]
Any suggestions?

---

### Post by bel3atar on 2010-09-24
to run something as root use sudo

---

### Post by F104G on 2010-09-26
> **bel3atar said:**
> to run something as root use sudo

Aha!  Thank you :)

I'm new to all this (as you probably guessed).  With the addition of those 4 letters everything went swimmingly.  I am now happily listening to Agitation Free.

:cool::cool::cool::cool::cool::cool::cool:

---

