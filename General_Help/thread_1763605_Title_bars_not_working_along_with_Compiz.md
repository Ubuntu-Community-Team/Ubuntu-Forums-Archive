---
title: "Title bars not working along with Compiz"
date: 2011-05-20
forum: General Help
---

### Post by komputerkurt on 2011-05-20
I installed ubuntu 11.04 today.
I got advanced compiz manager from the software center. I turned on the desktop cube and turned off the unity plugin (I had no clue what it did) and basically I had nothing to use to open anything.

I used recovery mode to turn it back on and then booted in to the normal session. Unity worked but now there were no title bars (in 10.04 and 10.10 this sometimes happened when I used emerald, but emerald(or maybe compiz, I forget)--replace fixed that problem). I uninstalled compiz then restarted. Still no title bars. Now I did compiz --replace, gtk-window-decorator --replace, and nothing worked. I reinstalled compiz. No title bars for you. So I turned on the window decorator and now I got the title bars.

Only thing is they won't move so I can't drag anything around even with alt+click. When I did compiz --replace I got some errors but I can't show you them since hitting ctrl+c in the terminal hangs ubuntu for a while then removes the title bars and closes chromium, which I was using originally to post this. I am now using Windows 7, the only thing that actually works for anything. To get those useless bars back compiz --replace would fix it but I can't get you the errors it gives me since it just hangs so I'm in a endless loop of resetting a malfunctioning compiz. 

Any idea on how to fix this short of reinstalling ubuntu (using wubi) and having to let the ubuntu iso file download itself again, then have to wait for it to install on both ends and then update my ubuntu release which should take somewhere around **6 hours** on my internet connection?

Not having any control over the windows placement almost makes me feel claustrophobic like fear... man I'm so relieved to use Windows 7 and open explorer and move around the window. In the low graphics node on ubuntu it looks like 10.10 and works but I want to use the new features as well as the seemingly removed feature to have title bars.

---

### Post by komputerkurt on 2011-05-20
Well well well looks like I figured out how to fix this. Somehow compiz disables the compiz control for moving windows (wtf). 
Another problem now though, changing compiz settings makes the top bar get messed up and I need to use compiz --replace to fix it... 

I guess that I will have to just use that command now to fix things.

---

### Post by Mat11 on 2011-12-23
You may have to reinstall Ubuntu desktop first.
Use can use: sudo apt-get install ubuntu-desktop.(using a wired internet link)
What i did next was to delete any unwanted items on my bottom pane/bar- except the waste bin and windows selector.
The pane at the top came back straight afterwards for me using Maverick 10.10 on my X86 64 laptop.
The bottom window bar/pane should become more stable and any flickering there should stop.

Hope this works for you.
Merry Xmas

Matt

---

