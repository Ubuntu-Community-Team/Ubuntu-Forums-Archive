---
title: "Sharper system and firefox fonts"
date: 2009-10-10
forum: General Help
---

### Post by ashatron on 2009-10-10
Hi all :)
im new to the forum so go easy! Also only installed ubuntu about 2 weeks ago and loving it!! :D

Im sure you've been asked this many times before, but how do i get my fonts to look sharper? on ubuntu intrepid 8.10. 

Im migrating from windows xp (slowly but surely), and the fonts in windows xp are very clear, in ubuntu they are a bit softer, which is OK.

My only gripe is firefox...the fonts dont look as they did on my xp, which is only a problem because im a web designer and need to check how my sites look.

So how do i get my firefox looking as it did on my xp machine?
Making the system fonts in my ubuntu look as clear as they did on xp would be great too.

Ive tried the apperance preferences > Fonts > subpixel smoothing.
i tried many settings in that but no luck.

ive researched and found this - 
[http://ubuntuforums.org/showthread.php?t=20976](http://ubuntuforums.org/showthread.php?t=20976)
but that was written 4 years age and seems complicated, so a more up to date one would be great.

Thanks guys, hope you can help :)

---

### Post by fragos on 2009-10-10
IMHO the Dejavu fonts look better than the default ones. In Appearances you can change them for the system. Most browsers also allow you to select the default fonts for the browser. I also like the subpixel smoothing you've selected.

---

### Post by ashatron on 2009-10-10
Bump!
Someone please help!

Need clearer fonts!

thanks :P

---

### Post by RedRat on 2009-10-10
I have had this problem too! Most of the fonts, kind of look tacky. 

You might want to see if verdana is installed. I have tried the Bitstream fonts and really did not like them. Verdana is a sans serif font, which I prefer. I believe the Verdana fonts might come from the Microsoft font package. Search for a package in Synaptic called 'msttcorefonts', that will include Verdana and other TrueType Fonts. 

My understanding is that Verdana was designed spedifically to be more pleasing at small font sizes. 

I even have Verdana now in my terminal and it plays far better than any other sans serif font on my machine.

---

### Post by oldfred on 2009-10-10
this is a newer version of better fonts:

