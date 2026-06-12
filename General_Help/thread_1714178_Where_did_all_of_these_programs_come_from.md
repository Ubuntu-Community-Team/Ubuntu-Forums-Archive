---
title: "Where did all of these programs come from?"
date: 2011-03-25
forum: General Help
---

### Post by andyman420 on 2011-03-25
Hello Folks, 

I've been using ubuntu 10.10 on both of my machines since November 2010.  I absolutely love it, and I have no complaints at all.  These forums are especially helpful.  

Here is my situation:

Today I installed compiz from the terminal using the following command:

sudo apt-get install compiz*

After this i installed the compiz advanced settings manager, and the compiz icon.  This all went well, and I am able to take advantage of all of the great desktop effects that compiz has to offer.  

However, after doing this I notice that my machine now has all sorts of KDE applications that were never installed before.  Many of the menu entries that have been added for these programs diplay a "?" icon, and when clicked they do nothing.

Can anyone help me with this?  I'd like to be rid of them, and back down the the great software that was either bundled with my original install, or that I installed myself.

---

### Post by idoitprone on 2011-03-25
> **andyman420 said:**
> Hello Folks, 


Today I installed compiz from the terminal using the following command:

sudo apt-get install compiz*



Do you know whats does a star "*" do?

It a wild card that tell the console to find the find anything following the star

lets make an example

> touch 1 2 3 4 12 123 24
ls
 1 2 3 4 12 123 24
rm 1
ls
 2 3 4 12 123 24

it removed file one. Now show what happen with *

> touch 1 2 3 4 12 123 24
ls
1 2 3 4 12 123 24
rm 1*
ls
2 3 4 24
note: i made up a random example in a few seconds without testing. Please forgive me if ls show these numbers out of order. It only meant for a proof of concept

notice how 1 12 123 are deleted
It finds all the characters before without regard for the rest of the letters regardless of size or characters

So you might install packages that depend on other packages. KDE once use compiz heavily

---

### Post by andyman420 on 2011-03-25
Idiotprone, prshah:

Thanks for the information.

---

### Post by prshah on 2011-03-25
> **andyman420 said:**
> 
sudo apt-get install compiz*

Using compiz* has selected compiz-kde as well. These are the packages that are installed with compiz-kde on a gnome desktop```
The following extra packages will be installed:
  compizconfig-backend-kconfig docbook-xsl docbook-xsl-doc-html hal hal-info
  kdebase-runtime kdebase-runtime-data kdelibs-bin kdelibs-data kdelibs4c2a
  kdelibs5-data kdelibs5-plugins kdoctools kubuntu-debug-installer libattica0
  libavahi-qt3-1 libclucene0ldbl libdbusmenu-qt2 libdirectfb-1.2-9 libgif4
  libhal-storage1 libiodbc2 libkatepartinterfaces4 libkdecorations4
  libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkfile4 libkhtml5
  libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4
  libknotifyconfig4 libkntlm4 libkparts4 libkpty4 libkrosscore4 libkrossui4
  libktexteditor4 libkutils4 liblua50 liblualib50 libnepomuk4
  libnepomukquery4a libphonon4 libplasma3 libpolkit-qt-1-0 libqapt-runtime
  libqapt1 libqca2 libqt4-opengl libqt4-svg libqtwebkit4 libsolid4 libsoprano4
  libssh-4 libstreamanalyzer0 libstreams0 libthreadweaver4 libts-0.0-0
  libvirtodbc0 libxcb-shape0 libxine1 libxine1-bin libxine1-console
  libxine1-misc-plugins libxine1-x oxygen-icon-theme phonon
  phonon-backend-xine plasma-scriptengine-javascript qapt-batch
  shared-desktop-ontologies smartdimmer soprano-daemon tsconf ttf-dejavu
  ttf-dejavu-extra virtuoso-minimal virtuoso-opensource-6.1-bin
  virtuoso-opensource-6.1-common

```

My guess is that uninstalling the listed packages should put everything back as it was. However, I don't know if any "dependency effect" will occur.

Hope this helps.

---

### Post by idoitprone on 2011-03-25
> **andyman420 said:**
> Idiotprone:

Thanks for the information.  Oddly enough these programs seemed to have uninstalled themselves after I uninstalled only once of them using the ubuntu software center.  


-Andy

You should thank ubuntu for that. They manage dependencies. If you manage to uninstall a key dependency they just uninstall the rest or tell you to use.
> sudo apt-get autoremoveI am a lazy person I rather have my distro take care of stupid little things like that rather than give myself headaches.

---

### Post by Script Warlock on 2011-03-25
i'm just curious, what if you reverse the process sudo apt-get remove compiz* and of course be sure to apt-get install ubuntu-desktop afterwards.

---

