---
title: "OpenOffice not working"
date: 2011-10-10
forum: General Help
---

### Post by canhoto on 2011-10-10
Hi.

My OpneOfficeOrg applicactions are not launching. I have the "OpenOffice.Org 3.2" screen, but afterwards nothing happens. I already removed all the suite (usng Synaptic), and reinstalled again, but without success.

Any help, please?

---

### Post by Haneef Mubarak on 2011-10-10
Why are you using OpenOffice? Use LibreOffice instead.

---

### Post by wildmanne39 on 2011-10-11
Hi, type openoffice in the terminal if it does not open it should give you errors in the terminal that tells you why.
Thank you

---

### Post by canhoto on 2011-10-11
> **Haneef Mubarak said:**
> Why are you using OpenOffice? Use LibreOffice instead.

I would (I have it on my mac) but is there a Libre Office for Power Pc Ubuntu? I thought not.

---

### Post by canhoto on 2011-10-11
> **wildmanne39 said:**
> Hi, type openoffice in the terminal if it does not open it should give you errors in the terminal that tells you why.
Thank you
I did that. Same behaviour (the Openoffice window loading, then nothing), and no error messages in terminal.

---

### Post by wildmanne39 on 2011-10-11
Hi, try it this way then please.
```
sudo apt-get --purge remove openoffice
```
This will remove all configuration files too, so you may want to save your documents to an external source.
Then restart your computer, I do not think this step is needed but better to be on the safe side.

The run this command please:
```
sudo apt-get install openoffice
```
Thank you

---

### Post by canhoto on 2011-10-11
> **wildmanne39 said:**
> Hi, try it this way then please.
```
sudo apt-get --purge remove openoffice
```This will remove all configuration files too, so you may want to save your documents to an external source.


I ran it (but with openoffice.org, because just openoffice didn't exist) and I had this:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgladeui-1-9 libgtk2.0-0-dbg libgsf-gnome-1-114 rhythmbox-dbg
  gstreamer0.10-plugins-base-dbg libatk1.0-dbg libgda-4.0-common
  libgsf-1-114-dbg libdevhelp-1-1 libgda3-common evince-dbg libpango1.0-0-dbg
  libgfortran3 libgnomevfs2-0-dbg libopts25 epiphany-browser-data
  libopts25-dev evolution-dbg autogen libwebkit-1.0-2-dbg eog-dbg libatspi-dbg
  anjuta-common libgdl-1-dbg libxft2-dbg exuberant-ctags python-cairo-dbg
  libfontconfig1-dbg intltool libtool libgoffice-dbg anjuta
  libgsf-gnome-1-114-dbg python-numpy devhelp-common anjuta-dbg
  gstreamer0.10-plugins-ugly-dbg libgda-4.0-4 gstreamer0.10-plugins-good-dbg
  libloudmouth1-0-dbg libxml2-dbg gnome-panel-dbg libgnomecanvas2-dbg
  libnss3-1d-dbg libblas3gf nautilus-dbg python-numpy-dbg libgtkhtml3.14-dbg
  liblapack3gf gnome-applets-dbg liboobs-1-4-dbg libgda3-bin libgda3-3
  librsvg2-dbg libnspr4-0d-dbg libgda3-3-dbg libgnomeui-0-dbg libglib2.0-0-dbg
  libgnome2-dbg libvala0 totem-dbg libltdl-dev libgail-gnome-dbg libgdl-1-3
  gimp-dbg python-gobject-dbg libgstreamer0.10-0-dbg python-gtk2-dbg
  libgdl-1-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  openoffice.org*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 45,1kB disk space will be freed.
Do you want to continue [Y/n]? 
 

I think if I go ahead it only removes 45,1 KB openoffice.org package.

So what should I do?

---

### Post by wildmanne39 on 2011-10-11
Hi, that is what it looks like to me too.

Are you sure you have not uninstalled it already? maybe that is why you can not open it. 
Thank you

---

### Post by canhoto on 2011-10-11
> **wildmanne39 said:**
> Hi, that is what it looks like to me too.

Are you sure you have not uninstalled it already? maybe that is why you can not open it. 
Thank you

It appears has installed, both in Synaptic and Ubuntu Software Center

---

### Post by wildmanne39 on 2011-10-11
Hi, in synaptic is the openoffice.org-core installed?

If it is then I am out of ideas.
Thank you

---

### Post by canhoto on 2011-10-11
> **wildmanne39 said:**
> Hi, in synaptic is the openoffice.org-core installed?

If it is then I am out of ideas.
Thank you

It was. I tried all with synaptic. complete removal of all that had openoffice.org on it, reinstalling the suite, removing the suite again, reinstalling only the writer, and even removing all and installing BrOffice. It was always the same: the loading screen appearde, then nothing. And I'm stuck: no office suite to work with (I think Libreoffice has no ppc package; Koffice doesn't seem good).

So, any help would be great. Or I will have to return to Mac OS (which, after years of use, was becoming my secondary OS in the last weaks). 

Is there a way of performing a clean installation of the system without loosing the data? Or something similar?

---

### Post by malachi1990 on 2011-10-11
Make sure it's not just opening up in the system tray (if you have it turned on). I had this happen to me a couple of times with OO and Rhythmbox. But your terminal output would also be very helpful here so we can see if it's a bug in OO or something else.

If that doesn't work, try Abiword. It's not a perfect drop in, but it's still competent.

---

### Post by canhoto on 2011-10-11
> **malachi1990 said:**
> Make sure it's not just opening up in the system tray (if you have it turned on).

And where's that?

---

### Post by wildmanne39 on 2011-10-11
Hi, a clean install you would need to back up your data or home partition with all your personal files in it to an external source so you can restore them after the install is complete.

Did you have openoffice working and it just quite or did it never work?

It is strange when you ran it from the terminal it did not show any output.
Thank you

---

### Post by canhoto on 2011-10-11
> **wildmanne39 said:**
> Hi, a clean install you would need to back up your data or home partition with all your personal files in it to an external source so you can restore them after the install is complete.

Did you have openoffice working and it just quite or did it never work?

It is strange when you ran it from the terminal it did not show any output.
Thank you

I had it running well. I think in the beginning I had, not the suite, but the isolated programs (Writer, Calc, etc.). Then I installed the suite. 
But I don't know if it has something to do with it. I also installed Lubuntu, but I see no relation neither (I've been using Gnome, anyway).

And it's true, the Terminal gives no output. It just launches the loading window. Then nothing. What's this system tray about?

---

### Post by wildmanne39 on 2011-10-11
Hi, it depends, if you are running 11.04, I guess the other person thought it might be opening to the launcher that is on the left side.

Also you should check and make sure it is not opening on another desktop, I have had that happen before.
Thank you

---

### Post by canhoto on 2011-10-12
No, nothing. And I'm astonished with the fact that I can't simply uninstall and make a clean installation of Openoffice.Org. It worked once!

I'm using AbiWord for the moment, but it would be better to have a full productivity suite. I'll miss iWork, MSOffice... but especially, I'll miss OpenOffice or LibreOffice (which I had been using on Macs, also). There is no LibreOffice package for PowerPC, is there?

---

### Post by wildmanne39 on 2011-10-12
Hi, I did a google search and here is a link that includes libreoffce for mac, I do not know anything about a mac, I have never seen one.
[http://www.libreoffice.org/download](http://www.libreoffice.org/download)
Thank you

---

