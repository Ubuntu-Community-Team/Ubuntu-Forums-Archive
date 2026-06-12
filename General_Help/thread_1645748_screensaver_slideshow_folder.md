---
title: "screensaver slideshow folder"
date: 2010-12-15
forum: General Help
---

### Post by AmazonasGrun on 2010-12-15
I'm would like my screensaver slideshow to display the pictures that I have on an external USB drive.  The path is

/media/My Book/Pics/Outdoors1

I tried the suggestions in this thread:

[http://ubuntuforums.org/showthread.php?t=1057684&highlight=screensaver+folder](http://ubuntuforums.org/showthread.php?t=1057684&highlight=screensaver+folder)

Post #7 says you need "escape sequences" if a folder in the path has a space, as I do in "My Book".  I tried entering two backslashes as shown, but it doesn't work.  I also tried the suggestion on post #14, but I've got the same problem.  What do I type so that the system can properly read the path /media/My Book/Pics/Outdoors1?

Thanks!

---

### Post by tredegar on 2010-12-15
Easiest might be just to rename "My Book" to My_Book".

Otherwise you just need a single \ to escape the single space:
**/media/My\ Book/Pics/Outdoors1**

---

### Post by AmazonasGrun on 2010-12-15
Thank you.  The single backslash did the trick.  My screensaver now pulls the pics from the external drive.

---

