---
title: "Where to find evolution mail icon for a launcher?"
date: 2010-07-24
forum: General Help
---

### Post by L a r r y on 2010-07-24
The short version:  I have created a launcher shortcut on my Desktop for Evolution Mail, and right now it uses the springboard icon.  I would like to use the icon that I see in the applications menu launcher for Evolution.  Where do I find this icon?

The longer version:

A few Ubuntu versions ago, I got rid of the Evolution Mail icon from the top panel, as there was no apparent way for me to set mail accounts to other than the standard ports.  I went with Thunderbird instead.

Well, while Thunderbird gives me a box to set the port number in, Evolution doesn't, but I can still specify my nonstandard port by placing a : and the port number after:  example.com:26 for a mail server at example.com om port 26.


**Now, I have put Evolution Mail to use, and have created a desktop launcher for it.**

For now I am using the default springboard icon.  I see the envelope icon in the applications menu for Evolution but I have no idea of the icon's address.

I am familiar with Windows XP, and it is easy to assign a program's icon to a new shortcut.  I have just added shortcut for example.exe.  I go to the shortcut's Properties and click on the icon, and immediately see the program or library file that contains the icon I am currently using, either as an embedded icon or set of icons, or I see an .ico file for that icon.

I can navigate to Program Files\example\ and see either example.exe with its embedded icons or example.ico.


**I created a new shortcut on my Ubuntu Desktop...**
... and was presented with a springboard icon.  I click on the icon in the creation process and am presented with a pile of generic icons, much the same as with Windows.

However, if I open the Properties and click on the icon, I end up looking at a listing in my Home directory.  This is regardless of where the current icon is located.

I looked in /usr/share/applications/evolution and saw icons folder, but it had no envelope for Evolution Mail.  All I see is icons dealing with the calendar, in anything from 16x16 to 48x48 and scalable.

---

### Post by SlidingHorn on 2010-07-24
try looking in /usr/share/icons/Humanity/apps -- there will be folders for the different sizes, and I know there are some Evolution icons in there.

Hope this helps! :)

---

### Post by cavalier911 on 2010-07-24
```
sudo find / -name evolution.svg 
```
/usr/share/icons/Humanity/apps/24/evolution.svg 
/usr/share/icons/Humanity/apps/48/evolution.svg

---

### Post by L a r r y on 2010-07-27
> **SlidingHorn said:**
> try looking in /usr/share/icons/Humanity/apps -- there will be folders for the different sizes, and I know there are some Evolution icons in there.

Hope this helps! :)

> **cavalier911 said:**
> ```
sudo find / -name evolution.svg 
```
/usr/share/icons/Humanity/apps/24/evolution.svg 
/usr/share/icons/Humanity/apps/48/evolution.svg

**Thanks folks!  You were both on-target.**  I thought for a moment there is no Evolution icon here, but it just took me awhile to apparently load everything in to see it.

Thank you!

---

### Post by orethrius on 2010-07-27
For future reference, this can also be found from the GUI.

1.  Open System > Preferences > Main Menu (some variants have System under the distro logo menu).
2.  Click "Internet" in the left pane, then "Evolution" in the right pane.
3.  Click "Properties", then click the program's icon in the resulting window.
4.  Note the full path to the file, substituting "/" between each directory "box".  In my case, I'm testing this with Pidgin, so it would be **/usr/share/icons/hicolor/48x48/apps/pidgin.png**.
5.  Close all those windows.  Now, right-click the desktop icon select "Properties", then click that springboard icon.
6.  If you already typed out the full icon path, you can just copy-paste it into the "Location:" dialog here and hit "Open".
7.  Close those windows and you're there! :)

Now, *an even shorter* UI method is to do this:
Right-click the Evolution menu item and click "Add this launcher to desktop".
One easy step! :)

---

### Post by AFD8766 on 2012-02-08
Thanks everyone, especially orethrius for the GUI version.

I like Ubuntu.  I use forums when I have an issue, often without success because the answers are non-GUI.  Terminal is powerful and I appreciate that.  Just the same, I will NOT run commands whose meaning is mysterious -- to risky because how would I undo it??

SO:  More GUI answers will mean more happy Ubuntu users, judging from my experience.

---

