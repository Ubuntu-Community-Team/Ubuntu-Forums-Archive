---
title: "How can I get better window resizing in Ubuntu?"
date: 2010-07-17
forum: General Help
---

### Post by KonfuseKitty on 2010-07-17
I've seen this problem mentioned before but never a direct solution: when moving the mouse cursor to the edge of a window to resize it, the invisible resize bar seems to be only 1 pixel wide.  It's soooo annoying hunting for that one pixel to be able to accomplish this very simple task.  And no, I don't like pressing modifier keys or shortcuts for the other way of doing this.  I'm too used to easy window resizing on other OSs, there has got to be a better way here on Linux as well.

If there is no way to get an improvement with this in the Gnome desktop that Ubuntu provides, would a different desktop package be better?  Is there a plugin maybe, some kind of hack?  Something, anything!  Please help if you have the answer, I know I'm not the only one who would appreciate a solution to this.

---

### Post by stinkeye on 2010-07-17
You can either install a different metacity theme with thicker borders
[**_[COLOR="DarkRed"]Polaris[/COLOR]_**]("http://gnome-look.org/content/show.php/Polaris?content=93896")
or 
if your using compiz, install emerald theme manger and an [**_[COLOR="#8b0000"]emerald theme[/COLOR]_**]("http://gnome-look.org/index.php?xcontentmode=103"), and use as your window decorator.
Emerald theme manager allows you to easily change the border thickness.

---

### Post by KonfuseKitty on 2010-07-18
Thanks for responding, but I've downloaded emerald and uninstalled it.. I don't want to mess up the window theme I have.  If emerald just let me change the border, that would be sweet, but it seems it's either all or nothing.

Any other ideas?

---

### Post by digitalcitizenx on 2010-07-18
A quick [Google search]("http://www.google.com/#hl=en&source=hp&q=ubuntu+window+border+width&aq=2&aqi=g7&aql=&oq=ubuntu+window+border&gs_rfai=Czr4-_45DTOssldzKBMqPsMgKAAAAqgQFT9CLpFM&fp=6f146f4f6152193c") revealed:

[http://ubuntuforums.org/showthread.php?t=439329](http://ubuntuforums.org/showthread.php?t=439329)

---

### Post by KonfuseKitty on 2010-07-18
Doh!... it never occurred to me to search for "border", I kept searching for "resize"...  But seriously, thanks a lot, that's fixed it.  I'm enjoying my new 4 pixel borders! :D

I'll quote the text from the link above to help others doing similar searches here:

> It is relatively painless to change the dimensions of the surrounding border for themes. That said, you may end up with a gaudy looking heavy window, but I assume that you don't care about that.

To change border widths, simply open up the theme's Metacity XML file. For example, Human's theme is located in /usr/share/themes/Human/metacity-1/metacity-theme-1.xml

The stanza in question should be apparent:
  <distance name="left_width" value="5"/>
  <distance name="right_width" value="5"/>
  <distance name="bottom_height" value="5"/>

Try mucking with the values until you get something you are happy with. Unfortuanately, resolution dependency still plagues much of Gnome.
Run "gksudo gedit <PATH TO THEME FILE>" to edit the file, it needs root access.

---

### Post by digitalcitizenx on 2010-07-19
Just mark as solved and we're done.

---

