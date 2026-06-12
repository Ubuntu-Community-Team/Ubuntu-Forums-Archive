---
title: "How to remove KDE?"
date: 2006-02-05
forum: General Help
---

### Post by Piggah on 2006-02-05
I recently installed the KDE desktop using "sudp apt-get install kubuntu-desktop"  to see if I liked it or not. I decided that I'd rather just stick with gnome. The only problem I have now is that I don't know how to remove KDE. I imagine it's something simple, but I don't have a clue. If anyone could explain how I'd really appreciate it. 

Thanks in advance. :)


(I wasn't sure which forum this went in, sorry if this is wrong.)

---

### Post by audax321 on 2006-02-06
If you installed via Synaptic then you should just be able to go to File > History and find the log where you installed KDE and remove it. Otherwise, its going to be difficult unless you can find a list of packages installed...

I can tell you this, when I go install kubuntu-desktop it wants to install these packages (btw, I have never installed KDE on this computer and do not have any KDE applications installed, so this should be everything):

```

adept (version 1.0) will be installed
akode (version 4:3.4.3-0ubuntu1) will be installed
akregator (version 4:3.4.3-0ubuntu3) will be installed
amarok (version 2:1.3.1-0ubuntu4) will be installed
amarok-gstreamer (version 2:1.3.1-0ubuntu4) will be installed
ark (version 4:3.4.3-0ubuntu1) will be installed
arts (version 1.4.3-0ubuntu1) will be installed
artsbuilder (version 4:3.4.3-0ubuntu1) will be installed
debtags (version 1.4+svn20050912-0ubuntu1) will be installed
enscript (version 1.6.4-7) will be installed
gtk2-engines-gtk-qt (version 0.60-1ubuntu5) will be installed
gwenview (version 1.2.0-0ubuntu4) will be installed
ivman (version 0.6.3-0ubuntu2) will be installed
k3b (version 0.12.2-0ubuntu2) will be installed
k3blibs (version 0.12.2-0ubuntu2) will be installed
kaddressbook (version 4:3.4.3-0ubuntu3) will be installed
kaffeine (version 0.7-0ubuntu4) will be installed
kaffeine-gstreamer (version 0.7-0ubuntu4) will be installed
kamera (version 4:3.4.3-0ubuntu2.2) will be installed
kappfinder (version 4:3.4.3-0ubuntu6) will be installed
karm (version 4:3.4.3-0ubuntu3) will be installed
katapult (version 0.2-0ubuntu3) will be installed
kate (version 4:3.4.3-0ubuntu6) will be installed
kaudiocreator (version 4:3.4.3-0ubuntu1) will be installed
kcontrol (version 4:3.4.3-0ubuntu6) will be installed
kcron (version 4:3.4.3-0ubuntu1) will be installed
kde-guidance (version 0.4.0-0ubuntu4) will be installed
kde-style-lipstik (version 1.3-0ubuntu1) will be installed
kde-systemsettings (version 0.0svn20050613-0ubuntu3) will be installed
kdeadmin-kfile-plugins (version 4:3.4.3-0ubuntu1) will be installed
kdebase-bin (version 4:3.4.3-0ubuntu6) will be installed
kdebase-data (version 4:3.4.3-0ubuntu6) will be installed
kdebase-kio-plugins (version 4:3.4.3-0ubuntu6) will be installed
kdebluetooth (version 0.99+1.0beta1-2ubuntu3) will be installed
kdegraphics-kfile-plugins (version 4:3.4.3-0ubuntu2.2) will be installed
kdelibs-bin (version 4:3.4.3-0ubuntu2) will be installed
kdelibs-data (version 4:3.4.3-0ubuntu2) will be installed
kdelibs4c2 (version 4:3.4.3-0ubuntu2) will be installed
kdemultimedia-kappfinder-data (version 4:3.4.3-0ubuntu1) will be installed
kdemultimedia-kfile-plugins (version 4:3.4.3-0ubuntu1) will be installed
kdemultimedia-kio-plugins (version 4:3.4.3-0ubuntu1) will be installed
kdenetwork-filesharing (version 4:3.4.3-0ubuntu1) will be installed
kdenetwork-kfile-plugins (version 4:3.4.3-0ubuntu1) will be installed
kdepasswd (version 4:3.4.3-0ubuntu6) will be installed
kdepim-kio-plugins (version 4:3.4.3-0ubuntu3) will be installed
kdepim-wizards (version 4:3.4.3-0ubuntu3) will be installed
kdeprint (version 4:3.4.3-0ubuntu6) will be installed
kdesktop (version 4:3.4.3-0ubuntu6) will be installed
kdm (version 4:3.4.3-0ubuntu6) will be installed
kfind (version 4:3.4.3-0ubuntu6) will be installed
kghostview (version 4:3.4.3-0ubuntu2.2) will be installed
khelpcenter (version 4:3.4.3-0ubuntu6) will be installed
kicker (version 4:3.4.3-0ubuntu6) will be installed
kio-apt (version 0.11-0ubuntu1) will be installed
kio-locate (version 0.4.2tvo0.2) will be installed
klaptopdaemon (version 4:3.4.3-0ubuntu1) will be installed
klipper (version 4:3.4.3-0ubuntu6) will be installed
kmail (version 4:3.4.3-0ubuntu3) will be installed
kmenuedit (version 4:3.4.3-0ubuntu6) will be installed
kmilo (version 4:3.4.3-0ubuntu1) will be installed
kmix (version 4:3.4.3-0ubuntu1) will be installed
knetworkconf (version 0.6.1-3ubuntu6) will be installed
knotes (version 4:3.4.3-0ubuntu3) will be installed
koffice-data (version 1:1.4.1-0ubuntu7.2) will be installed
koffice-libs (version 1:1.4.1-0ubuntu7.2) will be installed
konq-plugins (version 4:3.4.3-0ubuntu1) will be installed
konqueror (version 4:3.4.3-0ubuntu6) will be installed
konqueror-nsplugins (version 4:3.4.3-0ubuntu6) will be installed
konserve (version 0.10.3-1ubuntu2) will be installed
konsole (version 4:3.4.3-0ubuntu6) will be installed
kontact (version 4:3.4.3-0ubuntu3) will be installed
konversation (version 0.18-1ubuntu3) will be installed
kooka (version 4:3.4.3-0ubuntu2.2) will be installed
kopete (version 4:3.4.3-0ubuntu1) will be installed
korganizer (version 4:3.4.3-0ubuntu3) will be installed
kpdf (version 4:3.4.3-0ubuntu2.2) will be installed
kpf (version 4:3.4.3-0ubuntu1) will be installed
kppp (version 4:3.4.3-0ubuntu1) will be installed
krdc (version 4:3.4.3-0ubuntu1) will be installed
krfb (version 4:3.4.3-0ubuntu1) will be installed
krita (version 1:1.4.1-0ubuntu7.2) will be installed
kscd (version 4:3.4.3-0ubuntu1) will be installed
kscreensaver (version 4:3.4.3-0ubuntu1) will be installed
ksmserver (version 4:3.4.3-0ubuntu6) will be installed
ksnapshot (version 4:3.4.3-0ubuntu2.2) will be installed
ksplash (version 4:3.4.3-0ubuntu6) will be installed
ksvg (version 4:3.4.3-0ubuntu2.2) will be installed
ksysguard (version 4:3.4.3-0ubuntu6) will be installed
ksysguardd (version 4:3.4.3-0ubuntu6) will be installed
ksystemlog (version 0.3.2-0ubuntu1) will be installed
kubuntu-artwork-usplash (version 1:5.10-19) will be installed
kubuntu-default-settings (version 1:5.10-19) will be installed
kubuntu-desktop (version 0.55) will be installed
kubuntu-docs (version 5.10-0.6.1) will be installed
kubuntu-konqueror-shortcuts (version 0.1-0ubuntu2) will be installed
kuser (version 4:3.4.3-0ubuntu1) will be installed
kwalletmanager (version 4:3.4.3-0ubuntu1) will be installed
kwifimanager (version 4:3.4.3-0ubuntu1) will be installed
kwin (version 4:3.4.3-0ubuntu6) will be installed
libarts1c2 (version 1.4.3-0ubuntu1) will be installed
libdbus-qt-1-1c2 (version 0.36.2-0ubuntu7) will be installed
libflac++5c2 (version 1.1.2-1ubuntu2) will be installed
libgadu3 (version 1:1.5+20050411-2ubuntu3) will be installed
libgpgme11 (version 1.0.2-1build1) will be installed
libjpeg-progs (version 6b-10) will be installed
libkcal2a (version 4:3.4.3-0ubuntu3) will be installed
libkcddb1 (version 4:3.4.3-0ubuntu1) will be installed
libkdepim1 (version 4:3.4.3-0ubuntu3) will be installed
libkipi0 (version 0.1.1-2build2) will be installed
libkleopatra0a (version 4:3.4.3-0ubuntu3) will be installed
libkonq4 (version 4:3.4.3-0ubuntu6) will be installed
libkpimexchange1 (version 4:3.4.3-0ubuntu3) will be installed
libkpimidentities1 (version 4:3.4.3-0ubuntu3) will be installed
libkscan1 (version 4:3.4.3-0ubuntu2.2) will be installed
libksieve0 (version 4:3.4.3-0ubuntu3) will be installed
libktnef1 (version 4:3.4.3-0ubuntu3) will be installed
liblockdev1 (version 1.0.1-7) will be installed
libmimelib1a (version 4:3.4.3-0ubuntu3) will be installed
libnetpbm10 (version 2:10.0-8ubuntu1.2) will be installed
liboggflac3 (version 1.1.2-1ubuntu2) will be installed
libopenexr2c2 (version 1.2.2-3ubuntu1) will be installed
libopenobex-1.0-0 (version 1:1.0.0-rel-3) will be installed
libpythonize0 (version 0.3.1-0ubuntu2) will be installed
libqt3-mt (version 3:3.3.4-8ubuntu5) will be installed
libsamplerate0 (version 0.1.1-2) will be installed
libsensors3 (version 1:2.9.1-4ubuntu3) will be installed
libtag1c2 (version 1.3.1-1.1ubuntu1) will be installed
libtdb1 (version 1.0.6-13) will be installed
libtunepimp2c2 (version 0.3.0-2ubuntu7) will be installed
libxcomposite1 (version 1:0.2.0-3) will be installed
menu-xdg (version 0.2ubuntu1) will be installed
netpbm (version 2:10.0-8ubuntu1.2) will be installed
openoffice.org2-kde (version 1.9.129-0.1ubuntu4) will be installed
poster (version 20020830-2) will be installed
psutils (version 1.17-17) will be installed
python-kde3 (version 3.11.4+snapshot20050316-0ubuntu7) will be installed
python-opengl (version 2.0.1.09-1ubuntu4) will be installed
python2.4-dev (version 2.4.2-1) will be installed
python2.4-kde3 (version 3.11.4+snapshot20050316-0ubuntu7) will be installed
python2.4-opengl (version 2.0.1.09-1ubuntu4) will be installed
python2.4-qt3 (version 3.14.1-2ubuntu4) will be installed
python2.4-sip4-qt3 (version 4.2.1-1ubuntu4) will be installed
qca-tls (version 1.0-1build1) will be installed
qobex (version 0.99+1.0beta1-2ubuntu3) will be installed
sanekonsole (version 0.2-0ubuntu1) will be installed
speedcrunch (version 0.6beta1-0ubuntu1) will be installed
ttf-dejavu (version 1.11-1) will be installed
vorbis-tools (version 1.0.1-1.4) will be installed
xlibs (version 6.8.2-77) will be installed

```

---

### Post by luna6 on 2006-02-06
its easy as "sudo apt-get remove kubuntu-desktop" ....voila

---

### Post by Piggah on 2006-02-06
[QUOTE=luna6]its easy as "sudo apt-get remove kubuntu-desktop" ....voila[/QUOTE]

I don't think that removes all the packages it brought with it though. It only says the file it's going to remove is like 43kb. =\

And I didn't use synaptic, so I guess I'm doing it the hard way. 

Thanks

---

### Post by audax321 on 2006-02-06
Yup, you're going to have to do it the hard way. :(  I normally only install apps for testing through Synaptic because of the log. Kubuntu-desktop is just a metapackage, in other words, it installs all the packages needed for something (in this case, KDE)... so removing it will only remove the package list and not the packages themselves... althouhg it would be nice if there was an option to remove all packages associated with a metapackage besides one's being used by other packages (and just list the one's that the package manager can't remove).  Hmmm, I should post a request to the Synaptic bugzilla for it. :-k

---

### Post by Piggah on 2006-02-06
Meh, I have my /home on its own partition so a re-install would be quick and painless. 

Then again, I may just remove the KDE packages from my menus and such and keep KDE in case I feel like experimenting further. That should be relatively easy I imagine. I'm not short on space, so I can let KDE sit for a while. :P

---

### Post by NeoChaosX on 2006-02-06
**sudo aptitude remove kubuntu-desktop** should, in theory, get rid of it (Aptitude has the ability to remove dependencies that are no longer used). However, deleting the menu entries for KDE apps will also get rid of them in KDE as well. You may want to try the instructions in [this thread](http://www.ubuntuforums.org/showthread.php?t=59455) to hide them in GNOME.

---

### Post by Neo Ex on 2006-02-06
If you uninstall kdelibs-bin or kdelibs-data or kdelibs4c2 it will uninstall almost every KDE program. After uninstalled them, search in Synaptic for 'kde' and uninstall the other packages that have not uninstalled.

---

### Post by xfile087 on 2006-11-14
> **Piggah said:**
> I don't think that removes all the packages it brought with it though. It only says the file it's going to remove is like 43kb. =\

And I didn't use synaptic, so I guess I'm doing it the hard way. 

Thanks

I just installed KDE onto my Edgy Eft installation and tried KDE. I don't like it all that much so I wanted to remove it

> sudo apt-get remove kde

Worked perfectly, it removed all the packages except for konsole and konqueror which I removed myself.

---

### Post by finferflu on 2006-11-14
The best method is manually remove all you had installed (the reason why you can't just uninstall kubuntu-desktop is that you used apt-get instead of aptitude). Just follow this link:

[http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

Hope it helps...

---

### Post by imgp on 2007-02-01
I just get an opposit question: how can I remove gnome from KDE?
I'm using 
sudo apt-get install ubuntu-desktop

to install genome in my KUBUNTU when I find this topic

---

### Post by bodhi.zazen on 2007-02-01
Same problem, same solution:

Edgy: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

Dapper: [http://www.psychocats.net/ubuntu/purekdedapper](http://www.psychocats.net/ubuntu/purekdedapper)

---

### Post by imgp on 2007-02-03
SEE&#65281;

Thanks&#65374;&#65374;&#65374;

---

### Post by camarojones on 2007-09-20
> **finferflu said:**
> The best method is manually remove all you had installed (the reason why you can't just uninstall kubuntu-desktop is that you used apt-get instead of aptitude). Just follow this link:

[http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

Hope it helps...

And yet months later I still find myself coming back to this specific thread. LOL

As much as I love to play...I keep going back to Gnome...Guess I've gotten comfortable with it

And if I knew a way to shrink my XP partition, I would probably left it installed and kept playing...oh well...

---

### Post by gryzzly on 2007-12-17
Interesting thing that i used 
```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```
and still couldn't remove KDE with simple 
```
sudo aptitude remove kubuntu-desktop
```
as was recomended and promised everywhere :)
anyway found a solution [here]("http://www.psychocats.net/ubuntu/puregnome.php")

---

### Post by graphikeye on 2008-01-11
I'm in the same boat. I just installed kde 3.5 and kde 4 to try them out, but realised I like Gnome much more, and now I want to remove them...

---

### Post by breaking on 2008-01-21
> **Piggah said:**
> I don't think that removes all the packages it brought with it though. It only says the file it's going to remove is like 43kb. =\

And I didn't use synaptic, so I guess I'm doing it the hard way. 

Thanks

I got the same message when I used: [PHP]sudo aptitude remove kubuntu-desktop[/PHP]

I didn't like the way KDE changed the boot options, or the way it took the "shutdown" option away from the button.

---

### Post by yon2501 on 2008-01-21
> **finferflu said:**
> The best method is manually remove all you had installed (the reason why you can't just uninstall kubuntu-desktop is that you used apt-get instead of aptitude). Just follow this link:

[http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

Hope it helps...

how can i undo that, because i just wanted to remove the kde desktop manager not all my applications.

---

### Post by aysiu on 2008-01-21
> **yon2501 said:**
> how can i undo that, because i just wanted to remove the kde desktop manager not all my applications.
That isn't going to remove all your applications--just the KDE ones.

---

### Post by yon2501 on 2008-01-21
well it did remove allot of my programs such as nautalis, compiz fusion, amarok, ext ext and get this i can still boot into a kde desktop

---

### Post by aysiu on 2008-01-21
> **yon2501 said:**
> well it did remove allot of my programs such as nautalis, compiz fusion, amarok, ext ext and get this i can still boot into a kde desktop
Is it possible that you didn't copy the entire command? The last part of the command will not allow you to remove Nautilus: ```
&& sudo apt-get install ubuntu-desktop
``` But, yes, you didn't specify you needed AmaroK, which is a KDE application, so it would remove AmaroK.

Perhaps you can try this command instead: ```
sudo apt-get remove arts enscript kappfinder kate kcontrol kdebase kdebase-data kdelibs kdepasswd kdeprint kfind khelpcenter kicker klipper kmenuedit konqueror konqueror-nsplugins konsole kpager kpersonalizer ksmserver ksplash ksysguard ksysguardd ktip kwin poster psutils
```

---

### Post by yon2501 on 2008-01-21
well ive gotten gnome working again but i was only looking into this because i had kde on and i wanted it gone so i could put kde4 in which is having issues of its own, but gnome is working again so no worries

---

### Post by agibby5 on 2008-05-15
This worked for me: 

```
sudo apt-get remove kdelibs-data
```

Also, if you have problems removing kio-umountwrapper go here: [https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729](https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729)

> I don't know Debian/Ubuntu packaging system well (I'm just about to learn it;), so bear that in mind;)
But I fixed that on my Hardy installation by issuing the following commands as root:
mkdir -p /usr/share/apps/d3lphin/servicemenus/
touch /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib

Now you should be able to remove kio-umountwrapper. Afterwards you can delete /usr/share/apps/d3lphin and its contents.

---

