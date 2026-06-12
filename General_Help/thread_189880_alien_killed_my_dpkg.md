---
title: "alien killed my dpkg"
date: 2006-06-05
forum: General Help
---

### Post by sharperguy on 2006-06-05
Ok, do theres no repository for Armagetron Advanced, only Armagetron.

So I got an RPM off of [http://armagetronad.net](http://armagetronad.net) and conveted it with alien, using --scripts.

Installed with dpkg and it failed, but armagetronad, ran!!!!!!!

However when I want to use apt i get:

```

sharp@ali2600:~/Desktop$ sudo apt-get install cheese
Password:
Reading package lists... Done
Building dependency tree... Done
E: The package armagetronad needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by detour on 2006-06-05
I had a similar problem using the cedega .deb once. Have you tried using Synaptic's 'Fix Broken Packages' option?
System -> Administration -> Synaptic Package Manager
Edit -> Fix Broken Packages

---

### Post by sharperguy on 2006-06-05
nope, that dosn't help .

I've tryed deinstalling the package with dpkg but it desparatly wants to reinstall, but it just fails the same way every time.

---

### Post by sharperguy on 2006-06-06
Is there anyone who knows how to help because this is pretty much killing my liking for dapper since I have to set it all up again after a clean install and I cant install any more software.

---

### Post by .t. on 2006-06-06
Run apt-get -f install in a terminal, and post the output.

---

### Post by sharperguy on 2006-06-06
nope that gives me the same message ](*,)

---

### Post by ifokkema on 2006-06-06
[QUOTE=sharperguy]nope that gives me the same message ](*,)[/QUOTE]

What happens if you run
sudo dpkg -r <filename.deb>

I think that will remove the package without apt's interference.

---

### Post by sharperguy on 2006-06-06
```

dpkg: error processing armagetronad (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 armagetronad

```

I did say it wanted to reinstall only.

---

### Post by ifokkema on 2006-06-06
[QUOTE=sharperguy]I did say it wanted to reinstall only.[/QUOTE]

Then you need to fix the error it throws at you when installing the package. You say it 'fails'. Could you post the output?

---

### Post by sharperguy on 2006-06-06
If I leave the scripts out i get:

```

Selecting previously deselected package armagetronad.
(Reading database ... 84905 files and directories currently installed.)
Preparing to replace armagetronad 0.2.8.1-2 (using armagetronad_0.2.8.1-2_i386.deb) ...
/var/lib/dpkg/info/armagetronad.prerm: line 2: /share/games/armagetronad/scripts/sysinstall: No such file or directory
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
dpkg: error processing armagetronad_0.2.8.1-2_i386.deb (--install):
 there is no script in the new version of the package - giving up
/var/lib/dpkg/info/armagetronad.postinst: line 2: /share/games/armagetronad/scripts/sysinstall: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 armagetronad_0.2.8.1-2_i386.deb

```

And if i use --scripts (with alien) i get:

```

(Reading database ... 84905 files and directories currently installed.)
Preparing to replace armagetronad 0.2.8.1-2 (using armagetronad_0.2.8.1-2_i386.deb) ...
/var/lib/dpkg/info/armagetronad.prerm: line 2: /share/games/armagetronad/scripts/sysinstall: No such file or directory
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: line 2: /share/games/armagetronad/scripts/sysinstall: No such file or directory
dpkg: error processing armagetronad_0.2.8.1-2_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/armagetronad.postinst: line 2: /share/games/armagetronad/scripts/sysinstall: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 armagetronad_0.2.8.1-2_i386.deb

```

---

### Post by ifokkema on 2006-06-06
[QUOTE=sharperguy]If I leave the scripts out i get:

```

(...)

```

And if i use --scripts (with alien) i get:

```

(Reading database ... 84905 files and directories currently installed.)
Preparing to replace armagetronad 0.2.8.1-2 (using armagetronad_0.2.8.1-2_i386.deb) ...
/var/lib/dpkg/info/armagetronad.prerm: line 2: /share/games/armagetronad/scripts/sysinstall: No such file or directory
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: line 2: /share/games/armagetronad/scripts/sysinstall: No such file or directory
dpkg: error processing armagetronad_0.2.8.1-2_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/armagetronad.postinst: line 2: /share/games/armagetronad/scripts/sysinstall: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 armagetronad_0.2.8.1-2_i386.deb

```[/QUOTE]

OK - sounds to me you've got a few options here.
- Try and mess with the pre-removal and post-install scripts. My guess is that it's supposed to refer to /usr/share/games/armagetronad/scripts/sysinstall. Does that file exist?
- Check what happens if you create the /share/games/armagetronad/scripts/ directory and put a softlink to the correct file in the /usr/share/games/armagetronad/scripts/ directory.
- If the script doesn't exist in the suggested location, try an empty file (with executable bit set) in /share/games/armagetronad/scripts/sysinstall and see what happens then.

I'm off now - will read any comments tomorrow.

Hope this helps!

Ivo

---

### Post by sharperguy on 2006-06-11
ok ive reinstalled ubuntu

it was some .package file that messed  everything up, luckly it wasnt that much of a hassle thanks to automatix

now ive got armagetronad working AND dpkg/apt

and pretty much everything i had before the reinstall, even backed up all my settings thanks to them all being in ".foobar" folders in home

---

### Post by braddcadd on 2007-07-15
OK, I have the same problem, also from playing with alien :).  But I'm afriad a fresh install is not possible for me right now.

Can anyone help?

```

E: The package installbuilder needs to be reinstalled, but I can't find an archive for it.

```

```

subprocess new pre-removal script returned error exit status 127
chown: `javier:javier': invalid user
chown: `javier:javier': invalid user
chown: `javier:javier': invalid user
chown: `javier:javier': invalid user
chown: `javier:javier': invalid user
.
.
.
There has been an error.
Error reading file /opt/installbuilder-4.5.0/projects/demo.xml
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1

```

I have created the javier user in effort to correct the broekn package but the demo.xml error still appears and leaves me in the same situation.  Any help would be appreciated.
Thanks

---

### Post by braddcadd on 2007-07-15
For those looking, here is a link that helps some people (mostly virtual box people).  See the commensts at the bottom.

[http://www.ubuntugeek.com/package-installation-error-and-solution.html](http://www.ubuntugeek.com/package-installation-error-and-solution.html)

---

### Post by braddcadd on 2007-07-15
Well, I think i fixed the problem with some combination of installing, forced removal (despite re-install required status), and editing the installbuilder.postinst file.

---

