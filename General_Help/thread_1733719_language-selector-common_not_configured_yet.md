---
title: "language-selector-common not configured yet"
date: 2011-04-19
forum: General Help
---

### Post by gepolv on 2011-04-19
When I try to install packages, I always got an error:

"
Errors were encountered while processing:
 language-selector-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
"

However, even with this error, the packages are still successfully installed.

Any suggestions?

Thanks.

---

### Post by stoneage on 2011-04-19
Just tried to install updates, and all was fine until the end, when it reported not being able to configure language-selector-common

I tried 

> sudo apt-get clean
sudo apt-get install -f
and
> sudo dpkg --configure -a
Setting up language-selector-common (0.6.7) ...
dpkg: error processing language-selector-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on language-selector-common (= 0.6.7); however:
  Package language-selector-common is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on language-selector-common; however:
  Package language-selector-common is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Processing triggers for python-central ...
Errors were encountered while processing:
 language-selector-common
 language-selector
ubuntu-standard


Found a suggestion here:- [http://z0manifest.blogspot.com/2010/01/ubuntu-fix-subprocess-pre-removal.html](http://z0manifest.blogspot.com/2010/01/ubuntu-fix-subprocess-pre-removal.html) that I could remove, then reinstall without errors. This made it worse, as now ubuntu-standard is a problem too.

Some more sensible suggestions would be very much appreciated :)

Ubuntu 10.10 64 bit

---

### Post by aljazek on 2011-04-19
I also got this error with code:
```
Setting up language-selector-common (0.6.7) ...
dpkg: error processing language-selector-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on language-selector-common (= 0.6.7); however:
  Package language-selector-common is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for python-central ...
Errors were encountered while processing:
 language-selector-common
 language-selector
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by stoneage on 2011-04-19
+1

[http://ubuntuforums.org/showthread.php?t=1733722](http://ubuntuforums.org/showthread.php?t=1733722)

---

### Post by vajorie on 2011-04-19
Don't worry about ubuntu-desktop and ubuntu-standard; those are something like virtual packages: when you install ubuntu-desktop, you get everything that is installed in a clean ubuntu desktop box, but the package ubuntu-desktop itself is empty. 

Once they identify the problem with language-selector (bug report is here, subscribe to it to be kept up-to-date: [https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/766412](https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/766412) ), they'll upload a new version of it and you'll be able to install the virtual packages too. 

PS. I'm having the same issue.

Edit: I downgraded language-selector and language-selector-common to a previous version and installed ubuntu-desktop so that (1) apt-get behaves when I want to install something else, and (2) I don't forget about that virtual package. Language-selector(-common) are here: [http://mirrors.us.kernel.org/ubuntu//pool/main/l/language-selector/](http://mirrors.us.kernel.org/ubuntu//pool/main/l/language-selector/) I used the "_0.5.8_all" versions. Hope this helps a bit :)

---

### Post by vajorie on 2011-04-19
+1, bug report: [https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/766412](https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/766412)

---

### Post by aljazek on 2011-04-19
Someone proposed a patch...how can I use it?

---

### Post by flipper T on 2011-04-19
i had same issue, and whilst i cannot _solve_, the problem can be _resolved_ by unselecting "proposed updates" from your software sources,

i'd guess these are errors to be expected when installing what are essentially beta-upgrades.

i'm going to leave it for a while then reselect "proposed" in a couple of days time. hopefully problem will have been sorted by then.

---

### Post by stoneage on 2011-04-19
Nice, thanks very much.

Subscribed :)

---

### Post by superdaveozzborn on 2011-04-19
same issue here, just updated 6 machines and all have same issue. what a mess.
:popcorn:

---

### Post by mattgen88 on 2011-04-19
Update affected my machine as well. Any known fixes?

---

### Post by bapoumba on 2011-04-19
Hmm :)
Should have read the forums more carefully before running my updates.
Ther eis a patch in the bug report and a workaround. I'd wait for a package fix.

---

### Post by LieToPurify3 on 2011-04-19
Having the same problem. I didn't have proposed updates selected, so that fix won't work for me. Also, I did not use the wubi installer. I installed from cd months ago and haven't had any problems. Looks like and update probably broke something for me. 

Posting the error in case it will help:

```
Do you want to continue [Y/n]? Y
Setting up language-selector-common (0.6.7) ...
dpkg: error processing language-selector-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on language-selector-common (= 0.6.7); however:
  Package language-selector-common is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Processing triggers for python-central ...
Errors were encountered while processing:
 language-selector-common
 language-selector
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by fleggle on 2011-04-19
not sure if its worked 100% but its let me install packages again. I went to synaptic package manager and removed the language-selector package (and its related files). I then rebooted the system and hey presto. Hope this helps!

