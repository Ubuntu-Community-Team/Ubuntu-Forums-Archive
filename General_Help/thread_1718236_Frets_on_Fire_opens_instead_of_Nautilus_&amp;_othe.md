---
title: "Frets on Fire opens instead of Nautilus &amp; other programs"
date: 2011-03-31
forum: General Help
---

### Post by Bujiraso on 2011-03-31
Hello
I just started using Ubuntu about a month ago, it's my first Unix or  Linux-based Operating System so I'm green as it gets, but I'm otherwise  familiar with computers.
I have Ubuntu 10.10 Maverick Meerkat installed on an Acer Aspire 5520 and I have a bit of a strange problem.

There are a few assorted commands, both by GUI and terminal which,  instead of performing their proper actions, try to open Frets on Fire.  Even though I've purged the program (cause I didn't know why this was  happening)

If I extract something from a zip or what have you, and then say "View  Files" it tries to open Frets on Fire. As well, Minecraft tries to open  Frets on Fire when I try to view the folder where the add-ons are  stored. I'd wager it's *very much* related to the file manager, which I believe is called Nautilus.

There are a few other times where this occurs, and I'll link a picture  down below of one of the instances, but searches haven't really yielded  me any good results.

Relevant random facts are that I downloaded an Add-on pack of some  variety from this forums and tried to install it to /opt/ by the tar  -jxvf command (that's about the only thing in terminal that I've done  with Frets on Fire). Not understanding this command at all I am not sure  if this matters, but there it is anyway.
Other than that I'm right lost.

Any ideas?

Thanks in advance!

---

### Post by wolfen69 on 2011-03-31
Have you deleted your fretsonfire config file?

---

### Post by Krytarik on 2011-03-31
Please post the content of "~/.local/share/applications/mimeapps.list", in code-tags please, the #-button in the editor.
It's a text file, simply open it with the text editor.

Btw., your panels are horribly messed up. Yeah, I know, for the most part of that the theme is to blame. And it seems like you deliberately placed the clock applet at the middle of your upper panel.

Greetings.

---

### Post by Bujiraso on 2011-03-31
As far as I know I deleted the config, but where would that be - just for safe measures?

As to the file requested, it does contain a few programs I don't have anymore (Kdevelop) as well as Frets on Fire right there.
```

[Added Associations]
application/x-ms-dos-executable=wine.desktop;
inode/directory=userapp-fretsonfire-59RMSV.desktop;
application/x-ole-storage=wine.desktop;
text/x-java=userapp-wine-HESITV.desktop;kde4-kdevelop.desktop;

```As for my panels I'm not sure what "horribly messed up" means, but if you mean that it is expanded so that I have my main menu and window selector on the left, clock in the middle, and notification icons & logout on the right: that's just the way I like it :P
Also not sure which "theme" we're talking about.

---

### Post by Krytarik on 2011-03-31
You may just purge the entire file, since there is nothing special in there, aside from the faulty ones, it will get recreated when you choose custom apps for specific file types. Generally, when you use the "Open With -> Other Application" dialog, make sure to only leave the option "Remember this application" ticked for appropriate fily type associations.
Also see here: [http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

As for the mentioned config file, I guess *wolfen69* meant one that may be located somewhere in your home directory. However, that wouldn't have any effect.

Regarding your panels, what I actually meant was that your chosen theme isn't properly fitting them, in various aspects, at least since you've set a custom panel background.

---

### Post by Bujiraso on 2011-03-31
Brilliant! Thanks very much! Now I don't get Frets on Fire opening, the File Browser opens instead. I shoulda thought better to realize that it was a file association thing, but "oh well".

bahahaha, oh yeah, no the colours? Yeah, they are all screwed up. I - quite frankly - have no idea how to change it from the flat black (I'd like the whole thing to be transparent)

Thanks again! 
Solved!

---

### Post by Krytarik on 2011-03-31
You're welcome! :)

//of topic: What theme is it actually? I would say it's default Maverick Ambiance, but I can't believe that it screwes the panel items that much up, especially those at the right side. Also, the bottom panel looks completely different, if it's actually one, since it seems to be located above of Firefox' add-on bar (formerly known as statusbar), and it's completey black!? I guess, I could easily fix the panel background for you, if you would like it!

---

### Post by Bujiraso on 2011-03-31
Actually I've attached a new picture cause that one definitely screwed up. I now see what you mean, the colours were all off.

It is the default Maverick Ambience. I like it on my windows, I just wish the gnome-panel didn't have to be that exact colour. like I say, more glassy would suit me. Also that one icon has a white background, kinda annoying.
Not sure if those things can be fixed though.

That other panel on the bottom is just Download Statusbar 0.9.8 and actually isn't all black, but - again - that shot came out weird.

---

### Post by Krytarik on 2011-03-31
As for the "bottom panel", what made me think that it may be one, is that in the screenshot it hosts the task item of the Archive Manager. Doesn't it?

I took a look into Maverick Ambiance's config file for the panels, and like I guessed, it was quite easy to modify it that way that you can use any custom panel background now without having the usual panel background overlay it in the button areas. But I believe it won't affect the white background of those single item, since it is specified by the item itself.

To modify Maverick Ambiance the way I described:

- backup the default panel config file:
```
sudo cp /usr/share/themes/Ambiance/gtk-2.0/apps/gnome-panel.rc /usr/share/themes/Maverick/gtk-2.0/apps/gnome-panel-original.rc
```- open the panel config file for editing:
```
gksudo gedit /usr/share/themes/Ambiance/gtk-2.0/apps/gnome-panel.rc
```- modify/add the marked entries:

If you want to modify the text colors of the panel items, uncomment the "[fg]" entries and modify the hex color codes like you want them. However, the default colors should look just fine with your current custom panel background.
```

# ==============================================================================
# GNOME PANEL SPECIFIC SETTINGS
# ==============================================================================

style "panel" = "dark"
{
    xthickness = 0
    ythickness = 0

[COLOR=Red][B]    #bg_pixmap[NORMAL] = "img/panel.png"
[/B][/COLOR]    bg[NORMAL] = "#4b4a46"

[B][COLOR=Blue]    #fg[NORMAL]        = "#dfdbd2"
    #fg[PRELIGHT]      = "#fff"
    #fg[ACTIVE]        = "#fff"
    #fg[SELECTED]      = "#fff"
    #fg[INSENSITIVE]   = shade (0.5, "#3c3b37")[/COLOR][/B]

    engine "murrine" {
        #contrast = 1.0
        textstyle = 2
        text_shade = 0.35
    }
}
```- save/quit
- re-apply the theme

Have fun! :-)

---

### Post by Bujiraso on 2011-03-31
Yep. Download statusbar for Firefox is pretty nice looking. I prefer its Windows-start-bar-esque look for downloaded items instead of having them all in an annoying (I find) pop-up window 

But yeah the theme modification sounds great! Will do!
Thanks again a ton : D

---

