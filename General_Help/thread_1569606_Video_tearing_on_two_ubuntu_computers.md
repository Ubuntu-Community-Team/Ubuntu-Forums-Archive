---
title: "Video tearing on two ubuntu computers"
date: 2010-09-07
forum: General Help
---

### Post by Manuwash on 2010-09-07
Hey!

I got heavy video tearing on both my Ubuntu desktop and laptop computers. The desktop has an nvidia video card and the laptop an ati radeon. I tried all tips I could find in google and no luck.

I think I am gonna try windows 7 because really I haven't stopped troubleshooting since I turned to Ubuntu, and that's not exactly the way I wanna spend my time.

---

### Post by no2498 on 2010-09-07
write down your settings so you can set them back if needed

this comes from cheese

&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

---

### Post by Manuwash on 2010-09-08
I installed windows 7 on both my laptops and I couldn't be happier. It was an interesting experience with Ubuntu, and I don't regret it, but I don't want to spend my time fixing things. I have windows 7 running with dreamscenes on a 5 year old celeron laptop and it runs smooth as hell. I am back to the dark side.

---

### Post by Manuwash on 2010-09-08
One thing I will miss is cairo-dock, Fabounet you should do a windows version ;) ( sorry this must sound a bit like blasphemy around here hehe)

---

### Post by no2498 on 2010-09-08
let me think you spent $150.00 on 1 computer = $300.00 for 2
i can buy a new computer for that and not have any cold windows to heat
ill stay with ubuntu and enjoy the ride or take the $ 300.00 an fix this computer 
we all have are fun in the end

---

