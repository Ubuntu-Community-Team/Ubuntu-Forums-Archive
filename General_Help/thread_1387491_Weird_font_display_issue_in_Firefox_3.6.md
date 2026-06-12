---
title: "Weird font display issue in Firefox 3.6"
date: 2010-01-21
forum: General Help
---

### Post by bluelamp999 on 2010-01-21
Hello

I've installed (without issue) Firefox 3.6 from the Ubuntuzilla repository - [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation).

However, there's an issue with text in web pages. There's a weird greenish-blue shadow/interference effect visible, especially with words that have sequential vertical characters (e.g. Moz*ill*a.)

If you check out the following screen shots, you'll see what I'm on about...

Firefox 3.5.7 - [http://imgur.com/8WwZK.png]("http://imgur.com/8WwZK.png")

Firefox 3.6 - [http://imgur.com/g2s6L.png]("http://imgur.com/g2s6L.png")

If you examine both, you'll see a definite greenish tinge in the 3.6 image as mentioned above. This is most noticeable in the word 'will'.

Is anybody else seeing this behaviour? Any ideas how to resolve?

This is on an 1280x1024 LCD (Dell 1906FP ) and the TFT of my laptop.

Cheers

---

### Post by lovinglinux on 2010-01-21
Try this:

```
gedit ~/.fonts.conf
```

then replace the content of that file with this:

```
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

Save it and restart Firefox.

Please report if that works or not. It seems this will be a very common question.

---

### Post by bluelamp999 on 2010-01-21
> **lovinglinux said:**
> Try this:

```
gedit ~/.fonts.conf
```

then replace the content of that file with this:

```
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

Save it and restart Firefox.

Please report if that works or not. It seems this will be a very common question.

Zounds!!! It worked!

Funny thing is, I tried that when I had the issue on on my first 3.6 install with no success. I only re-installed 3.6 to get the screen shot for this post...

However, all seems well now. Thank you!

Btw, I've noticed that you've been performing outstanding work on the forums this evening - kudos and kharma to you.

---

### Post by lovinglinux on 2010-01-21
> **bluelamp999 said:**
> Zounds!!! It worked!

Funny thing is, I tried that when I had the issue on on my first 3.6 install with no success. I only re-installed 3.6 to get the screen shot for this post...

However, all seems well now. Thank you!

You are welcome. I have included this on the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).


> **bluelamp999 said:**
> Btw, I've noticed that you've been performing outstanding work on the forums this evening - kudos and kharma to you.

Thank you very much.

---

### Post by nanotube on 2010-01-22
> **bluelamp999 said:**
> Hello

I've installed (without issue) Firefox 3.6 from the Ubuntuzilla repository - [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation).

However, there's an issue with text in web pages. There's a weird greenish-blue shadow/interference effect visible, especially with words that have sequential vertical characters (e.g. Moz*ill*a.)

If you check out the following screen shots, you'll see what I'm on about...

Firefox 3.5.7 - [http://imgur.com/8WwZK.png]("http://imgur.com/8WwZK.png")

Firefox 3.6 - [http://imgur.com/g2s6L.png]("http://imgur.com/g2s6L.png")

If you examine both, you'll see a definite greenish tinge in the 3.6 image as mentioned above. This is most noticeable in the word 'will'.

Is anybody else seeing this behaviour? Any ideas how to resolve?

This is on an 1280x1024 LCD (Dell 1906FP ) and the TFT of my laptop.

Cheers

hey, i know you've already solved the problem and all... but i just wanted to say that for the life of me i can't see even a bit of difference between the two screenshots you posted (besides that one is shifted a little position-wise relative to the other). 

maybe my eyes are not what they used to be... :)

---

### Post by bhagwad on 2010-01-22
It works! Thanks a whole bunch!

---

### Post by lovinglinux on 2010-01-22
> **nanotube said:**
> hey, i know you've already solved the problem and all... but i just wanted to say that for the life of me i can't see even a bit of difference between the two screenshots you posted (besides that one is shifted a little position-wise relative to the other). 

maybe my eyes are not what they used to be... :)

They both have the same problem.

---

### Post by nanotube on 2010-01-22
> **lovinglinux said:**
> They both have the same problem.

haha so that's why i couldn't see any difference, that explains it all. :) 

i see the green thing shadows in both easily, at that magnification. :)

---

### Post by bluelamp999 on 2010-01-22
> **nanotube said:**
> haha so that's why i couldn't see any difference, that explains it all. :) 

i see the green thing shadows in both easily, at that magnification. :)

