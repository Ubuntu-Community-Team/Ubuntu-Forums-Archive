---
title: "Allowing Mono to use more of the &quot;Memory Usage&quot;"
date: 2012-01-03
forum: General Help
---

### Post by connor99994 on 2012-01-03
I'm using a linux VPS server using Ubuntu 10.04. With the gnome GUI. I run an .exe using  mono through the terminal (Terraria Online server). I'm VERY new to  linux and will try my best to explain what I'm having an issue with. I'm  trying to allow mono to run the .exe with more than just the 300mb it  allows it. I have a total of 2gigs to use and want to expand it to at  least 1gig. How, or what can I do to increase the allocation of mono or  the .exe itself? 


Please don't insult me because I'm only 16 and am only a tenth of the nerd level of most of the posts I've seen thus far ;) O:)

---

### Post by connor99994 on 2012-01-03
Please help me out! I'm completely confused and can't find a solution anywhere.

---

### Post by connor99994 on 2012-01-04
I literally have nowhere else to turn to figure this problem out. HElP ME :-({|=

---

### Post by directhex on 2012-01-04
Mono doesn't work like Java. It will use as much memory as it needs, rather than Java which lets you set a hard limit on memory usage for an app.

If your process is using 300M, then that's all it's asking for. You can't forcibly increase it if there's nothing to fill it with.

---

### Post by connor99994 on 2012-01-04
Thank you so much! Big life saver haha. :D

---

