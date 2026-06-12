---
title: "how do i force install a package"
date: 2009-08-19
forum: General Help
---

### Post by shiggydiggy on 2009-08-19
Hey, i did a re-install, I'm trying to install some packages from my old installation (big hdd, didn't delete it) some depend on each other....
like audacious-plugins_1.5.1-2ubuntu3_i386.deb and audacious_1.5.1-4ubuntu3_i386.deb
I can't install either because they need each other.
How do I force install one of them first?

BTW, the reason I'm doing such madness is because my internet BW is very limited :(

---

### Post by Post Monkeh on 2009-08-19
2.2 How to use APT locally

Sometimes you have lots of packages .deb that you would like to use APT to install so that the dependencies would be automatically solved.

To do that create a directory and put the .debs you want to index in it . For example:

     # mkdir /root/debs

You may modify the definitions set on the package's control file directly for your repository using an override file. Inside this file you may want to define some options to override the ones that come with the package. It looks like follows:

     package priority section

package is the name of the package, priority is low, medium or high and section is the section to which it belongs. The file name does not matter, you'll have to pass it as an argument for dpkg-scanpackages later. If you do not want to write an override file, just use /dev/null. when calling dpkg-scanpackages.

Still in the /root directory do:

     # dpkg-scanpackages debs file | gzip > debs/Packages.gz

In the above line, file is the override file, the command generates a file Packages.gz that contains various information about the packages, which are used by APT. To use the packages, finally, add:

     deb file:/root debs/

After that just use the APT commands as usual. You may also generate a sources repository. To do that use the same procedure, but remember that you need to have the files .orig.tar.gz, .dsc and .diff.gz in the directory and you have to use Sources.gz instead of Packages.gz. The program used is also different. It is dpkg-scansources. The command line will look like this:

     # dpkg-scansources debs | gzip > debs/Sources.gz

Notice that dpkg-scansources doesn't need an override file. The sources.list's line is:

     deb-src file:/root debs/




from

[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html)

for debian, but i'd imagine it should work

---

### Post by abrari on 2009-08-19
never force install a package that missing dependencies.
apt will report a "broken package"

---

### Post by bodhi.zazen on 2009-08-19
Why not simply :

```
sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get install audacious
```

Probably not a great idea to force those older deb to install.

---