I can see a definite difference between them, must be my display (maybe?)

But as far as I'm concerned the issue is fixed for me...

---

### Post by Michalxo on 2010-01-23
Hello! I am having the same problem as guy in post #1. Although it did not help to **make** ~/.fonts.conf and paste there that xml dtd code :-(
Any another advices please?
Karmic 9.10 here
Thank You


edit: I have tried this workaround [http://ubuntuforums.org/showthread.php?p=7094387](http://ubuntuforums.org/showthread.php?p=7094387) with no success :-(

---

### Post by dcstar on 2010-01-23
> **lovinglinux said:**
> 
.........
Please report if that works or not. **It seems this will be a very common question.**

Ever since FF 3.5 when they decided to no longer use the actual Gnome font aliasing settings you set for the rest of your Ubuntu system - which still actually works in FF 3.0.x.

It is a common question because the FF developers basically broke the link between FF and the way Ubuntu controls these things.

---

### Post by yyka on 2010-01-24
[delete this plz], don't know how to delet]

---

### Post by yyka on 2010-01-24
> **lovinglinux said:**
> Try this:

```
gedit ~/.fonts.conf
```

then replace the content of that file with this:

```
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

Save it and restart Firefox.

Please report if that works or not. It seems this will be a very common question.

hey, ! big up for your tip !

"works like a charm " as  you say in Usa :), very good , I'm search for this for about 2 days ! your .fonts.conf is excelent for me.....

[[img]http://i.imagehost.org/t/0419/Capture-2.jpg[/img]](http://i.imagehost.org/view/0419/Capture-2)

thanks you

---

### Post by lovinglinux on 2010-01-24
> **yyka said:**
> hey, ! big up for your tip !

"works like a charm " as  you say in Usa :), very good , I'm search for this for about 2 days ! your .fonts.conf is excelent for me.....

[[img]http://i.imagehost.org/t/0419/Capture-2.jpg[/img]](http://i.imagehost.org/view/0419/Capture-2)

thanks you

You are welcome. It isn't actually mine. I took that from the forums a while back and can remember from where. So I just posted the one I use :)

---

### Post by Michalxo on 2010-01-24
Ok, so no help from that you posted :-(
Making .fonts.conf and rebuilding fonts made it actually even worse in firefox 3.6 and 3.7 I removed .fonts.conf and rebuilded again. So, now I have ugly fonts in 3.6 but normal in 3.7. Any other guesses how to fix that? :-/

Attached image: 3.7 vs 3.6

---

### Post by lovinglinux on 2010-01-24
> **Michalxo said:**
> Any other guesses how to fix that? :-/

Nope. :oops:

---

### Post by yyka on 2010-01-24
[QUOTE=. So, now I have ugly fonts in 3.6 but normal in 3.7. Any other guesses how to fix that? :-/

[/QUOTE]

so only use firefox 3.7 :), why not ?

---

### Post by Joey B. on 2010-01-24
>  hey, ! big up for your tip !

"works like a charm " as  you say in Usa :smile:, very good , I'm search for this for about 2 days ! your .fonts.conf is excelent for me.....

[[IMG]http://i.imagehost.org/t/0419/Capture-2.jpg[/IMG]]("http://i.imagehost.org/view/0419/Capture-2")

thanks you
I can't really tell the difference.

---

### Post by Michalxo on 2010-01-24
> **yyka said:**
> so only use firefox 3.7 :), why not ?

I am using chromium, but I prefer "stable" releases a bit more over instable and 3.7 is not that good... and this problem may arise in more PCs then only in mine.. I can be wrong though ;-)

lovinglinux - thanks anyway ;-)

---

### Post by Michalxo on 2010-01-25
Interesting thing is, that I have similar ugly fonts in VLC too.

---

### Post by spiritofelric on 2010-01-25
> **Michalxo said:**
> Interesting thing is, that I have similar ugly fonts in VLC too.

That's the issue i'm having.  I started a new post:
[http://ubuntuforums.org/showthread.php?p=8723391](http://ubuntuforums.org/showthread.php?p=8723391)

---

### Post by omne on 2010-01-30
Same probleme here. It’s beter with the .fonts.conf but it looks like firefox 3.7 (and 3.5) got better fonts than 3.6.

---

### Post by Michalxo on 2010-02-01
Please, remove tag "[SOLVED]" please. Thanks.

---

### Post by hugmenot on 2010-02-01
Heh ,you just disabled subpixel rendering. You could have achieved that via the font preferences, and it might not even be what people ask for.

The problem is a bug in Firefox that ignores Ubuntu’s better choice of LCD filter.

---

### Post by mfortunat on 2010-02-04
Hi all,

I'm currently using an LCD display, so I did some little changes to the originally posted .fonts.conf file.
My file is:

```
<?xml version='1.0'?>
 <!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
 <fontconfig>
  <match target="font" >
   <edit mode="assign" name="rgba" >
    <const>rgb</const>
   </edit>
  </match>
  <match target="font" >
   <edit mode="assign" name="hinting" >
    <bool>true</bool>
   </edit>
  </match>
  <match target="font" >
   <edit mode="assign" name="hintstyle" >
    <const>**hintfull**</const>
   </edit>
  </match>
[B]  <match target="font" >
   <edit mode="assign" name="lcdfilter" >
    <const>lcddefault</const>
   </edit>
  </match>[/B]
  <match target="font" >
   <edit mode="assign" name="antialias" >
    <bool>true</bool>
   </edit>
  </match>
 </fontconfig>

```

and it works perfectly with FF 3.6 on Ubuntu 9.10

Fore more info take a look at: [http://fontconfig.org/fontconfig-user.html]("http://fontconfig.org/fontconfig-user.html")

---

### Post by gm112 on 2010-02-07
> **mfortunat said:**
> Hi all,

I'm currently using an LCD display, so I did some little changes to the originally posted .fonts.conf file.
My file is:

```
<?xml version='1.0'?>
 <!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
 <fontconfig>
  <match target="font" >
   <edit mode="assign" name="rgba" >
    <const>rgb</const>
   </edit>
  </match>
  <match target="font" >
   <edit mode="assign" name="hinting" >
    <bool>true</bool>
   </edit>
  </match>
  <match target="font" >
   <edit mode="assign" name="hintstyle" >
    <const>**hintfull**</const>
   </edit>
  </match>
[B]  <match target="font" >
   <edit mode="assign" name="lcdfilter" >
    <const>lcddefault</const>
   </edit>
  </match>[/B]
  <match target="font" >
   <edit mode="assign" name="antialias" >
    <bool>true</bool>
   </edit>
  </match>
 </fontconfig>

```and it works perfectly with FF 3.6 on Ubuntu 9.10

Fore more info take a look at: [http://fontconfig.org/fontconfig-user.html](http://fontconfig.org/fontconfig-user.html)

Thank you for that post :P. It definitely helped improve the text rendering a bit.. Shame that the font mysteriously had to "go bad" on us :|..

---

### Post by Michalxo on 2010-02-07
> **hugmenot said:**
> Heh ,you just disabled subpixel rendering. You could have achieved that via the font preferences, and it might not even be what people ask for.

The problem is a bug in Firefox that ignores Ubuntu’s better choice of LCD filter.

If you'd read the whole thread, you'll see that this bug is not in Firefox only, but in VLC and other apps. :-(
I can see the difference between using and not using .fonts.conf. This is clearly some bigger bug... :-(
I am unable to just click it in Font preferences. My font preferences are unchanged :-( 
Sadly. Bug must be somewhere else :-(

---

### Post by lovinglinux on 2010-02-17
> **Michalxo said:**
> If you'd read the whole thread, you'll see that this bug is not in Firefox only, but in VLC and other apps. :-(
I can see the difference between using and not using .fonts.conf. This is clearly some bigger bug... :-(
I am unable to just click it in Font preferences. My font preferences are unchanged :-( 
Sadly. Bug must be somewhere else :-(

I'm experiencing this problem on every gtk application since I upgraded KDE to 4.4 version. The .fonts.conf file actually works, but I can't get the fonts to look like the ones on KDE applications.

---

### Post by Michalxo on 2010-02-22
> **lovinglinux said:**
> I'm experiencing this problem on every gtk application since I upgraded KDE to 4.4 version. The .fonts.conf file actually works, but I can't get the fonts to look like the ones on KDE applications.

Exactly my problem apart from fact that I am using gnome and it happens not only in KDE apps. Dunno what is the cause of this bug :-( I'll probably move to lucid soon, so let's see by then...

---

### Post by Michalxo on 2010-02-28
Interesting thing is, that I had similarly weird font in 10.04 Lucid Alpha 3 firefox too. Is it just a coincidence?? (I think it was in firefox 3.6.2-pre)

---

### Post by Michalxo on 2010-04-06
Nice! After yesterdays Firefox update (Namaroka turned to Firefox 3.6.3) whole text and fonts went back to great again! :-) Yipee :-)
Now it's really Solved :-)

---

