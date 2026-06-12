---
title: "New to KDE - How do I add themes?"
date: 2006-03-05
forum: General Help
---

### Post by m.musashi on 2006-03-05
I decided to play around with KDE but want to change the default kubuntu theme. I figured out how to change wallpaper and change color schemes but how do I add a new theme that I download from kde-look? I searched the forum a bit and found references to compiling themes. Is it actually a drawn out process to install new themes or is there a way to click or drop to install (ala gnome)?

Also, if I chose to keep gdm when installing kubuntu-desktop, is it possible to switch to kdm and then back if I don't like it?

Thanks.

---

### Post by arcanistherogue on 2006-03-05
what do you mean by themes?  There are different components to themes, there are:

-Icons
-Window Decorations
-Style

Icons is just iconsets.  I use the custom one from kde-look called "Crystal Clear".  If you have a proper .tar.bz2 or .tar.gz (most complete ones from KDE look are) you can just go to System Settings, appearance, Icons, then drag the tar.gz or .tar.bz2 archive into there, and it will install.  

I believe the same is so for window borders and styles, just select the appropriate category.

---

### Post by ComplexNumber on 2006-03-05
have a look in kde-look.org. you can change the icons, theme styles, colour schemes, and the theme manager themes (these allow you to change the whole look and feel with one press of the button - they include, icons, styles, colour schemes, wallpaper, and sometime much more). the theme manager themes can be installed via the theme manager themes and icons section in the kde control centre. some icon sets, most of the kwin themes and kde stylkes need to be compiled from source, and can sometimes be a real pain in the derrier. if only kde was as friendly and as usable as gnome :p.


>  Also, if I chose to keep gdm when installing kubuntu-desktop, is it possible to switch to kdm and then back if I don't like it? i imagine that kubuntu has kdm as default and ubunutu has gdm as default. i think it would be just a case of uninstalling kdm.

---

### Post by m.musashi on 2006-03-05
Okay, I figured out how to add an icon theme but what about the color of windows, title bars and menu or task bar?

By theme I guess I'm referring to a color scheme for the various parts of the desktop. In Gnome, for example, I found a brushed metal theme. When I choose it, the various application menu areas and boarders are brushed metal looking as are the panels. On kde-look.org there is a category for themes/styles. If I download one of those, where do I install it and select it? In system settings I see an option for style and window decorations but I don't see how to install a new one as I did for icons.

---

### Post by ren wins on 2006-03-05
i'd like to know the answer to this theme question, and possibly add "how do i change the splash screen?"

in response to the "can i switch back to gdm from kdm?"

yes, if you make the full switch to kubuntu, when you log in you can select to log into gnome without having to uninstall anything.  I ran ubuntu for about a month w/ KDE installed and i would switch btwn the 2 frequently

---

### Post by ComplexNumber on 2006-03-05
> but what about the color of windows, title bars and menu or task bar?they are determined by colour schemss. if you have a look at the colour schemes (.kcsrc files), they are just text files that can be easily modified. if you download and install a package from this site called dekorator, you can then install many dekorator themes which will allow you to tweak the window decorations to your hearts content. they're crap and not much good IMO. get colour schemes from kde-look.org. they go in /usr/share/apps/kdisplay

> 
By theme I guess I'm referring to a color scheme for the various parts of the desktop. theme = style + colour scheme. all the kde styles are rubbish except qtcurve because thats the only one that i've found to look near decent. there are very few of them.


> 
On kde-look.org there is a category for themes/styles. If I download one of those, where do I install it and select it?  sorry to beat the gnome drum again, but theming gnome is just sooooo much easier and more effective. i've always found it a real pain because there are lots of different (and illogical) locations for where everything shoud go. when you go to the control centre, you can install themes that way, but they only apply to you rather than being system wide for every user. if you want to install things sytem wide, store in the kwin, kstyles, tkdthememgr subdirectoriees in the /usr/share/apps directory.
the theme styles go in /usr/lib (for the style libraries. these are equivelent to gtk engines) and /usr/share/apps/kstyle directory.




> add "how do i change the splash screen?" go to the control centre.

---

### Post by ren wins on 2006-03-05
what do you mean 'control center'?

i dont know of any control center, unless you mean system settings? in which case you'll have to explain the process a bit more. :(

---

### Post by ComplexNumber on 2006-03-05
> what do you mean 'control center'? isn't it in you menu?  it should be. otherwise, go onto the command line and type: kcontrol.

---

### Post by m.musashi on 2006-03-05
I'm getting the impression that you don't so much install a theme (ala gnome) as you do tweek a lot of different settings. If that is the KDE way then fine.

