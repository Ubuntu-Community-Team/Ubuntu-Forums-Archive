---
title: "Googe Chrome"
date: 2010-06-06
forum: General Help
---

### Post by papaphil4 on 2010-06-06
how to uninstall it?

---

### Post by wojox on 2010-06-06
How did you install it first of all?

---

### Post by papaphil4 on 2010-06-06
> **wojox said:**
> How did you install it first of all?

just downloaded it and it installed

---

### Post by papaphil4 on 2010-06-06
> **papaphil4 said:**
> how to uninstall it?

does anybody have the answer for this so I can get rid of it

---

### Post by mkvnmtr on 2010-06-06
You might try finding it in the Synaptic package manager and uninstalling it from there.

---

### Post by bodhi.zazen on 2010-06-06
> **papaphil4 said:**
> just downloaded it and it installed

That did not answer the question. Was it a .deb ? .tar.gz ? what steps did you take to install it ?

Otherwise we really can not help you.

---

### Post by Timmer1240 on 2010-06-06
go to system administration synaptic package manager open that in the left hand column pick installed then on the right scroll down to google crome right click it and mark for complete removal then apply in the top of synaptic package manager!

---

### Post by sXeChris on 2010-06-06
Or, open Synaptic type "chromium" in the search box, it should pop up with the small input box to the left of it filled with green (meaning it's installed) click that same box, select complete removal, and click apply changes on the toolbar above.

---

### Post by mannamae on 2010-07-02
I am unable to uninstall Google Chrome. I searched Synaptic for google, Chromium and chrome and cant find it. I put all of the codes into the terminal that were mentionied in another thread. I have Ubuntu 8.04, i believe I downloaded a .deb file to install it
here is the terminal feed:
~$ sudo apt-get remove google-chrome-unstable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package google-chrome-unstable
~$ sudo dpkg -r chromium-browser
dpkg - warning: ignoring request to remove chromium-browser which isn't installed.
~$ sudo apt-get remove google-chrome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package google-chrome
~$ ls -l /usr/bin | grep chrom
lrwxrwxrwx 1 root root         32 2010-06-25 15:58 google-chrome -> /opt/google/chrome/google-chrome
~$ sudo apt-get remove google-chrome-beta
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package google-chrome-beta
~$ sudo apt-get remove google-chrome-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package google-chrome-stable

---

### Post by bodhi.zazen on 2010-07-03
If it is a deb it should be listed ...

```
dpkg -l > installed.txt
```

Now grep that file for chrome / google / etc

```
grep google installed.txt
```

Better, what was the name of the .deb you installed ?

---

### Post by mannamae on 2010-07-03
32 bit .deb (For Debian/Ubuntu) is the one i pulled from the google chrome linux download site

---

### Post by bodhi.zazen on 2010-07-03
> **mannamae said:**
> 32 bit .deb (For Debian/Ubuntu) is the one i pulled from the google chrome linux download site

Does this .deb have a full name ?

dpkg -r name

drop the ".deb" and any version numbers.

---

### Post by mannamae on 2010-07-03
Here is what I get when I out in the terminal codes you gave me


ii  google-chrome-stable                        5.0.375.86-r49890                                             The web browser from Google
ii  libgdata-google1.2-1                        2.22.3-0ubuntu3netbook1                                       Client library for accessing google POA thro
ii  libgdata1.2-1                               2.22.3-0ubuntu3netbook1                                       Client library for accessing google POA thro

---

### Post by bodhi.zazen on 2010-07-03
What happens when you use apt-get ?

```
sudo apt-get purge google-chrome-stable libgdata-google libgdata
```

?

---

### Post by steveneddy on 2010-07-03
To the OP:

You realize that chrome is available in the repos - right?

To install from a web site when it is available in a secure package from the maintainers is silly.

Not preaching, but next time if you look for it in the Ubuntu channels you will have better luck uninstalling the software if you decide that you don't like it.

*******************

Another way to uninstall is to - in terminal - 

```
locate <name-of-program>
```

without the < >'s  - for instance:

```
locate google-chrome
```

or 

```
locate chromium-browser
```

and deleting every directory with that name - this way you will manually uninstall it.

Then simply remove it from your menu and you are done.

---

### Post by t.rei on 2010-07-03
```
sudo apt-get purge google-chrome-stable
```

thats the package used on my install (from the official google download)

---

### Post by mannamae on 2010-07-03
Re3sponse from apt get

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package google-chrome-stable


and I found the name of the  package that was installed... google-chrome-stable_current_i386.deb

---

### Post by bodhi.zazen on 2010-07-03
If ```
sudo apt-get purge google-chrome-stable_current
``` does not work , time for you to file a bug with google.

---

### Post by steveneddy on 2010-07-04
> **mannamae said:**
> Re3sponse from apt get

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package google-chrome-stable


and I found the name of the  package that was installed... google-chrome-stable_current_i386.deb

OK - then in terminal:

```
sudo dpkg -r package_name
```

or in your case:

```
sudo dpkg -r google-chrome-stable_current_i386.deb
```

That should do it.

---

### Post by mannamae on 2010-07-04
guess I'll be filing a bug....
:~$ sudo dpkg -r google-chrome-stable_current_i386.deb
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

~$ sudo dpkg -r google-chrome-stable_current

dpkg - warning: ignoring request to remove google-chrome-stable_current which isn't installed.

---

### Post by RMuscaritolo on 2010-07-04
Try running "sudo dpkg-query -l | grep chrome" to get the correct name, than run the dpkg uninstall or purge...

---

### Post by mannamae on 2010-07-05
it says it requires "superuser privileges" to remove that package. ii google-chrome-stable.

---

### Post by bodhi.zazen on 2010-07-05
> **mannamae said:**
> it says it requires "superuser privileges" to remove that package. ii google-chrome-stable.

use sudo ...

---

### Post by steveneddy on 2010-07-05
```
sudo dpkg -r google-chrome-stable
```

Maybe this will work?

---

### Post by mannamae on 2010-07-05
YAY it's finally gone. I swear I ran the sudo before and got the not there response. But it worked this time... Yippee

---

### Post by mannamae on 2010-07-05
feeling more and more like a noob with each passing minute. Now when I try to run the update manager I get this
Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry  main/binary-lpia/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

and it says it hasnt updated for 11 days

---

### Post by RMuscaritolo on 2010-07-05
> **mannamae said:**
> feeling more and more like a noob with each passing minute. Now when I try to run the update manager I get this
Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry  main/binary-lpia/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

and it says it hasnt updated for 11 days

Ok, this one is a little more advanced, but should be easy to remove... 

When you installed Google Chrome it automatically added a new software repository that your computer checks against to confirm whether it is up to date or not. The repositories are pretty the databases that lets your computer know what is new or should be updated.

To fix your error, go to the "System --> Administration --> Software Sources" menu. (use your Sudo password if prompted!) From there, go to the second tab called "Other Software". Near the bottom of the list you should see the "http://dl.google.com/linux/deb/dists/stable/Release" entry. Go ahead and delete/remove it and you should be all set.

---

### Post by mkvnmtr on 2010-07-05
Go to your software sources and uncheck the box for the repository for Google Chrome.

---

### Post by mannamae on 2010-07-05
thanks, that worked. My issues are now solved.... for the moment anyways

---

### Post by steveneddy on 2010-07-06
Let's mark the thread as solved then.

---

