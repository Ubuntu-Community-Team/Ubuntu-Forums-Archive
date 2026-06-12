---
title: "desktop crash"
date: 2011-11-15
forum: General Help
---

### Post by Betanu701 on 2011-11-15
Hello,

I had 2 screens hooked up with an nvidia 8700 card, 
It was set as twinview but I changed it to seperate x with xinera enabled
Restarted computer
I was able to enter my log in credentials but then the computer freezes, the background of the login will not disapear.
Keyboard and mouse still work.
Tried disabling lightdm logging into a root shell.

Unpluged the second monitor and restarted the computer. Was able to log in but the side bar is gone only thing at the top is 

file edit view go bookmarks help

That is all that is displayed.

Running ubuntu 11.10 with nvidia 8700 video card with the latest kernal.

If someone could help that would be awesome

Thanks,

Beta

---

### Post by Betanu701 on 2011-11-15
Thinking it might be unity, I switched to screen using alt-ctrl-f6
Then I used
unity -- reset
Did a bunch of stuff.
The 2nd to last line stats
"Xlib: extension "xinerama" missing on display ":0"."

If this helps solve my issue

Any questions I will try to answer

Beta

---

### Post by Betanu701 on 2011-11-15
What I think could solve my problem is if I could reset the nvidia control back to twinview. But the only way that I have access to do it is through command line.
I do not know how to do this.

Any help is appreciated

Beta

---

### Post by Mark Phelps on 2011-11-15
One thing that might work -- is forcing the reinstall of compiz and unity.  So, with the largest screen connected by itself, follow the details in the link below -- that should get you back to a working desktop:  

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---

### Post by Betanu701 on 2011-11-15
Thanks mark

That worked.

---

