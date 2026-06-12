---
title: "Input Fields with Dark Themes"
date: 2010-06-07
forum: General Help
---

### Post by Exosus on 2010-06-07
Alright, I'm using a really dark theme and I love the look it gives me, but the problem is that  input fields stay black in some applications. That makes pages look really strange - random black bars in the middle of otherwise normal white pages. The same thing doesn't happen in Chrome, but I honestly don't especially like Chrome and just keep it around to test things (like this). I followed the suggestions in this thread: [http://ubuntuforums.org/showthread.php?t=1239446](http://ubuntuforums.org/showthread.php?t=1239446) and messed with Gnome Colors, appearance preferences, and added a .css from [http://ubuntusatanic.org/dark-themes.php](http://ubuntusatanic.org/dark-themes.php). That last fixed some boxes but not others. Google does it correctly now, though iGoogle doesn't; Certain parts of this site work correctly where others don't, etc. It seems to depend on the type of field, though I don't know enough about fields to say what the difference is. I am also having similar problems in Skype.

Anyone have any suggestions? I'm tempted to just go back to a lighter font, but I hate to just give up on a solvable problem...

---

### Post by bodhi.zazen on 2010-06-07
This is the #1 problem with dark themes.

Potential solutions are application specific, for firefox go to Edit>Preferences>Content>Colors

Do not use system themes or set a different font color (white).

With some apps you just need to fall back to a different, non dark theme.

---

### Post by Exosus on 2010-06-07
I tried your suggestion with the Firefox settings - they were already set the way you recommended. Any other thoughts? I guess I can always go back to a lighter font, but I spent soooo long  piecing this one together I kind of hate to.

Thx.

---

### Post by bodhi.zazen on 2010-06-07
No easy solution. You could try writing a custom css sheet.

Here is a link on the Arch Linux forums

[http://bbs.archlinux.org/viewtopic.php?id=69854](http://bbs.archlinux.org/viewtopic.php?id=69854)

It links to additional forums or use google.

here is one from Satanic Edition:

[http://ubuntusatanic.org/forum/comments.php?DiscussionID=106&page=1](http://ubuntusatanic.org/forum/comments.php?DiscussionID=106&page=1)

Direct link : [http://ubuntusatanic.org/scripts/ff3/userContent.css](http://ubuntusatanic.org/scripts/ff3/userContent.css)

---

### Post by Exosus on 2010-06-07
Yeah the code he has listed there is the same one I picked up and used as my .css for firefox. After that guy posted it in the forum, the admin added it to the guide I put up. I looked into .css's a little bit and honestly I can't find any reason that code shouldn't just make everything work correctly, but somehow something is overriding those alterations.

I'm going to wander around the ArchLinux post and see what I can come up with there. If I find anything effective I'll bring it back for posterity, but honestly I think I may be a touch out of my depth here. Oh well, if all else fails this will have been a little learning experience for me in custom style sheets I guess lol.

Thanks for your help.

---

