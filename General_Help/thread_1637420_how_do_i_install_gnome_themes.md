---
title: "how do i install gnome themes?"
date: 2010-12-04
forum: General Help
---

### Post by grcunning on 2010-12-04
I've become very frustrated trying to install new themes in Gnome.  I've tried several times to figure it out, using what little instructions are available on gnome-look.  And yes, I've used google.  I've read dozens of threads on ubuntu forums, usually discussing what .theme directory to use, and whether it is metacity or gtk, or in my home directory, or not...and usually relating to gutsy or hardy. 
I finally found about Gnome-Art, an application that supposedly does all this for you.  I opened it, found a cool icon theme and clicked install.  Of course this did nothing.  Well, it said that it was downloading something, then it opened the appearance properties dialog, but there weren't any icons there. I checked every tab, and tried to figure out where the heck these icons were.
I'm perfectly capable of following Instructions, I understand that i have to install icons, window borders,background, etc in a bunch of different directories.  I can handle that(although a mature operating system should have automated that process long ago).
I've managed with some trouble to sort of get a couple of themes installed before, although they look nothing like the screenshots on gnome-look, something always looks screwed up,like the title bar. I just need a solid set of instructions(using meerkat) on how to do this.  I'm tired of trying to follow someone's crappy instructions that don't work, and doing it again and again until my entire gui is screwed up and i have to start over.  Why doesn't gnome art work? and if it does, why are there no instructions on how to install the stuff when hitting the install button does nothing?
Please point me to some comprehensive instructions on how to install gnome themes(all components of gnome themes).  Sorry about my ramblings, I'm uber confused.  I just need some solid instructions.

---