---

### Post by lores on 2011-04-19
[SIZE="4"][COLOR="Red"]**A relatively clean fix:**[/COLOR][/SIZE]



Just tested the following fix from [https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/766412](https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/766412) :

> you can edit the file /var/lib/dpkg/info/language-selector-common.postinst go to the line with this content :
kill $(pgrep -U root '^ls-dbus-backend$') 2>/dev/null
at the end add || true to get this line
kill $(pgrep -U root '^ls-dbus-backend$') 2>/dev/null || true

run apt-get upgrade again

It works.

---

### Post by daoman on 2011-04-19
Thanks Lores!

It works!

---

### Post by stoneage on 2011-04-19
Thanks lores, that fixed mine......

---

### Post by beew on 2011-04-19
But I also have a problem ugrading teh kernel.

---

### Post by nullr1 on 2011-04-19
[B][SIZE=4]IF ANYONE STILL LOOKING HERE IS AN EASY FIX.
[/SIZE][/B] 
Got this problem today completely broke apt-get for any program install. This has to do with an update simple fix using synaptic. Just follow these steps. The fix seems long but its less than 3 minutes of simple search and click. 

Open synaptic
Search "language-selector" 
Right click and select mark for removal on both language-selector and language-selector common
Hit apply and wait for it to finish (keep synaptic open)
If the search clears search for "language-selector" again
Select language-selector-common (left click) and press ctrl+e (or click package and force version) 
Be sure to pick version 0.6.6
Hit apply and wait for it to finish installing 0.6.6 
Left click on language-selector-common (search again if it clears out)
Click package and check the "Lock Version" box.
Now click language-selector and ctrl+e (or click package and force version)
Pick version 0.6.6 for this also.
Hit apply and wait for it to install.
Then mark the language-selector package for "Lock Version" to prevent updating.
Fixed.

Worked for me tried forcing version for both and installing both at once but it would not stick so I tried one package at a time locking the version in between and it worked.

---

### Post by lisbonacid on 2011-04-19
0.6.8 just dropped, fixing this issue.

---

### Post by aljazek on 2011-04-19
Bug fixed!

---

### Post by nullr1 on 2011-04-19
Good to hear that was fast.

---

### Post by Theredbaron1834 on 2011-04-19
I just uninstalled it. Correct me if I am wrong, but inless you need to change languages, which isn't likely for most, I don't think it is needed.

---

### Post by mattgen88 on 2011-04-19
update upgrade fixed it. Awesome.

---

### Post by baconmaker on 2011-04-19
What is the purpose of language-selector-common and language-selector ? 
Are they necessary?

I had the same issue with update today.  And the more I fixed the worse I got.  Finally I just did a complete removal of the various packages for which I was getting error messages. Then one-by-one I reinstalled the packages which I removed. Everything went fine until I tried to reinstall language-selector-common and language-selector and replicated my problems. 

At this point in time I have language-selector-common and language-selector removed and everything seems to be working fine.  But, I am a newbie and know enough to be dangerous.

---

### Post by superdaveozzborn on 2011-04-19
G that was fun, 7 machines. thanks lores!
your the best.

---

### Post by baconmaker on 2011-04-19
How do you get v.0.6.6?  The only thing my package manager shows is v.0.6.8. What you described is simple to do if I could find v.0.6.6.

Thanks

---

### Post by lores on 2011-04-19
> **superdaveozzbonr said:**
> G that was fun, 7 machines. thanks lores!
your the best.

The credit goes to [https://launchpad.net/~gastonsa](https://launchpad.net/~gastonsa) .

---

### Post by vajorie on 2011-04-19
Fixed in launchpad -> sudo apt-get update && sudo apt-get upgrade fixes it now. And I have to say: they *are* fast. I was expecting to wait for a few days or more for a fix to be released :)

---

### Post by vajorie on 2011-04-19
> **baconmaker said:**
> How do you get v.0.6.6?  The only thing my package manager shows is v.0.6.8. What you described is simple to do if I could find v.0.6.6.

Thanks

no need, just update it again and it will be fixed now.


> **superdaveozzbonr said:**
> G that was fun, 7 machines. thanks lores!
your the best.

Yay, I would definitely use a test machine for a setup like that

---

### Post by baconmaker on 2011-04-20
Thanks,
Just installed the fixes.  Smooth as silk.
Thank you and keep up the good work.

---

### Post by bapoumba on 2011-04-20
Fixed here too.

---

### Post by spyd4r on 2011-04-20
I am still only being offered

language-selector-common (0.6.7)

still bugged here

edit: mirror.anl.gov is just outdated, picked a new mirror and i'm golden.

---

### Post by bapoumba on 2011-04-20
Threads merged.

---

