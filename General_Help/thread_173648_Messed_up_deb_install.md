---
title: "Messed up deb install"
date: 2006-05-10
forum: General Help
---

### Post by Grimmy on 2006-05-10
Whilst attempting to install Denyhosts from .debs I managed to mess something up.

Now I keep getting

```

E: The package denyhosts-common needs to be reinstalled, but I can't find an archive for it.

```

Whenever I try and apt-get or if I use dpkg --remove denyhosts-common I get:

```

dpkg --remove denyhosts-common
dpkg: error processing denyhosts-common (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 denyhosts-common

```

If I try and reinstall from the deb I get

```

Selecting previously deselected package denyhosts-common.
(Reading database ... 99058 files and directories currently installed.)
Preparing to replace denyhosts-common 2.3-2 (using denyhosts-common_2.3-2_all.deb) ...
invoke-rc.d: initscript denyhosts, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 5
dpkg - trying script from the new package instead ...
invoke-rc.d: initscript denyhosts, action "stop" failed.
dpkg: error processing denyhosts-common_2.3-2_all.deb (--install):
 subprocess new pre-removal script returned error exit status 5
invoke-rc.d: initscript denyhosts, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 5
Errors were encountered while processing:
 denyhosts-common_2.3-2_all.deb

```

Any ideas on how I can clean this up?

---

### Post by Sef on 2006-05-10
try this from the terminal:

```
dpkg --configure -a
```

note: you might have to run it more than once.

---

### Post by Grimmy on 2006-05-10
[QUOTE=Sef]try this from the terminal:

```
dpkg --configure -a
```

note: you might have to run it more than once.[/QUOTE]

That gives me

```

# dpkg --configure -a
dpkg: error processing denyhosts-common (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 denyhosts-common

```

everytime I run it.

---

### Post by tonyr on 2006-05-10
Your downloaded package(s) may be corrupt.  Try removing them with **sudo rm**.
On my machine they are, in /var/cache/apt/archives, **denyhosts-common_2.3-2_all.deb** 
and d**enyhosts-python2.4_2.3-2_all.deb**.  Then try the **apt-get install**
again.

If there are still problems, try **apt-get remove --purge <package-name>**, and
then retry the install.

---

### Post by Grimmy on 2006-05-12
There wasn't a package in there.

It was originally installed with dpkg -i

I've tried removing every file i can find related to denyhosts using locate, and I still get the errors when I try any of the above.  (i've tried redownloading the .deb as well) - It must be referenced in some config file somewhere?

I can't run apt-get at all because it always gives

```

E: The package denyhosts-common needs to be reinstalled, but I can't find an archive for it.

```

There must be some way to fix this without flattening the install?

---

### Post by tonyr on 2006-05-12
This problem should be solveable with package management tools,  You
shouldn't have to attack it with hammer and chisel. The fact that there are no
**denyhosts** files in **/var/cache/apt/archives** causes the "I can't find 
an archive" error message.  What **apt-get** command are you running?

Have you tried this?
```

sudo apt-get install -d denyhosts-common

```
That should download the package without trying to install it. If that works, 
you should download the other **denyhosts** package, too.  Then 
```

cd /var/cache/apt/archives sudo dpkg -i <denyhosts-common-package-file>

```

You may need to do the same for the denyhosts-python package file.
If the apt-get install -d doesn't work, you should be able to get package files
directly from the repository web page. If you're using **bertorello**, that's
[URL="http://bertorello.ns0.it/debian/binary"]
http://bertorello.ns0.it/debian/binary[/URL]

---

### Post by Grimmy on 2006-05-13
[QUOTE=tonyr]This problem should be solveable with package management tools,  You
shouldn't have to attack it with hammer and chisel. The fact that there are no
**denyhosts** files in **/var/cache/apt/archives** causes the "I can't find 
an archive" error message.  What **apt-get** command are you running?

Have you tried this?
```

sudo apt-get install -d denyhosts-common

```
i <denyhosts-common-package-file>
[/CODE]
[/quote]

That gives the "The package denyhosts-common needs to be reinstalled, but I can't find an arhive for it." error.

As does any apt-get install, or apt-get upgrade commands.


> 
If the apt-get install -d doesn't work, you should be able to get package files
directly from the repository web page. If you're using **bertorello**, that's
[URL="http://bertorello.ns0.it/debian/binary"]
http://bertorello.ns0.it/debian/binary[/URL]

It was debs from that site that got me into this mess in the first place.
Trying to install it gives the error listed in my original post.  I've tryed re-downloading it, and even different versions of it and it still gives the same error.