### Post by uRock on 2010-12-04
This person has a few vids on youtube explaining how to install themes and do other customizations. [http://www.youtube.com/watch?v=gl-tmGfQrzs&feature=fvw](http://www.youtube.com/watch?v=gl-tmGfQrzs&feature=fvw)

---

### Post by juny20 on 2010-12-04
Maybe you already read this information...but if you haven't, it is very comprehensive on how to change almost everything. Hope it helps.

[https://help.ubuntu.com/community/UbuntuEyeCandy]("https://help.ubuntu.com/community/UbuntuEyeCandy")

---

### Post by rtimai on 2010-12-04
I sort of agree with grcunning. The suggestions here lead to irritating self-conscious flash video presentations. What I want is plain instructions in text without any effort to sound witty or clever. Just instructions, like in the O'Reilly books. Yes, I have them too, but not for Meerkat.

I've been trying to get the Gnome olive folders in Nautilus, yet keep the Ubuntu red Shutdown and Switch User icons in the upper toolbar. Changing either switches the other back. I have not been able to find any workaround for this behavior. As much as I LOVE Linux, it is definitely behind Windows in customizing Appearance. I don't care about the fancy compositing features, I just want to control my icons. Why is that so hard to do in Linux?

---

### Post by BigCityCat on 2010-12-04
To install themes in gnome. Download gtk2 themes, right click on download, extract here, sometimes twice, drag and drop into appearance window. Not where the backgrounds are but into the themes section of the appearance window. Sometimes it will ask if you want to apply the theme and sometimes it will just say successfully installed. If the later then hit customize and look for the new theme controls in controls. 

Sometimes it will say not a valid theme. Usually this indicates that you need to open the extracted folder and drag and drop the folder within that folder.

For emerald window decorations you will need compiz and emerald. You will also need fusion icon so you can select your window manager and your window decoration manager. All are in the repositories. Otherwise you can just stick with metacity window decorations.

---

### Post by BigCityCat on 2010-12-04
> **rtimai said:**
> I sort of agree with grcunning. The suggestions here lead to irritating self-conscious flash video presentations. What I want is plain instructions in text without any effort to sound witty or clever. Just instructions, like in the O'Reilly books. Yes, I have them too, but not for Meerkat.

I've been trying to get the Gnome olive folders in Nautilus, yet keep the Ubuntu red Shutdown and Switch User icons in the upper toolbar. Changing either switches the other back. I have not been able to find any workaround for this behavior. As much as I LOVE Linux, it is definitely behind Windows in customizing Appearance. I don't care about the fancy compositing features, I just want to control my icons. Why is that so hard to do in Linux?

Download icon themes in gnome-look.org. Right click download and Extract file, drag and drop into your appearance window, theme tab. New people usually talk up windows when they can't figure it out. Linux is far more customizable, you just have to learn how to use it.

---

### Post by uRock on 2010-12-04
> **rtimai said:**
> I sort of agree with grcunning. The suggestions here lead to irritating self-conscious flash video presentations. What I want is plain instructions in text without any effort to sound witty or clever. Just instructions, like in the O'Reilly books. Yes, I have them too, but not for Meerkat.
:D Thanks for saying thanks. The second link in this thread has lots of nice screen shots and documentation.

---

### Post by rtimai on 2010-12-04
I apologize, uRock, I'm a little irritable today I guess. It's really a trivial change, but the folders and toolbar icons apparently are tied together in the Desktop Theme. A Gnome theme results in the olive folders in Nautilus, but the green man Switch User icon and the lightswitch Shutdown icon. Most of the other themes result in the figure-arrow Switch User icon, and the red schematic Shutdown icons, but cause Nautilus folder to revert back to orange. IOW I want Gnome folders, Ubuntu panel icons, and I can't find a theme that sets these, or a workaround that won't mess up an upgrade. The suggested links here provide instructions for changing ready-made themes, not for hacking them to change individual components of a theme. 

Ubuntu Tweak doesn't provide a way either. 

It's really, really trivial, I know, maybe that's why it annoys me so much. A catastrophic error, and then I'm really humble. Heh heh. Thanks for your input.

---

### Post by grcunning on 2010-12-08
Listen bigcitycat, I'm not talking up windows at all. I have just been using windows because my parents used it,and my professors insist on everything being in Visual Studio Project format. I want more flexibility, and I am loving Linux. I just hate Ubuntu's default theme, and all my attempts to change it have only worked half way. 

ok, I downloaded the following theme:
[http://gnome-look.org/content/show.php/Dark+Ice?content=69886](http://gnome-look.org/content/show.php/Dark+Ice?content=69886)
it's called Dark Ice, looks cool to me.
I extracted it, and it contains
Folders:
gtk-2.0
metacity-1

Files:
panelbg_black.png
panelbg_white.png
startbutton.png

I tried dragging it to the themes tab of the appearance window(the main darkice directory), and got:
Installation for theme "Dark-Ice" failed. can't move directory over directory.

So I went into the directory and tried dragging both the gtk and metacity dirs over to the themes tab and got:
There was an error installing the selected file "gtk-2.0" does not appear to be a valid theme.(the same for metacity)

Why is it saying "file"? You told me do extract, and drag and drop into the appearance window. Do I drag the directory, or some file? Both the gtk and metacity dirs have lots of directories and lots of files.  What exactly am I supposed to drag and drop?
Gary

p.s I also copied it into my .themes directory, went to appearances and hit install and chose the directory, no luck

---

### Post by Frogs Hair on 2010-12-08
Some common theme file types you will have to extract include , zip , gzip and rar. The theme "Dark-Ice " is a tar.gz file and does not need to be extracted. I just installed Dark-Ice using drag and drop . you can see in the screen shot I opened the downloads folder and dragged it into Appearance Preferences. I hope this helps . Try this link I used it when I started. [http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by grcunning on 2010-12-08
OK frogs hair, I didn't realize that I shouldn't extract the file,but just drag the .tar.gz file into appearances. I did that, and it worked, but look at what I got:

[http://i898.photobucket.com/albums/ac189/grcunning/Screenshot-1.png](http://i898.photobucket.com/albums/ac189/grcunning/Screenshot-1.png)

as you can see, the menu bar has the dark ice color, but the title bar looks like crap, and if you look at the bottom panel, I can't even read the names of my open applications.
It's next to worthless, and I can't figure out how to fix the top and bottom panels and the title bar.
There is a panelbg_black.png and panelbg_white.png in the dark ice folder that the install clearly didn't use, so how do I install them manually?

---

### Post by Frogs Hair on 2010-12-08
Go into Appearance Preferences > customize window borders and make sure the correct window border is being used . As for the light color on the panels , that is the way the the theme shows for me too .:-s 
I won't be keeping this one YUK !

To install manually download and and extract the folder , drag the folder to your desktop from downloads . Open your home folder and press Ctrl  and H key to show your hidden folders. Scroll to the .themes folder , open and move the theme file from the desk top into the .themes folder . Now you will be able to use the theme from Appearance Preferences

To change the way the fonts appear on the panel try customize> icons and find a set with the correct colors , you should have 5 different default sets.

---

