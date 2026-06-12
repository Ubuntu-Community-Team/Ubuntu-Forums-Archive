---
title: "How do I install the Unigine Heaven 2.0 benchmark?"
date: 2010-03-29
forum: General Help
---

### Post by martini1179 on 2010-03-29
<rant>
I love Linux, and have been happily using Ubuntu for over a year now, but when I come across something this complicated, it frustrates me to no end. Why can't Linux have a unified binary system, like Windows does with *.EXE? Double click, "I Agree", next, next, next, finish. Done.  
</rant>

Ok, so I downloaded the [Unigine Heaven 2.0 benchmark]("http://unigine.com/download/files/Unigine_Heaven-2.0.run"), I made the .run file executable and ran it, only to have it spawn a subdirectory with four different shell scripts, and a /bin directory under that. The /bin directory contains two "executable" files, neither of which I'm able to run via the terminal.  

Can someone offer some step-by-step instructions?

---

### Post by Gemnoc on 2010-03-29
Hi Martini,

No need to get all worked up. :p

What you see as a nuisance (multiple install systems) is the result of free choice. Even though I too was confused by all the chaos that is the GNU/Linux world, now I understand the reason, and I prefer that to Microsoft's domination. ;)

I had tested v1.1 in the past so I told myself what the heck, and downloaded the v2 from your link (plenty of megabytes left on my limited account for this month :p). Well it's like the v1.1.

There is actually no install to make. It's rather silly to provide such a .run executable, because a zip or .tar.gz archive would have given the same result. (oh, I think the scripts are generated based on your screen resolution)

Do not look for the executables in the bin subfolder. Use one of the 4 shell scripts. If your Ubuntu is 32-bit, choose either x86_fullscreen_(your resolution).sh, or x86_windowed_1024x768.sh.

If your Ubuntu is 64-bit, then choose one of the x64 scripts.

Verify that the script is executable by right-clicking on it and choose Properties, then the Permissions tab (it should already been set).

Then, simply double-click on it! At the dialog window, click on the "Launch" button. That's it.

P.S. Nvidia GF9800GT running at 63ºC while in the windowed demo. Not bad, with my old GF8600GTS fanless and the Unigine v1.1 demo, I had to remove my PC's side panel to let the system cool off!!! I have really bad sound though.

---

### Post by martini1179 on 2010-03-29
/facepalm

Thank you. I followed your instructions, and for some reason it worked. I say it like this because before I sought help I had done those exact steps after I extracted everything from the .run file, and the script would not execute. I'm not sure if I needed to restart X or the system to get things to work, but apparently what had not worked before, works now. 

I hope you can understand my initial frustrations, given this new information.  

Anywho, thank you again.

---

### Post by martini1179 on 2010-03-29
/facepalm

Thank you. I followed your instructions, and for some reason it worked. I say it like this because before I sought help I had done those exact steps after I extracted everything from the .run file, and the script would not execute even though it was marked as executable. I'm not sure if I needed to restart X or the system to get things to work, but apparently what had not worked before, works now. 

I hope you can understand my initial frustrations, given this new information.  

Anywho, thank you again.

---

### Post by Gemnoc on 2010-03-31
No problem. ;)

---

