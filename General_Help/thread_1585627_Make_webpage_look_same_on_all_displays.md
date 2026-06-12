---
title: "Make webpage look same on all displays"
date: 2010-09-30
forum: General Help
---

### Post by Bucky Ball on 2010-09-30
Hi all,

I have recently put together a website for my local club using Kompozer, Filezilla, and other open-source apps:

[http://wckrsl.org](http://wckrsl.org)

Very simple; no CSS or frames, just tables. My question is this: How do I get the webpage to appear uniform on all displays? When I work on it on my own machine all is looking good, everything nice. But when I go to the club and check on one of their boxes or use a computer somewhere else, things are bent out of shape; the layout is too wide or thin, things are oversized or not, the main heading is on two lines instead of one. A real dog's breakfast.

I learn as I go but one thing I'm figuring is that I should scale my images in Gimp to the desired size rather than drag them to size in Kompozer. 

I have looked for an answer to this, tried a few things adding various code to the page, but nothing so far seems to be working. I'm sure this is simple fix but I just haven't stumbled over it yet.

All help appreciated.

---

### Post by Bucky Ball on 2010-10-03
Well, I tried this. I made a one cell table, set it to 800 pixels wide, and copy/pasted my whole web page into that. Worked a treat but not sure if works on all browsers. 

Could people have a look. The 'West Croydon & Kilkenny RSL/Community Club' should all be on ONE line. 

[http://wckrsl.org](http://wckrsl.org)

Also, the tables I now have inside the 800 pixel wide table; should I set their width to 100% of cell or 800 pixels also? (Or 799?) Suggestions?

---

### Post by bumanie on 2010-10-03
Bucky Ball, it works for me on a 15.4" wide-screen laptop. Only have firefox on ubuntu as the browser, so can't help with others.

---

### Post by Bucky Ball on 2010-10-03
Excellent. That's a promising sign. Thanks bumanie. I have a couple of 17" displays and a 15" laptop. Strange thing is: Two desktops with identical screens, one running Ubuntu and the other Xubuntu, both 8.04, and fine on Ubuntu, heading on two lines with Xubuntu. I resized the window with Ctrl/-  (minus key) and the text stayed on two lines rather than expand to one!

That Xubuntu box has always had a few strange quirks, probably because its a bit of a hybrid. Stable enough though. Checked first thing I had the right fonts installed and they're there. Odd. They have a variety of computers at the club this website is for so might head down there and see what it looks like on their machines.

---

### Post by dcstar on 2010-10-03
> **Bucky Ball said:**
> Hi all,

I have recently put together a website for my local club using Kompozer, Filezilla, and other open-source apps:
........
I have looked for an answer to this, tried a few things adding various code to the page, but nothing so far seems to be working. I'm sure this is simple fix but I just haven't stumbled over it yet.

All help appreciated.

You should submit your web site to one of the many on-line HTML checkers to see if there are any compatibility issues with different browsers/platforms.

Web sites that strictly adhere to the standards usually render the same on almost all environments.

---

### Post by lisati on 2010-10-03
Looks OK on FF 3.6.10 on my laptop. 

One observation: the credits at the bottom were a bit hard for me to read, maybe a background for that text only that provides a bit of contrast might be useful.

---

### Post by Bucky Ball on 2010-10-03
> **dcstar said:**
> You should submit your web site to one of the many on-line HTML checkers to see if there are any compatibility issues with different browsers/platforms.

Web sites that strictly adhere to the standards usually render the same on almost all environments.

Thanks for that. As I learn about doing this I have noticed there's a set of standards. Great suggestion, I'll dig deeper.

> **lisati said:**
> Looks OK on FF 3.6.10 on my laptop. 

One observation: the credits at the bottom were a bit hard for me to  read, maybe a background for that text only that provides a bit of  contrast might be useful.

Good news. It's sounding as if this might have worked! And thanks for the suggestion about the credits, Lisati

---

### Post by sendblink23 on 2010-10-03
Bucky Ball... for cross browsing....  you need windows
*I'm kidding with you

It looks fine for me ;)

Oh...  hmm the Gallery - is it a private *facebook area?
Isn't there like a share album link for non facebook members to view them?

---

### Post by Bucky Ball on 2010-10-03
Thanks for that sendblink23. I'll check on the facebook settings. I fiddled and thought I had made it public but I'll have another look.

Wondering if all could do me another favour. Further down the home page is a 'Bowls Entrance' sign, a photo and a 'Petanque Entrance' sign. Are they all in one row straight across the page? That is the only other thing that is showing up oddly on my Xubuntu box but not everything else. Appreciate all your comments and help. :)

---

### Post by Bucky Ball on 2010-10-03
Thanks for that sendblink23. I'll check on the facebook settings. I  fiddled and thought I had made it public but I'll have another look.

Wondering if all could do me another favour. Further down the home page  is a 'Bowls Entrance' sign, a photo and a 'Petanque Entrance' sign. Are  they all in one row straight across the page? That is the only other  thing that is showing up oddly on my Xubuntu box but not the other  computers. Appreciate all your comments and help. :smile:

Despite my Xubuntu box issues I'm thinking that putting creating a one  cell table, setting the width of the table, and putting the lot in that  cell was the fix for someone in my predicament.

---

