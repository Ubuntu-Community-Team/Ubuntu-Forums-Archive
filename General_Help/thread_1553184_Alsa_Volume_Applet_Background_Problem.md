---
title: "Alsa Volume Applet Background Problem"
date: 2010-08-14
forum: General Help
---

### Post by defensorfedei on 2010-08-14
Hi All. I recently upgraded from 9.04 to 10.04.  I had to uninstall Pulseaudio and rely on Alsa in order to get multichannel audio to work on my laptop.  However in 10.04 when I got rid of Pulse, I lost my volume control applet in the panel.  I have read that this is a problem for Alsa users since Karma came out.

I found a solution in the forums here: [http://ubuntuforums.org/showthread.php?p=8494502](http://ubuntuforums.org/showthread.php?p=8494502)  

I seem to have a problem that no one else is having.  I followed the instructions perfectly and it seems that the applet background doesn't like to play well with the image I have chosen for my gnome panel.  After some tinkering, I have observed that the volume-applet background is dependent on the "window" background color as chosen in the gtk theme preferences settings.

Edit:  I can find nothing in the code for volbar.py that would indicate it should use the gtk theme window background color as its background color.  This would leave me to believe that there is a default somewhere else which points to this preference.  If someone knew where the python applet defaults are, maybe that could be a starting point for a fix?

Here is a picture of what I mean. [http://s976.photobucket.com/albums/ae246/defensorfedei/?action=view&current=volume-applet.png](http://s976.photobucket.com/albums/ae246/defensorfedei/?action=view&current=volume-applet.png)

If someone knows how to change the scripting of volbar.py so that the background is clear or neutral or whatever, could they please clue me in.

Thanks in advance for your help.

---

### Post by DocteurX on 2010-08-15
You are not only one having this issue (I also got rid of pulse-audio using the thread you mentioned).

The buggy background color annoyed me and your post motivated me to look for a solution. I must mention that few hours ago I knew nothing about gtk... A just manage some "work around" and it seems to work! 

The problem appear to be a well known bug with egg.trayicon. Looking around on the web, people simply suggest to use gtk.StatusIcon instead... so that's what I did. Only, I didn't want to rewrite the rest of the code so I simply add the StatusIcon on top to the trayicon... not very nice.  

Simply replace your old volbar.py by this one. Btw, only the icon gets the "good" color, the slide bar still get the wrong one...

Enjoy anyway :)

One last thing, I changed the set of icons by a nicer one using an absolute file path. If it causes problem, uncomment line 116 and comment line 118.

---

### Post by defensorfedei on 2010-08-15
You truly are the Doctor!!!!!  Thanks man, that did the trick.  I did uncomment line 116, since I prefer the icons I am using.  Good deal though.  I was racking my brain going through the code of the original volbar.py file and was not sure what to do.  Figuring out that it was the egg.trayicon was genius.  My only complaint is that I lost the double-click xfce mixer. I noticed that there is some differences in the character spacing between your code and the original volbar.py.  I wonder if that has anything to do with it?  I will fiddle with it some and see if I can get it to work again.  Do you have the same problem I wonder?

 You should also post this on the original fix thread so other people can make use of this.

Thanks again.

---

### Post by DocteurX on 2010-08-16
You're right, I didn't thought about the "double-click xfce mixer"... I'll try to do something about it.

---

### Post by DocteurX on 2010-08-16
There you go! I also got the "scrolling" function back.

As you suggested, I'll post it on the original thread.

---

### Post by defensorfedei on 2010-08-17
Great Work!  Everything works as it should now.  Thanks again for taking the time to do this.  I think many people will benefit from this.

PS. In the new volbar.py, if you want to change back to the sound icon that belongs to your current theme, you need to uncomment line 102, and comment line 104.  It is no longer on line 116 and 118 in the new script.

---

