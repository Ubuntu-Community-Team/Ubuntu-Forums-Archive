---
title: "HOWTO: Move the Minimize/Maximize/Close Buttons back the Right Side"
date: 2010-04-29
forum: General Help
---

### Post by motersho on 2010-04-29
If you are like me, you can't stand the new placement of the Minimize, Maximize, and Close buttons.  

Here is a useful how to guide, with screen shots, on how to put them back on the right side:

[http://motersho.com/blog/index.php/2010/03/08/fix-minimizemaximizeclose-button-order-in-ubuntu-10-04-lucid-lynx/]("http://motersho.com/blog/index.php/2010/03/08/fix-minimizemaximizeclose-button-order-in-ubuntu-10-04-lucid-lynx/")

---

### Post by antenna on 2010-04-29
Or more simply, change the theme.

---

### Post by Uncle Spellbinder on 2010-04-29
> **antenna said:**
> Or more simply, change the theme.
Unless you really like the theme but hate the buttons on the left.


**Edit:**
The quickest, easiest way to put the buttons back *where they belong* is with Ubuntu Tweak...

[COLOR="DarkRed"][SIZE="1"]**Click Image To Enlarge**[/SIZE][/COLOR]
[[IMG]http://content.imagesocket.com/thumbs/ButtonsOnRight09dc8a.jpeg[/IMG]](http://content.imagesocket.com/images/ButtonsOnRight09dc8a.jpeg)

---

### Post by svenskmand on 2010-05-01
> **Uncle Spellbinder said:**
> Unless you really like the theme but hate the buttons on the left.


**Edit:**
The quickest, easiest way to put the buttons back *where they belong* is with Ubuntu Tweak...

[COLOR="DarkRed"][SIZE="1"]**Click Image To Enlarge**[/SIZE][/COLOR]
[[IMG]http://content.imagesocket.com/thumbs/ButtonsOnRight09dc8a.jpeg[/IMG]](http://content.imagesocket.com/images/ButtonsOnRight09dc8a.jpeg)
Could you then please explain how to install this "Ubuntu Tweak" program? I could not find it in the repository :S

---

### Post by kaibob on 2010-05-01
> **motersho said:**
> If you are like me, you can't stand the new placement of the Minimize, Maximize, and Close buttons.  

Here is a useful how to guide, with screen shots, on how to put them back on the right side:

[http://motersho.com/blog/index.php/2010/03/08/fix-minimizemaximizeclose-button-order-in-ubuntu-10-04-lucid-lynx/]("http://motersho.com/blog/index.php/2010/03/08/fix-minimizemaximizeclose-button-order-in-ubuntu-10-04-lucid-lynx/")

I had previously moved the buttons back to the right side by changing the colon, but the buttons were in the wrong order. As a result, I kept closing the window when I wanted to maximize it and maximized the window when I wanted to close it. After looking at the how-to, I realized that you can easily reorder the buttons by changing the text. So, all is well.

Thanks for the post.

---

### Post by alvevind on 2010-05-01
Another easy way to get the window buttons back on the right and in the standard order is to install the right aligned theme:

Step-by-step procedure:
1. Download the modified theme [http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz](http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz)
2. Open the menu "System" > "Preferences" > "Appearance"
3. Click the button "Install"
4. Open the folder "Downloads"
5. Select the file "Ambience_Radiance-Right.tar.gz"
6. Click "Open"
7. Select the new theme "Ambiance-right"

You then have both the standard unmodified left-aligned theme and the right-aligned theme available and can easily switch back and forth between them with a single click, without adjusting the button position every time.

---

### Post by Topher88 on 2010-05-01
> **Uncle Spellbinder said:**
> Unless you really like the theme but hate the buttons on the left.


**Edit:**
The quickest, easiest way to put the buttons back *where they belong* is with Ubuntu Tweak...

[COLOR=DarkRed][SIZE=1]**Click Image To Enlarge**[/SIZE][/COLOR]
[[IMG]http://content.imagesocket.com/thumbs/ButtonsOnRight09dc8a.jpeg[/IMG]]("http://content.imagesocket.com/images/ButtonsOnRight09dc8a.jpeg")

Wow, that was easy!  I like this program.

And to the person asking where to find it...  [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by linuxman94 on 2010-05-01
By far the easiest way is to use this python script.  Simply download it, change it's permissions to allow executing it, and double click it.

[IMG]http://lh6.ggpht.com/_FJH0hYZmVtc/S5bF_mfdfnI/AAAAAAAAGdw/-XSZh2wOONI/s1600-h/unknown_007%5B2%5D.png[/IMG]

[IMG]http://lh3.ggpht.com/_FJH0hYZmVtc/S5bGBSObTaI/AAAAAAAAGd4/yGvPM34G_RY/s1600-h/Selection_006%5B2%5D.png[/IMG]

---

### Post by stchman on 2010-05-05
Do the following to get the minimize, maximize, and close on the right side in the right order.

Hit ALT - F2

Type gconf-editor

Go to the following:

apps --> metacity --> general

Find the button_layout parameter, right mouse click, and select Edit Key

Change the value to the following:

:minimize,maximize,close

Don't forget the colon on the left side of the text.

You will then have it the way you are used to it.

---

### Post by meldroc on 2010-05-05
Good tip.

I personally arrange my buttons differently - with close on the left, and minimize & maximize on the right.

That makes it less likely you'll accidentally close a window when you meant to maximize it.

the line in gconf-editor, in this case would be "close:minimize,maximize"

---

### Post by meldroc on 2010-05-05
Or if you're feeling especially evil (DON'T DO THIS - YOU'LL GET STABBED IF YOU DO), you could change the line to ":minimize,close,maximize" and see how long it takes for the user to notice...

---

### Post by DomesDKG on 2010-05-05
The theme changing approach is officially considered to be the "correct" approach, according to the forum sticky FAQ.

While there is currently no problem with changing the icons to the left using the metacity method, it stands to break a future feature, windicators.  Read about it here: [http://www.markshuttleworth.com/archives/333](http://www.markshuttleworth.com/archives/333)

Go about it whichever way you want, but if you use a method other than the theme changing method, make a mental note of it in case it causes problems for you in the future.

---

### Post by c2x on 2010-05-06
> **stchman said:**
> Do the following to get the minimize, maximize, and close on the right side in the right order.

Hit ALT - F2

Type gconf-editor

Go to the following:

apps --> metacity --> general

Find the button_layout parameter, right mouse click, and select Edit Key

Change the value to the following:

:minimize,maximize,close

Don't forget the colon on the left side of the text.

You will then have it the way you are used to it.


Thanks Man! Easiest way to do it!

---

### Post by philinux on 2010-05-06
Except.

See General Help forum Sticky re lucid.

---

### Post by Calash on 2010-05-06
> **DomesDKG said:**
> The theme changing approach is officially considered to be the "correct" approach, according to the forum sticky FAQ.

While there is currently no problem with changing the icons to the left using the metacity method, it stands to break a future feature, windicators.  Read about it here: [http://www.markshuttleworth.com/archives/333](http://www.markshuttleworth.com/archives/333)

Go about it whichever way you want, but if you use a method other than the theme changing method, make a mental note of it in case it causes problems for you in the future.

Does anybody have any information on exactly how moving the buttons via gconf-editor will break future updates?  I see it stated a lot but cannot grasp why this simple change that themes can easily overwrite will cause problems.  When you change your theme this is what gets edited..or am I not understanding correctly?

---

### Post by Mr. Picklesworth on 2010-05-06
> **Calash said:**
> Does anybody have any information on exactly how moving the buttons via gconf-editor will break future updates?  I see it stated a lot but cannot grasp why this simple change that themes can easily overwrite will cause problems.  When you change your theme this is what gets edited..or am I not understanding correctly?

As far as I'm aware, it shouldn't break regular upgrades (just the gconf default is changed by those, not your personal changes), but as new themes roll in it can certainly cause problems.

The easiest way to see the issue first-hand is if you change the gconf key manually, then change your theme. It provides a nice little notification telling you that it changed the button layout (where you had set a different one manually), but that isn't really perfect.

Instead, the easiest solution is to go with the flow and do this in the theme, just as you set your GTK theme and colours in the GUI instead of gconf.

Besides, the [tiny little theme package]("http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz") I made makes things really easy ;)
(Although there seems to be some disagreement here about what "easy" is. My personal definition includes "low maintenance").

So, sure, you can change it in gconf manually, but it's high maintenance and easy to break. I wouldn't recommend pointing someone at that route unless they already know it exists or are keen on extensive tinkering.

---

### Post by Fraoch on 2010-05-06
> **DomesDKG said:**
> The theme changing approach is officially considered to be the "correct" approach, according to the forum sticky FAQ.

While there is currently no problem with changing the icons to the left using the metacity method, it stands to break a future feature, windicators.  Read about it here: [http://www.markshuttleworth.com/archives/333](http://www.markshuttleworth.com/archives/333)

Go about it whichever way you want, but if you use a method other than the theme changing method, make a mental note of it in case it causes problems for you in the future.

Ahh - whoops.  For those of us who put in the gconf-editor "fix" without reading this thread straight through, what's the default configuration again?

Is it ```

close,minimize,maximize:
``` ?

---

### Post by Mr. Picklesworth on 2010-05-06
> **Fraoch said:**
> Ahh - whoops.  For those of us who put in the gconf-editor "fix" without reading this thread straight through, what's the default configuration again?

Is it ```

close,minimize,maximize:
``` ?

The gconf default (what appears if you right click the key and choose Unset Key) is still "menu:minimize,maximize,close", as always. The Ambiance theme sets "close,minimize,maximize:", so that's what people get out of the box.

The theme you select will override that very button_layout key and your changes won't hurt anything. No need to put it back ;)

Although, to bring sense to my rambling here, usually when you want to revert a gconf key the easiest way is to right click it and choose Unset. Setting it to its original value manually works, but has a different meaning. When you unset the key, gconf looks directly at the default value, so as that changes your configuration changes. If you set the key to anything (even if it's the same as the value was originally), that's a value specific to your account, so as the default changes the value you set will not. No biggy (these things are *very* robust!) but it may help to know.

---

### Post by Fraoch on 2010-05-06
Weird - I'm using Human-Clearlooks probably inherited from a previous version default.  The Known Issues thread indicated that it should not have changed (only Ambience, Radiance and Dust) - but it did.

However now that I've set it back to menu:minimize,maximize,close the buttons are on the right as I'd expect them to be.  I'm sure that the buttons were on the left earlier, and I never changed them from default until now, so it's somewhat confusing (looks like the upgrade changed them even though it shouldn't with Human-Clearlooks).

But everything looks as I'm used to it and gconf is back at default, so everything is as it should be in the end.

Thanks.

---

### Post by Calash on 2010-05-06
> **Mr. Picklesworth said:**
> As far as I'm aware, it shouldn't break regular upgrades (just the gconf default is changed by those, not your personal changes), but as new themes roll in it can certainly cause problems.

The easiest way to see the issue first-hand is if you change the gconf key manually, then change your theme. It provides a nice little notification telling you that it changed the button layout (where you had set a different one manually), but that isn't really perfect.

Instead, the easiest solution is to go with the flow and do this in the theme, just as you set your GTK theme and colours in the GUI instead of gconf.

Besides, the [tiny little theme package]("http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz") I made makes things really easy ;)
(Although there seems to be some disagreement here about what "easy" is. My personal definition includes "low maintenance").

So, sure, you can change it in gconf manually, but it's high maintenance and easy to break. I wouldn't recommend pointing someone at that route unless they already know it exists or are keen on extensive tinkering.

My confusion is in that the setting in gconf changes when you change your theme.  How is letting the theme change it any less maintenance than doing it by hand?

(ie:  I change to Ambiance and the key reads as follows

```

close,minimize,maximize:

```


When I change the theme to Human, or any theme where the buttons are on the right, it now reads

```

menu:minimize,maximize,close

```

So the key has changed, even without me touching gedit-conf.

I absolutely understand the need not to spread bad information on things that may cause future updates to break and I am not trying to argue that.  I am just not seeing the difference between letting the theme change this key and doing it by hand.



edit:

> 
Although, to bring sense to my rambling here, usually when you want to revert a gconf key the easiest way is to right click it and choose Unset. Setting it to its original value manually works, but has a different meaning. When you unset the key, gconf looks directly at the default value, so as that changes your configuration changes. If you set the key to anything (even if it's the same as the value was originally), that's a value specific to your account, so as the default changes the value you set will not. No biggy (these things are very  robust!) but it may help to know.


Ok, I think that is what I was looking for.  Let me just summarize what I think I understand

What you see by default in the gedit-conf key is the value set by the theme, or the default value if there is none.
The value set by the theme has no effect on the default value but overrides it.
Setting the value by hand resets the default value.  Being the last set it overrides the theme.

Is that close?  :)

---

### Post by Mr. Picklesworth on 2010-05-06
> **Calash said:**
> I absolutely understand the need not to spread bad information on things that may cause future updates to break and I am not trying to argue that.  I am just not seeing the difference between letting the theme change this key and doing it by hand.

It's a difference in attitude, is all. I think it's harmful to tell anyone to change the gconf key manually if they want a permanent solution, because they *will* have to do it again and again; things won't behave as they may expect.

On the other hand, if you're comfortable using gconf-editor and want to play with new and exciting button layouts (there are actually [lots of buttons]("http://people.collabora.co.uk/~tthurman/cowbell/doc/buttons.svg") that never get used, though not many themes support them), there's certainly no harm in it. It just may become a tad fiddly at times :)

---

### Post by Ubunthree on 2010-05-06
Another method, using basic Appearance Preferences without any GConf editing or theme installations:

Choose a theme that *has* the buttons on the right side, like Clearlooks. Then hit Customize, and set the Controls and Window Border to Ambiance or whichever one has the appearance that you want. Save the custom theme as "ambiance_right" or whatever you want to call it.

This works for me, anyway; my theme looks just like Ambiance as far as I can tell, except the buttons are on the right side. It has remained stable so far.

---

### Post by vhof on 2010-05-07
> **stchman said:**
> Do the following to get the minimize, maximize, and close on the right side in the right order.

Hit ALT - F2

Type gconf-editor

Go to the following:

apps --> metacity --> general

Find the button_layout parameter, right mouse click, and select Edit Key

Change the value to the following:

:minimize,maximize,close

Don't forget the colon on the left side of the text.

You will then have it the way you are used to it.

Easy:)

---

### Post by mb_webguy on 2010-05-07
From what I've read, the gconf method might cause things to break in the future, and the "preferred" method is to open System->Preferences->Appearance, choose New Wave, click Customize, then select Ambiance under the Controls and Window Border tabs (and make any other changes you'd like under the other tabs).  That will give you the same result without risk of future breakage.

---

### Post by Calash on 2010-05-07
> **mb_webguy said:**
> From what I've read, the gconf method might cause things to break in the future, and the "preferred" method is to open System->Preferences->Appearance, choose New Wave, click Customize, then select Ambiance under the Controls and Window Border tabs (and make any other changes you'd like under the other tabs).  That will give you the same result without risk of future breakage.

But how will it break?  Personally I like to understand the mechanics behind something before telling everybody I know that it is a bad thing.

I think what I need to understand is how gconf changes the value and how a theme changes that same value.  If they are different then life is good, if a bit confusing.  If they are the same then the only difference is guiding people to use a singular method that only appears to be less damaging.

---

### Post by philinux on 2010-05-07
> **Ubunthree said:**
> Another method, using basic Appearance Preferences without any GConf editing or theme installations:

Choose a theme that *has* the buttons on the right side, like Clearlooks. Then hit Customize, and set the Controls and Window Border to Ambiance or whichever one has the appearance that you want. Save the custom theme as "ambiance_right" or whatever you want to call it.

This works for me, anyway; my theme looks just like Ambiance as far as I can tell, except the buttons are on the right side. It has remained stable so far.

You must have read the forum sticky then ;)

---

### Post by newbiefly on 2010-05-07
thanks stchman that was buggin me SO HARD.

---

### Post by hai2lp on 2010-05-08
thanks stchman,,,

it's so easy.... :)

:guitar:

---

### Post by turbuntu on 2010-05-13
the thumbnails in appearance manager shows the buttons on the right but applying takes them to left weird!
I wish they change the icons colors in some day too!

---

### Post by motersho on 2010-05-13
Even easier way 

```
gconftool-2 --type string --set /apps/metacity/general/button_layout ":minimize,maximize,close"
```

---

### Post by motersho on 2010-05-21
Also if you want a menu icon on the left side of your title bar then use the command above but add a the word "menu" before the colon.

---

### Post by GIRI MURALI on 2010-07-01
1. Press 'alt+f2' keys to open run window
2. In run window type 'gconf-editor' and then click run to open configuration editor window
3. Explore 'apps > metacity > general'
4. Select button-layout on the right-pane double click on the 'close,minimize,maximize:' on it's right side and edit  it as 'menu:minimize,maximize,close'. Now the buttons should be reached on the right side

for more help visit this post [http://www.beubuntu.co.cc/2010/06/how-to-move-close-minimize-maximize_30.html](http://www.beubuntu.co.cc/2010/06/how-to-move-close-minimize-maximize_30.html)

---

### Post by giovmendoza on 2010-07-09
> **mb_webguy said:**
> From what I've read, the gconf method might cause things to break in the future, and the "preferred" method is to open System->Preferences->Appearance, choose New Wave, click Customize, then select Ambiance under the Controls and Window Border tabs (and make any other changes you'd like under the other tabs).  That will give you the same result without risk of future breakage.

I prefer this method since it is not that complicated, and probably more stable.

---

### Post by smittycity on 2010-09-19
> **linuxman94 said:**
> By far the easiest way is to use this python script.  Simply download it, change it's permissions to allow executing it, and double click it.

[IMG]http://lh6.ggpht.com/_FJH0hYZmVtc/S5bF_mfdfnI/AAAAAAAAGdw/-XSZh2wOONI/s1600-h/unknown_007%5B2%5D.png[/IMG]

[IMG]http://lh3.ggpht.com/_FJH0hYZmVtc/S5bGBSObTaI/AAAAAAAAGd4/yGvPM34G_RY/s1600-h/Selection_006%5B2%5D.png[/IMG]

Yes, this is the easiest way to fix this.

---

### Post by cplai on 2010-11-18
Hello,
 
If I  use **mwm** — The Motif Window manager rather than using Metacity as the window manager, then how to disable Minimize/Maximize/Close buttons.
 
Your help is high appreciated.
 
 
[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]
 
CP Lai

---

