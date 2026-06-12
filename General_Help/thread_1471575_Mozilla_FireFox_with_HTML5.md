---
title: "Mozilla FireFox with HTML5"
date: 2010-05-03
forum: General Help
---

### Post by jaketheman987 on 2010-05-03
Hello Everyone, I'm fairly new to Linux and everything and still doesn't understand a lot of things about it. But as most of you may know that youtube is probably going to switch to HTML5 (so I heard) and I can not get Firefox to work with it. It is really annoying and I have flash player working but some videos require HTML5. 
Thanks for your considerations to this question
-Jacob

---

### Post by WorMzy on 2010-05-03
HTML5 hasn't been standardised yet (AFAIK), but Fx has some HTML5 support already (such as Canvas support). Can you link to one of these HTML5-only videos?

Also, check this site: [Sketchpad - Online Paint/Drawing application]("http://mugtug.com/sketchpad/")

Does it work? It uses the HTML5 canvas element I just mentioned

---

### Post by jaketheman987 on 2010-05-03
[http://www.youtube.com/watch?v=FNJhOWrDYbE&playnext_from=TL&videos=bpnHtps0_Cw&feature=sub](http://www.youtube.com/watch?v=FNJhOWrDYbE&playnext_from=TL&videos=bpnHtps0_Cw&feature=sub)

Don't worry. I'm not addicted to Pokemon or anything... lol

---

### Post by WorMzy on 2010-05-03
That makes one of us. :P

To me, that video is working, but appears to be  using Flash Player 10 rather than HTML5. Have you got ubuntu-restricted-extras installed?

---

### Post by jaketheman987 on 2010-05-03
I'm not quite sure. Like I said earlier, I'm a straight up n00b. Could you tell me how?

---

### Post by golanbatrac on 2010-05-03
You'll need to use Chrome to view HTML5 video on Youtube.  Firefox uses Ogg Theora format while YouTube uses the patented H.264 format.

---

### Post by WorMzy on 2010-05-03
> **jaketheman987 said:**
> I'm not quite sure. Like I said earlier, I'm a straight up n00b. Could you tell me how?

Open a terminal (Applications -> Accessories -> Terminal) and type:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by jaketheman987 on 2010-05-03
Awesome! Thank you sooo much!

---

### Post by frappe1 on 2010-05-03
On the flip side of the coin, is there any way to completely nuke the HTML5 support from Firefox? Up until now, purging Flash was an easy way to fix the problem. Now, with 5, slow page loads, annoying marketing, and frivolous fluff have become a recognized standard.

---

