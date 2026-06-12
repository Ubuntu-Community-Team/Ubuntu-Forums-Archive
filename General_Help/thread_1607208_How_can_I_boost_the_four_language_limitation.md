---
title: "How can I boost the four language limitation?"
date: 2010-10-27
forum: General Help
---

### Post by ambeginnersearchinginfo on 2010-10-27
In the menue of Kubuntu 10.10  (live-CD) for selecting the keyboard layouts
appears a message saying that 
there is a limit of selecting maximum four keyboard layouts, 
if  I try to select a fifth one.
That is very little four people involved/dealing with languages or 
for computers shared by several people from different countries.
Does anybody knows anything about this limit and how to increase this number?
In windows you can select more than a dozen languages. Where is the problem?
Is it a problem of the KDE or of the linux kernel or what kind of problem is it?
An other user told that this problem exists also in other versions e.g. in Ubuntu.
Thank you.

---

### Post by james_xxx on 2010-10-27
I very much agree.

I also cannot figure out why in the world any dev would have somehow felt there was a need to put a limit on the number of keyboard layouts that can be selected from using this widget.

It has seemed to me that sometimes limitations like this were just put in place arbitrarily rather than for any kind of practical reason.

Honestly, most people using this system tray widget will want to configure it for exactly the number of keyboard layouts a person needs.

In my case, that number happens to be 5.

---

### Post by blueridgedog on 2010-10-27
You can set it on the fly with setxkbmap: 

```
sudo setxkbmap -model pc104 -layout us
```

Man setxkbmap for more information.

---

### Post by ambeginnersearchinginfo on 2010-10-28
Thank you for the answer.
I am new to Kubuntu and didn't do any programming yet here.
I have first to learn how to use such stuff.
There are two questions.
If I select in the KDE menu language number one, language number two, language number three and language number four and if I select with
sudo setxkbmap -model pc104 -layout us
language number five, do I have then a fifth language and I can select still the other four by clicking on the bottom of the screen on the language symbol?
I guess everytime when I want to change the language, I have to make up a command like that, very annoying for people changing often languages.
I guess the solution would be changing the limit.
But using your hint I searched and found further threads.
Thank you.

---

### Post by blueridgedog on 2010-10-28
You could make short scripts that did the switch for your and place them on the desktop, so a user could select the layout they wanted.

And example:

```
#!/bin/bash
gksudo setxkbmap -model pc104 -layout us
```

Save this to a file on the desktop called (for example) "uslayout", then make the file executable (bring up a terminal and chmod 755 /path/to/file, assumed to be /home/USER/Desktop/uslayout - or right click the file and change the option under properties)

From my search, it will not add a fifth language, but a way to change on the fly.

---

### Post by ambeginnersearchinginfo on 2010-10-29
Thank you very much for your answer.
Sorry I am a newbie here. 
I don't know how to get a file with a certain content on the destop.  
Maybe I can try to write with something like open office and save it and try to find out how to move it to the desktop.
But I am not sure if it is possible to write programs using open office, maybe open office is inserting control code for text layout.
Which editor I should use?
As I understand, you are saying that I can put an icon on the screen and by clicking on it, I get this specific input language this icon is for.
Then I could put any number of icons on the screen and could choose among any number of languages at any time by one click, is this right?
Then it would be nice to get these icons somewhere on the very bottom of the screen, e.g. left of the actual time usually display in the lower right corner or right of the KDE botton in the lower left corner.  Would this be possible?

When I am switching off and on the computer, I have to renew 
all tese commands. Is there any autoexec file or something like that which is executed automatically once everytime the system is started, where I could put these commands in and how they would look like in such an autoexec file?
Or do I have to get these files into the isofile in a certain manner in order to get them on the desktop or on the bottom bar automatically?

Thank you.

---

### Post by Vaphell on 2010-10-29
IIRC the 4 keyboard layout limit is an ungodly old legacy cruft of X protocols, it should have been redone long time ago but it wasn't.

