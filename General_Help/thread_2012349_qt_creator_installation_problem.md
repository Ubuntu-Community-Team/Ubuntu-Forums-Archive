---
title: "qt creator installation problem"
date: 2012-06-29
forum: General Help
---

### Post by solitario on 2012-06-29
hi folks.
i'm trying to go through the software center and I'm getting the following. Any idea what it means or how to resolve it?
muchos thanks.

> The following packages have unmet dependencies:

qt4-demos: Depends: libqt4-dbus (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
           Depends: libqt4-declarative (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
           Depends: libqt4-designer (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4 is to be installed
           Depends: libqt4-help (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4 is to be installed
           Depends: libqt4-network (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
           Depends: libqt4-opengl (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
           Depends: libqt4-script (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
           Depends: libqt4-scripttools (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4 is to be installed
           Depends: libqt4-sql (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
           Depends: libqt4-svg (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
           Depends: libqt4-test (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4 is to be installed
           Depends: libqt4-xml (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
           Depends: libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
           Depends: libqtcore4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
           Depends: libqtgui4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
qt4-dev-tools: Depends: libqt4-dbus (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
               Depends: libqt4-declarative (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
               Depends: libqt4-help (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4 is to be installed
               Depends: libqt4-xml (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
               Depends: libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
               Depends: libqtcore4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
               Depends: libqtgui4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
qtcreator: Depends: libqt4-help (>= 4:4.7.1) but 4:4.8.1-0ubuntu4 is to be installed
           Depends: libc6 (>= 2.15) but 2.15-0ubuntu10 is to be installed
           Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
           Depends: libqt4-declarative (>= 4:4.7.4) but 4:4.8.1-0ubuntu4.1 is to be installed
           Depends: libqt4-designer (>= 4:4.7.1) but 4:4.8.1-0ubuntu4 is to be installed
           Depends: libqt4-network (>= 4:4.7.1) but 4:4.8.1-0ubuntu4.1 is to be installed
           Depends: libqt4-script (>= 4:4.7.1) but 4:4.8.1-0ubuntu4.1 is to be installed
           Depends: libqt4-sql (>= 4:4.7.1) but 4:4.8.1-0ubuntu4.1 is to be installed
           Depends: libqt4-svg (>= 4:4.7.1) but 4:4.8.1-0ubuntu4.1 is to be installed
           Depends: libqt4-xml (>= 4:4.7.1) but 4:4.8.1-0ubuntu4.1 is to be installed
           Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.1 is to be installed
           Depends: libqtgui4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.1 is to be installed
           Depends: libstdc++6 (>= 4.4.0) but 4.6.3-1ubuntu5 is to be installed

---

### Post by Redblade20XX on 2012-06-29
Try installing through the terminal:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get install qtcreator
```

-Red

---

### Post by houseworkshy on 2012-06-29
I haven't tried this program but for the sake of bumping here are some ideas. First check to see which repositories are enabled, could be something to do with that especially if the qt creater is more modern than the qt stuff in the standard repositorties.  If you are in synaptic take a look at the settings in software sources while you are at it, you may need to enable backports. As a check you could also try putting in some other qt program which works and look at it's properties for version numbers.  Good that you mentioned which method of installing you used, apt-get should be the same as synaptic but debs and apt:urls ( which can also install repositories ) could be by anyone from anywhere so you need to be very sure of the source.  Try to avoid being tempted.  You could try forcing it but with that many dependancies unresolved I doubt it would work ( enter "man dpkg" in the terminal for details ).  It could even be a 32/64 bit thing. Not amazingly helpful I know but a bump.

---

### Post by solitario on 2012-06-29
hello folks.
thanks for the help.
going through terminal provided better results, but no dice. Something about "broken packages". No worries, I think I'm going to get a whole other laptop for learning QT and install whatever it needs.

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 qtcreator : Depends: libqt4-help (>= 4:4.7.1) but it is not going to be installed
             Depends: libqt4-designer (>= 4:4.7.1) but it is not going to be installed
             Recommends: qt4-demos but it is not going to be installed
             Recommends: qt4-dev-tools but it is not going to be installed
             Recommends: qt4-qmlviewer but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

