---
title: "Odd problem with Mozilla firefox"
date: 2011-04-28
forum: General Help
---

### Post by rapattack1 on 2011-04-28
Earlier i was using firefox and i got onto a website that i can't remember right now and a popup came up but i could not close it via the file>quit but it wouldn't let me do it. I am not sure what i am supposed to do now as after i rebooted the machine the damn thing has basically taken firefox over and i can't use it. I am using another browser now. I have never been through this with Linux before so i am puzzled :0) Any advice please :0) ?

---

### Post by Paddy Landau on 2011-04-28
This is indeed bizarre. It's a pity you can't tell us which website it was so that we can check it. If you remember, please let us know.

Try this.

[LIST=1]
[*]Open your home folder.
[*]View > Show Hidden Files (or Ctrl-H).
[*]Find the folder called [FONT=Courier New].mozilla[/FONT] (note the leading dot).
[*]Rename the folder to (say) [FONT=Courier New]backup.mozilla[/FONT].
[*]Run Firefox and check whether it work.
[/LIST]
Be aware that if this works, you will need to reinstall all your add-ons. You can import your bookmarks from [FONT=Courier New]~/backup.mozilla/firefox/[somefunnyname]/bookmarks.html[/FONT].

Once you are happy, you can delete the [FONT=Courier New]backup.mozilla[/FONT] folder.

---

### Post by rapattack1 on 2011-04-28
[IMG]http://i273.photobucket.com/albums/jj202/rapattack_album/Untitled.jpg[/IMG]
OK will try that now and report back. This is the thing that went wrong btw

---

### Post by rapattack1 on 2011-04-28
Thanks so much that worked a treat. So how to i get those backups? I have never done that before. I don't have many addons to reinstall as this is a fairly new install of the OS :0):P

---

### Post by Paddy Landau on 2011-04-28
I presume you are using Firefox 3.6, as you are using 10.04.


[LIST=1]
[*]Bookmarks > Organise Bookmarks (or Ctrl-Shift-O).
[*]Import and Backup > Restore > Choose File
[*]Navigate to [FONT=Courier New]~/backup.mozilla/firefox/[somefunnyname]/bookmarks.html[/FONT] (I hope this works -- I've never used it before! If it doesn't work, go to step 4.)
[*]If step 3 didn't work: Do steps 1 & 2, then navigate to [FONT=Courier New]~/backup.mozilla/firefox/[somefunnyname]/bookmarkbackups/bookmarks-[latestdate].json[/FONT]
[/LIST]

You could also try just copying [FONT=Courier New]~/backup.mozilla/firefox/[somefunnyname]/bookmarks.html[/FONT] to [FONT=Courier New]~/mozilla/firefox/[somefunnyname]/bookmarks.html[/FONT]

The good thing is that if you really mess it up, just delete [FONT=Courier New]~/.mozilla[/FONT] and try again.

When you are happy with Mozilla, you can delete [FONT=Courier New]~/backup.mozilla[/FONT].

---

### Post by Paddy Landau on 2011-04-28
I've looked at [1pau.glomobi.com]("http://1pau.glomobi.com/") (from your screenshot).

WOT rates glomobi as [very low in trustworthiness]("http://www.mywot.com/en/scorecard/glomobi.com").

I strongly suggest that you install [WOT]("https://addons.mozilla.org/firefox/addon/wot-safe-browsing-tool/") and leave your own rating and comments (anything that manages to screw Linux is very unsafe!).

BTW, please mark your thread as solved.

---

### Post by rapattack1 on 2011-04-29
Thanks Paddy it was the 2nd way of getting the bookmarks that did the trick :0)
 Oh yes i forgot about WOT. I had it installed on a previous install :0) All installed thanks for the recommendation.
That site was something that came up to do with something else. I dunno what i was doing at the time as i am often doing way too much at the same time to remember a specific thing :0)
How do i report that site? i looked at the preferences and can't see anything. I didn't know what was for doing that.
Oh yes marking the thread as solved now. Your such a big help!!!!
Oh yes i have never had anything like that go wrong while surfing. Very odd!

---

### Post by Paddy Landau on 2011-04-29
> **rapattack1 said:**
> How do i report that site?
After you have installed WOT and created an account, you will see a circle next to the URL bar. Click on it, and you see a brief ratings guide; simply click your mouse in each section to rate it.

If you want, you can add your own comments (see the mouse pointer in the screenshot below). You can also see other people's comments.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190342&d=1304065486[/IMG]

---

### Post by rapattack1 on 2011-04-29
Oh thanks i figured it out once i got on the wot site and rated 1pau.glomobi.com . Horrible site!!!!
:popcorn:

---

