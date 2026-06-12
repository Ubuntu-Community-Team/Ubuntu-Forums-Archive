---
title: "How to change the default media player?"
date: 2006-02-14
forum: General Help
---

### Post by matts0344 on 2006-02-14
I've searched  for the answer to this question on here and the web and I can't find an answer. I'm new to Linux/Ubuntu so the answer could be really obvious but how do I change it so when I click on a movie file it opens VLC instead of Totem? Totem can't play anything, it keeps giving me an error, but I can play things in VLC, but I need to right click on things and click 'Open with VLC'.

Is there a simple way to just change what media player opens up when I double click a file?

On a side note, I've tried installing the Win32 codecs for Totem, but it didn't change anything.

Thanks for any help you can give.

-Matt

---

### Post by angkor on 2006-02-14
Right click the file -> Properties -> Open with tab and select (or add) your preffered app. From now on all the media files in the same format should be opened with that application.

For your totem trouble, try installing totem-xine

sudo apt-get install totem-xine

---

### Post by ap9er on 2006-02-14
Right click on the file, properties and then go to 'open with' and select the player. It'll change the default from there.

---

### Post by matts0344 on 2006-02-14
Can't believe I didn't find that before.

Thank you!! :D

---

