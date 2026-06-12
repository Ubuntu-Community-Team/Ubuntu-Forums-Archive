---
title: "creating menus in unity"
date: 2011-04-29
forum: General Help
---

### Post by donkyhotay on 2011-04-29
I just upgraded to 11.04 today and am a little bothered by the new unity system. Don't really like it but I understand why they're making the transition and I figure it'll be fine once I get it tweaked the way I want it, tweaking it is the big thing. I've read a number of different articles and posts here and while I've gotten things *mostly* the way I want there is one big thing that bothers me... lack of menus. For things I use all the time like firefox I'm fine with having the big icon right there (and I really like having that), for things I rarely use the "search applications" is fine as well. However there are some applications (mostly games) that I don't use often enough to want to have them clutter up the unity dock individually but I also don't want to have to "search" for them or click on a number of different catagories to get too (dock, applications, drop-down, catagory of application, application - that's way too many clicks). What I really want is a menu system where I can click on an icon in the unity dock and have it show up a list of different applications of that type and of course from there allow me to select the one I want. Been looking around and while I can find the old classic "main menu" option in the settings it doesn't affect unity in any way and the unity settings doesn't have any way of doing so. Found a few things that recommended creating custom desktop files but I'm lazy and went lots of effort getting the menus the way I wanted them in the old version and these settings would *mostly* work with only a little customisation so I'd prefer to do that. Any one know how to do this?

---

### Post by kherring7383 on 2011-04-29
I too am not to happy with Unity and its layout. Ever since I started using Ubuntu, I've always like the simplicity of pull down menus and launcher icons on the panel at the top. I'm kind of old school so it's hard for me to switch even though I too understand the direction Ubuntu is going, but if you still wish to use the classic desktop, simply logout and at the bottom of the screen there a pull-down menu that let's you select the classic Gnome desktop. Then if you like, open Login Screen under System  Administration and change the default session to classic. Now every time you login, you'll have the good old Gnome Desktop.

---

### Post by donkyhotay on 2011-04-29
I am aware of how to change back to the "classic" GUI however I don't really want to do that. I'd prefer to actually use unity but I want to customise it. Currently if I go to the unity dock I have to click on applications, then either search for what I want or click the dropdown to show a specific category. If I could just find a way to add icons to specific categories within the unity window I'd be content.

---

### Post by mc4man on 2011-04-29
Atm you could in a limited way, slightly mentioned - 
You can create a .desktop, for instance games.desktop
Then use quicklists to create entries for the r.click on launcher icon, each entry running a different game. *or anything

You can't tree the quicklists but they can contain as many entries as you'd like (to a point

The icon itself doesn't have to to anything or can run one app
You can add anything (a command) to a quicklist (ex. I can have a gnome-terminal launcher, one of the quicklists could open vlc - not that I'd want to, just to show you can do whatever you want

---

### Post by mc4man on 2011-04-29
As an example of what you can do - just made this install so don't have many apps around yet,  used 3 music players on hand
Created a barebones .desktop in ~/.local/share/applications, added the 3 quicklist entries (blue), then added the .desktop to launcher and a log out/in to set.

These can be considered menu launchers , (and only 2 clicks instead of the 3 in gnome-panel for those that are counting

The icon (l. click),  doesn't do anything atm because left the Exec= line blank, it could run a command (like the default you want for that group, available both from single l. click or the r.click > left click

> [Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=
Name=Music apps
Icon=/usr/share/icons/gnome/48x48/categories/applications-multimedia.png
[COLOR="Blue"]X-Ayatana-Desktop-Shortcuts=Audacious;Vlc;Totem;

[Audacious Shortcut Group]
Name=Audacious
Exec=env UBUNTU_MENUPROXY=0 audacious
TargetEnvironment=Unity

[Vlc Shortcut Group]
Name=Vlc
Exec=/usr/bin/vlc
TargetEnvironment=Unity

[Totem Shortcut Group]
Name=Totem
Exec=totem
TargetEnvironment=Unity[/COLOR]



---

### Post by awakephd on 2011-05-01
I've tried this multiple times, and can't get a quick list to save my life. I've tried copying this exact code, and others like it -- no dice. Yet there are quick lists in, e.g., the LibreOffice launcher icons.

Is anyone else having this sort of trouble??

---

### Post by wgarcia on 2011-05-01
To make the quicklist work I have found that the following are important:

1) make sure not to introduce any typing mistake in the code

2) open the file browser and navigate to the folder where you have your ".desktop" file, double click on it. If you have created the ".desktop" file yourself and you get something like "not authenticated" when clicking on it, make sure it has the right permissions. 

3) try the quicklist clicking on the icon that appears on the Unity launcher. 

4) if everything works click on "keep on launcher".

---

### Post by abumaia on 2011-05-01
You can save some clicks by right-clicking the applications lens, which will open a menu with the different categories.

---

### Post by awakephd on 2011-05-01
Okay, I discovered the problem. I was using the nautilus-home.desktop as a template, and it had the line OnlyShownIn=GNOME. Removing (or commenting out) this line solved the problem.

---

### Post by donkyhotay on 2011-05-04
Doing some research I found that what I really want/need is the ability to *easily* customize the lenses. Wasn't certain what to call them earlier (I thought of them as panel). This is really my only gripe/complaint with unity. The changes make sense on the whole but the thing I always liked about linux was the ease I had with customizing/tweaking it the way I liked to meet my needs. I've been looking online for a way to do this but haven't found anything yet (took me until now just to get the correct name for what I was looking, I'd been calling the lenses "panels"). Don't think there is a solution beyond coding something myself at this point but it seems so silly that people complain about the lack of customization of the dock section of it (which can be worked around with CCSM) and not with the lenses which are used to actually select applications.

---

### Post by Leed on 2011-05-04
Wow, that some cool instructions here... 

Now all we need is a good GUI to automate these things. Perhaps a program at start, later something integrated into unity. 

Of we could all make the code ourselves, but that wouldn't be productive... What's missing is something simple, like the way you can group Icons on an Iphone. After all most people want to spend their time in front of the PC doing things, not setting up an ultimate system.

---

### Post by donkyhotay on 2011-05-04
Customizing the icons/desktop files would be pretty easy. Lots of tutorials on it and there has to be a FOSS app floating around to automate it. Even if there isn't I think it'd be easy enough even I could manage to crank out some code. I'd do it too if I could find some documentation on how to modify/edit the lenses as well. If modifying lenses wasn't any harder then modifying the desktop files then a project for some sort of "unity config" program would be easy to do and I'd be with that I'd be willing to attempt ubuntu again. Problem is I can't find any documentation or tutorials or anything on how to customize or edit the lenses within unity and without that it's useless. This reminds me of when I had problems customizing the menus in gnome and it took me awhile to find "alacarte" to customize it. Eventually ubuntu got smart and just renamed that program to "main menu" and made it a default install. We just need the unity equivalent to "alacarte" and it really bothers me that unity shipped without something like that.

---

### Post by mc4man on 2011-05-04
I don't think you'll find any easy way to modify/extend the dash lenses in natty short of modding the source, though I'd think things will improve there in 11.10

Myself don't care that much, don't plan on using natty for too long and with 3 or 4 unity launcher menus can surpass anything gnome2 offered as far as menus I'm interested in having and using.
(in accessibility, customizing and speed of use unity is better

Atm the only limitation is quicklist's are only 1 level deep - the icon is the 'category', the quicklist is the menu. - 1 or 2 clicks to execution

Did file a bug on enabling subsets in quicklists, maybe I'll get an response sometime

---