However, [this](http://www.kde-look.org/content/show.php?content=153) is the most downloaded "theme" on kde-look.org and it looks like a kind of meta-theme in that it changes many things to look like osx. If I wanted to use this theme (I'm not advocating it, it's just the most popular and an example) after I download the tar.bz2 file what do I do? "Install" it somewhere or unpack it and put the various parts in various places? There must be a way to do this. Can anyone spell it out for a newbie who isn't getting it?

Thanks.

---

### Post by m.musashi on 2006-03-05
[QUOTE=ComplexNumber]isn't it in you menu?  it should be. otherwise, go onto the command line and type: kcontrol.[/QUOTE]
It's not in my menu list (at least I can't find it) but launching from a terminal worked. It looks similar to the System Settings app. Maybe it's a parallel app. It does have a "theme manager" though. Is that where I would add a downloaded tar.gz or tar.bz2?

---

### Post by ComplexNumber on 2006-03-05
> I'm getting the impression that you don't so much install a theme (ala gnome) as you do tweek a lot of different settings. If that is the KDE way then fine. yup, thats about it. there are about a million different locations where evrything goes. in gnome its so straighforward - icons go in /usr/.share/icons, and gtk & metacity themes  go in /usr/share/themes. changing a theme is just a case of tweaking the index.theme file in gnome where you can select which icons, which metacity and which gtk style goes with which theme. 


