---
title: "I can't install Open Office"
date: 2010-10-16
forum: General Help
---

### Post by Tarid on 2010-10-16
I am using 
**Ubuntu Netbook Edition**

I downloaded this **OOo_3.2.1_Linux_x86_install-deb_en-US** and I tried installing Open office using the directions posted here

[http://ubuntuforums.org/showthread.php?t=1404156](http://ubuntuforums.org/showthread.php?t=1404156)



I received the following error after running this in the terminal

```
sudo dpkg -i ~/Desktop/OOO320_m18_native_packed-1_en-US.9502/DEBS/*.deb

```[B]
Could not find a Java Runtime Environment! [/B]

It appears to be installed but when I click on an open office icon like base it does not open

Also, I have been using ubuntu for about 4 weeks so I know nothing.

---

### Post by Tarid on 2010-10-16
Update:



I then tried installing the JRE by typing this in the terminal:
 
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```but I received this error

```
The following packages have unmet dependencies:
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
                 Depends: sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not installable
                 Recommends: gsfonts-x11 but it is not installable
  sun-java6-plugin: Depends: sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not going to be installed
E: Broken packages

```

---

### Post by gradinaruvasile on 2010-10-16
You have to install the .deb.from the DEBS/desktop-integration/ folder to get the menu entries.
Java is optional for openoffice. And it seems you have some messed up repositories.

---

### Post by Tarid on 2010-10-16
How can I do this?

---

### Post by deepakjoy on 2010-10-16
Have you tried installing Java from Synaptic?

---

### Post by coffeecat on 2010-10-16
@Tarid, which release of Ubuntu are you using, 10.04 or 10.10? The repository version of OpenOffice is 3.2.0 for 10.04 and 3.2.1 for 10.10. It's much easier to install Open Office from the repository - that's if it's not installed already. Does OO not come with the netbook version of Ubuntu?

Anyway, have a look in Synaptic or Software Centre. Unless you have a specific reason for wanting 3.2.1 in Lucid/10.04.

One advantage of the repository version is that it's the Go-OO build of Open Office.

---

### Post by Tarid on 2010-10-16
> **gradinaruvasile said:**
> You have to install the .deb.from the DEBS/desktop-integration/ folder to get the menu entries.
Java is optional for openoffice. And it seems you have some messed up repositories.

how can i do this?

---

### Post by Tarid on 2010-10-16
> **deepakjoy said:**
> Have you tried installing Java from Synaptic?


No, what java package do I install from Synaptic? There are quite a few packages.

---

### Post by Tarid on 2010-10-16
> **coffeecat said:**
> @Tarid, which release of Ubuntu are you using, 10.04 or 10.10? The repository version of OpenOffice is 3.2.0 for 10.04 and 3.2.1 for 10.10. It's much easier to install Open Office from the repository - that's if it's not installed already. Does OO not come with the netbook version of Ubuntu?

Anyway, have a look in Synaptic or Software Centre. Unless you have a specific reason for wanting 3.2.1 in Lucid/10.04.

One advantage of the repository version is that it's the Go-OO build of Open Office.

Ubuntu Release 10.04 (lucid)

Linux version 2.6.32-25-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010

**It's much easier to install Open Office from the repository - that's if  it's not installed already. **

I tried installing it from the repository but received a dependency error.  

Package dependencies cannot be resolved 
details openoffice.org

**Does OO not come with the netbook version of Ubuntu?**
Yes, it did but it did not include base. So I uninstalled it and tried to install the full version. 


**Anyway, have a look in Synaptic or Software Centre. Unless you have a specific reason for wanting 3.2.1 in Lucid/10.04.**

I tried installing from Synaptic or Software Centre and I received a dependency error

---

### Post by Tarid on 2010-10-17
> **gradinaruvasile said:**
> You have to install the .deb.from the DEBS/desktop-integration/ folder to get the menu entries.
Java is optional for openoffice. And it seems you have some messed up repositories.


I ran this 

```
sudo dpkg -i ~/Desktop/OOO320_m18_native_packed-1_en-US.9502/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9502_all.deb
```


I  attempted to open base and received this error message

**openoffice.org requires a java runtime environment (JRE) to perform this task. Please install a JRE and restart openoffice.org**

---

### Post by Tarid on 2010-10-17
When I try to install Open JDK  java 6 runtime from Ubuntu Software Center I get the following message

**Package dependicies cannot be resolved.**

---

### Post by Tarid on 2010-10-17
These are my software sources.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

---

### Post by Tarid on 2010-10-17
This

```
sudo apt-get install sun-java6-jre
```

gets this
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
                 Depends: sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not installable
                 Recommends: gsfonts-x11 but it is not installable
E: Broken packages

```

---

### Post by Tarid on 2010-10-23
Bump

---

### Post by ugm6hr on 2010-10-23
Stop for a second... If you are an Ubuntu beginner - stick with repositories. Use Software Center.

If you haven't done too much customisation, it might be easier to start again with a fresh install.

And if you want to install Base, you don't need to remove anything - just install Base on top of the other components.

If there is a dependency error, it is because you have tried to manually add a repository:
**deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main**
Note the "jaunty" in that - it will always go wrong if you use the wrong version's repository (and this is an unofficial one too).

To correct - remove that repository, then...
In Terminal:
```
sudo apt-get update
sudo apt-get install -f
sudo apt-get remove --purge openoffice*
```
Copy and paste the output here. This tries to fix dependency problems.

Once done, you should hopefully be able to use Software Centre again.

---

### Post by Tarid on 2010-10-23
Note, selecting openoffice.org-hyphenation-sh for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-si for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-te for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-ro for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-sk for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-tg for regex 'openoffice*'
Note, selecting openoffice.org2-l10n-pa-in for regex 'openoffice*'
Note, selecting openoffice.org-l10n-pa-in instead of openoffice.org2-l10n-pa-in
Note, selecting openoffice.org-hyphenation-sl for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-th for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-ru for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-ug for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-rw for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-sr for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-tn for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-ss for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-ve for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-st for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-uk for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-sv for regex 'openoffice*'
Note, selecting openoffice.org-help-2.4 for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-tr for regex 'openoffice*'
Note, selecting openoffice.org-zemberek instead of openoffice.org-hyphenation-tr
Note, selecting openoffice.org-hyphenation-vi for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-ts for regex 'openoffice*'
Note, selecting openoffice.org-writer2latex for regex 'openoffice*'
Note, selecting openoffice.org2-writer for regex 'openoffice*'
Note, selecting openoffice.org-writer instead of openoffice.org2-writer
Note, selecting openoffice.org-hyphenation-en-za for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-xh for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-uz for regex 'openoffice*'
Note, selecting openoffice.org-help-3.1 for regex 'openoffice*'
Note, selecting openoffice.org-writer2xhtml for regex 'openoffice*'
Note, selecting openoffice.org-help-3.2 for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-zu for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-pt-br for regex 'openoffice*'
Note, selecting openoffice.org-l10n-pa-in for regex 'openoffice*'
Note, selecting openoffice.org-java for regex 'openoffice*'
Note, selecting openoffice.org-core instead of openoffice.org-java
Note, selecting openoffice.org-l10n-common for regex 'openoffice*'
Note, selecting openoffice.org2-base for regex 'openoffice*'
Note, selecting openoffice.org-base instead of openoffice.org2-base
Note, selecting openoffice.org2-l10n-ast for regex 'openoffice*'
Note, selecting openoffice.org-l10n-ast instead of openoffice.org2-l10n-ast
Note, selecting openoffice.org-ure for regex 'openoffice*'
Note, selecting openoffice.org2-l10n-be-by for regex 'openoffice*'
Note, selecting openoffice.org-l10n-be-by instead of openoffice.org2-l10n-be-by
Note, selecting openoffice.org-mimelnk for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus for regex 'openoffice*'
Note, selecting libserializer-java-openoffice.org for regex 'openoffice*'
Note, selecting openoffice.org-help-pa-in for regex 'openoffice*'
Note, selecting openoffice.org-l10n-be-by for regex 'openoffice*'
Note, selecting openoffice.org-style-human for regex 'openoffice*'
Note, selecting openoffice.org-sdbc-postgresql for regex 'openoffice*'
Note, selecting openoffice.org2-calc for regex 'openoffice*'
Note, selecting openoffice.org-calc instead of openoffice.org2-calc
Note, selecting openoffice.org2-l10n-hi-in for regex 'openoffice*'
Note, selecting openoffice.org-l10n-hi-in instead of openoffice.org2-l10n-hi-in
Note, selecting openoffice.org2-filter-so52 for regex 'openoffice*'
Note, selecting openoffice.org-filter-binfilter instead of openoffice.org2-filter-so52
Note, selecting openoffice.org2-l10n-pt-br for regex 'openoffice*'
Note, selecting openoffice.org-l10n-pt-br instead of openoffice.org2-l10n-pt-br
Note, selecting openoffice.org-presenter-console for regex 'openoffice*'
Note, selecting openoffice.org-l10n-hi-in for regex 'openoffice*'
Note, selecting openoffice.org-help-be-by for regex 'openoffice*'
Note, selecting openoffice.org-l10n-pt-br for regex 'openoffice*'
Note, selecting openoffice.org-l10n-mr-in for regex 'openoffice*'
Note, selecting openoffice.org-1.9.125 for regex 'openoffice*'
Note, selecting openoffice.org-l10n-ast for regex 'openoffice*'
Note, selecting openoffice.org-l10n-1.9.108 for regex 'openoffice*'
Note, selecting openoffice.org-l10n-1.9.114 for regex 'openoffice*'
Note, selecting openoffice.org-l10n-1.9.121 for regex 'openoffice*'
Note, selecting openoffice.org-bundled for regex 'openoffice*'
Note, selecting openoffice.org-core instead of openoffice.org-bundled
Note, selecting openoffice.org-style-galaxy for regex 'openoffice*'
Note, selecting openoffice.org-gtk-gnome for regex 'openoffice*'
Note, selecting openoffice.org-gnome instead of openoffice.org-gtk-gnome
Note, selecting openoffice.org-help-hi-in for regex 'openoffice*'
Note, selecting openoffice.org-presentation-minimizer for regex 'openoffice*'
Note, selecting openoffice.org3-math for regex 'openoffice*'
Note, selecting openoffice.org-help-pt-br for regex 'openoffice*'
Note, selecting openoffice.org-evolution for regex 'openoffice*'
Note, selecting openoffice.org-pdfimport for regex 'openoffice*'
Note, selecting openoffice.org-math for regex 'openoffice*'
Note, selecting openoffice.org-l10n-ta-in for regex 'openoffice*'
Note, selecting openofficeorg-desktop-integration for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-af for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-ca for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-ca instead of openoffice.org2-thesaurus-ca
Note, selecting openoffice.org2-thesaurus-bg for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-da for regex 'openoffice*'
Note, selecting libloader-java-openoffice.org for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-ar for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-bn for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-as for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-de for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-br for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-bs for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-fa for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-cs for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-cs instead of openoffice.org2-thesaurus-cs
Note, selecting openoffice.org2-java-common for regex 'openoffice*'
Note, selecting openoffice.org-java-common instead of openoffice.org2-java-common
Note, selecting openoffice.org2-thesaurus-ga for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-el for regex 'openoffice*'
Note, selecting openoffice.org-common for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-fi for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-eo for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-cy for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-es for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-he for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-et for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-eu for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-dz for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-gl for regex 'openoffice*'
Note, selecting openoffice.org-spellcheck-en-us for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-fr for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-fr instead of openoffice.org2-thesaurus-fr
Note, selecting openoffice.org2-thesaurus-id for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-ja for regex 'openoffice*'
Note, selecting openoffice.org-dev-doc for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-ka for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-gu for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-hr for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-hu for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-hu instead of openoffice.org2-thesaurus-hu
Note, selecting openoffice.org2-thesaurus-it for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-km for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-kn for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-ko for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-nb for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-ne for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-mk for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-ku for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-ml for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-oc for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-mn for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-lt for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-nl for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-lv for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-mr for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-nn for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-om for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-nr for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-ns for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-pl for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-or for regex 'openoffice*'
Note, selecting openoffice.org2-core for regex 'openoffice*'
Note, selecting openoffice.org-core instead of openoffice.org2-core
Note, selecting openoffice.org2-thesaurus-pt for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-ta for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-si for regex 'openoffice*'
Note, selecting openoffice.org2-evolution for regex 'openoffice*'
Note, selecting openoffice.org-evolution instead of openoffice.org2-evolution
Note, selecting openoffice.org2-thesaurus-te for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-ro for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-ro instead of openoffice.org2-thesaurus-ro
Note, selecting openoffice.org2-thesaurus-sk for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-sk instead of openoffice.org2-thesaurus-sk
Note, selecting openoffice.org2-thesaurus-tg for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-sl for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-th for regex 'openoffice*'
Note, selecting openoffice.org for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-ru for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-ug for regex 'openoffice*'
Note, selecting openoffice.org3-writer for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-sr for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-rw for regex 'openoffice*'
Note, selecting openoffice.org-debian-menus for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-tn for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-ss for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-ve for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-st for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-uk for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-sv for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-tr for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-vi for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-ts for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-xh for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-uz for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-zh-cn for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-zu for regex 'openoffice*'
Note, selecting openoffice.org-voikko for regex 'openoffice*'
Note, selecting openoffice.org3-impress for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-en-au for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-zh-tw for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-en-gb for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-en-us instead of openoffice.org-thesaurus-en-gb
Note, selecting openoffice.org-hyphenation for regex 'openoffice*'
Note, selecting openoffice.org2-draw for regex 'openoffice*'
Note, selecting openoffice.org-draw instead of openoffice.org2-draw
Note, selecting openoffice.org-base-core for regex 'openoffice*'
Note, selecting openoffice.org-unbundled for regex 'openoffice*'
Note, selecting openoffice.org-debian-menus instead of openoffice.org-unbundled
Note, selecting openoffice.org-spellcheck-de-ch for regex 'openoffice*'
Note, selecting myspell-de-ch instead of openoffice.org-spellcheck-de-ch
Note, selecting openoffice.org-style-andromeda for regex 'openoffice*'
Note, selecting openoffice.org-spellcheck-de-de for regex 'openoffice*'
Note, selecting myspell-de-de instead of openoffice.org-spellcheck-de-de
Note, selecting openoffice.org-spellcheck-de-at for regex 'openoffice*'
Note, selecting myspell-de-at instead of openoffice.org-spellcheck-de-at
Note, selecting openoffice.org-debian-files for regex 'openoffice*'
Note, selecting openoffice.org2-officebean for regex 'openoffice*'
Note, selecting openoffice.org-officebean instead of openoffice.org2-officebean
Note, selecting openoffice.org-thesaurus-en-us for regex 'openoffice*'
Note, selecting openoffice.org-wiki-publisher for regex 'openoffice*'
Note, selecting openoffice.org2-dev-doc for regex 'openoffice*'
Note, selecting openoffice.org-dev-doc instead of openoffice.org2-dev-doc
Note, selecting openoffice.org2-l10n-zh-cn for regex 'openoffice*'
Note, selecting openoffice.org-l10n-zh-cn instead of openoffice.org2-l10n-zh-cn
Note, selecting openoffice.org2-thesaurus-en-gb for regex 'openoffice*'
Note, selecting openoffice.org-help-af for regex 'openoffice*'
Note, selecting openoffice.org-help-ca for regex 'openoffice*'
Note, selecting openoffice.org-help-bg for regex 'openoffice*'
Note, selecting openoffice.org-help-da for regex 'openoffice*'
Note, selecting openoffice.org-report-builder for regex 'openoffice*'
Note, selecting openoffice.org-help-ar for regex 'openoffice*'
Note, selecting openoffice.org-help-bn for regex 'openoffice*'
Note, selecting openoffice.org-help-as for regex 'openoffice*'
Note, selecting openoffice.org-help-de for regex 'openoffice*'
Note, selecting openoffice.org-help-br for regex 'openoffice*'
Note, selecting openoffice.org-help-bs for regex 'openoffice*'
Note, selecting openoffice.org-help-fa for regex 'openoffice*'
Note, selecting openoffice.org-help-cs for regex 'openoffice*'
Note, selecting openoffice.org-help-ga for regex 'openoffice*'
Note, selecting openoffice.org-help-el for regex 'openoffice*'
Note, selecting openoffice.org-help-fi for regex 'openoffice*'
Note, selecting openoffice.org-help-en for regex 'openoffice*'
Note, selecting openoffice.org-help-eo for regex 'openoffice*'
Note, selecting openoffice.org-help-cy for regex 'openoffice*'
Note, selecting openoffice.org-officebean for regex 'openoffice*'
Note, selecting openoffice.org-help-es for regex 'openoffice*'
Note, selecting openoffice.org-help-he for regex 'openoffice*'
Note, selecting openoffice.org-help-et for regex 'openoffice*'
Note, selecting openoffice.org-help-eu for regex 'openoffice*'
Note, selecting openoffice.org-help-dz for regex 'openoffice*'
Note, selecting openoffice.org-help-gl for regex 'openoffice*'
Note, selecting openoffice.org-help-fr for regex 'openoffice*'
Note, selecting openoffice.org-help-id for regex 'openoffice*'
Note, selecting openoffice.org-l10n-3.2 for regex 'openoffice*'
Note, selecting openoffice.org-emailmerge for regex 'openoffice*'
Note, selecting openoffice.org-style-crystal for regex 'openoffice*'
Note, selecting openoffice.org-help-ja for regex 'openoffice*'
Note, selecting openoffice.org-help-ka for regex 'openoffice*'
Note, selecting openoffice.org-help-gu for regex 'openoffice*'
Note, selecting openoffice.org-help-hr for regex 'openoffice*'
Note, selecting openoffice.org-l10n-zh-cn for regex 'openoffice*'
Note, selecting openoffice.org-help-hu for regex 'openoffice*'
Note, selecting openoffice.org-help-it for regex 'openoffice*'
Note, selecting openoffice.org-help-2.0.0 for regex 'openoffice*'
Note, selecting openoffice.org-help-2.0.1 for regex 'openoffice*'
Note, selecting openoffice.org-help-km for regex 'openoffice*'
Note, selecting openoffice.org-help-2.0.2 for regex 'openoffice*'
Note, selecting openoffice.org-help-kn for regex 'openoffice*'
Note, selecting openoffice.org-help-2.0.3 for regex 'openoffice*'
Note, selecting openoffice.org-help-ko for regex 'openoffice*'
Note, selecting openoffice.org-help-nb for regex 'openoffice*'
Note, selecting openoffice.org-help-ne for regex 'openoffice*'
Note, selecting openoffice.org-help-mk for regex 'openoffice*'
Note, selecting openoffice.org-help-ku for regex 'openoffice*'
Note, selecting openoffice.org-help-ml for regex 'openoffice*'
Note, selecting openoffice.org-help-oc for regex 'openoffice*'
Note, selecting openoffice.org-help-mn for regex 'openoffice*'
Note, selecting openoffice.org-help-lt for regex 'openoffice*'
Note, selecting openoffice.org2-l10n-zh-tw for regex 'openoffice*'
Note, selecting openoffice.org-l10n-zh-tw instead of openoffice.org2-l10n-zh-tw
Note, selecting openoffice.org-help-lv for regex 'openoffice*'
Note, selecting openoffice.org-help-nl for regex 'openoffice*'
Note, selecting openoffice.org-help-mr for regex 'openoffice*'
Note, selecting openoffice.org-help-nn for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-en-us for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-en-us instead of openoffice.org2-thesaurus-en-us
Note, selecting openoffice.org-help-nr for regex 'openoffice*'
Note, selecting openoffice.org-help-om for regex 'openoffice*'
Note, selecting openoffice.org-help-ns for regex 'openoffice*'
Note, selecting libxml-java-openoffice.org for regex 'openoffice*'
Note, selecting openoffice.org2-thesaurus-en-za for regex 'openoffice*'
Note, selecting openoffice.org-help-pl for regex 'openoffice*'
Note, selecting openoffice.org-help-or for regex 'openoffice*'
Note, selecting openoffice.org-help-pt for regex 'openoffice*'
Note, selecting openoffice.org-help-ta for regex 'openoffice*'
Note, selecting openoffice.org-help-si for regex 'openoffice*'
Note, selecting openoffice.org-help-te for regex 'openoffice*'
Note, selecting openoffice.org-help-ro for regex 'openoffice*'
Note, selecting openoffice.org-help-sk for regex 'openoffice*'
Note, selecting openoffice.org-help-tg for regex 'openoffice*'
Note, selecting openoffice.org-help-sl for regex 'openoffice*'
Note, selecting openoffice.org-help-th for regex 'openoffice*'
Note, selecting openoffice.org-help-ru for regex 'openoffice*'
Note, selecting libopenoffice-oodoc-perl for regex 'openoffice*'
Note, selecting openoffice.org-help-ug for regex 'openoffice*'
Note, selecting openoffice.org-help-sr for regex 'openoffice*'
Note, selecting openoffice.org-help-rw for regex 'openoffice*'
Note, selecting openoffice.org-help-tn for regex 'openoffice*'
Note, selecting openoffice.org-help-ss for regex 'openoffice*'
Note, selecting openoffice.org-help-ve for regex 'openoffice*'
Note, selecting openoffice.org-help-st for regex 'openoffice*'
Note, selecting openoffice.org-help-uk for regex 'openoffice*'
Note, selecting openoffice.org-help-sv for regex 'openoffice*'
Note, selecting openoffice.org-help-tr for regex 'openoffice*'
Note, selecting openoffice.org-help-vi for regex 'openoffice*'
Note, selecting openoffice.org-help-ts for regex 'openoffice*'
Note, selecting openoffice.org-help-xh for regex 'openoffice*'
Note, selecting openoffice.org-help-uz for regex 'openoffice*'
Note, selecting openoffice.org-help-zu for regex 'openoffice*'
Note, selecting openoffice.org-l10n-zh-tw for regex 'openoffice*'
Note, selecting openoffice.org-l10n-te-in for regex 'openoffice*'
Note, selecting openoffice.org-help-zh-cn for regex 'openoffice*'
Note, selecting openoffice.org2-common for regex 'openoffice*'
Note, selecting openoffice.org-common instead of openoffice.org2-common
Note, selecting openoffice.org-hyphenation-pa-in for regex 'openoffice*'
Note, selecting openoffice.org2-l10n-en-gb for regex 'openoffice*'
Note, selecting openoffice.org-l10n-en-gb instead of openoffice.org2-l10n-en-gb
Note, selecting openoffice.org-crashrep for regex 'openoffice*'
Note, selecting openoffice.org-dmaths for regex 'openoffice*'
Note, selecting openoffice.org-style-tango for regex 'openoffice*'
Note, selecting openoffice.org-zemberek for regex 'openoffice*'
Note, selecting openoffice.org-help-zh-tw for regex 'openoffice*'
Note, selecting libfonts-java-openoffice.org for regex 'openoffice*'
Note, selecting libpentaho-reporting-flow-engine-java-openoffice.org for regex 'openoffice*'
Note, selecting openoffice.org-l10n-en-gb for regex 'openoffice*'
Note, selecting openoffice.org2-l10n-en-za for regex 'openoffice*'
Note, selecting openoffice.org-l10n-en-za instead of openoffice.org2-l10n-en-za
Note, selecting openoffice.org-hyphenation-be-by for regex 'openoffice*'
Note, selecting openoffice.org-coooder for regex 'openoffice*'
Note, selecting openoffice.org3-base for regex 'openoffice*'
Note, selecting openoffice.org-l10n-gu-in for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-ast for regex 'openoffice*'
Note, selecting python-openoffice for regex 'openoffice*'
Note, selecting openoffice.org-presenter-screen for regex 'openoffice*'
Note, selecting openoffice.org-presenter-console instead of openoffice.org-presenter-screen
Note, selecting openoffice.org-base for regex 'openoffice*'
Note, selecting openoffice.org-l10n-en-us for regex 'openoffice*'
Note, selecting openoffice.org-common instead of openoffice.org-l10n-en-us
Note, selecting openoffice.org2-thesaurus-ast for regex 'openoffice*'
Note, selecting openoffice.org-l10n-en-za for regex 'openoffice*'
Note, selecting librepository-java-openoffice.org for regex 'openoffice*'
Note, selecting openoffice.org-help-en-gb for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-hi-in for regex 'openoffice*'
Note, selecting openofficeorg-debian-menus for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-ca for regex 'openoffice*'
Note, selecting openoffice.org3-calc for regex 'openoffice*'
Note, selecting openoffice.org-headless for regex 'openoffice*'
Note, selecting openoffice.org-core instead of openoffice.org-headless
Note, selecting openoffice.org-thesaurus-cs for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-fr for regex 'openoffice*'
Note, selecting openclipart-openoffice.org for regex 'openoffice*'
Note, selecting openoffice.org-calc for regex 'openoffice*'
Note, selecting openoffice.org-hyphenation-pt-br for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-hu for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-it for regex 'openoffice*'
Note, selecting openoffice.org3-dict-en for regex 'openoffice*'
Note, selecting openoffice.org3-dict-es for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-ne for regex 'openoffice*'
Note, selecting openoffice.org3-dict-fr for regex 'openoffice*'
Note, selecting openoffice.org-help-en-us for regex 'openoffice*'
Note, selecting openoffice.org-help-en-za for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-pl for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-ro for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-sk for regex 'openoffice*'
Note, selecting openoffice.org-thesaurus-ru for regex 'openoffice*'
Note, selecting openoffice.org-l10n-as-in for regex 'openoffice*'
Note, selecting docvert-openoffice.org for regex 'openoffice*'
Note, selecting openoffice.org-reportdesigner for regex 'openoffice*'
Note, selecting openoffice.org-report-builder instead of openoffice.org-reportdesigner
Note, selecting openoffice.org-qa-ui-tests for regex 'openoffice*'
Note, selecting openoffice.org-starter-guide for regex 'openoffice*'
Note, selecting openoffice.org-l10n-af for regex 'openoffice*'
Note, selecting openoffice.org-l10n-ca for regex 'openoffice*'
Note, selecting openoffice.org-l10n-bg for regex 'openoffice*'
Note, selecting openoffice.org-l10n-da for regex 'openoffice*'
Note, selecting openoffice.org-l10n-ar for regex 'openoffice*'
Note, selecting openoffice.org-l10n-bn for regex 'openoffice*'
Note, selecting openoffice.org-l10n-as for regex 'openoffice*'
Note, selecting openoffice.org-l10n-de for regex 'openoffice*'
Note, selecting openoffice.org-l10n-br for regex 'openoffice*'
Note, selecting openoffice.org-l10n-bs for regex 'openoffice*'
Note, selecting openoffice.org-l10n-fa for regex 'openoffice*'
Note, selecting openoffice.org-l10n-cs for regex 'openoffice*'
Note, selecting openoffice.org-l10n-ga for regex 'openoffice*'
Note, selecting openoffice.org-l10n-el for regex 'openoffice*'
Note, selecting openoffice.org-l10n-fi for regex 'openoffice*'
Note, selecting openoffice.org-l10n-en for regex 'openoffice*'
Note, selecting openoffice.org-l10n-eo for regex 'openoffice*'
Note, selecting openoffice.org-l10n-cy for regex 'openoffice*'
Note, selecting openoffice.org-l10n-es for regex 'openoffice*'
Note, selecting openoffice.org-l10n-et for regex 'openoffice*'
Note, selecting openoffice.org-l10n-he for regex 'openoffice*'
Note, selecting openoffice.org-l10n-eu for regex 'openoffice*'
Note, selecting openoffice.org-l10n-dz for regex 'openoffice*'
Note, selecting openoffice.org-l10n-gl for regex 'openoffice*'
Note, selecting openoffice.org-l10n-fr for regex 'openoffice*'
Note, selecting openoffice.org-l10n-id for regex 'openoffice*'
Note, selecting openoffice.org-l10n-ja for regex 'openoffice*'
Note, selecting openoffice.org-l10n-ka for regex 'openoffice*'
Note, selecting openoffice.org-l10n-gu for regex 'openoffice*'
Note, selecting openoffice.org2-gnome for regex 'openoffice*'
Note, selecting openoffice.org-gnome instead of openoffice.org2-gnome
Note, selecting openoffice.org-l10n-hr for regex 'openoffice*'
Note, selecting openoffice.org-l10n-in for regex 'openoffice*'
Note, selecting openoffice.org-l10n-hu for regex 'openoffice*'
Note, selecting openoffice.org-l10n-it for regex 'openoffice*'
Note, selecting openoffice.org-l10n-km for regex 'openoffice*'
Note, selecting openoffice.org-l10n-kn for regex 'openoffice*'
Note, selecting openoffice.org-l10n-ko for regex 'openoffice*'
Note, selecting openoffice.org-l10n-nb for regex 'openoffice*'
Note, selecting openoffice.org-l10n-ne for regex 'openoffice*'
Note, selecting openoffice.org-l10n-mk for regex 'openoffice*'
Note, selecting openoffice.org-l10n-ku for regex 'openoffice*'
Note, selecting openoffice.org-l10n-ml for regex 'openoffice*'
Note, selecting openoffice.org-l10n-oc for regex 'openoffice*'
The following packages will be REMOVED:
  ooobasis3.2-base* ooobasis3.2-binfilter* ooobasis3.2-calc* ooobasis3.2-core01*
  ooobasis3.2-core02* ooobasis3.2-core03* ooobasis3.2-core04* ooobasis3.2-core05*
  ooobasis3.2-core06* ooobasis3.2-core07* ooobasis3.2-draw* ooobasis3.2-en-us*
  ooobasis3.2-en-us-base* ooobasis3.2-en-us-binfilter* ooobasis3.2-en-us-calc*
  ooobasis3.2-en-us-draw* ooobasis3.2-en-us-help* ooobasis3.2-en-us-impress*
  ooobasis3.2-en-us-math* ooobasis3.2-en-us-res* ooobasis3.2-en-us-writer*
  ooobasis3.2-gnome-integration* ooobasis3.2-graphicfilter* ooobasis3.2-images*
  ooobasis3.2-impress* ooobasis3.2-javafilter* ooobasis3.2-kde-integration* ooobasis3.2-math*
  ooobasis3.2-onlineupdate* ooobasis3.2-ooofonts* ooobasis3.2-oooimprovement*
  ooobasis3.2-ooolinguistic* ooobasis3.2-pyuno* ooobasis3.2-testtool* ooobasis3.2-writer*
  ooobasis3.2-xsltfilter* openoffice.org-debian-menus* openoffice.org-ure* openoffice.org3*
  openoffice.org3-base* openoffice.org3-calc* openoffice.org3-dict-en* openoffice.org3-dict-es*
  openoffice.org3-dict-fr* openoffice.org3-draw* openoffice.org3-en-us*
  openoffice.org3-impress* openoffice.org3-math* openoffice.org3-writer*
0 upgraded, 0 newly installed, 49 to remove and 0 not upgraded.
After this operation, 209MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 148862 files and directories currently installed.)
Removing openoffice.org3-base ...
Removing ooobasis3.2-base ...
Purging configuration files for ooobasis3.2-base ...
Removing ooobasis3.2-binfilter ...
Removing openoffice.org3-calc ...
Removing ooobasis3.2-calc ...
Purging configuration files for ooobasis3.2-calc ...
Removing openoffice.org3-dict-en ...
javaldx: Could not find a Java Runtime Environment! 
Removing openoffice.org3-dict-es ...
javaldx: Could not find a Java Runtime Environment! 
Removing ooobasis3.2-pyuno ...
Removing openoffice.org3-impress ...
Removing openoffice.org3-writer ...
Removing openoffice.org3-draw ...
Removing openoffice.org3-en-us ...
Removing openoffice.org3-math ...
Removing openoffice.org3-dict-fr ...
javaldx: Could not find a Java Runtime Environment! 
Removing openoffice.org3 ...
dpkg: warning: while removing openoffice.org3, directory '/opt/openoffice.org3/share/uno_packages/cache' not empty so not removed.
dpkg: warning: while removing openoffice.org3, directory '/opt/openoffice.org3/share/uno_packages' not empty so not removed.
dpkg: warning: while removing openoffice.org3, directory '/opt/openoffice.org3/share' not empty so not removed.
dpkg: warning: while removing openoffice.org3, directory '/opt/openoffice.org3' not empty so not removed.
Removing ooobasis3.2-core06 ...
Removing ooobasis3.2-core07 ...
Removing ooobasis3.2-core04 ...
Removing ooobasis3.2-core05 ...
Removing ooobasis3.2-core02 ...
Purging configuration files for ooobasis3.2-core02 ...
Removing ooobasis3.2-core03 ...
Removing ooobasis3.2-gnome-integration ...
Removing ooobasis3.2-kde-integration ...
Removing ooobasis3.2-testtool ...
Removing ooobasis3.2-impress ...
Purging configuration files for ooobasis3.2-impress ...
Removing ooobasis3.2-ooofonts ...
Removing ooobasis3.2-ooolinguistic ...
Removing ooobasis3.2-math ...
Purging configuration files for ooobasis3.2-math ...
Removing ooobasis3.2-xsltfilter ...
Removing ooobasis3.2-oooimprovement ...
Removing ooobasis3.2-javafilter ...
Removing ooobasis3.2-onlineupdate ...
Removing ooobasis3.2-en-us-math ...
Removing ooobasis3.2-en-us-binfilter ...
Removing ooobasis3.2-en-us-impress ...
Removing ooobasis3.2-en-us-base ...
Removing ooobasis3.2-en-us-draw ...
Removing ooobasis3.2-en-us-help ...
Removing ooobasis3.2-en-us-writer ...
Removing ooobasis3.2-en-us-res ...
Removing ooobasis3.2-en-us-calc ...
Removing ooobasis3.2-en-us ...
Removing ooobasis3.2-images ...
Removing ooobasis3.2-writer ...
Purging configuration files for ooobasis3.2-writer ...
Removing ooobasis3.2-graphicfilter ...
Removing ooobasis3.2-draw ...
Purging configuration files for ooobasis3.2-draw ...
Removing ooobasis3.2-core01 ...
Removing openoffice.org-debian-menus ...
/usr/bin/gtk-update-icon-cache
gtk-update-icon-cache: Cache file created successfully.
/usr/bin/gtk-update-icon-cache
gtk-update-icon-cache: Cache file created successfully.
Purging configuration files for openoffice.org-debian-menus ...
dpkg: warning: while removing openoffice.org-debian-menus, directory '/usr/share/applnk' not empty so not removed.
Removing openoffice.org-ure ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for shared-mime-info ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gnome-icon-theme ...
Processing triggers for python-support ...

---

### Post by Tarid on 2010-10-23
This is what I get when try to install software center.

```
package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.

openjdk-6-jre
```

---

### Post by ugm6hr on 2010-10-23
Did you remove the jaunty repository?
Run again:
```
sudo apt-get remove sun-java6-jre
sudo apt-get update
sudo apt-get autoremove
sudo apt-get install -f
```
Post your repository list again, just to check.

---

### Post by Tarid on 2010-10-24
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

---

### Post by Tarid on 2010-10-24
bump

---

### Post by ugm6hr on 2010-10-25
Your repository list appears to be missing the main repository:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid restricted main multiverse universe

Add the main repo, then try again.
```
sudo apt-get remove sun-java6-jre
sudo apt-get update
sudo apt-get autoremove
sudo apt-get install -f
```

Then see if Openoffice will install

---

