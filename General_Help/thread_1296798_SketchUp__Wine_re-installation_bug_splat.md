---
title: "SketchUp / Wine re-installation bug splat"
date: 2009-10-21
forum: General Help
---

### Post by nikkkko on 2009-10-21
Hi,

A quick post for anyone pulling their hair out over a SketchUp / Wine installation. 

I recently re-installed both Wine and SketchUp only to find that SketchUp refused to run anymore. The "Start SketchUp" dialogue box would appear allowing me to choose a template but that lead only to repeated bug splats. Half a day later I discovered that I needed to delete the directory :

/user/share/wine

and let SketchUp re-install the Gecko html reader to resolve the problem.  

So, if you are re-installing and having trouble, this is what I did to make it work :

```
sudo apt-get remove --purge wine
```
Then delete the directorys /home/(user)/.wine and /user/share/wine
Then
```
sudo apt-get install wine
```
Check Wine is working by opening the Wine config menu found at Applications>Wine>Configure Wine.  If that's OK then install SketchUp, allowing it to download and install Gecko when asked.

Hope that helps someone.

Nick

---

