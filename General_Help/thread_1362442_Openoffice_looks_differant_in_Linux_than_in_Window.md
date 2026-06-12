---
title: "Openoffice looks differant in Linux than in Windows"
date: 2009-12-23
forum: General Help
---

### Post by sofasurfer on 2009-12-23
I downloaded OpenOffice.org for windows and when installed and run it displays a screen that has all of the differant OpenOffice programs such as Calc, Writer, Spreadsheet, etc, etc. You just click on the one you want to use.

For Ubuntu, you download OpenOffice and the best you get is 4 differant OpenOffice titles in the applications menu.

I want the one like windows has. Is it available or is the Windows version just differant than the Ubuntu version?

---

### Post by prshah on 2009-12-23
> **sofasurfer said:**
> it displays a screen that has all of the differant OpenOffice programs such as Calc, Writer, Spreadsheet, 

Press Alt+F2 and give the command```
/usr/bin/ooffice
``` You can create a custom launcher for this command if you like. Please post back if you want more instructions on how to do this.

---

### Post by SecretCode on 2009-12-23
What's bundled into Ubuntu by default isn't the whole of OO.o - for example, Base isn't included.

If you run ```
sudo aptitude install openoffice.org
``` you'll get the whole package - but still not a menu item for the whole package. However, as well as prshah's suggestion, if you open one of the apps, like "OpenOffice.org Word Processor" and close the child window without closing the main window, e.g. with Ctrl-F4, you do still get the main package window listing all the applications.

---

### Post by 3rdalbum on 2009-12-23
> **sofasurfer said:**
> I downloaded OpenOffice.org for windows and when installed and run it displays a screen that has all of the differant OpenOffice programs such as Calc, Writer, Spreadsheet, etc, etc. You just click on the one you want to use.

For Ubuntu, you download OpenOffice and the best you get is 4 differant OpenOffice titles in the applications menu.

I want the one like windows has. Is it available or is the Windows version just differant than the Ubuntu version?

It's just the way the program launchers are created.

On Ubuntu, the "main program" does not have a launcher for it. It still exists, though - just create a launcher for "openoffice.org" or type it into the command-line to run it.

---

### Post by sofasurfer on 2009-12-23
prshah...
That did it. Thanks.
I then found that all I need to do is type "openoffice".
But this does not work in a terminal. Whats the differance between a terminal and "alt+f2"?
Thanks again.

---

### Post by oakgrove on 2009-12-23
> **sofasurfer said:**
> prshah...
That did it. Thanks.
I then found that all I need to do is type "openoffice".
But this does not work in a terminal. Whats the differance between a terminal and "alt+f2"?
Thanks again.

alt+f2 uses a program called gnome-open that tries to use your default application for whatever file you are trying to open.  For example, if you type [http://www.google.com](http://www.google.com) into the alt+f2 run box, it will open that web page in your default browser.  If you just type . into the box, it will open nautilus in your home directory since . means "current directory".  If you have a document in your home directory called file.txt and  you type file.txt into the run box, the file will be opened in your default text editor provided that file isn't marked executable.  Obviously the terminal doesn't use this feature unless you preface any document with gnome-open, e.g. $ gnome-open example.pdf would open example.pdf in evince.

---

### Post by prshah on 2009-12-23
> **sofasurfer said:**
> I need to do is type "openoffice".
But this does not work in a terminal.

No difference. It should work in the terminal as well. Please check your spelling. Or in the terminal try ```
openoffice.org
```

If you are trying to create a launcher, then it is good practice to use the entire path. You can find that with the "which" command.

It's weird, but on my laptop the command is "openoffice", but on the desktop the command is "openoffice.org". Go figure. Probably something to do with custom PPAs.

 Or post back (from the terminal) the output of ```
which openoffice
which openoffice.org
```

---

### Post by sofasurfer on 2009-12-24
Thamk you all.
Whats weird...Apparently I have never tries to open OpenOffice in a terminal before. I assumed I did but I guess I have only opened it from the menu. What a simple mistake.

And thanks for the "which" command. That is something I have needed for a long time.

---

### Post by sofasurfer on 2009-12-24
I just edited one of the main menu entries by making it open with /usr/bin/openoffice.org.
Then I noticed that there is a non-checked openoffice.org item in the main menu edit window. It uses ooffice %U to execute the file. I guess that teaches me to be sure I know what is available to me in the system>pref>main-menu edit window.

---

