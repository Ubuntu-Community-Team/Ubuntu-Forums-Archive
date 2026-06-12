---
title: "GIMP 2.7.4 Error"
date: 2012-02-06
forum: General Help
---

### Post by ssherwood on 2012-02-06
Hiya Ubuntu Users,

I am wondering if anyone can help me with a little issue I have with the GNU Image Manipulation Program --GIMP--.

The error that I am having is I cannot use any of the fonts pre-installed and installed by me as when I click on the font icon to change the font GIMP automatically closes without any error message.

It is bugging me as I cannot do any web design or simple images for my college work and my projects.

Any & All help will be appreciated.

Thanks Stephen. ssherwood

---

### Post by uRock on 2012-02-06
Start GIMP via the command line to see what error messages come up when it errors out. To do this, open a Terminal and enter **gimp**, then copy and paste the output here.

---

### Post by bluexrider on 2012-02-06
Using version 2.6.11 and not having any issues. May consider having a bug issue. 

Sorry, you filled to mention what Ubuntu version and platform you are using.

---

### Post by ssherwood on 2012-02-06
> uRock

Start GIMP via the command line to see what error messages come up when it errors out. To do this, open a Terminal and enter gimp, then copy and paste the output here.

OUTPUT

```

[COLOR="Red"](gimp:3145): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'TeX Gyre Adventor Bold 16'

(gimp:3145): Pango-WARNING **: font_face status is: out of memory

(gimp:3145): Pango-WARNING **: scaled_font status is: out of memory
gimp: fatal error: Segmentation fault
gimp (pid:3145): [E]xit, [H]alt, show [S]tack trace or [P]roceed: p

(script-fu:3152): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error[/COLOR]


```

> bluexrider

Using version 2.6.11 and not having any issues. May consider having a bug issue. 

Sorry, you filled to mention what Ubuntu version and platform you are using.


OS: Ubuntu 11.10;
Architecture: x32;


Thanks Guys...

---

### Post by Rodney9 on 2012-02-06
This section attempts to give you a helpful overview.

[http://docs.gimp.org/en/gimp-using-fonts.html](http://docs.gimp.org/en/gimp-using-fonts.html)

For the most authoritative and up-to-date information on fonts in GIMP, consult the &#8220;[Fonts in GIMP 2.0]("http://docs.gimp.org/en/bibliography.html#bibliography-online-gimp-fonts")&#8221; page [GIMP-FONTS] at the GIMP web site. 

Rodney

---

### Post by ssherwood on 2012-02-06
Thanks Rodney9, I'll Take a look at that.

P.S Do you prefer Lubuntu to Ubuntu GUI Wise and speed...

---

### Post by ssherwood on 2012-02-07
Thanks you guys for your suggestions and support. I have now fixed the error with gimp and found the font which had been causing the issue.

Again thanks,

Stephen

---

### Post by Rodney9 on 2012-02-07
> **ssherwood said:**
> Thanks Rodney9, I'll Take a look at that.

P.S Do you prefer Lubuntu to Ubuntu GUI Wise and speed...

Yes I sure do, I'm bit old school and love the minimal setup. Lubuntu is mainly targeted at old machines, but on newer ones it fly's.

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by ssherwood on 2012-02-08
Thanks I'll Take a look at it.

Stephen

---

