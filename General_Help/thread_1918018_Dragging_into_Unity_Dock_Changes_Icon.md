---
title: "Dragging into Unity Dock Changes Icon"
date: 2012-01-31
forum: General Help
---

### Post by Quarkrad on 2012-01-31
Newbie running 11.10.  I have created a Desktop icon like I use to have in 10.10. The icon is used to launch BBC Radio 4 using the command **firefox [http://www.bbc.co.uk/iplayer/console/bbc_radio_fourfm](http://www.bbc.co.uk/iplayer/console/bbc_radio_fourfm)** - to make this more user friendly I change the firefox icon to a Radio 4 one.  (When I had 10.10 I had a number of icons in cario-dock for specific radio stations, each one with, not the firefox icon, but an icon for the particular radio station).  I've created the same launchers on my 11.10 desktop but when I drag them into the unity launcher the icon changes to the firefox icon.  Is there a way of keeping the icon you assign when it is on the desktop?

---

### Post by Quarkrad on 2012-02-01
bump

---

### Post by Quarkrad on 2012-02-01
I have found ways of changing the icons for launchers in the launcher bar but not so far for specific launchers.  I.e. it appears I can change the icon for firefox but not for different instances of firefox.  (I know there are ways to do this differently - have shortcuts on the firefox toolbar - but I set up various icons to specific web pages in cario-dock for my elderly in-laws when they had 10.10 and having given them 11.10 they would like the same, from me,  in their new 'vertical' launcher.  This must be easy to do in Unity - I know it can do it running gnome shell (done it) but it must also be easy in native unity.

---

### Post by Quarkrad on 2012-02-04
bump

---

### Post by Quarkrad on 2012-02-06
not sure how many 'bumps' one is allowed.

---

### Post by Quarkrad on 2012-02-06
Guess I need an admin person to do something here re this user - thought somebody had a answer for me, damn.

---

### Post by yetiman64 on 2012-02-06
I'm also on 11.10 and use a custom firefox launcher to open ubuntuforums index page. Have a look at the attachment and confirm for me if this is what you are trying to do. Note the second icon in the Unity launcher is a firefox launcher as well (heavily modified) with a custom icon.

If this is what you are after, its a bit involved but easy enough to get working. Let me know if this is what you are trying to achieve, if it is I can post back instructions/tips etc.

Don't let the launcher being on the bottom of the screen put you off, it is actually Unity I'm using :)

---

### Post by Quarkrad on 2012-02-06
Yes - I think this is exactly what I'm looking for.  In your Desktop Custom Launcher (10.10 speak) is the command you are using something like **firefox [http://ubuntuforums.org/](http://ubuntuforums.org/)**  ?   This is how far I got (but using a different web site) - my problem, that you seemed to have cracked, is how you got the ubuntu icon for the launcher rather than the default firefox one.

---

### Post by doobrie on 2012-02-06
An easy way to create a shortcut like this (including icon), is to use Chromium instead of Firefox.

If you open the page in Chromium, you can choose the "File | Create Application Shortcuts" menu option to create a shortcut on the desktop.  You can then drag this to the Unity bar and it will keep its icon.

I'm not sure if this is an options for you as it uses Chromium rather than Firefox, but it does work and its easy to do.

---

### Post by yetiman64 on 2012-02-06
Ok, first put the BBC radio4 icon in your home folder in a folder called .icons (the system will pick it up from here without an absolute path being required in the .desktop file - also you will be able to simply change the contents of my .desktop file below to suit your launchers needs). Note: don't name your icon or launcher the same as firefox's icon or launcher.

The Exec= line in my launcher is to open ubuntuforums in a new tab (if firefox is already running. If not running, it will open firefox and open ubuntuforums in it.)

> Exec=firefox -new-tab ubuntuforums.org/index.php is my actual command in use.

My launcher (is saved as ubuntuforums.desktop and is stored in ~/.local/share/applications):
```

[Desktop Entry]
Version=1.0
Name=Ubuntuforms.org in Firefox Web Browser tab.
Comment=Open Ubuntuforms.org main index page in Firefox.
GenericName=Ubuntuforms.org in Firefox Web Browser tab.
Exec=firefox -new-tab ubuntuforums.org/index.php
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=Ubuntuforums.png
Categories=GNOME;GTK;Network;WebBrowser;
StartupWMClass=Firefox
StartupNotify=true
NoDisplay=true
``` This is the firefox launcher from /usr/share/applications copied and stripped down to suit my needs. I have removed Mimetype= entry and added NoDisplay=true to stop my launcher integrating into the system as I store it in ~/.local/share/applications. It is from here I drag and drop it onto the Unity sidebar.

To use the above launcher copy and paste the contents to a new file on your desktop, alter the lines: "Name=",  "Comment=", "GenericName=", "Exec=", "Icon=" to suit your situation. Save as <your-launcher-name>.desktop and save it to /home/<user>/.local/share/applications. Drag and drop to the Unity launcher from there.

Hope this works out for you. Cheers.

---

### Post by Quarkrad on 2012-02-06
Thank you very much - that did it.  What size icon did you use?

---

### Post by yetiman64 on 2012-02-06
> **Quarkrad said:**
> Thank you very much - that did it.  What size icon did you use?
You're welcome Quarkrad, I used a screenshot crop of this sites logo downsized to 64x64 pixels. (saved it as a .png file)

Cheers, yetiman64 :)

