---
title: "codexs-video"
date: 2006-02-28
forum: General Help
---

### Post by morphineinduced on 2006-02-28
i just installed this and i cant get any of the codecs to run through totem..... is it that i need a different media player and i need all the codecs that are possible for the movies and prolly audio .. but if i could get some help here it would be most appreciated

---

### Post by Perfect Storm on 2006-02-28
Totem needs gstreamer libs. Easist way is using Automatix which can be found in my sig.
If you're looking for another mediaplayer I recommend mplayer and/or VLC.

---

### Post by ronmarley1 on 2006-02-28
Artificial Intelligence is right, Automatix will will give you all the codecs you need.  Here's the link: [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563).  Please read the whole thread on Automatix; some folks don't like it (I do).  The only difference between me and Artificial Intelligence is that I use Xine with the Totem front end for DVD playback.

---

### Post by morphineinduced on 2006-02-28
hey so i added this but now under applications it says Debian and has everything that i had in my system file in it plus some more stuff ...... so did i just do something wrong .... i mean is it suppost to look like this or did i do something wrong and if i did is there a way to fix this without pulling my hair out.............also i am running on debian so why do i have this ..... did i just install another debian kernel or something....also if this is how its suppost to be how the hell do i get rid of some of the doubles up there in the application bar.....

---

### Post by ronmarley1 on 2006-02-28
[QUOTE=morphineinduced]hey so i added this but now under applications it says Debian and has everything that i had in my system file in it plus some more stuff ...... so did i just do something wrong .... i mean is it suppost to look like this or did i do something wrong and if i did is there a way to fix this without pulling my hair out.............also i am running on debian so why do i have this ..... did i just install another debian kernel or something....also if this is how its suppost to be how the hell do i get rid of some of the doubles up there in the application bar.....[/QUOTE]

The Debian menu just shows you what's installed on your system.  I just does an inventory of what's installed and gives you another way to launch programs.  You didn't do anything wrong.  If you don't want it, just remove it using ```
sudo rm /etc/xdg/menus/debian-menu.menu
```  If you installed Automatix and then added the Debian menu, that's how you got it.  You did not install another kernal, just the Debian menu.  Use the code above to remove the Debian menu.  Here's a link to a thread that discusses it: [http://www.ubuntuforums.org/showthread.php?p=118184](http://www.ubuntuforums.org/showthread.php?p=118184)

---

### Post by morphineinduced on 2006-02-28
thanks but since i have this thread running can i ask u something i just downloaded ctorrent-1.3.4 and i want to install it into the directory with the archive manager , is this a bad idea or is it harder doing it this way ..... and honestly ..lol......iv been through this with other distros ...... iv i could figure out how to install programs i think i would be set and wouldnt really have anymore questions .... well for the moment...... is there a link or something that could help with this , ill keep looking around but if u know of one please send it my way .....thanks

---

### Post by ronmarley1 on 2006-02-28
Sorry morphine, I know nothing of ctorrent-1.3.4.  Have you tried BitTorrent that's installed with Ubuntu Breezy?  Good luck!

---

### Post by RAOF on 2006-02-28
1) The "Installing programs in Ubuntu" link in my sig has a section on installing-from-source.

2) **Please** use grammatical English where possible.  It's **much** easier to understand and read when a post is broken up into logical sentences, uses appropriate capitalisation, and has the occasional paragraph/line break.

If it's easy to read/understand, it's more likely to get replied to :)

---

### Post by morphineinduced on 2006-02-28
You can find it on SourceForge.net ..... and I will try to take my time and type out correctly....I have the Azeruos loaded and its working fine but I figured it would be easier to learn how to install this  its a tar.gz file ... I mean I tried that Firestarter firewall and I seem to not be able to get that to configure out of my own ignorance , is there any better or easier firewalls like KDE uses ....... I remember using this one for SuSE and it seemed to be just more nub friendly

---

### Post by RAOF on 2006-02-28
You probably don't need a firewall.  The default Ubuntu setup doesn't include any services that listen to the internet, so it's not possible for your Ubuntu box to be remotely expolited.

Thanks.  Even just the capitalisation of 'I' makes your posts that much easier to read :)

And installing from a .tar.gz file will be the same as installing from source - check out the link.

---

### Post by hugo491 on 2006-03-01
firestarter is the simplest firewall. It should be a simple install, then run firestarter in a terminal window, and a setup process will begin. The only issue I have had is that I have to save it into my session so that it boots up, and it asks for a password every time I boot. But aside that, its a nice program. Very secure.

---

### Post by morphineinduced on 2006-03-01
hey i just started up a new thread about Gush its a messenger server off of jabber client ...... i need some help with it if you all dont mind answering it there or in a email ......... i installed it into the directory but its not showing up on my desktop anywhere ..... i read the instructions on how to install but they said that i should be done now and I just dont see anything

---

