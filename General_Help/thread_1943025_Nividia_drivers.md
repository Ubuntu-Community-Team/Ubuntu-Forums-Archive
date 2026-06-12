---
title: "Nividia drivers"
date: 2012-03-18
forum: General Help
---

### Post by Spewed on 2012-03-18
I installed the Nvidia drivers for my GTX 570 graphics card, does this mean that I have Directx 9.0 or 11? Or am I still using Open GL and need to install Directx? 

I installed the drivings using the additional drivers option in Ubuntu.

---

### Post by HiImTye on 2012-03-18
Direct3D is a windows only specification, Ubuntu (or rather, Linux in general) uses OpenGL primarily. if you are using Direct3D in WINE, for instance, it is an OpenGL implementation of Direct3D

note: DirectX is just a re-branding of Direct3D

---

### Post by Spewed on 2012-03-18
> **HiImTye said:**
> Direct3D is a windows only specification, Ubuntu (or rather, Linux in general) uses OpenGL primarily. if you are using Direct3D in WINE, for instance, it is an OpenGL implementation of Direct3D

note: DirectX is just a re-branding of Direct3D


Oh okay, thank you! That explains why call of duty mw3 was so painfully laggy. I'll install it direct3d via wine then, and that MAY solve it. If not, since I only game casually it wont be a problem to keep my gaming on Windows.

---

### Post by 3rdalbum on 2012-03-18
> **Spewed said:**
> Oh okay, thank you! That explains why call of duty mw3 was so painfully laggy. I'll install it direct3d via wine then, and that MAY solve it. If not, since I only game casually it wont be a problem to keep my gaming on Windows.

Don't install DirectX, it will break Wine.

Wine already includes a DirectX they have written as a compatibility library. If you are getting lagginess, it is probably not fixable. The game just may not run on Wine very well.

---

### Post by HiImTye on 2012-03-18
youll get mixed results installing Direct3D in wine, some games benefit from it and others dont. make sure to install winetricks and try it out in a clean prefix so as to not break your other apps. the general rule of thumb is to install each game in its' own prefix so that your required configurations dont clash with your other games
to install winetricks use:
```
sudo apt-get install winetricks
```
and to install directx use:
```
env WINEPREFIX=/home/<your username>/.wine/<Prefix name> winetricks d3dx9
```
will install the latest DirectX9

for instance, I have a game called Trine2 which requires DirectX libraries to run properly. it has its own prefix so I used the following:
```
env WINEPREFIX=/home/tye/.wine/Trine2/ winetricks d3dx9
```
it then grabbed it and set up the library override

best thing to do is always check [WineHQ]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true") to see if your game runs with or without extra configuration

---

### Post by 3Miro on 2012-03-18
Many games work under wine just fine, many game do not work at all. Google "You Game + winehq" to get results about people that have trued to get your game working under wine.

I am playing Starcraft II, Civilization IV and V, Dragons Age I and II, Elder Scrolls Oblivion and Skyrim as well as Heroes of Might and Magic V. All of them under wine and all work great. However, Heroes of Might and Magic VI does not work. It is a hit and miss thing, read winehq for details on how to set things up.

---