---

### Post by Quarkrad on 2012-02-10
Afraid I've left this for a few days and i'm in a mess again.  These are the steps I am taking:

1.  Create 48x48 icon called bbc.png gkand store in ~/.icons

2.  In terminal run gksu gedit ~/.local/share/applications/bbc.desktop

3.  In gedit window that opens copy in this code 

[Desktop Entry]
Version=1.0
Name=bbc.co.uk in Firefox Web Browser tab.
Comment=Open [www.bbc.co.uk](www.bbc.co.uk) main index page in Firefox.
GenericName=bbc in Firefox Web Browser tab.
Exec=firefox -new-tab [www.bbc.co.uk](www.bbc.co.uk)
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=bbc.png
Categories=GNOME;GTK;Network;WebBrowser;
StartupWMClass=Firefox
StartupNotify=true
NoDisplay=true




4. Open ~/.local/share/applications  and drag bbc.desktop into launcher  (pic 1)  the launcher  has a ? mark as the icon

5. Open ~/.local/share/applications  and drag bbc.desktop onto desktop (pic 2)  the desktop file has a lock on it because the owner is root*

6. Run gksudp nautilus ad navigate to bbc.desktop and change ownership from root to 'myname' (pic3)

7. Right click on bbc.desktop choose Permissions and tick Allow executing file as program (pic 4)

8. Desktop now has icon (see pic 5)

9. Drag desktop file into launcher (pic6) – icon has ? mark

---

### Post by Quarkrad on 2012-02-10
this is pic6

---

### Post by yetiman64 on 2012-02-10
Firstly check the ownership and permissions of the .desktop fie in ~/.local/share/applications/ that you own it and its permissions are 755 (mine is set executable - this shows the icon in nautilus, I suspect it may affect the icon in the Unity bar also.) 

```
ls -l ~/.local/share/applications/bbc.desktop
``` in terminal or view Properties in Nautilus, can be checked there as well.

If that's alright next open the bbc.desktop launcher in gedit and check the name of the icon including file extension matches the icon in ~/.icons.

If all looks good try clearing the one on the Unity bar and then directly dragging back onto the Unity bar.

Footnote:[B]
I just spotted gksu in use,[/B] **don't use it or sudo in your home folder**,  it will mess with ownership to root if you save the file. You use the  command like ```
gedit ~/.local/share/applications/bbc.desktop
```  to edit files in your home folder. Looks like you may need to put the launcher back in your ownership. Good luck, yetiman64

Edit: just noted you reset the ownership, check the launcher is set executable and shows its icon in nautilus.

---

### Post by Quarkrad on 2012-02-10
I'm a newbie and appreciate your help - I need a bit of advice.  If I have a file in home/.local/share/applications called bbc.desktop do I enter the command  **sudo chmod 755 -R /~/.local/share/applications/bbc.desktop** in terminal?

---

### Post by yetiman64 on 2012-02-10
> **Quarkrad said:**
> I'm a newbie and appreciate your help - I need a bit of advice.  If I have a file in home/.local/share/applications called bbc.desktop do I enter the command  **sudo chmod 755 -R /~/.local/share/applications/bbc.desktop** in terminal?

In your home folder use ```
chmod 755 ~/.local/share/applications/bbc.desktop
``` you only raise privileges with sudo or gksu when root owns what you are altering. No need for the recursive switch (-R) as you are operating the command on a file (recursive is used on a folder to pass the changes down to all subfolders and files).

Edit: easy way to change the permissions is to right click bbc.desktop and go to ths Properties tab an set the tick box on the bottom, and check the top setting is "Read and Write" and the 2 lower ones are "Read Only". That's the gui method.

---

### Post by Quarkrad on 2012-02-10
This is fighting a bit.  I changed the permissions and the check in terminal shows this:

[B]mimi@mimi-VirtualBox:~$ ls -l ~/.local/share/applications/bbc.desktop
-rwxr-xr-x 1 mimi mimi 371 2012-02-10 13:17 /home/mimi/.local/share/applications/bbc.desktop
mimi@mimi-VirtualBox:~$[/B] 

which looks OK to me.  The folder bbc.desktop in ~/.local/share applications/ looks like pic 7.  With the .local/share/applications folder open I drag the file into the bottom of the launcher and I get pic 8 - the ? mark again.  pic 9 shows the content of my .icons folder.

---

### Post by Quarkrad on 2012-02-10
Though it might be something to do with using png file.  Changed to jpg and it's made no difference.  When I drag from the ...share/applications/ folder the icon changes just as it goes into the side launcher bar.

---

### Post by Quarkrad on 2012-02-10
Just logged off and back on, this time as Unity 2D - same thing.  Icon changes to ? mark.  This never was a problem in 10.xx

---

### Post by Quarkrad on 2012-02-10
Sorted - but I could not get it to work with your exact method.  I made a slight change - I took the icons from /.icons and put them in /usr/share/pixmaps and it worked!  I changed the icon address in the xxx.desktop file to point to .../pixmaps  and it liked it.  Many thanks for your help.

---

