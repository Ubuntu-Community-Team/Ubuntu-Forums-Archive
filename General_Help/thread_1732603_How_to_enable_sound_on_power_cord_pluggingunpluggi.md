---
title: "How to enable sound on power cord plugging/unplugging"
date: 2011-04-18
forum: General Help
---

### Post by Zorgoth on 2011-04-18
I'm using natty and currently my laptop is in a position where the power cord is falling out a lot, and I don't always notice.  I'd like my computer to make a sound when the power cord goes in or out.  How can I do this?

---

### Post by Raybo on 2011-11-13
Well it's been awhile since you posted. In my search to accomplish the same as you wanted I found your post.  I solved the problem and thought I would post the solution for you or others.

Your sound theme files are in /usr/share/sounds.  If you are using the ubuntu theme you want to cd into /usr/share/sounds/ubuntu/stereo.  Find an .ogg sound that you want to use and then symlink it to a file named power-unplug.ogg.  Example:

sudo ln -s phone-outgoing-busy.ogg power-unplug.ogg

You could create your own sound file and copy to the directory, just name it appropriately.  You can test in your terminal using:
canberra-gtk-play -i power-unplug
Of course unplug your power to really test it.  Worked like a charm on my laptop.  This is the page that helped me get the solution:
[http://unix.stackexchange.com/questions/363/how-to-integrate-sound-with-desktop-events](http://unix.stackexchange.com/questions/363/how-to-integrate-sound-with-desktop-events)

---

