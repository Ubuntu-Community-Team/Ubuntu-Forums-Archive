---
title: "Japanese &amp; Chinese fonts in Firefox are erratic"
date: 2009-11-01
forum: General Help
---

### Post by GoGoGulliver on 2009-11-01
In Firefox, kanji come out all jagged. This also applies to Chinese hanzi characters. In Epiphany, this doesn't happen!  At all! It's a fairly minor thing, but it annoys me every time I go online and read Japanese. I would use Epiphany all the time, were it not prone to crashing reliably on livemocha.com (on which I am learning Chinese).

I've tried everything sensible (editing fonts.conf in various ways after some creative forum searching and googling, installing new fonts), but it still looks like this:[IMG]http://dl.getdropbox.com/u/2078257/FF-Ep-Kanji.png[/IMG]
Any suggestions>

---

### Post by NanoPC on 2009-11-02
In Firefox you can choose the font you want for japanese (preferences>content). I have Meiryo for japanese, is the one I like most.

---

### Post by Dakanya on 2009-11-07
I've been having this problem in every program I've used so far even after installing MS Gothic and MS Mincho but I use Pidgin instead of Empathy.

[s]EDIT: After some research, I realized that before Karmic Koala, you were able to prioritize the fonts you wanted by editing ~/.fonts.conf but this file doesn't exist in Karmic.[/s]

EDIT: X interprets .fonts.conf differently now, see: [http://bit.ly/Ef3y1](http://bit.ly/Ef3y1)
      Editing /etc/fonts/conf.d/ may be easier? 
      configuring CJK fonts in Karmic is lame due to the new change

---

### Post by Dakanya on 2009-11-08
I found a working solution today: sudo apt-get remove ttf-wqy-zenhei

[http://ubuntuforums.org/showpost.php?p=8268282&postcount=3](http://ubuntuforums.org/showpost.php?p=8268282&postcount=3)

---

### Post by 1stdayonthejob on 2009-11-29
> **Dakanya said:**
> I found a working solution today: sudo apt-get remove ttf-wqy-zenhei

[http://ubuntuforums.org/showpost.php?p=8268282&postcount=3](http://ubuntuforums.org/showpost.php?p=8268282&postcount=3)

So just by removing this font the font issues are fixed?  Is there a need to edit conf.d and/or .fonts.config still?  Would this work if I want to use English locale as default?  I'm thinking of installing Ubuntu and would like to know these font issues are fixable before I take the plunge.

---

### Post by SilvereX on 2009-12-17
It's not necessary to uninstall the font. Fontconfig in Ubuntu is explicitly configured for this behaviour.

The fix (in *karmic*):

```
rm /etc/fonts/conf.d/66-wqy-zenhei-sharp.conf
```

(This command removes a symlink to the actual configuration file ../conf.avail/66-wqy-zenhei-sharp.conf where it's explicitly specified that fonts named *WenQuanYi Zen Hei*, &#25991;&#27849;&#39551;&#27491;&#40657; or &#25991;&#27849;&#39515;&#27491;&#40657; are not antialiased, but rather their embedded bitmaps are used for rendering.)

---