A Comprehensive Guide to Getting Microsoft Fonts Right in Ubuntu
[http://hawn.be/tag/ubuntu-fonts-msttcorefonts-microsoft-fonts-tahoma-arial-times-new-roman/](http://hawn.be/tag/ubuntu-fonts-msttcorefonts-microsoft-fonts-tahoma-arial-times-new-roman/)

---

### Post by ashatron on 2009-10-11
Thanks all :D

> **oldfred said:**
> this is a newer version of better fonts:

A Comprehensive Guide to Getting Microsoft Fonts Right in Ubuntu
[http://hawn.be/tag/ubuntu-fonts-msttcorefonts-microsoft-fonts-tahoma-arial-times-new-roman/](http://hawn.be/tag/ubuntu-fonts-msttcorefonts-microsoft-fonts-tahoma-arial-times-new-roman/)

That guide doesnt appear to make the fonts sharper, it only changes them to microsfot system fonts.

This is how i want ti to look -
[http://home.comcast.net/~ddamian/ubuntu/howto/firefox_nonaa_ubuntu.png]("http://home.comcast.net/%7Eddamian/ubuntu/howto/firefox_nonaa_ubuntu.png")

---

### Post by Rob_H on 2009-10-11
Did you try adjusting the anti-aliasing and hinting style? I find this makes a huge difference. In KDE, you can adjust this by going to System Settings > Appearance > Fonts. I'm not sure where the equivalent settings live in GNOME (assuming they exist), but maybe someone who uses GNOME can point you to them...?

---

### Post by The Cog on 2009-10-11
In Ubuntu it's System->Preferences->Appearance, then the Fonts tab, then the Details button. Changing the amount of smoothing and hinting makes quite a difference. I have to say, that screenshot looks awful. It looks to me like you have smoothing disabled - all skinny and jaggy. Ugh! Personally, I like Greyscale smoothing with medium hinting.

Note that although most windows change immediately, firefox (or, at least, the one downloaded from Mozilla) needs a restart to use the new fonts.

---

### Post by ashatron on 2009-10-12
im surprised no one knows how to do this :/

Would have thought its requested quite often.

---

### Post by leandromartinez98 on 2009-10-12
> **ashatron said:**
> im surprised no one knows how to do this :/

Would have thought its requested quite often.


Sometimes the problem is the video card driver. Which video card
are you using? Are there restricted drivers available for your
video card? (System -> Administration -> Hardware drivers)

---

### Post by Rob_H on 2009-10-12
> **ashatron said:**
> im surprised no one knows how to do this :/

Would have thought its requested quite often.

No one knows how to do what? Did you try the anti-aliasing and hinting style as suggested?

---

### Post by ashatron on 2009-10-12
i have a geforce go 7900 GTX and im using Nvidia accelerated graphics driver (version 180) 

This is annoying...

---

### Post by ashatron on 2009-10-12
> **Rob_H said:**
> No one knows how to do what? Did you try the anti-aliasing and hinting style as suggested?
I have indeed.

I have access to it as suggest, i had previously tried changin this but to no avail.

As i want sharper fonts i find it best to set the smoothing to "NONE"
and hinting to ""Full"

This makes firefox look GREAT! so thanks.

However this makes my system fonts sharp, but a little messy -
[http://img440.imageshack.us/img440/7752/80597646.png](http://img440.imageshack.us/img440/7752/80597646.png)

The image is showing my firefox tabs, but the same problem applies to my menus throughout ubuntu, Applications, Places, the task bar at the bottom of the screen etc.

---

### Post by ashatron on 2009-10-12
Right,

So for the most part ive got it working.

i installed tahoma,
registered the font

then set all my fonts to tahoma 8pt
Smoothing to none
Hinting to Full

So now my fonts are sharp and great and firefox looks good.
However when browsing the web, large fonts display bizarrely.
hope this image helps -
[http://img11.imageshack.us/img11/5675/screenshotxv.png](http://img11.imageshack.us/img11/5675/screenshotxv.png)

This is clearly because i have smoothing set to none - as i have put smoothing on and it looks ok
this is how it looks with smoothing on -
[http://img18.imageshack.us/img18/2711/smoothingon.png](http://img18.imageshack.us/img18/2711/smoothingon.png)
As you can see the larger fonts look ok, but the small ones are too blurry for me.

[B]So, is it possible to set font smoothing for fonts over a certain size?
Id like to set font smoothing to work only for fonts over 12pt.[/B]

---

### Post by fragos on 2009-10-12
Tahoma was designed by MS for the text display on PDAs and I agree that it is the most readable MS font. Perhaps your issues with larger point sizes relate to the font design. Perhaps beauty is in the eyes of the beholder. IHOM my display gives superior results to your images with the Dejavu fonts and default subpixel multiplexing. My video card is an FX6200 using the same ver 180 driver as you. My monitor is a 1440x900 19 inch widescreen Viewsonic VA1912wb. When running Wine and IE6, to test my web sites, the text display is really terrible for the MS fonts -- clearly a software issue since those same fonts render better in the Linux environment. Note, Web sites that specify fonts will display with their choice and not the defaults you've selected.

---

### Post by ashatron on 2009-10-13
> **fragos said:**
> Tahoma was designed by MS for the text display on PDAs and I agree that it is the most readable MS font. Perhaps your issues with larger point sizes relate to the font design. Perhaps beauty is in the eyes of the beholder. IHOM my display gives superior results to your images with the Dejavu fonts and default subpixel multiplexing. My video card is an FX6200 using the same ver 180 driver as you. My monitor is a 1440x900 19 inch widescreen Viewsonic VA1912wb. When running Wine and IE6, to test my web sites, the text display is really terrible for the MS fonts -- clearly a software issue since those same fonts render better in the Linux environment. Note, Web sites that specify fonts will display with their choice and not the defaults you've selected.
thats not really answered my question in anyway.
And i dont like the Dejavu fonts, i find the soft edges horrible.

> **fragos said:**
> Web sites that specify fonts will display with their choice and not the defaults you've selected.
Thats not completely true, Websites will display the font of their choice (at times), however the smoothing (which is what im asking about) is not chosen by the website.

[B]So, is it possible to set font smoothing for fonts over a certain size?
Id like to set font smoothing to work only for fonts over 12pt.

[/B]thanks :)

---

### Post by Rob_H on 2009-10-13
> **ashatron said:**
> So, is it possible to set font smoothing for fonts over a certain size?
Id like to set font smoothing to work only for fonts over 12pt.

Like this?

---

### Post by ashatron on 2009-10-13
> **Rob_H said:**
> Like this?
YES SIR! THANK YOU SIR!

you are running 9.04 it would appear.
im on 8.10, you dont know how to do it on 8.10 intrepid do you?

---

### Post by Rob_H on 2009-10-13
> **ashatron said:**
> YES SIR! THANK YOU SIR!

you are running 9.04 it would appear.
im on 8.10, you dont know how to do it on 8.10 intrepid do you?

No, sorry. Also, it is Kubuntu (KDE). I don't know if GNOME in 9.04 has this setting.

---

### Post by vinutux on 2009-10-13
in your home folder press Ctrl+H to show hidden files

Open [COLOR="Red"].fonts.conf [/COLOR]with gedit with su

```
sudo gedit /home/Yourusername/.fonts.conf
```


and play with it [Must abck up this file before editing and saving anything]

---

### Post by ashatron on 2009-10-13
> **vinutux said:**
> in your home folder press Ctrl+H to show hidden files

Open [COLOR=Red].fonts.conf [/COLOR]with gedit with su

```
sudo gedit /home/Yourusername/.fonts.conf
```and play with it [Must abck up this file before editing and saving anything]
thank you!
Will try :D

---

### Post by ashatron on 2009-10-14
> **vinutux said:**
> in your home folder press Ctrl+H to show hidden files

Open [COLOR=Red].fonts.conf [/COLOR]with gedit with su

```
sudo gedit /home/Yourusername/.fonts.conf
```and play with it [Must abck up this file before editing and saving anything]

Sorted i think :D
i pasted this in - 

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
 <test compare="more" name="pixelsize" qual="any">
  <double>0</double>
 </test>
 <test compare="less" name="pixelsize" qual="any">
  <double>20</double>
 </test>
 <edit mode="assign" name="antialias">
  <bool>false</bool>
 </edit>
</match>
<!-- UNCOMMENT THIS SECTION TO ENABLE ANTIALIAS FOR BOLD FONTS
<match target="font">
 <test name="weight">
  <const>bold</const>
  <const>black</const>
 </test>
 <edit name="antialias" mode="assign">
  <bool>true</bool>
 </edit>
</match>
-->
<match target="pattern">
            <test qual="any" name="family">
                    <string>Bitstream Vera Sans</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Arial</string>
            </edit>
</match>
    <match target="pattern">
            <test qual="any" name="family">
                    <string>Helvetica</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Arial</string>
            </edit>
</match>
<match target="pattern">
            <test qual="any" name="family">
                    <string>Palatino</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Georgia</string>
            </edit>
</match>
</fontconfig>

LOOK HOW NICE IT LOOKS - 
[http://img126.imageshack.us/img126/6250/screenshot1fr.png](http://img126.imageshack.us/img126/6250/screenshot1fr.png)

YAY :D

---

### Post by flugh on 2009-10-14
I'm guessing the new fonts or configuration hints came from warez-bb.org (on your Bookmarks Toolbar) right? Or do they have a Linux apps section? :-#

I'm not sayin', I'm just sayin', you know, like, I mean, you know what I'm sayin'?

:popcorn:

---

