---
title: "No Network folders displayed during file upload"
date: 2010-07-27
forum: General Help
---

### Post by Hovik on 2010-07-27
Greetings,
So I am trying to upload a photo to craigslist from a NAS drive on my network but when I go to choose the file, the network resources are not listed in the file tree. Or maybe I am not looking in the right place? Take a look at the attached. This is what I see, but there should be something on the left pane that says "Network" so that you can access your workgroup shares. 

I also attached a screenshot from my "files & folders" menu which clearly shows such a "network" option in the file tree. How come it's in one place and not the other? Any help would be appreciated...
H

---

### Post by Hovik on 2010-09-17
Bump! Nobody knows the answer to this after almost 2 months????

---

### Post by Hovik on 2010-11-20
Hi again folks. Does anyone have any idea how to fix this? I am sure I can't be the first user to run into this problem. How many of you have uploaded a photo from a shared folder on your network to Facebook or some other site. How do you do that?

---

### Post by Hovik on 2010-12-18
Seriously people? 
After almost 6 months nobody can so much as make a peep about this issue? 

Go to Craigslist, post an ad and try to add a photo from your Network Attached Storage (NAS). You can't do it because NAS drives don't show up in the file tree that pops up when you click upload. I can't believe I am the only one to have this problem or post on the issue. 

PLEASE HELP!

---

### Post by the_loominator on 2011-02-21
Hovik,

I was having this same problem today, and ran across your post.  I solved it after viewing this thread.

[http://www.google.com/support/forum/p/gmail/thread?tid=75aa25b536768c74&hl=en](http://www.google.com/support/forum/p/gmail/thread?tid=75aa25b536768c74&hl=en)

Steps I took
1. In the file upload screen, press CTRL + H (to bring up hidden files)
2. Find '.gvfs' in your home folder
3. Double click on this and it should show your network connections

That's what worked for me.  To put this into your file bookmarks, right click on '.gvfs' and 'Add Bookmark'.

Hope this helps somebody!

Dave

---

### Post by Hovik on 2011-02-23
Loom, Thank you so much. This is an excellent solution to the problem. It works perfectly for me. 

It was so long since I wrote the thread that I didn't believe anyone else tripped across this problem (as hard as it is to believe).

Thank you again!

---

