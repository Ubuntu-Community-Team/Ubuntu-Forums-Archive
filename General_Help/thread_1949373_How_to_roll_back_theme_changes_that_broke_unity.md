---
title: "How to roll back theme changes that broke unity?"
date: 2012-03-30
forum: General Help
---

### Post by Los Frijoles on 2012-03-30
So, I was messing with my theme the other day trying to install some GTK 3.x themes from gnome-look. I found one that looked cool and so I tried installing it and it didn't completely work (some things changed, others did not). So, I decided to switch back the the default Ambiance theme. However, some things didn't change back...namely the text colors in some windows. I have a problem with the Software Manager colors (I can't see the names of the software since it is white text on a white background), but the worst is the advanced settings window:
[IMG]http://i44.tinypic.com/2gxlok3.png[/IMG]
Another oddity is nautilus. The background should be white and the text dark:
[IMG]http://i44.tinypic.com/15s8owg.png[/IMG]
And also text in the default textbook which has a white background is also impossible to read.

The theme I tried to install was [Malys Unisex]("http://gnome-look.org/content/show.php/malys+-+uniSEX+?content=149602") and [Malys revoltgs]("http://gnome-look.org/content/show.php/malys+-+revoltGS?content=147845").

I am pretty much to the point of just re-installing the OS since even trying to use ppa-purge to get rid of the stuff installed from the revoltGS cause a ton of warnings about dependencies to come up (I aborted the removal...it said it was going to remove the mesa drivers and I spent way too long getting that to work on this computer). Does anyone know what I can do or is the only way to fix this just to re-install the OS?

I have been using I Ubuntu for a while now and I have never had a problem like this before and I was really surprised that it was giving me so much trouble about the theme (I had a really easy time themeing back with Gnome 2.x).

Also, Conky doesn't work properly either now and the login screen also is having the white text problem.

---

### Post by krustenBrot on 2012-03-30
Have you tried typing > unity --reset into a terminal? (CTRL + ALT + TAB - to open up a terminal)

---

### Post by Los Frijoles on 2012-03-30
I reset unity (and also restart the computer to just for good measure) and it still has the problems.

I think there may be a problem with the packages I have installed for Gnome 3. I noticed that installing one of the PPAs replaced many of my gnome 3 packages with ones that were more up to date, but were probably not in the main repository for a good reason. So, I now have a bunch of local packages more up to date than the ones in oneric-updates, but if I try to force them to downgrade to a version it tells me it has to uninstall pretty much everything, rather than downgrade them as well. I think if I were to downgrade every package back to oneric-updates the problem might be fixed...but I don't know how to do that.

---

### Post by stinkeye on 2012-03-30
Use **ppa-purge** to disable the PPA and revert to official packages.
If your not sure on how to use ppa-purge in the terminal, install **Y PPA Manager**.
```
sudo add-apt-repository ppa:webupd8team/y-ppa-manager
sudo apt-get update
sudo apt-get install y-ppa-manager
```
To run, start typing y-ppa-manager in the dash.("ppa" should bring it up)

Click on **Advanced** and then **Purge a PPA**

---

