---
title: "Toggle between button and text-based location bar Nautilus - Lucid"
date: 2010-05-02
forum: General Help
---

### Post by Donnw on 2010-05-02
How do you toggle between the button and text-based location bar in Nautilus in Lucid  . I can only get Nautilus to show the directory path as  buttons and not as as text based in the form of /home/Desktop.Previously there was a button to toggle between them.

---

### Post by Elfy on 2010-05-02
Ctrl+L I think

---

### Post by Ginsu543 on 2010-05-02
Yup, Ctrl+L.

---

### Post by akakingess on 2010-05-02
Okay, so CTRL +L will change it to text, is there a different shortcut to go back to buttons, or do you just have to close and reopen Nautilus?

---

### Post by Ginsu543 on 2010-05-02
Just hit ESC. That will toggle it back to buttons.

---

### Post by Elfy on 2010-05-02
[s]does not Ctrl+L toggle it back?[/s]

oh ok then :)

---

### Post by Ginsu543 on 2010-05-02
No, it doesn't. But ESC works.

---

### Post by akakingess on 2010-05-02
It's not doing it on my system, I just close it and reopen and it's back to buttons, but hitting CTRL +L again doesn't seem to take it 'back' from text to buttons.

Thanks Ginsu543, that's what I was looking for!

---

### Post by Donnw on 2010-05-02
Thanks, I will try that.

---

### Post by aftabnaveed on 2010-05-03
I guess, they should have not changed the way it was, there was a little button to the very left of the location bar, which would toggle between text and icons. 

Please let me know if that feature is still there ?

Thanks

---

### Post by gadolinio on 2010-05-03
> **aftabnaveed said:**
> I guess, they should have not changed the way it was, there was a little button to the very left of the location bar, which would toggle between text and icons. 


+1.
That button is very useful. Another interesting feature it has is that once you toggle the text mode, it remains that way until you decide to go back to the button mode; there's no need to press Ctrl+L every time you open a new window.

---

### Post by Mr.Goose on 2010-05-03
+1 It seems a totally a daft decision to remove the button. :confused: @ Developers -** please, please can we have it back?**

Some of you folks may be interested in a (closed as "solved") thread in the *"[Lucid Lynx Testing and Discussion]("http://ubuntuforums.org/showthread.php?t=1430803")"* forum on this subject...

