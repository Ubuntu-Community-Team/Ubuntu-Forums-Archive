---
title: "Occasional Ubuntu crashes"
date: 2010-03-07
forum: General Help
---

### Post by uShafee on 2010-03-07
hai.i have been using ubuntu for the last week. It was pretty good at the start. Great eye candy, responsive and nice. However, after a while, ubuntu started crashing on me. When it does, it just becomes totally unresponsive ( cant move cursor, cant open a virtual terminal or anything in between ) and i lose everything i happen to be working on.

My PC isnt that bad hardware config wise. Its got 1.5GB RAM, 256MB graphics memory (nVidia GeForce 7300 with N A driver v 185 installed) and a 120GB hard disk. I was running Windows 7 before and it ran pretty well with the above hardware.

Can someone help me with troubleshooting this?

---

### Post by joeknoodle on 2010-03-07
Sorry If I can't help directly, but you may wish to think about what extra stuff you've added since the install. 
Maybe list these extras here in case someone knows of a specific issue.

Maybe try removing later apps one by one and comparing.

---

### Post by woodmaster on 2010-03-07
check your log files for anything extraordinary.  on base install I had sound error freezes related to pulse audio.  I fixed that by:
[HTML]http://ubuntuforums.org/showthread.php?t=789578[/HTML]
Then I started having x-server freezes which was solved by:
> Originally Posted by **pompiuses** [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8576889#post8576889") 
[I]Looks like there's a cure afterall :smile:. Disabling Compiz and installing the Xorg intel driver to 2.4 fixed it completely. So at least on my Dell Dimension 2400 the problem was graphics related.

Following this post:
[[COLOR=#444444]http://ubuntuforums.org/showpost.php...0&postcount=15[/COLOR]]("http://ubuntuforums.org/showpost.php?p=8341830&postcount=15")[/I] 

---

