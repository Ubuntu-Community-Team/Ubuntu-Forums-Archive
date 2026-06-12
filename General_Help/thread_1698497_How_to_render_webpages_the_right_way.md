---
title: "How to render webpages the right way?"
date: 2011-03-02
forum: General Help
---

### Post by razorblade_mp on 2011-03-02
Hello there,
i love ubuntu, i mean siriously, i love it. 
The only thing that i dont like is the font rendering.
I am a web developer and fonts are crucial to my job.
All i want is firefox to render the fonts just like if im on a windows machine, is this possible? 
For example i install tahoma and microsoft core fonts but in the FF they're not appearing right. This is a straggle to my work and believe me, i 've searched the entrire internet for a solution!

Thanks for any answers and sorry for my english :)

---

### Post by Mariane on 2011-03-02
Have you tried another browser? There is a version of Chrome for Ubuntu, and there are others browsers too, which all display stuff a bit differently. I like seamonkey better than firefox but this is just my personal choice, other people can prefer other browsers. 

If you want to try seamonkey you can install it by typing: 
```

sudo apt-get install seamonkey

```

Mariane

---

### Post by razorblade_mp on 2011-03-02
Oh tha was fast!
Thanks for your advice but i want fonts to work in all the browsers not just firefox or chrome etc.
I have to test my pages in several browsers so change of my basic browser is no a solution.

---

### Post by TeoBigusGeekus on 2011-03-02
Do you have the correct dpi settings?
Right click Desktop>Appearance Settings.

---

### Post by SeijiSensei on 2011-03-02
You're never going to see pages displayed identically on both platforms.  Heck, you won't see pages rendered identically by IE and Firefox both running on Windows.

This issue tends to come up when I'm dealing with someone who has come from a print background.  It's often next-to-impossible to explain to them that HTML was not designed to produce documents that look identical across browsers and platforms.  

I've long ago given up trying to cope with these issues.  I design for Firefox since it's more standards-compliant and platform-independent than IE.  I'll look at a site in IE (running Windows in VirtualBox) to make sure it doesn't look atrocious.  So far, I haven't had major difficulties with my clients, nearly all of whom are using IE.

---

### Post by Mariane on 2011-03-02
OK, but if you install new fonts on your machine this will only solve the problem on your machine, and not on the machines of people reading your web site. 

When Firefox does not have the font it is asked to display it defaults to a another one (this can be specified by the user). You can test different fonts to figure out how they are displayed by several browsers (try "true type" fonts first) and choose one which you like among these which are displayed same way. Also remember that the user can override the default font size - quite a few people don't like small fonts as they find them hard to read. 

Another way, but only for a title or such, is to created the title in a paint program. Then you cut off the unwanted bits and put it online as a picture. With koulourpaint you can set a transparent backgound so the title won't interfer with the background picture. The picture-title will display exactly the same way on every browser - except in the few cases where the user does not want pictures to be displayed. 

Mariane

---

### Post by razorblade_mp on 2011-03-02
Thank you all for your answers!
The dpi is at 96 wicht is nice i think.

The all think is a total headache!
I can't develop something blind folded cause if for example i choose tahoma for the font-family firefox bold it up and the result is very different.
My problem is with the basic fonts, arial, tahoma, verdana etc. the are all wrong.

---

### Post by kostkon on 2011-03-02
> **razorblade_mp said:**
> Thank you all for your answers!
The dpi is at 96 wicht is nice i think.

The all think is a total headache!
I can't develop something blind folded cause if for example i choose tahoma for the font-family firefox bold it up and the result is very different.
My problem is with the basic fonts, arial, tahoma, verdana etc. the are all wrong.
Install the [MS fonts package]("http://packages.ubuntu.com/maverick/ttf-mscorefonts-installer").

---

### Post by razorblade_mp on 2011-03-02
I did this already.I have all the fonts i need. The thing is that firefox dont render them right :/

---

