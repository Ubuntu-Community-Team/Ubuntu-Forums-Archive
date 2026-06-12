---
title: "A few questions"
date: 2009-10-28
forum: General Help
---

### Post by Zael Faroe on 2009-10-28
Hello, I've been trying the netbook remix of 9.10 for a few days now.

I have been customizing the netbook remix launcher. I am trying to figure out how to change the items in the "Files & Folders" area. I figured out that certain items can be changed by changing the bookmarks in Nautilus. I would like to know how to get rid of the Desktop folder and Downloads folder. They show up even though they aren't bookmarked. I understand that the Desktop folder itself may be required for gnome, but I was hoping I could at least hide it from the remix launcher since the netbook remix doesn't really have a "Desktop". I also don't understand why the Downloads folder is showing up when it is no longer bookmarked.

Also where is the Help launcher that starts in the Favorites? I want to rearrange the Favorites section, but it seems the only way I can do that is by removing items and re-adding them, but I cannot find where the Help launcher is so that I can add it back after rearranging the Favorites section.

One last thing. I think that I heard that compiz doesn't work with the netbook remix. Does that mean there are not alternatives to window switching with alt+tab from the default on netbook remix?

Thanks.

---

### Post by fluffman86 on 2009-10-28
For help, you should be able to go to system > preferences > main menu and create a launcher in another folder (either under accessories or administration, if it were me).

In the launcher information, use the command "yelp" and name it "Help"

For the default Humanity icon, use /usr/share/icons/Humanity/apps/48/help-browser.svg

From there, you should be able to find other icons for other themes.

For the alt+tab question, you can always try enabling graphic acceleration under System > Preferences > Appearance, but it would probably slow a netbook WAAAAY down...I know I wouldn't want it on mine.

---

### Post by Zael Faroe on 2009-10-28
I used to have a decent amount of compiz affects on eeebuntu 8.10 before I switched to Ubuntu 9.10 NBR, so slow down isn't a problem on my netbook. 

Another question. Is there anyway to move the notification box that pops up in the upper right hand corner of the screen? 

Again thanks.

---

### Post by Big Iain on 2009-10-28
compiz crashes under the nbr desktop mode

---

### Post by fluffman86 on 2009-10-28
If you mean the bubble notifications (notify-osd), then sorry, you can't change that.  It's all hard coded in to notify-osd.  You might find a hacked version somewhere online, or be able to change the source yourself...but that's probably not much help.

if it makes you feel better, there's currently a bug filed against notify-osd because certain nvidia users with dual screens (like myself :P) have the message pop up in the top right of a monitor that's way out of the way or potentially in another room.  My workaround is to turn off desktop affects, but that kinda sucks as well.  Sorry. :(

---

### Post by Zael Faroe on 2009-10-28
Ok. Well I will get over the notify-osd for now then. Thanks for the info... Anybody have an idea about the Downloads and Desktop launchers in the Files & Folders panel of the remix launcher?

Thanks for all the info.

---

