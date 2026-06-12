---
title: "Desktop"
date: 2009-11-18
forum: General Help
---

### Post by toswells on 2009-11-18
I have had a difficult time to describe this issue and therefore have not been very successful in searching the forum.

  I started playing around with Ubuntu 9.4 under windows a few months ago and when 9.10 came out I installed it as a dual boot.  Very soon after that I installed the Studio version.  I love this OS and the 9.10 fixed my issues with my wireless connection.  

  My question is, an Icon use to pop up on the desktop when I inserted a CD, flash card, etc.  But now I don't, I have to go to the menu system to find the flash card I just inserted.  I should note that this is an SD card in a card reader.  as I am typing this, I am not sure what happens if I insert a usb stick.  There have been a number of changes all at once.  I bought a new computer, installed Ubuntu 9.10 then decided I wanted to play around with the studio version and promptly upgraded.  So I don't know if it because of the card reader, 9.10, the studio version or if it was something I inadvertently disabled.

---

### Post by hwttdz on 2009-11-18
What about going to system->prefs->"removable drives and media" and checking some boxes there?  Any help?

---

### Post by toswells on 2009-11-18
I'll check when I get back home, I'll also check to see if a usb stick works any differently.   It's strange, I never noticed when this option stopped working, but I really miss it now.

---

### Post by toswells on 2009-11-18
Nope, still can't find the settings for this.  oh, and a usb stick doesn't pop up on the desktop either.

---

### Post by hwttdz on 2009-11-18
Do you find "removable drives and media"?

---

### Post by toswells on 2009-11-18
No, I don't see "removable drives and media" under sys<pref or sys<administration

I also checked under the menu settings to see if it just wasn't checked as well.

---

### Post by hwttdz on 2009-11-18
So this is almost certainly not the best way to go about it, but it seems likely to work.  If you install thunar, which is xfce's file manager then run "/usr/lib/thunar-volman/thunar-volman-settings" (don't know why that's not a bin).  You should be able to check some boxes.  Let me know how that goes.  If you're unsuccessful let me know what goes wrong, i.e. the error, you weren't able to find something, it didn't have the desired effect...

And another alternative and possibly the gnome way is to open nautilus, edit->preferences->media, then change the options to what you will.

---

### Post by toswells on 2009-11-18
Ok, i have thunar installed and the setting up without any problems.  However i still does not pop an icon to the desk top.  While searching the "ununtupocketguide" looking for the screen capture shortcut key, I found a section related to "removable drives".  It shows where to change the settings ot rather what to do when a meda card or cd is mounted.  This still does not help, but I can at least have it ask me what to do when a card is inserted.

---

### Post by toswells on 2009-11-18
I just had a thought.  I changed the top and bottom panels around so that I only have one one the top.  could this be an application on the panel that I removed?

---

### Post by hwttdz on 2009-11-18
Sorry, I think I misunderstood your first post, what you want is to run gconf-editor and check, "/apps/nautilus/desktop/volumes_visible".

I'm not sure how it decides which volumes are eligible for display there.  i.e. my / and /home are on different drives and I also have an extra drive for media, and I believe it only shows the media drive if I check that option.  

Also in order for this to work you need to have nautilus drawing your desktop (if you have any desktop icons then nautilus is already drawing your desktop, if not it's just another checkbox in gconf-editor).

---

### Post by toswells on 2009-11-18
ok,  I received an error with the gconf-editor.  yes there are icon on the desktop, a couple of files that I have downloaded but haven't deleted yet. 

The "never prompt or start applications on media insertion" was checked.  I just un checked it to make it more readable.  I see something else is going on.  after I chaptered a screen shot, I saved it to my desktop.  However, it does not show up on the desktop but I can find it thru the places<desktop folder.  <screen shot attached> 
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by hwttdz on 2009-11-18
Ok, what's the error you get when you attempt to run gconf-editor?

The drive is being mounted, so we just need to get it to display an icon for the drive on the desktop, which we do through gconf-editor.  I thought the issue was setting up autoplay or something similar, so you can ignore most of what I said in my first few posts.

---

### Post by toswells on 2009-11-18
the error

scott@was:~$ /apps/nautilus/desktop/volumes_visible
bash: /apps/nautilus/desktop/volumes_visible: No such file or directory
scott@was:~$ 


should I remover thunar?  I started to, but it seams to be well integrated into the sys.  I can remove thunar and thunar-volman, but it tells me this will only remove two of 30 files.


I mean if nautilus is there as the file manager, should I get ride or thunar?

---

### Post by hwttdz on 2009-11-18
Sorry, I suppose I could have been more clear run gconf-editor from the terminal, then browse through the tree to the location "/apps/nautilus/desktop/" and check the box "volumes_visible".

If you previously had to install thunar then you can remove it without fear of breaking your system, however there is no need to, and I find it sometimes convenient to have around, it's a sort of trimmed down version of nautilus.

---

### Post by toswells on 2009-11-18
ok, this is looking interesting.  seams like lots of choices, but i don't see what I think we are looking for .  do you?  also, I noticed a number of items under the desktop-metadata that look like previously plugged in devices or cards.  should this be keeping a record or is this left over from the device being removed improperly?  see attached image

---

### Post by hwttdz on 2009-11-18
In your attached screenshot, see on the right hand side of the image, there is a checkbox with "volumes_visible" in the name column, and an empty checkbox on the right hand side, check it.

---

### Post by toswells on 2009-11-18
AH HA,  Ok thanks very much HWTTDZ.  I found it.

---

### Post by toswells on 2009-11-18
I was sitting here staring strait at that volume visible block and it just hit me. that's it.  I know it can be a pain trying to when that person is not quite up to speed, so I really appreciate the help.[IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

---

