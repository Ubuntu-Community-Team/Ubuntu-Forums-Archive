---
title: "Openoffice.org Menu and toolbars disappear!!"
date: 2006-04-08
forum: General Help
---

### Post by maxomai on 2006-04-08
I've got a rather bizarre problem here which I'm hoping is just a matter of some package accidentally crawling out of alpha and winding up in Ubuntu without proper vetting. 

I'm sitting in front of a friend's new installation of Ubuntu 5.10, which I supplemented with kubuntu-desktop at her request. This install is fresh as of this morning, but I've updated all the packages to their latest versions.

Whenever I use one of the OpenOffice.org applications (e.g. OOo writer) the toolbar icons disappear on opening. If I switch to another application, they re-appear in full, only to disappear again when I move my mouse over one of the widgets. The same happens with elements on the menu bar. 

The thing is, from the looks of it, this is most likely a problem in OOo's GUI redrawing logic. If this were Java I'd say they were mixing Swing and AWT components in the same frame. This tells me that this is most likely either an actual bug in OOo or a package error (that is, that OOo needs for correct behavior, but does not require for installation, some bits of java or another.) 

I'm going to install a JRE and see if that fixes it. In the meanwhile, if someone can shed light further light on this situation, it would be most appreciated.

---

### Post by shane.reid on 2006-04-08
I experienced this with Dapper as well - as soon as I installed kubuntu, logged into KDE, ran Openoffice from within KDE... it happened in Gnome.

I created a new user, Im certain there is a better solution, but I was in the process of creating a new user anyway.

That DID fix the problem, so it is clearly some config file in ~/

---

