---
title: "Calculator bug?"
date: 2009-12-15
forum: General Help
---

### Post by rj123 on 2009-12-15
Hi. 
I was using the calculator on ubuntu 9.10 ( gcalctool )  and I'm having a problem.

I want to use engineering format e.g. 3E-2 that should be 0.03 and if I use the Exp button (that was suppose to be the Exp format) it uses Neper (3e^-2 or np) instead. It is possible calculate using 3 * 10^-2 but is real annoying. Can any one confirm this, or is just me being getting it the wrong way.

---

### Post by rj123 on 2009-12-16
Any one?

---

### Post by synapsys on 2009-12-16
Maybe try calcoo (scientific calculator)

---

### Post by rj123 on 2009-12-16
> **synapsys said:**
> Maybe try calcoo (scientific calculator)

Using that one, it works, but it should be working on the official ubuntu calculator, right?
So you can't do it using the default ubuntu calculator either?

---

### Post by ean5533 on 2009-12-16
> **rj123 said:**
> Using that one, it works, but it should be working on the official ubuntu calculator, right?
So you can't do it using the default ubuntu calculator either?

I'm sure there's a way to do it, but unfortunately I'm not near an Ubuntu machine right now. I can check when I get home from work later tonight.

---

### Post by ean5533 on 2009-12-16
> **rj123 said:**
> Using that one, it works, but it should be working on the official ubuntu calculator, right?
So you can't do it using the default ubuntu calculator either?
Ok, so I finally got home and loaded up gnome-calculator. I set it into "Scientific" mode (View->Scientific) and I had an Exp button to use. I typed:

1 <CLICK EXP BUTTON> - 2 <PRESS ENTER KEY>

And it turned into 0.718281828. Is that what you want it to do?

---

### Post by rj123 on 2009-12-16
> **ean5533 said:**
> Ok, so I finally got home and loaded up gnome-calculator. I set it into "Scientific" mode (View->Scientific) and I had an Exp button to use. I typed:

1 <CLICK EXP BUTTON> - 2 <PRESS ENTER KEY>

And it turned into 0.718281828. Is that what you want it to do?

No when u use 1 <CLICK EXP BUTTON> - 2 <PRESS ENTER KEY>
it's suppose to be 0.01

1E-2 = 0.01
the calculator is assuming Exp buton as e neper number, like:
1e-2 = 0.7182...

I think the calculator isn't working correctly.

To be clear I want to do
1E-2 = 0.01
I don't wanna do 
1e-2 = 0.7182...

Thanks!
;)

---

### Post by ean5533 on 2009-12-16
> **rj123 said:**
> No when u use 1 <CLICK EXP BUTTON> - 2 <PRESS ENTER KEY>
it's suppose to be 0.01

1E-2 = 0.01
the calculator is assuming Exp buton as e neper number, like:
1e-2 = 0.7182...

I think the calculator isn't working correctly.

To be clear I want to do
1E-2 = 0.01
I don't wanna do 
1e-2 = 0.7182...

Thanks!
;)
Ok, I'm an idiot. I have no idea why in my brain I thought, "1*(10^-2).. yep, 0.7182, that's right." I think it's been a long day.

The good news is that I figured out why it's happening, and you're right. If you just type in "1 <EXP> <PRESS ENTER>", it comes out to 2.7182. It was then subtracting two from that number and spitting out 0.7182.

But then if you do, "1 <EXP> 2 <PRESS ENTER>", it correctly spits out 100. It's like it can't handle negative numbers for some reason, and I have no idea why. I sat here for fifteen minutes trying to figure out how to make it play nice and it just won't do it. I'm stumped.

This has got to be a bug, there's no other way to explain how the EXP button does two different things depending on how you happen to use it. I don't know what else to think.

---

### Post by Vaphell on 2009-12-16
gcalctool 5.26 in 9.04 has no problems, 5e-2 gives 0,05
i guess someone has to file a bug

edit:
[https://bugs.launchpad.net/ubuntu/+source/gcalctool/+bug/495551](https://bugs.launchpad.net/ubuntu/+source/gcalctool/+bug/495551)
[https://bugs.launchpad.net/ubuntu/+source/gcalctool/+bug/483730](https://bugs.launchpad.net/ubuntu/+source/gcalctool/+bug/483730)

---

### Post by rj123 on 2010-01-05
Bug corrected with the last gcalctool update. :)

---

### Post by forumid123 on 2010-01-05
Thanks for sharing
 

[IMG]http://tinytwitt.com/content/17/smile.gif[/IMG]

---