open office includes a ton of formatting in the document by default. To program you need a plain text editor like gedit, kate or some kind of IDE - codeblocks, kdevelop, eclipse...

and the answers for your questions is yes.
you can initialize stuff, for example you can put the script in the startup applications (System > Prefs > Startup - or whatever its called in EN)
and as long you can do something with a command/script in terminal, you can create a launcher doing the same thing.

---

### Post by blueridgedog on 2010-10-29
> **ambeginnersearchinginfo said:**
> 
I don't know how to get a file with a certain content on the destop.  


Just open gedit and make the file you want and save it on the desktop.

> **ambeginnersearchinginfo said:**
> 
Then I could put any number of icons on the screen and could choose among any number of languages at any time by one click, is this right?

Yes, you can have any number of files on your desktop.

> **ambeginnersearchinginfo said:**
> 
Then it would be nice to get these icons somewhere on the very bottom of the screen, e.g. left of the actual time usually display in the lower right corner or right of the KDE botton in the lower left corner.  Would this be possible?


With KDE, you will need to place them in the desktop applet, as the KDE implementation uses a new interface now, but you should still be able to access them.

> **ambeginnersearchinginfo said:**
> When I am switching off and on the computer, I have to renew 
all tese commands.

No, once made they will stay there and you can run them by double clicking them.

> **ambeginnersearchinginfo said:**
> do I have to get these files into the isofile in a certain manner in order to get them on the desktop or on the bottom bar automatically?

I don't think they can get to the bottom bar, but as simple files that run a simple bash script, they will survive a reboot, exist on the desktop where you put them.  Creating a file that is nothing more than a set of commands is called creating a shell script or bash script in Linux and is the same as creating a *.bat file in windows.  If you create one, you will get the hang of it and the process will seem easier in practice than in theory.  The only hurdle is making the file executable.

---

### Post by ambeginnersearchinginfo on 2010-10-31
Thank you very much for these many informations.
In the meantime I changed to ubuntu, because the KDE got stuck in the loading
process of the language packages or turned black, so I had to switch the power off and on and I couldn't get the languages to run.  Now with Ubuntu 10.10 the languages work, except for the four language layouts limit.

I have to excuse me, because I was inaccurate. I am using a live system completely without any other memory. That means, everything I need and should be saved, has to be inserted into the isoimage. After I will have learned to program your suggestions, I have to learn how to get them into the isoimage.
To put it on the desktop, will be at least an option which allows the user to use languages as I understand it now. But the desktop is usually covered by the applications windows. And the idea to have them on the bar, which is never covered,  is very interesting. Maybe it is possable to find out, how to get them there. Maybe it is also possible to open another bar.
Maybe we collect some more information and propose to put an multilingual option into ubuntu, because many people are really angry about this limit!!!
I will try what you proposed and report the result then, what I will find out.
Thank you.

---

### Post by blueridgedog on 2010-10-31
> **ambeginnersearchinginfo said:**
> After I will have learned to program your suggestions, I have to learn how to get them into the isoimage.

You could put the bash scripts onto a USB drive, or put them in an ISO image with the tool remastersys.  It would require that you have access to a system to do an install on, then customize as you see fit, then but the custom setup to a DVD.

---

