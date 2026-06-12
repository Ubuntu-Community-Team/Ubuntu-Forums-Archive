---
title: "&quot;Failed to fetch&quot; files for Bibus? Why?"
date: 2009-09-28
forum: General Help
---

### Post by oldtime on 2009-09-28
[FONT=Arial]Hey Linux team:
I'm trying to install Bibus on my 8.04. I've tried to follow the directions for installing Bibus ([http://bibus-biblio.sourceforge.net/wiki/index.php/Installation](http://bibus-biblio.sourceforge.net/wiki/index.php/Installation)), but keep getting the same error. After updating my /etc/apt/sources.list, I run sudo apt-get update - my machine looks in all the usual places for Hardy updates, but when it gets to the Sourceforge (Bibus) files, it "fails to fetch" them. Here's the terminal output:

...yada yada...
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Err [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Packages
  302 Found
Err [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Sources
  302 Found
W: Failed to fetch [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/./Packages.gz](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/./Packages.gz)  302 Found

W: Failed to fetch [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/./Sources.gz](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/./Sources.gz)  302 Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

Someone else posted a similar problem ([http://ubuntuforums.org/showthread.php?t=1143493](http://ubuntuforums.org/showthread.php?t=1143493)) - looks like the key wasn't up to date. I've updated the key from the Sourceforge site (based on what this last-cited post suggested, and following the instructions therein), and that still didn't fix my problem!

Any help? I actually posted this problem to "Installation and Upgrades" recently and didn't get the help I needed to fix my problem. This post can be read at ([http://ubuntuforums.org/showthread.php?t=1272072](http://ubuntuforums.org/showthread.php?t=1272072)) - if you need more info. I'm really sorry for cross-posting to categories - I know I'm not supposed to do that!

Also, I tried using the command "sudo aptitude install bibus" (per the directions posted at bibus-biblio address posted at the top of this thread), and got the following:
me@mycomputer:~$ sudo aptitude install bibus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "bibus"
Couldn't find any package whose name or description matched "bibus"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done     

This seems like a similar error - as if my machine is just not finding "bibus" anywhere. I feel like, by adding the deb [http://.](http://.).. lines to my /etc/apt/sources.list, it should take care of that. Argh!

At this point, I'm ready to install WINE (and deal with those issues) and then install my Endnote X - I need a reference manager for my job and I'm frustrated and, I guess, mostly just confused as to why my machine won't fetch the bibus files. I've pasted (and typed) the deb [http://switch](http://switch)... addresses several times, so I really don't think it's human error on that end.

Thanks, in advance - from a 3-month newbie. I've found this forum really helpful over the past couple months, and have learned a ton about my computer through the process. I like that.



[/FONT]

---

### Post by zvacet on 2009-09-28
You can try add [this]("https://launchpad.net/~scubuntu-dev/+archive/ppa") line in your source list.Put # sign in front of sourceforge line.Refresh your source list with 

```
sudo apt-get update
```

---

### Post by oldtime on 2009-09-28
Thanks for writing.
I added the PPA and authenticated it per the directions at [https://launchpad.net/~scubuntu-dev/+archive/ppa](https://launchpad.net/~scubuntu-dev/+archive/ppa) - here's what my /etc/apt/sources.list looks like now:

...yada yada...
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/tobydox/lmms/ubuntu](http://ppa.launchpad.net/tobydox/lmms/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/tobydox/lmms/ubuntu](http://ppa.launchpad.net/tobydox/lmms/ubuntu) hardy main

## Bibus
deb [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./
deb-src [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./

##PPA for Scubuntu and 'untrusted' sites
deb [http://ppa.launchpad.net/scubuntu-dev/ppa/ubuntu](http://ppa.launchpad.net/scubuntu-dev/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/scubuntu-dev/ppa/ubuntu](http://ppa.launchpad.net/scubuntu-dev/ppa/ubuntu) hardy main

Once the ppa.launchpad stuff was loaded, I got this (segment) of output in my terminal: I think it indicates, to me, that it has contacted and downloaded ppa.launchpad stuff just fine:
...
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages [497B]
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources [379B] 
...
So now ppa.launchpad is alright. When I go to get bibus files (by running sudo apt-get update), I get the same output:
...
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources    
Err [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Packages                     
  302 Found
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Err [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Sources
  302 Found
Fetched 1B in 1s (1B/s)  
W: Failed to fetch [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/./Packages.gz](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/./Packages.gz)  302 Found

W: Failed to fetch [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/./Sources.gz](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/./Sources.gz)  302 Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
...
And when I try "sudo aptitude install bibus", it says, "Couldn't find any package whose name or description matched "bibus"" in my terminal window.

It's like my computer has a block against finding bibus files.
Any other ideas? Thanks.

---

### Post by zvacet on 2009-09-28
Let lines 

deb [http://switch.dl.sourceforge.net/sou...e/bibus-biblio](http://switch.dl.sourceforge.net/sou...e/bibus-biblio) ./
deb-src [http://switch.dl.sourceforge.net/sou...e/bibus-biblio](http://switch.dl.sourceforge.net/sou...e/bibus-biblio) ./

look like this

#deb [http://switch.dl.sourceforge.net/sou...e/bibus-biblio](http://switch.dl.sourceforge.net/sou...e/bibus-biblio) ./
#deb-src [http://switch.dl.sourceforge.net/sou...e/bibus-biblio](http://switch.dl.sourceforge.net/sou...e/bibus-biblio) ./

Refresh sources list and then try again to install desired package.

---

### Post by oldtime on 2009-09-28
That's what I thought you meant originally.
I inserted a "#" in front of the sourceforge lines in my /etc/apt/sources.list. I ran sudo apt-get update and everything went fine, but of course it skipped the bibus stuff. 

What does it mean to "refresh sources list and then try again to install the desired package"? I tried your suggestion, then "sudo apt-get update bibus", but I keep getting the error "Failed to fetch bibus". 

I think that's what I tried to do. In the Software Sources > Third Party Software GUI, I tried to add the sourceforge sites and it gave me the same error as in my terminal: "The repsoitory may no longer be available or could not be contacted because of network problems. Failed to fetch http://swithc.dl.sourceforge..." yada yada

I don't understand what the "#" insertion would do for me, except tell the computer to skip those sources when looking for updates. My computer just isn't finding the files. 

So I've tried an alternate route to this. I downloaded the bibus_1.1.3-3_all.deb package from the sourceforge website ([http://sourceforge.net/projects/bibus-biblio/](http://sourceforge.net/projects/bibus-biblio/)). I've also installed all the other dependencies I thought I needed (sudo apt-get install bibus libsqliteodbc python-pysqlite2 python-wxgtk2.6 python-uno ). When I go to install the bibus_1.1.3-3_all.deb package, I get an error from my Package Installer that says "Error: Dependency is not satisfiable: python-central".

Looking at my Synaptic Package Manager, my "python-central" package is checked (with a green box), version 0.6.7ubuntu0.1 (looks like the latest package). Why, then would there be a python-central dependency problem? That's really perplexing. Is there some other python package I should install? Argh!

Thanks for all your help. Sorry this is so weird.

---

### Post by zvacet on 2009-09-28
I told you to comment sourceforge repository,because you added ppa repository witch have same package.You don´t need two sources for one package and they can be on the way to each other.Only source you need is ppa repo and that is why I told you to commment sourceforge repo.

---

### Post by oldtime on 2009-09-28
Thanks!
I see what you mean - I found the bibus package at the launchpad site ([https://launchpad.net/~scubuntu-dev/+archive/ppa/+packages](https://launchpad.net/~scubuntu-dev/+archive/ppa/+packages)). I tried installing it and got the following error in my package installer: "error: Dependency is not satisfiable: python-central"
After refreshing my sources list and trying to install bibus, I get:

me@mycomputer:~$ sudo apt-get install bibus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bibus is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package bibus has no installation candidate

I installed all the other packages I thought I was supposed to (according to [http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu](http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu)) with: 
sudo apt-get install libsqliteodbc python-pysqlite2 python-wxgtk2.6 python-uno 
...but then still got the "bibus has no installation candidate" error.

I went through my synaptic package manager and my python looks pretty up-to-date - my python-central is 0.6.7ubuntu0.1

Any ideas about what to do next?

---

### Post by zvacet on 2009-09-29
If you added 

deb [http://ppa.launchpad.net/scubuntu-dev/ppa/ubuntu](http://ppa.launchpad.net/scubuntu-dev/ppa/ubuntu) jaunty main

to your source list and you still can not install desired package,maybe it is time for somebody with more knowledge then I have.Don't give up!Somebody will give you right answer.

---

### Post by mc4man on 2009-09-29
> o I've tried an alternate route to this. I downloaded the bibus_1.1.3-3_all.deb package from the sourceforge website ([http://sourceforge.net/projects/bibus-biblio/](http://sourceforge.net/projects/bibus-biblio/))

Possibly a typo on your part..? there is no 1.1.3-3, although there is a 1.4.3 which is not for hardy ( uses python2.6

You can install 1.4.2 on hardy, all deps can be satisfied

( no need to preinstall them, whatever is missing, if anything, will be installed by gdebi

[http://sourceforge.net/projects/bibus-biblio/files/](http://sourceforge.net/projects/bibus-biblio/files/)

pick the 1.4.2-1_all.deb

from the control file for 1.4.2-1

> Package: bibus
Version: 1.4.2-1
Architecture: all
Maintainer: Pierre Martineau <pmartino@users.sourceforge.net>
Installed-Size: 8448
Depends: python (>= 2.3), python-central ([COLOR="Blue"]>= 0.5.8 )[/COLOR], python-sqlite | python-pysqlite1.1 | python-pysqlite2, python-wxgtk2.6
Recommends: bibus-doc-en, openoffice-pyuno | python-uno, openoffice.org | openoffice.org2, python-mysqldb
Suggests: libmyodbc | libsqliteodbc, odbcinst1 | odbcinst1debian1, unixodbc
Section: x11
Priority: optional


from the 1.4.3-3

> package: bibus
Version: 1.4.3-3
Architecture: all
Maintainer: Pierre Martineau <pmartino@users.sourceforge.net>
Installed-Size: 4320
Depends: python (>= 2.3), python-central (>= 0[COLOR="Red"].6.11[/COLOR]), python-wxgtk2.6 | python-wxgtk2.8, python-sqlite | python-pysqlite1.1 | python-pysqlite2
Recommends: openoffice.org | openoffice.org2, openoffice-pyuno | python-uno, bibus-doc-en, python-mysqldb

---

### Post by oldtime on 2009-09-30
AWESOME!!!
I downloaded the 1.4.2-1_all.deb and installed it with my package manager (not in the terminal - oh yeah, and the "1.1.3-3" was something I accidentally made up - typo! Sorry!). 

mc4man - HOW COULD I HAVE KNOWN 1.4.3-1 WASN'T COMPATIBLE WITH HARDY? Or better yet, how did YOU know? Is there a way I could have found this out and saved myself a headache...I mean, learning experience? 

Anyway, after install I followed the directions and (thought I had) set it up right, but then it wouldn't insert citations, giving me the following error:

Cannot connect to Openoffice. See Documentation.
Connector : couldn't connect to pipe OOo_pipe(10))                      

I was sleuthing around ([http://ubuntuforums.org/showthread.php?t=583073](http://ubuntuforums.org/showthread.php?t=583073)) and looked at Martineau's comments about configuring OOo with a pipe to import citations. I was following the steps, but then realized my MACROS WERE DISABLED in OOo, and that was preventing the changes I was making (clicking on boxes to tell OOo and Bibus to use the pipe 'OOo_pipe' to communicate) from being saved. I found out how to enable macros (by permission, instead of just denying them all), and it worked!

This is empowering. Thanks for the help, anonymous forum people. You all rock, and it motivates me to help others out once my feet are sufficiently wet. Solved.

---

### Post by mc4man on 2009-09-30
Ther'es several ways to ck. dependencies, for .debs not in the ubuntu repo's I just downnload the .deb to desktop or a folder, whatever.

Then right click on the .deb -> "open with Archive Manager"

When it opens then d. left click on the "control.tar.gz", that will open another window, d. left click on the folder and finally d. left click on the control file (or ocassionally a conffiles

Then just read the depends and if needed check in synaptic

(this way I never install or try to install the .deb or even actually extract it, just a click thru

To cross reference versions and ubuntu release I go here and do a search (just bookmarked one page sorta at random

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=lame](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=lame)

---

### Post by aspergerian on 2009-10-31
The version of 1.4.2 for Ubuntu seems no longer available at [http://sourceforge.net/projects/bibus-biblio/files/](http://sourceforge.net/projects/bibus-biblio/files/)

---

