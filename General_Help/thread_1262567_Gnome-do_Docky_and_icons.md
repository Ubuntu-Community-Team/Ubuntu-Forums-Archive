---
title: "Gnome-do Docky and icons"
date: 2009-09-10
forum: General Help
---

### Post by The Funkbomb on 2009-09-10
I love Gnome-do Docky with three exceptions.  I don't like how you can't change the background color of the bar.  That dark grey doesn't really work with my color scheme.  That's forgiveable because my dock is set to autohide for the most screen real estate I can get.

The second issue is Gnome-do Docky doesn't play well with a few apps.  In my experience, the worst offender is the beloved VLC player.  You can throw cow manure into VLC player and it plays flawlessly.  The issue comes up when you open another window, say Firefox to IMDB an actor in a movie you're watching.  Click the VLC cone again and hey, where's my movie?!  The cone will only bring up the VLC control panel, not the actual movie screen.  Of course, this can be circumvented by selecting "Always on top" in VLC or just switching to another desktop to look things up.  The issue really becomes a pain when you accidentally minimize the screen.  Then you have a movie playing somewhere and as far as I can tell, you can't get it back.  Another offender is the Open Office Suite.  If you have the icon down there, you can't minimize or maximize using the dock, it just simply opens a new one.  

Sorry about going off on weird tangent rants. :/

This post is about the last issue.  Icons.  This isn't necessarily Gnome-Do's fault but the programmer's fault.  Either way, it's still an annoyance.

Some programmers don't use .SVG for their icons.  I guess they either use .PNG or I guess .XPM.  Neither of which are scalable like vector graphics.  This causes issues when a 16x16px or 24x24px icon gets blown up to I'd guess about 128x128px.  You get a very bad pixelated effect like when you try to enlarge any non-scalable graphic.

Here are a few examples of ones that got it right:

[ATTACH]128063[/ATTACH]

Look at how crisp Terminal is.  I think mostly all of the Ubuntu supplied apps use SVGs so thumbs up to you on that.

Here are some of the worst offenders.

[ATTACH]128064[/ATTACH]

Sun's Virtualbox.  Jeez.  That looks bad.  Pidgin is another offender as well as Skype and Thunderbird.

How can we fix this?  Instead of people drawing their own stuff in Inkscape or scanning through files and replacing their stock .pngs with svgs, how do we get programmers to make the switch?

---

### Post by longtom on 2009-09-10
Same problem here - with Cairo Dock:

Opera icon with Opera minimised:

[img]http://ubuntuforums.org/attachment.php?attachmentid=128069&stc=1&d=1252565791[/img]


Opera icon with Opera active:

[img]http://ubuntuforums.org/attachment.php?attachmentid=128070&stc=1&d=1252565791[/img]

Not sure the difference in quality is really visible here - it surely is on my desktop.

---

### Post by fabounet on 2009-09-10
with Cairo-Dock you can bypass this problem.
go to the Taskbar module, check the option "overwrite X icons", and you're done ! ;-)

---

### Post by longtom on 2009-09-10
> **fabounet said:**
> with Cairo-Dock you can bypass this problem.
go to the Taskbar module, check the option "overwrite X icons", and you're done ! ;-)

Thanks, but....

nope - I am afraid not.  If not checked (which it was) the low res version is permanent, if checked only, when Opera is minimised.

Any other ideas?

---

### Post by fabounet on 2009-09-11
never noticed such thing, maybe it's just the transparency which is lower when the icon is minimized ?
which version are you using ?

---

### Post by abdusamed on 2009-10-11
same problem here with my ubuntu.. i'm gettin a strange grey bar with my cairo bar... annoyin and ubuntu these days is gettin pretty annoyin :( this is the grey bar im talkin about
[IMG]http://img160.imageshack.us/img160/1170/new100.jpg[/IMG]ALSO.. i don't seem to get new icons on the bar eventhough i've already applied new icon set.. they don't go on the cario bar.. pLAZZZ HELP.. im thinkin to GET rid of ubuntu if i don't get this stupid probs SOLVED!

---

### Post by fabounet on 2009-10-12
please open a new topic.
you can come on cairo-dock.org to expose your specific problem about Cairo-Dock.

---

