---
title: "Fonts in Opera look terrible."
date: 2010-03-21
forum: General Help
---

### Post by sports fan Matt on 2010-03-21
I have Opera & Firefox set up about the same and this is the result I get in Opera: [http://my.opera.com/community/forums/topic.dml?id=436181](http://my.opera.com/community/forums/topic.dml?id=436181)

Firefox: [http://my.opera.com/community/forums/topic.dml?id=436181](http://my.opera.com/community/forums/topic.dml?id=436181)

How can I change this?  I accidently removed the font config from [http://ubuntuforums.org/showthread.php?t=837528&highlight=opera](http://ubuntuforums.org/showthread.php?t=837528&highlight=opera)

and used these commands: Then I found a blog that said to write in terminal:
cd /etc/fonts/conf.d
sudo rm 10-hinting-medium.conf
sudo rm 10-no-sub-pixel.conf
sudo ln -s ../conf.avail/10-hinting-full.conf

Which screwed up my fonts..Can anyone help?

---

### Post by howefield on 2010-03-21
I am trying to view your results but the links seems incorrect ?

---

### Post by sports fan Matt on 2010-03-21
They may look like duplicates.  Here is what I'm seeing in Opera. [http://my.opera.com/community/forums/topic.dml?id=436181](http://my.opera.com/community/forums/topic.dml?id=436181)

It seems very light compared to the rest of pages because in messing with my font settings from above, I think i deleted some font settings, or it may be an issue with incorrect hinting.  I'm not sure.

---

### Post by howefield on 2010-03-21
Should the links lead to an image describing your problem ?

For me they only go to the Opera forum, which I can browse and move around in. Perhaps it is Chrome, I'll try the links in Firefox.

Edit:
No difference in Firefox..

---

### Post by sports fan Matt on 2010-03-21
Not an image, but the difference in clarity (light letters in opera versus semidark in Firefox)

---

### Post by sanderd17 on 2010-03-21
We can't see the difference if there is somthing wrong with your opera browser unless you post an image. I don't think I'll be able to help but if you don't post an image, nobody will. 

To take a screenshot just press the prtsc key on you keyboar, wait a while and save the image.

---

### Post by sports fan Matt on 2010-03-21
Sorry about that it's been a long day.  

Screenshot is how opera looks
Screenshot1 is firefox

---

### Post by sports fan Matt on 2010-03-21
This is fixed..although I have no idea how I fixed it.  I suspect I reconfigured fonts or created a new .fonts conf in /home

---

### Post by Rasa1111 on 2010-03-21
glad you got it. ...

also...  is it just me..........  or do images displayed in opera... look terrible? 

every time i have ever used opera, on any computer....

 the images are very pixelated and look like total crap. 

yet i open firefox... and the images look perfectly fine. 

Ive long wondered...
 Is this just my experience?  or is that just how opera is?

 ive played with all kinds of settings... but no go.  lol

---

### Post by chillicampari on 2010-03-21
> **Rasa1111 said:**
> glad you got it. ...

also...  is it just me..........  or do images displayed in opera... look terrible? 

every time i have ever used opera, on any computer....

 the images are very pixelated and look like total crap. 

yet i open firefox... and the images look perfectly fine. 

Ive long wondered...
 Is this just my experience?  or is that just how opera is?

 ive played with all kinds of settings... but no go.  lol

Do you have Turbo mode on? If so, try turning that off.

---