### Post by ambeginnersearchinginfo on 2010-11-02
Thank you very much for all the information!
It is very complicated and too complicated for the usual user, and it takes weeks to review and understand it. How can I make a suggestion to put a multilingual option into Ubuntu?
I looked at the 
[http://www.gnome.org/](http://www.gnome.org/)
and found an excellent documentation how to get icons on a bar or create another bar from within Gnome,
but yet don't understand how to change the isofile in order to have the language icons  already on the bar.
Further information I found on 
[http://remastersys.sourceforge.net/](http://remastersys.sourceforge.net/)
and on 
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
. Thank you.

---

### Post by ambeginnersearchinginfo on 2010-11-06
First of all thank you very much.
I just found a thread saying that it is even possible to put a launcher icon on a bar of the firefox webbrowser window using an extension/add-on called FoxRunner.

In the upper left corner I opened the leftmost pull-down menu and under first entry opens another pull-down menu having an entry called text editor. I think this is the gedit, and I would suggest to pu in brackets behind the name 'gedit', to let the people know, what it is.
I wrote the command 

sudo setxkbmap -model pc105 -layout us

in the text editor and 
found the deskop in the editor window, so I could save it directly to the desktop using the name US.
The language short cuts I found on the live cd at

usr/share/X11/xkb/symbols

Then I found the terminal link near the text editor link.
I opened the terminal and wrote 

sudo chmod 755 /home/ubuntu/Desktop/US

meaning that the name of the desktop file is Us.
By 'return' I executed the command and closed the terminal window by clickeng on
the left corner of the terminal window. I hope this is a correct method for quitting the terminal.
I right-clicked on the icon on the desktop of the file US and under properties >permisions
I found a check saying that the file is executable.
Left double clicking on the US icon leadsa to a pop-up with for options,
running and running in the terminal leads indeed to an input language change.
I dragged the icon on the upper top bar of gnome and a window opened to 
specify the properties of the launcher I am going to intall on the bar/panel.
I selected 'application' and I wrote 'US' in the input entry, and the mouse over the launcher icon on the panel invoked an mouse over message saying 'US'.
I could indeed change the  input language by a single click the laincher icon on the panel.

But the icons are all the same and not telling the language except for mouse over.

For the questions how to create an icon showing two letters for the language short cuts
and
for finding a terminal command for creating a launcher on the gnome panel or another method for getting the launchers in the isoimage in order to have them automatically 
on the panel each time my Ubuntu 10.10 cd live system is started.
I will open seperate threads, if you don't have a hint how to do it.

Even though it is only a workaround, I mark it as solved.
The task to fix the bug in the system remains!

Thank you very much for all the help!!!

I save here some further information found in the forum for further review/reference without any comments.

Hit  ALT+F2 and type gconf-editor
Then open apps-->nautilus-->desktop and uncheck the volumes_visible sentence.

Places -> Computer -> View -> Side Pane (F9)
In this Side Pane you can rename, delete, add, drag, drop the Folders.

Just edit ~/.config/user-dirs.dirs

gvfs-* commands, gvfs-set-attribute, gvfs-info

[FONT=Arial][SIZE=2] general customization Guide[/SIZE][/FONT]
[http://ubuntuforums.org/showthread.php?t=1545480](http://ubuntuforums.org/showthread.php?t=1545480)

( read again)
[http://ubuntuforums.org/showthread.php?t=1556349](http://ubuntuforums.org/showthread.php?t=1556349)

Hints to find documentation for terminal commands:

[http://ubuntuforums.org/showthread.php?t=1495316](http://ubuntuforums.org/showthread.php?t=1495316)

concerning notification area/ system tray:

sudo cp ~/Desktop/notification-area-applet  /usr/lib/gnome-panel/notification-area-applet

Some terminal commands are explained at
 
[http://www.linuxmanpages.com/](http://www.linuxmanpages.com/)

[http://www.linuxcommand.org/superman_pages.php](http://www.linuxcommand.org/superman_pages.php)
.
icons can be found in

/usr/share/pixmaps
or
 /usr/share/icons
.
zenity similar to gdialog  (Gtk+ dialog boxes from the command line)


[http://library.gnome.org/users/zenity/stable/zenity-notification-options.html.en](http://library.gnome.org/users/zenity/stable/zenity-notification-options.html.en)

[http://www.harald-hoyer.de/personal/blog/shell-gnome-notification-applet](http://www.harald-hoyer.de/personal/blog/shell-gnome-notification-applet)

UCK Ubuntu Customization Kit:

[http://uck.sourceforge.net/](http://uck.sourceforge.net/)


system files e.g.

/usr/share/gnome-background-properties

---