[LIST][http://ubuntuforums.org/showthread.php?t=1430803](http://ubuntuforums.org/showthread.php?t=1430803)[/LIST]

My situation is particularly bizarre. I was in "text mode" when I upgraded from Karmic to Lucid. I am now **stuck** in text mode. *Ctrl+L* highlights the text and *ESC* toggles a trailing slash at the end of the path, on & off. I cannot actually get back to button mode at all!

Seems the only solution at the moment for those who want the toggle button back is to download the Nautilus source from GIT and compile it yourself. Hmmm...

Best wishes, G.

---

### Post by gadolinio on 2010-05-03
> **Mr.Goose said:**
> +1 It seems a totally a daft decision to remove the button. :confused: @ Developers -** please, please can we have it back?**

Some of you folks may be interested in a (closed as "solved") thread in the *"[Lucid Lynx Testing and Discussion]("http://ubuntuforums.org/showthread.php?t=1430803")"* forum on this subject...

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=1430803](http://ubuntuforums.org/showthread.php?t=1430803)
[/LIST]

My situation is particularly bizarre. I was in "text mode" when I upgraded from Karmic to Lucid. I am now **stuck** in text mode. *Ctrl+L* highlights the text and *ESC* toggles a trailing slash at the end of the path, on & off. I cannot actually get back to button mode at all!

Seems the only solution at the moment for those who want the toggle button back is to download the Nautilus source from GIT and compile it yourself. Hmmm...

Best wishes, G.

There's a way to at least get the functionality back, using gconftool. You have to create a new empty file, and open it with gedit text editor. Make the file's content like this:

```

#!/bin/bash

SHOW=$(gconftool-2 --get /apps/nautilus/preferences/always_use_location_entry)
if [ $SHOW = "true" ] ; then
   gconftool-2 --set /apps/nautilus/preferences/always_use_location_entry --type=bool false
else
   gconftool-2 --set /apps/nautilus/preferences/always_use_location_entry --type=bool true
fi

```

  Save it. And finally create a launcher to that script. The launcher's command should be:
sh /PATH_TO_SCRIPT/FILENAME. And in "type", choose "Application in terminal".
That way, the launcher becomes pretty much the same as that button we miss XD
but it will be in the panel instead of being by the location bar. I guess it's something...

---

### Post by aftabnaveed on 2010-05-04
[@gadolinio]("http://ubuntuforums.org/member.php?u=910735")
in Lucid Lynx it won't remember it, I mean you have to press Ctrl + L every time the window is reloaded or re painted.

---

### Post by bladze_dcotl on 2010-05-04
Ok thanks to aysiu I have found the solution to my problem and it may help some others as well.  They posted a way to permanently revert the "bread crumbs" back the the text bar using gconf-edit.  

>  Re: Has the text-based location bar been removed from Nautilus?
You can change it back to text-only.

Press Alt-F2 and paste in
Code:

gconf-editor

Then go to Apps > Nautilus > Preferences and check always_use_location_entry
Attached Thumbnails
Click image for larger version Name: locationbartext1.png Views: 14 Size: 82.1 KB ID: 153854   Click image for larger version Name: locationbartext2.png Views: 17 Size: 119.7 KB ID: 153855  


This may not help those who want to switch back and forth, but for me (I personally don't like the look and feel of the breadcrumbs at all) works out nicely.

My thanks go to aysiu.

John

---

### Post by OzzyFrank on 2010-05-04
Yeah... give me my toggle button back... or else

---

### Post by Crazy Jesus on 2010-05-04
> **OzzyFrank said:**
> Yeah... give me my toggle button back... or else


Seconded

---

### Post by BFG on 2010-05-05
> **OzzyFrank said:**
> Yeah... give me my toggle button back... or else

Thirded.

Apparently it was a gnome decision.  All bug reports I can find seem to lead here......
[https://bugzilla.gnome.org/show_bug.cgi?id=605608](https://bugzilla.gnome.org/show_bug.cgi?id=605608)


There doesn't seem to be much appetite from the development community, where keyboard shortcuts are the main language. ;)

---

### Post by gadolinio on 2010-05-05
> **aftabnaveed said:**
> [@gadolinio]("http://ubuntuforums.org/member.php?u=910735")
in Lucid Lynx it won't remember it, I mean you have to press Ctrl + L every time the window is reloaded or re painted.

I've tried the script in a virtual machine with Lucid, and it works. And other people propose using gconf-editor and then apps--> nautilus--> preferences, and check always_use_location_entry; as far as I know that does the same as the script, but from the terminal.

I'll try it and then restart the system, with one and the other option set, to see if it still remembers the configuration. I'll post results then.

Ctrl+L does indeed work for a single window, as ctrl+H does for hidden files. But the problem is that, in the end, ctrl+L doesn't really toggle between text and button mode; it's only intended to let you find some specific place. The same function is under "Go To" menu, then "Place...", which was also in Nautilus before, at least in Intrepid Ibex.
So the conclusion would be: developers didn't just make the function accesible with Ctrl+L; that GoTo already existed. They actually removed the toggle button :S And that function is now less accesible (gconf-editor, or gconftool).

---

### Post by nickwe on 2010-05-05
@[gadolinio]("http://swiss.ubuntuforums.org/member.php?u=910735")

I've create a launcher pointing to your script, it works fine but I don't know how to make it easily accessible in the side panel as you propose, could you please advise?

Thanks

---

### Post by gadolinio on 2010-05-05
> **nickwe said:**
> @[gadolinio]("http://swiss.ubuntuforums.org/member.php?u=910735")

I've create a launcher pointing to your script, it works fine but I don't know how to make it easily accessible in the side panel as you propose, could you please advise?

Thanks

I'm sorry, but I don't know how to put a button or any link to the script where it was in previous versions of nautilus. I can only use it from the panel. If you want it on the left, near nautilus's location bar, you could add a panel on the left of the screenand then put the launcher there... if you think it's worth it.

Regarding the persistence of the setting, I've tested it and what gconftool does remains that way even after a reboot. So the proposed launcher is for now the best approach to the button I know about... Maybe someone modifies and compiles nautilus again in some time... :P

---

### Post by nickwe on 2010-05-06
Oh OK, you were talking about a Desktop/Gnome panel and not a Nautilus side pane.

I've done like you said, and it fact it's working great and certainly the best workaround so far, thank you very much :p

---

### Post by gadolinio on 2010-05-06
> **nickwe said:**
> Oh OK, you were talking about a Desktop/Gnome panel and not a Nautilus side pane.

I've done like you said, and it fact it's working great and certainly the best workaround so far, thank you very much :p

Yes, I was talking about gnome-panel. It's also possible to use a nautilus script, which would be more nautilus-related, but not easier to use than a panel launcher. It would actually be some hassle, as it requires a right click, then, selecting the "scripts" menu, and then a final left click. And you would still have to move far from the location bar... 
But maybe someone modifies nautilus or writes some patch/addon in some time. Wish I knew how to do it...

---

### Post by lord_phantom on 2010-05-13
Hi guys!
Somebody found the file responsible for button layout of Nautilus (original topic: [http://ubuntuforums.org/archive/index.php/t-659294.html]("http://ubuntuforums.org/archive/index.php/t-659294.html")).

The file is located here: /usr/share/nautilus/ui/nautilus-navigation-window-ui.xml

We need to link somehow the previous bash script with a newly created button. If I'll succeed, I'll pass the info.

---

### Post by gadolinio on 2010-05-13
> **lord_phantom said:**
> Hi guys!
Somebody found the file responsible for button layout of Nautilus (original topic: [http://ubuntuforums.org/archive/index.php/t-659294.html](http://ubuntuforums.org/archive/index.php/t-659294.html)).

The file is located here: /usr/share/nautilus/ui/nautilus-navigation-window-ui.xml

We need to link somehow the previous bash script with a newly created button. If I'll succeed, I'll pass the info.

Wow, very interesting! Those xml files have tags with pre-existing values; I mean, there is somewhere else where "Edit Bookmarks", for example, is specifically described as a command or stg like that. So I wonder whether the toggle we're looking for is among those commands... It might be a matter of trying names it could have...

---

### Post by aj_the_first on 2010-05-24
> **Mr.Goose said:**
> +1 It seems a totally a daft decision to remove the button. :confused: @ Developers -** please, please can we have it back?**

Some of you folks may be interested in a (closed as "solved") thread in the *"[Lucid Lynx Testing and Discussion]("http://ubuntuforums.org/showthread.php?t=1430803")"* forum on this subject...

[LIST][http://ubuntuforums.org/showthread.php?t=1430803](http://ubuntuforums.org/showthread.php?t=1430803)[/LIST]

My situation is particularly bizarre. I was in "text mode" when I upgraded from Karmic to Lucid. I am now **stuck** in text mode. *Ctrl+L* highlights the text and *ESC* toggles a trailing slash at the end of the path, on & off. I cannot actually get back to button mode at all!

Seems the only solution at the moment for those who want the toggle button back is to download the Nautilus source from GIT and compile it yourself. Hmmm...

Best wishes, G.

Ditto that.  I much prefer breadcrumbs, but I use text every now and then.  I noticed that the toggle button had disappeared within about 3 minutes of using the new 10.04.  
I was on text when I upgraded, and now I can't go back to breadcrumbs.  I could live without the toggle button, (even though it was one of the things I cited as a major benefit over windows), but there is no way to make it go back.  Anyone figured out a solution? (I would like to just switch it instead of put a launcher on my toolbar)

---

### Post by xiphosurus on 2010-05-27
Pressing "/" also change the location bar to text-based. I find it more intuitive (and easier) than "Ctrl-L".

However, "/" only works in Icon and List mode, but not in Detail mode. It would be great it it worked in Detail too as I spend most of my browsing in that mode! :(

---

### Post by ditch_azeroth on 2010-06-17
dang! i was about to throw my monitor out of the window trying to figure this out - CTRL + L! aaaarghh! it was that easy!

---

### Post by philinux on 2010-06-17
> Nautilus location bar, bread crumbs vs text based.
Breadcrumbs is now the default. The button to switch between the two has been removed. Users can switch with ctrl+l and then esc to revert to breadcrumbs. To permanently switch to text users have to use gconf-editor from a terminal. Note: gconf-editor has been removed from the menus. The key is.
apps>nautilus> preferences> always_use_location_entry

From the General Help forum sticky.

---

### Post by Pokkels on 2010-07-05
Oky I have a different scenario,

I upgraded to Ubuntu 10.04 from Ubuntu 9.10, while keeping my home folder on a separate partition, so all my settings stayed the same from my installation with Ubuntu 9.10... Unfortunately one of my settings was that my location bar was text based.

In other words, when I press Ctrl+l, it stays text based, and if i press escape, it still stays text based. How can I change it to show the buttons?

Why on earth would they have removed the button to toggle between the two anyway?? It was so useful!

---

### Post by Awareness on 2010-07-19
As its been said in this thread before... just go to gconf-editor and uncheck apps>nautilus> preferences> always_use_location_entry

---

### Post by doug-M on 2010-07-30
> **Pokkels said:**
> Why on earth would they have removed the button to toggle between the two anyway?? It was so useful!

Yuck I have no idea, I've been watching all the poor choices in Microsoft UI changes (for example taking away the up button in windows explorer) now Linux is doing the same type of annoying stuff.

---

### Post by svaens on 2010-07-30
+1 

yes please Mr Mark Shuttleworth, bring back the toggle button (or at least, make the ctrl+l toggle it)

---

### Post by nitrofurano on 2010-07-31
ctrl+l works

---

### Post by Ronok on 2010-10-25
**[SIZE="3"]+1 [/SIZE]**for we want the Nautilus Location bar **[SIZE="3"]Toggle Button[/SIZE]** back

That is a "_Toggle Button_" to toggle between: 
button-based and text-based location bar Nautilus, 
it was at the left edge of the Nautilus Location bar before Ubuntu 10.04
I found it to be very useful and innovative

**Summarization:**
> 
Now
**A)** Pressing "Ctrl+L" will switch (not toggle) from button-based-location to text-based-location 
(temporarily, for a specific nautilus instance and location, navigate away & it reverts.
**B)** Pressing "Esc" will switch (not toggle) from text-based-location to button-based-location 
**C)** Pressing "/" also switches (not toggles) the location bar to text-based-location (with Only a: "/" and no current text-based-location showing)
**D)** Applications > accessories > Terminal > you@:~$ sudo gconf-editor > /apps/nautilus/preferences/always_use_location_entry = ADD Checkmark
gconf-editor's own Description: "If set to true, then Nautilus browser windows will _always_ use a textual input entry for the location toolbar, instead of the pathbar" ("always" Doesn't = Toggle)
**E)** The file responsible for button layout of Nautilus is 
located here: /usr/share/nautilus/ui/nautilus-navigation-window-ui.xml
(wise to make a back-up copy first, before altering)


...maybe how can we edit "E)" above to get a button ?
or there is a newer solution some place else ?
**Thanks** 
Ronok
[http://www.gongkuo.com/linuxcli.htm]("http://www.gongkuo.com/linuxcli.htm")

---

### Post by Alex1200GS on 2011-12-04
I wouldn't mind not having the toggle button if only I could make those breadcrumb buttons come back (typing / or ctrl+l would work fine for me). The gconf-editor solution doesn't work on my pc. I also tried the commands suggested earlier, but this text mode just won't go away. Any hints welcome.

---

