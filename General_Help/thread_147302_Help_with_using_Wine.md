---
title: "Help with using Wine"
date: 2006-03-19
forum: General Help
---

### Post by chowyunpat on 2006-03-19
I installed wine through autmatics and I know a little bit of how to use it, I know how to make the wineconfg command and thats about it.

I had to reinstall Ubuntu and I remember when I used to click on a link for a windows.exe file the download window in Firefox would pop up and say Open with Wine (default) but now its not doing that, it says Open with file-roller default how do I change that and also how do I open a windows.exe file that I download to my home folder?

---

### Post by Sutekh on 2006-03-19
You can change the default by right-clicking on the .exe, choosing properties then choosing the open with tab.  I think you may need to add Wine to the list of available applications, the command works the same way as below.

To open a windows.exe from you home folder use this command
```
wine /home/<username>/windows.exe
```

---

### Post by chowyunpat on 2006-03-20
Thanks, Im glad to learn commands like, but also raises another question, which is how do I add Wine to the applications menu?

Also I remember wine installed the windows icons on the Ubuntu desktop programs that were linked in with the wine program, so all I had to was click on the say DVDshrink icon and Dvd shrink would open, I dont remember what I entered to make wine do that, but It did it during the installation of a windows.exe file.

Unforntunately I had to reinstall Ubuntu because of some other problem and I am frustrated because I dont remember how did the stuff above I just mentioned. I have spent about 2 hours trying to figure it out.  I have DVDShrink installed just no way of running other than using the winefile in /usr/bin/.  I would appreciate any help in this matter.

---

### Post by Sutekh on 2006-03-20
[QUOTE=chowyunpat]Thanks, Im glad to learn commands like, but also raises another question, which is how do I add Wine to the applications menu?
[/QUOTE]Unless someone can tell you now I will look into it later.  It shouldn't be too hard

[QUOTE=chowyunpat]
Also I remember wine installed the windows icons on the Ubuntu desktop programs that were linked in with the wine program, so all I had to was click on the say DVDshrink icon and Dvd shrink would open, I dont remember what I entered to make wine do that, but It did it during the installation of a windows.exe file.[/QUOTE]To do this just create a launcher on your desktop and use a similar command as the one in my last post to open the program.

For example; I have a icon in a menu that runs DVD Shrink using the command
```
wine "C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe"
```
You can use a similar command, checking that the directory is the same.

---

### Post by Sutekh on 2006-03-20
Well when you re-installed wine, did you run **winecfg**?

I already have the right-click options (I didn't add them)

This is what options I have when right-clicking
[ATTACH]7316[/ATTACH]

This is what I have when right-clicking -> properties -> open with
[ATTACH]7317[/ATTACH]

If you don't have wine listed then you should be able to add it using the command **wine**

---

### Post by chowyunpat on 2006-03-20
Thanks for the tips, and now that you mention it, there is an option in right click to use Wine, but I have another problem.  I entered in something wrong, this is what I entered in:

                         *wine /home/<username>/dvdshrinkl.exe*

and now every .exe click does open with Wine, but instead of opening say DVDdecrypter, it opens DVDshrink. lol  If it's not one thing it's another.  

I will say a positive thing here, the community is quick to respond.

---

### Post by Sutekh on 2006-03-20
[QUOTE=chowyunpat]I entered in something wrong, this is what I entered in:

                         *wine /home/<username>/dvdshrinkl.exe*

and now every .exe click does open with Wine, but instead of opening say DVDdecrypter, it opens DVDshrink.[/QUOTE]

I don't understand.  Where did you enter this?

---

### Post by chowyunpat on 2006-03-28
I right clicked on DVDshrink.exe and then clicked Open with other applications, and then I typed in wine/home/<username>/Dvdshrink.exe, but no worries I reinstalled Ubuntu.

---