for the acqua theme, go into the acqua directory (after you've untarred it), fire up the command line and type in: ./install.sh.



> Is that where I would add a downloaded tar.gz or tar.bz2? yes, but ONLY for a theme manager theme. a theme manager theme is ALWAYS a .kth file. get them here:
[http://www.kde-look.org/index.php?xcontentmode=8]("http://www.kde-look.org/index.php?xcontentmode=8")
the tarball (eg b2z or tgz or gz) usually come with a kth file and all the rest. well, all the rest is contained within the kth file. the kth file just makes things simpler rather than manually installing all the rest in their respective directories (usually the /usr/share/apps/kthemmgr directory).

---

### Post by m.musashi on 2006-03-05
Thanks. This is starting to make sense.

---

### Post by ren wins on 2006-03-05
ah HA!
kcontrol is the way to go!
i got my splash-screen all set up! 
kcontrol is not in my menu (that i can see), i'll have to fix that

---

### Post by ComplexNumber on 2006-03-05
[quote=ren wins]ah HA!
kcontrol is the way to go!
i got my splash-screen all set up! 
kcontrol is not in my menu (that i can see), i'll have to fix that[/quote]
go into your commandline again and type 'kmenu' (kmenu is also in the control centre but i can't remember off hand where it is. the control centre is a total mess :p).
add the "control centre" to the menu. for the command, type in 'kcontrol'. then save.

---

### Post by ren wins on 2006-03-05
kmenu doesnt seem to exist on my computer?
```
laserwolf@violet:~$ kmenu&
[1] 12580
bash: kmenu: command not found

```

i've added things to the menu before tho, it shouldnt be a big deal

edit: aparently i have something called 'smeg' it worked
so did right clicking on the menu and selecting "menu edit"

---

### Post by ComplexNumber on 2006-03-05
[quote=ren wins]kmenu doesnt seem to exist on my computer?
```
laserwolf@violet:~$ kmenu&
[1] 12580
bash: kmenu: command not found

``` 
i've added things to the menu before tho, it shouldnt be a big deal[/quote]
go into the search tab of the control centre (its on the left hand side) and type in "menu". that should locate it.

---

### Post by m.musashi on 2006-03-06
Well, KDE fans, I won't say I'm a total convert yet but I have to say I'm liking this. Set up is indeed a pain but without too much effort I was able to tweek it and come up with something pretty cool. 

I attached a shot of what I've done so far. I like the transparent menu and found some nice icons.

Thanks for the help.

---

### Post by ComplexNumber on 2006-03-06
[quote=m.musashi]Well, KDE fans, I won't say I'm a total convert yet but I have to say I'm liking this. Set up is indeed a pain but without too much effort I was able to tweek it and come up with something pretty cool. 

I attached a shot of what I've done so far. I like the transparent menu and found some nice icons.

Thanks for the help.[/quote] looks good. i notice the umicon icons. they are a copy of gnome's gargantuan icons). the 3D wallpaper gels well with the rest.
you'll probably eventually  get bored of all the eye candy, as i did ;).

---

### Post by m.musashi on 2006-03-06
[QUOTE=ComplexNumber]looks good. i notice the umicon icons. they are a copy of gnome's gargantuan icons). the 3D wallpaper gels well with the rest.
you'll probably eventually  get bored of all the eye candy, as i did ;).[/QUOTE]
Probably. I'm still relatively new and tweaking it is a lot of how you learn it. Also, I work in a high school and I'm trying to turn some students on to linux. A nice flashy desktop seems to be more compelling than a discussion of how linux is better. I have one student who couldn't get windows to work on an old laptop but ubuntu is running fine. However, he has spent the last several days trying to make it look good rather than run well. I think the fact that linux works will attract them but having fun with it will hook them.

Thanks for the possitive comments. I'm not very color coordinated. I didn't know the icons were gnome but it might have said something like that on the site I found them. I still like gnome and will probably keep using it but this has been a fun diversion. Of course I should be doing grades right now.

---

### Post by tagg3rx on 2006-03-06
Theme-Manager Themes tend to be a little easier to get working
[http://www.kde-look.org/?xcontentmode=8](http://www.kde-look.org/?xcontentmode=8)

---

### Post by m.musashi on 2006-03-06
[QUOTE=tagg3rx]Theme-Manager Themes tend to be a little easier to get working
[http://www.kde-look.org/?xcontentmode=8](http://www.kde-look.org/?xcontentmode=8)[/QUOTE]
Yeah, I tried them first just as I had with gnome but my inability to make them work prompted this thread. It looks like I need to run a shell script rather than drop them in a theme manager. Unless you are refering to actual "theme-manager" themes. Someone else mentioned those but I haven't tried any yet.

---

### Post by ComplexNumber on 2006-03-06
**m.musashi**
they ARE theme manager themes :p. just extract the kth file from them and use the theme manager theme section in the control centre to install them. or you can add them as a system wide theme managaer theme by placing the kth file in /usr/share/kthememgr.

---

### Post by Jucato on 2006-03-06
@ren wins: I think ComplexNumber was actually refering to "kmenuedit", the KDE Menu Editor

Just for Info: KControl is KDE's official control center. System Settings is Kubuntu's specialized control center, but it doesn't include all options that KControl has.

Ok, some things about themes, styles, and looks:
1. Window Decorations - responsible for how window borders, titles and buttons (the minimize, maximize, close) look. Depending on what window decoration you installed, it can be found in different places (deKorator themes go to /home/username/.kde/share/apps/dekorator; IceWM themes go to /home/username/.kde/share/apps/kwin/icewm-themes)

2. Style - responsible for how widgets (tabs, progress bars, radio buttons, menu buttons, etc). I think (not absolutely sure) that styles are always installed as root/administrator. Also, you probably have to compile them. So they will be found in the directory where you compiled them, plus scattered in a few system directories as well (like /usr/share/apps/kstyle/themes). These are listed in KDE-Look as Theme/Style (nothing to do with Theme Manager).

3. Color schemes - need I explain what these do? :D Yes, they are basically just text files. You can tweak them manually, change them through the control center, or download a theme. System wide/root color themes are found in /usr/share/apps/kdisplay/color-schemes, while user color themes are found in /home/username/.kde/share/apps/kdisplay/color-schemes

4. Icons - need I say more? :D system icons  are in /usr/share/icons; user icons are in /home/username/.kde/share/icons

5. Background - otherwise known as wallpapers. Again, system wallpapers in /usr/share/wallpapers; your personal wallpapers in /home/username/.kde/share/wallpapers.

6. Fonts - still the same: system fonts: /usr/share/fonts; user fonts /home/username/.fonts (aha! this one was different! :D) NOTE: KDE has a very nice shortcut to access the system and user fonts. Type "fonts:/" in the Konqueror address bar (of course, minus the quotes)

Ok, that basically ends this Look'n'Feel 101. But there's a bit more. These things can be change/adjusted/customized individually through they're different modules in the control center (KControl or System Settings, whichever you prefer). OR you can change use the Theme Manager. this is where those .kth files come in. As the name suggests, the Theme Manager lets you organize your themes in one place. No need to choose the individual part from KControl. It lets you change the settings in one (or two) press of a button. It also lets you save your favorite settings for future use. This is perhaps the counterpart of the (detestably limited) themes found in Windows XP. kth files are in /home/username/.kde/share/apps/kthememanager/themes. system ones are found in /usr/share/apps/kthememanager. Oh and in case you are wondering. kth files are just G-zipped Tarballs (.tar.gz) that contain an .xml file, a wallpaper, and some other stuff. 

Hope this helps :D

---

### Post by m.musashi on 2006-03-07
Very nice. That really helped to explain a few things. Now I know what the heck widgets are. Thanks.

After I get a handle on all this, is there a 201 class somewhere or a nice, relatively complete but not overly technical manual or how to out there somewhere? I don't want to get all hung up on eye candy but this is fun and the skills do transfer somewhat to other tweaks later.

Thanks again.

---