I also tried with aptitude, but it just says that a problem occured and i'll need to fix it manually.

Edit:  It occured to me I should try the deb again after removing all the files... now it gives me this

```

$ sudo dpkg -i denyhosts-common_2.3-2_all.deb
(Reading database ...
dpkg: serious warning: files list file for package `denyhosts-python2.4' missing, assuming package has no files currently installed.
99058 files and directories currently installed.)
Preparing to replace denyhosts-common 2.3-2 (using denyhosts-common_2.3-2_all.deb) ...
invoke-rc.d: initscript denyhosts, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 5
dpkg - trying script from the new package instead ...
invoke-rc.d: initscript denyhosts, action "stop" failed.
dpkg: error processing denyhosts-common_2.3-2_all.deb (--install):
 subprocess new pre-removal script returned error exit status 5
invoke-rc.d: initscript denyhosts, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 5
Errors were encountered while processing:
 denyhosts-common_2.3-2_all.deb

```

Trying to install denyhosts-python2.4 gives

```

$ sudo dpkg -i denyhosts-python2.4_2.3-2_all.deb
(Reading database ...
dpkg: serious warning: files list file for package `denyhosts-python2.4' missing, assuming package has no files currently installed.
99058 files and directories currently installed.)
Preparing to replace denyhosts-python2.4 2.3-2 (using denyhosts-python2.4_2.3-2_all.deb) ...
Unpacking replacement denyhosts-python2.4 ...
dpkg: dependency problems prevent configuration of denyhosts-python2.4:
 denyhosts-python2.4 depends on denyhosts-common (= 2.3-2); however:
  Package denyhosts-common is not configured yet.
dpkg: error processing denyhosts-python2.4 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 denyhosts-python2.4

```

and as before:
```

$ sudo dpkg --configure -a
Setting up denyhosts-python2.4 (2.3-2) ...
dpkg: error processing denyhosts-common (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 denyhosts-common

```

and...

```

$ sudo apt-get install denyhosts-common
Reading package lists... Done
Building dependency tree... Done
E: The package denyhosts-common needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by tonyr on 2006-05-13
I'm running out of ideas here.

Have you tried 
```

sudo dpkg --purge denyhosts-common

```

I think I forgot that **apt-get** wasn't working for you when I suggested
**apt-get remove --purge**  previously.

---

### Post by Grimmy on 2006-05-14
[QUOTE=tonyr]I'm running out of ideas here.

Have you tried 
```

sudo dpkg --purge denyhosts-common

```[/QUOTE]

No I hadn't, but it gives a similar message to what i've had before:

```

$ sudo dpkg --purge denyhosts-common
dpkg: error processing denyhosts-common (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 denyhosts-common

```

edit:

After reading some stuff on google about different packages with a similar problem I tried this:

```

dpkg -P --force-all,remove-reinstreq denyhosts-common
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 99056 files and directories currently installed.)
Removing denyhosts-common ...
invoke-rc.d: initscript denyhosts, action "stop" failed.
dpkg: error processing denyhosts-common (--purge):
 subprocess pre-removal script returned error exit status 5
invoke-rc.d: initscript denyhosts, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 5
Errors were encountered while processing:
 denyhosts-common

```

Another package someone had problems with they had to edit the script inside the .deb.

---

### Post by Grimmy on 2006-05-14
Hurrah, i've finally fixed it.

It's a horribly hacky fix, but it worked:

A news group post I read for some other deb that failed recommended to extract the deb to a temporary directory and place the files manually, then try and remove it using --force-remove-reinstreq.

So I did 

```

dpkg-deb --extract denyhosts-common_2.3-2_all.deb tmp

```

And copied all the extracted files to their real places (it puts them inside the folders it should be in within the temp folder: e.g. ./tmp/etc/init.d/denyhosts goes in /etc/init.d).

This was still giving me an error I mentioned above when using force.

So... I edited denyhosts in /etc/init.d/ to always return 0  (success).

This allowed me to do 

```

dpkg -r --force-remove-reinstreq denyhosts-common

```

This removed it, and then I was able to do

```

dpkg --purge denyhosts-common

```

And that's it gone.  

I didn't realise it was in the repo's when I tried to install it from deb.  The question is, do I dare attempt to install it again? :)

Cheers.

---

### Post by tonyr on 2006-05-14
This is awesome!  This one is going in my blackmagic file of how to
do things.  I guess hammer and chisel was the right way to go after all.

---

