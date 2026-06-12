---
title: "Some questios about (small) annoying (!) problems..."
date: 2006-04-08
forum: General Help
---

### Post by sha_man on 2006-04-08
Hello, I just installed Ubuntu Breezy (in a very short time) succesfully and I'm dualbooting with win2000.
As most things work fine, I still have some things that annoys me very much ](*,) ](*,) ](*,) 
Here are my questions:

1. When opening a folder in a *maximized* window in Nautilus, where my mp3s are stored: I open a player, it comes to the foreground. Now I want to drag&drop from the maximized windows *behind* the player *into* the player (playlist). Normally in windows it would work, but in Ubuntu the window behind comes to the foregound and I can not see the player anymore :(  I'm forced to use windows, which are not maximized to drag&drop to a player :(

2. Most annoying of all: The motions of the *mouse*: The mouse does not have a fast, precise, **smooth** response like in windows 2000, but instead it jumps, the movement is really not smooth (!). Further, also the scrolling of a windows is stumbling, not smooth. Please help me fixing these annoyances.

3. If I'm in a big folder with many files i often just type the first letters (first 3, for ex.: ubu for ubuntu.txt) and in windows explorer it's selected (direct jump to the file). In Ubuntu, I can just type for ex. u and that's it, the first thing with an "u" is selected and if I type again "u" still the same file is selected, whereas there are others with beginning letter "u" which should then be selected as next.

4. In Firefox 1.5, which I installed using the wiki, I can not close tabs by clicking the *middle mouse button*. It worked with the default FF 1.0.x.

5. Also not understandable: I use a 1280x1024 resoluton with my ATI Radeon 9800XT card. I installed the driver using Method 1 from there: [http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)
However, I can just select a max. refreshing rate of  60 Hz. In Windows 2000 i  can select and use 75 Hz. How to do this in Ubuntu too?

6. How to do a search *in* Nautilus for a file in the actual folder?

I hope you can answer all my questions :) Then, Ubuntu will be THE OS for me:D 

Thanks

---

### Post by sands on 2006-04-08
#1.drag the mp3 file to the player in taskbar and then to the playlist
#2.I'm not sure..but try this system->prefs->mouse

---

### Post by xenmax on 2006-04-08
>  4. In Firefox 1.5, which I installed using the wiki, I can not close tabs by clicking the *middle mouse button*. It worked with the default FF 1.0.x.
I am using Firefox 1.5 and i can close tabs by middle mouse click - but i do not know if this is default behavior of firefox since i have installed an extension called "Tabbrowser Preferences"

---

### Post by sha_man on 2006-04-08
thanks, I finally managed to fix this middle mouse button in firefox problem with the help of this thread: [http://ubuntuforums.org/showthread.php?t=117891](http://ubuntuforums.org/showthread.php?t=117891)

---

### Post by sha_man on 2006-04-09
[QUOTE=sands]#1.drag the mp3 file to the player in taskbar and then to the playlist
[/QUOTE]
I can not do this, nothing happens:-k 

any solution to 3., 5. and 6. ?:confused:

---

### Post by Mustard on 2006-04-09
With regards to your resolutions issues try this thread...
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

With dragging and dropping your mp3's, when the player becomes visible, left click on the top left corner and choose 'On Top', then the player will always remain on top. (I just realised this won't work, in all situations.  Just ones in which you can still see the normal windows widgets. That covers quite a few of the players though. With xmms it has an always on top option.)

If I was searching for files I would use the search tool provided in the Places menu, or even use the terminal (along with the autocomplete TAB key function) to find specific files, or use the locate command in terminal. I'm not aware of any specific search functions in Nautilus.  Perhaps you could contact the developers of Nautilus and suggest it as a feature.

With regards to the middle mouse issue in Firefox, the default settings have changed in the latest version of Firefox 1.5.x, so you need to change your settings by typing about:config in the address bar and changing the relevant setting. The value you need to change is to make middlemouse.ContentLoadURL  false.  Use the filter to find the setting by typing 'middle' in the filter.

---

### Post by sands on 2006-04-09
yeah I forgot that option "On Top"
I use Alt+Space on apps and activate that option..
Use this for XMMS(or any player)..Its working..

---

### Post by disraeli on 2007-11-07
'3' bugs me as well!

---

### Post by paul.matthijsse on 2007-11-07
> **sha_man said:**
> Hello, I just installed Ubuntu BreezyHello, don't know about Breezy, using Feisty here. > **sha_man said:**
> 3. If I'm in a big folder with many files i often just type the first letters (first 3, for ex.: ubu for ubuntu.txt) and in windows explorer it's selected (direct jump to the file). In Ubuntu, I can just type for ex. u and that's it, the first thing with an "u" is selected and if I type again "u" still the same file is selected, whereas there are others with beginning letter "u" which should then be selected as next.In Feisty I can type 'u' (jumps to 1st filename that starts with that letter), then 'b' (selects 1st filename that starts with ub), then 'u' and it jumps to the first filename that starts with ubu... Doesn't this work in Breezy?

Cheers, Paul.

---

