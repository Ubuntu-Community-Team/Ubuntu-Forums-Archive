---
title: "Chane ONLY icon themes, not panel themes aswel"
date: 2010-08-06
forum: General Help
---

### Post by migel_wimtore on 2010-08-06
Hi, sorry if i'm missing something really obvious here, but perhaps someone could help me out. 

I would like to install a new icon theme without effecting my currently selected panel theme, as i think the Ambience panel theme looks really nice and unified but im not too keen on the Ubuntu-Mono icons.

Is this easily possible, without going into my icon folders and replacing all the instances of one style for another?

Are there any applications for gnome icon theming like OS X's Candybar?

Im sure others must desire to change only the icons and perhaps it is really easy and this is why i couldnt dig anythin up on google, that or im a useless googler.

Cheers.

---

### Post by darolu on 2010-08-06
First, you need to get a good set of icons (icons theme), there are tons at [http://www.gnome-look.org](http://www.gnome-look.org)

Then, copy the icons folder to /home/<yourusername>/.icons/; in Nutilus press Ctrl+H to see hidden files/folders; once your theme is in ~/.icons/ simply go to System->Preferences->Themes and select your theme, then click on Customize and select your new icons theme.

Alternatively, you can open System->Preferences->Theme and drag and drop your tar.gz icons file in to install it.

---

### Post by migel_wimtore on 2010-08-07
Wow, lightning fast reply. Thanks.

So, i tried manually placing my chosen icon theme folder in .icons and selecting the icons menu from the customize section in Appearance settings, however this still changes the look of the ions in the top panel as well, ie, the indicator applets, mail icon, volume icon, etc, and gives me a multicoloured ubuntu logo in the top left corner beside the Applications menu title. As if i had installed the theme via the Install button.

I just want the folder icons to change, none of the menu icons, dock icons or indicator applet icons. 

Is this possible without digging through the folders and replacing those particular icons from the Ubuntu-Mono theme, for panel applets etc, with those of my chosen theme? As that would be seemingly rather laborious.

Thanks again.

---

### Post by migel_wimtore on 2010-08-07
Done it!

And by jove was it fiddly.

Coppied and replaced all the desired panel icons from Ubuntu-Mono-Dark theme into my desired theme folder and placed it in ~/.icons, selected it from the icons menu in Appearance prefs and hey presto.

Sweet.

 Will be easier a second time im sure.

If i had the talent i would definitely write a Candybar type app for Linux.

Cheers.

---

