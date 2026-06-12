---
title: "make words permanently larger on ubuntu"
date: 2010-05-08
forum: General Help
---

### Post by tomsubt on 2010-05-08
Hi, is there anyway to make the words larger permanently when using ubuntu 10.04  I always have to use the Ctrl + keys to enlarge but thats not permanent? Thanks

---

### Post by meho_r on 2010-05-08
What words? Where? In a particular application or in general?

---

### Post by dagdeniz on 2010-05-08
I'm not sure if you mean that but...

when on desktop right click> change desktop background > fonts > application font - select any weight and size you want.

---

### Post by lecterror on 2010-05-08
Hm, "words" is a big vague, isn't it? :)

If you mean text in Firefox, I recommend you install a great add on called NoSquint:

[http://urandom.ca/nosquint/](http://urandom.ca/nosquint/)

It remembers your zoom settings for all the sites.

If you're not talking about Firefox, you're going to have to help us with a bit more info..;)

---

### Post by tomsubt on 2010-05-08
Sorry, I should have explained further, I mean in general and Firefox, my eyesight is not that good and the words are extremely small, there not that bad on windows though.
Thanks for the tip, I will look into firefox

---

### Post by dino99 on 2010-05-08
i'm frequently using this feature, ctrl+ or ctrl+ mouse wheel, and when i reboot these settings are automaticly loaded, thats mean on your end that they are not saved. You might have some errors into .xsessions or into /var/logs (system admin log viewer)

try : sudo dpkg --configure -a

---

### Post by tomsubt on 2010-05-08
Thanks I tried >>> sudo dpkg --configure -a

and nothing happened, do i have the sudo correct?

also unbuntu does not save my login, it never did?

---

### Post by tomsubt on 2010-05-08
Ok, I am using No Squint in firefox and it seems to work great but on ubuntu (as on this forum) the words are really small and the Ctrl++ reverts back to the small print when closing out and coming back on ubuntu! Any way of locking in the larger words so when I close out and come back they will still be enlarged on ubuntu? Thanks

---

### Post by louieb on 2010-05-08
Have you set System>Preferences>Appearance>Fonts Tab to your liking?  

Older guy here - older eyes too. The above + no squint - works for most of what I do.

---

### Post by fooman on 2010-05-08
> **tomsubt said:**
> Ok, I am using No Squint in firefox and it seems to work great but on ubuntu (as on this forum) the words are really small and the Ctrl++ reverts back to the small print when closing out and coming back on ubuntu! Any way of locking in the larger words so when I close out and come back they will still be enlarged on ubuntu? Thanks

to adjust no squint for ubuntu forums....first make sure you are on the forums site,  then look for a magnifying glass in the bottom right corner of the firefox window.  right-click on it and choose *site settings* from the menu.

adjust the text zoom level as desired.

---

### Post by tomsubt on 2010-05-08
louieb, I did as you mentioned and I can see Great now  Thank You

Fooman, I was just ready to reply that everything was much better now but I cannot see larger words on this forum and your email reply was just in time, did as you said, and I see great here now too, Thank You all for the replys

---

### Post by wvxvw on 2010-05-15
Hello, similar problem here... but not exactly the same.
Zoom scales the graphics too, so the layout gets fuzzy and worst yet, not all the fonts scale. Say and the site defines the font's height in pixels, then if I try to override the site defined CSS, I would either not see half of the text on the site, or I'll start having other bugs in layout (especially if all sorts of overflow-hidden are used).
[rant]
Lastly, I really hate antialized fonts. I don't understand who would want to use rasterized vector fonts for small text...
I've tried Opera, Chrome and Firefox and neither will use bitmap fonts for rendering the site content... so, is there any other browser (probably an older one) that would accept bitmap fonts? 
[/rant]
Or, is there any way to make either of the modern browsers to never use antialiazing?
Oh, forgot to mention this: I'm on Ubuntu Lucid Linux.

*[COLOR="Silver"]Something I would never understand... bitmap fonts worked perfectly! No one complained about that, why try to improve something that just works good...[/COLOR]*

---

