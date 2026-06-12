---
title: "How to get Ubuntu font for my website?"
date: 2010-10-23
forum: General Help
---

### Post by rcayea on 2010-10-23
As the title asks, how do I obtain Ubuntu font for to use on my website?

Thanks,
Randy

---

### Post by SavageWolf on 2010-10-23
You mean so that your visitors use it? You can't do that, I'm afraid...

---

### Post by rcayea on 2010-10-23
No. I would like to use the font when coding my website. Is that possible?

---

### Post by SeijiSensei on 2010-10-23
The clients need to have the font installed so you can reference it via CSS.  You could use CSS declarations like

```

body    { font-family: Ubuntu, Arial, sans-serif }

```

but this would only work for the tiny minority of visitors who come to your site with a Ubuntu version like 10.10 that natively includes the Ubuntu font.

There are ways to [download fonts to the browser]("http://www.evotech.net/blog/2010/01/font-face-browser-support-tutorial/"), but I've never tried to implement them.

---

### Post by rcayea on 2010-10-23
OK. Thanks for the info. I'll stick with a different font for now.

---

### Post by SavageWolf on 2010-10-23
You mean for your text editor? EDIT: Apparently not...

In gedit (or "Text Editor") go to Edit -> Preferences -> Font
In kate go to Settings -> Configure Kate -> Editor Component -> Fonts & Colours -> Font

I don't know about any more...

---

### Post by crichard on 2010-12-22
> **rcayea said:**
> As the title asks, how do I obtain Ubuntu font for to use on my website?

Thanks,
Randy

It's quite an old thread, but I'm gonna tell you the good news. You can use ubuntu font in your website. I've used it on my site [http://0ccultist.com](http://0ccultist.com) through Google Font API.
For more info, visit here
[http://googland-dev.blogspot.com/2010/12/gd-introducing-ubuntu-font-family-to.html](http://googland-dev.blogspot.com/2010/12/gd-introducing-ubuntu-font-family-to.html)
[http://code.google.com/webfonts/family?family=Ubuntu&subset=latin](http://code.google.com/webfonts/family?family=Ubuntu&subset=latin)

However, I've already changed the web page fonts selections to Ubuntu on my preferred browser Opera. So, other web pages without specific style display all font as Ubuntu family only. :)

---

### Post by colobix on 2010-12-22
> **SavageWolf said:**
> You mean so that your visitors use it? You can't do that, I'm afraid...

This is off-topic but yes you can.
When you make the css file and you choose the font and its settings.
Type in your font's filename (i.e ubuntufont.ttf) and make sure you upload the font to the same folder as your css file. or you can do; /fonts/ubuntufont.ttf.
Or you can do it like this:
font-ubuntu: "Ubuntu Font"; src: url([http://www.example.com/ubuntufont.ttf](http://www.example.com/ubuntufont.ttf))
So there you go.

To change your ubuntu apps font where you are coding the website, just right-click on your desktop, go to "change my background" and from the fonts tap you can change the font there.

---

