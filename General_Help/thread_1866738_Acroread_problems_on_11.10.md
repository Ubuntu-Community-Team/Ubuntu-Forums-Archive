---
title: "Acroread problems on 11.10"
date: 2011-10-21
forum: General Help
---

### Post by jcobban on 2011-10-21
I am having problems viewing PDF files under Firefox on 11.10 with Unity, Gnome 3 etc.

Firstly ever since installing 11.4 I have had problems loading PDFs from the web.  The load just stops almost immediately after being initiated, and I have to refresh multiple times before I get the document loaded.

Since going to 11.10 and installing the latest fixes for Acroread I find that the scroll bars don't work.  The thin orange line that is all that Gnome 3 shows for the scroll bar position moves appropriately in response to mouse clicks in the scrollbar, but the image in the window does not move.  I can scroll the image up and down using the trackwheel, but not by clicking in the scrollbar.  I have no way of scrolling from side to side.

---

### Post by lovinglinux on 2011-10-22
Personally, I don't recommend Acroread. It is a 290 Mb download and Adobe is dropping support for Linux in future versions. 

You could use mozplugger plugin wit Evince Document Viewer. Personally, I prefer a Firefox add-on, like [gPDF](https://addons.mozilla.org/en-US/firefox/addon/14814/). 

BTW, Chrome browser doesn't require a PDF plugin and Mozilla is also working on a built-in PDF reader.

---

### Post by Lars Noodén on 2011-10-22
Acroread should be avoided.  Evince and Okular are better viewers.

---

### Post by andisl on 2011-10-24
I have the same problem. Scroll bar do not appear in Acroread at all. 

Unfortunately use of Acroread is determined by necessity to be able to fill forms, for instance, some European funding programs produces forms, which can be filled only by Acrobat reader. Therefore, there is need for solution not for recommendations not to use this program.

---

### Post by Lars Noodén on 2011-10-24
> **andisl said:**
> I have the same problem. Scroll bar do not appear in Acroread at all. 

Unfortunately use of Acroread is determined by necessity to be able to fill forms, for instance, some European funding programs produces forms, which can be filled only by Acrobat reader. Therefore, there is need for solution not for recommendations not to use this program.

It may take a while to percolate down to Ubuntu with Evince and Okular, but that problem is fixed now in principle:  The FSF has announced the completion of [GNU PDF](https://www.fsf.org/blogs/community/gnu-pdf-project-leaves-high-priority-projects-list-mission-complete)

---

### Post by Daan on 2011-10-25
> **Lars Noodén said:**
> Acroread should be avoided.  Evince and Okular are better viewers.

I don't quite agree with Evince or Okular being better than acroread. Have a look at the screenshots I have attached. Note how the spacing of letters in Evince and Okular is uneven and sloppy when compared to acroread. Also, acroread has many more features than Evince and Okular. I in particular like the "Previous view" button, it gets you back after following a link, zooming, etc.

I also have a problem in acroread with scrolling, as andisl has. With me, there are scroll bars, the new minimal Gnome/Ubuntu style scroll bars, but they don't work (sliding them doesn't scroll anything). I use my mouse wheel in stead.

I'll check out GNU PDF, sounds promising.

---

### Post by philinux on 2011-10-25
11.10 clean install and acroread scroll bar works fine here.

Not had one problem with it.

---

### Post by Daan on 2011-10-25
> **philinux said:**
> 11.10 clean install and acroread scroll bar works fine here.

Not had one problem with it.

Does that mean: "Re-installing Ubuntu solved the scrolling problem, and I had no problems since", or does it mean: "I installed Ubuntu 11.10 freshly as opposed to via a distribution upgrade and I never had any scrolling problems is the first place."?

Re-installing the operating system to fix a minor bug seems such an overkill...

More annoying is that I cannot change the acroread settings, clicking in the settings dialog doesn't change anything, and clicking "OK" has no effect.

---

### Post by philinux on 2011-10-25
> **Daan said:**
> Does that mean: "Re-installing Ubuntu solved the scrolling problem, and I had no problems since", or does it mean: "I installed Ubuntu 11.10 freshly as opposed to via a distribution upgrade and I never had any scrolling problems is the first place."?

Re-installing the operating system to fix a minor bug seems such an overkill...

More annoying is that I cannot change the acroread settings, clicking in the settings dialog doesn't change anything, and clicking "OK" has no effect.

It means I did a clean install of 11.10 and I never had any scrolling problems is the first place.

Also never had a problem in 11.04.

---

### Post by scholzilla on 2011-11-06
i think i have the same problem. Neither the acroread nor the gpdf add-ons to firefox solve it either. If I try to open a pdf, I get a blank page and the word "Done" written in the lower left of the browser. This pretty much happens every time, though I had intermittent luck with opening pdfs in the browser with acroread. I'm using firefox 3.6.23. If I use chromium, I get a green screen that says "missing plug-in" even after installation of gpdf or other pdf viewers. When I'm at work using Windows, I have no problem displaying the same pdfs in firefox, so this seems to be a problem with ubuntu or at least firefox and chromium for linux. This problem began with a recent distro of ubuntu, but I'm not sure which one.

---

### Post by anlag on 2011-12-07
I'd be interested as well if anyone has found a solution to this. I'm using 11.10, dist-upgraded from 11.04 which was a clean install, and the scroll bars in acroread don't work. Other than that, I have no issues with it. I don't use it in a browser, by the way, this is standalone use.

Evince is nice and light program, but on occasion it seems to display especially figures in a strange way. Thin black lines can appear grey and be difficult to see, whereas in acroread they are are black, and very clear. I have no idea of the reasons for that kind of discrepancy, but a significant number of scientific articles (for example) display better in acroread than in Evince which means that I'd quite like to have a fully functional version of that program too. Not quite so much that I will reinstall my entire system for that sole reason, but you get the idea...

On a side note, the GNU PDF developments look very promising. Perhaps when those fixes to libpoppler simmer down to Evince, also the rendering issues I mentioned above will no longer be an issue?

---

### Post by jcobban on 2011-12-07
> **Lars Noodén said:**
> Acroread should be avoided.  Evince and Okular are better viewers.

I have been begging the site that hosts the files that I am viewing to avoid the PDF format, since they are only using it for images.  In other words they are just wrapping a PDF envelope around a JPEG, forcing the loading of the enormous Acrobat viewer.  However their concern is providing functionality to end-users who are locked into the mindless support provided by IE for JPEGs.  I cannot find any plug-in for either Evince or Okular for Firefox.  The gPDF plug-in redirects to Google Docs.  I am not entirely comfortable with that implementation.

Is anybody trying to address the basic problem?

---

