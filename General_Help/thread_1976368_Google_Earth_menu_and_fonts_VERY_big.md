---
title: "Google Earth menu and fonts VERY big"
date: 2012-05-08
forum: General Help
---

### Post by fede82 on 2012-05-08
Hi,

I upgraded ubuntu 11.10 to 12.04 and for some reason Google Earth got uninstalled.
I reinstalled it downloading de 32-bit .deb from the google earth website without issues, but when I open it both the top menu fonts as well as the left hand menu are incredibly big and take up more than 3/4 of the screen.

I tried the fix for the more common "garbled font" issue and all the other workarounds I found on the internet regarding the weird font thing but it didn´t help my "huge text" problem.

Using Ubuntu 12.04 32-bit, nVidia latest propietary drivers, latest GE build and ubuntu all up-to-date-

Any ideas?

Thank you!

---

### Post by Enigmapond on 2012-05-08
Do you have the MS fonts install? Mine looks just fine...

---

### Post by fede82 on 2012-05-08
yes, ms fonts and lsb-core too.  :(

---

### Post by Cincinnatux on 2012-06-11
I, too am running 12.04 (64-bit) with MS core fonts installed and find Google Earth's default menu font size entirely too big.  I stopped using the app because the sidebar was unreadable.  I was shocked that there is not a menu-driven view setting or preference setting to adjust this.  Why do basic things like font size still need to be manually hacked by each user?  

That rant aside, is there a known way to hack this?  I saw that in previous releases it was possible to change QT4 settings, but I have been unable to find QT settings of any sort in 12.04.  I also found guidance to change a file in ~/.googleearth but the location of that file has changed since the original guidance was posted.  Ideally, I'd like to just change Google Earth, not my entire OS, since every otehr application currently dispays the way I want it to.

BTW, the guidance to change the file in Google Earth directly did not come from UbuntuForums, but from a blog:
[http://michielvwessem.wordpress.com/2007/02/17/googleearth/](http://michielvwessem.wordpress.com/2007/02/17/googleearth/)
> To adjust the font size of Google Earth in Linux:

    cd ~/.googleearth/Registry/google/
    googleearthplus/User/render/

and edit the file: guifontsize to your desired fontsize (I set mine to 12 which is a farsight better than the fontsize 6 it was set to.

---

### Post by MrHara on 2013-02-06
Does anyone know where font size is defined on GE 7.0 ? as I have too small fonts.:confused:

---

### Post by Rich.T. on 2013-02-15
> **MrHara said:**
> Does anyone know where font size is defined on GE 7.0 ? as I have too small fonts.:confused:

Ihave the exact same problem with Google Earth 7.0: the GUI font is [SIZE="1"]tiny[/SIZE].

I have increased the system font size in my Ubuntu (12.04) so that it displays nicely on my large screen and this shows up well in other applications' interfaces, but alas, not in GE.

I have tried the above fix, but the location referred to above does not exist:

> To adjust the font size of Google Earth in Linux:

cd ~/.googleearth/Registry/google/
googleearthplus/User/render/

and edit the file: guifontsize to your desired fontsize (I set mine to 12 which is a farsight better than the fontsize 6 it was set to. 

I have also tried adding the line ```
GuiFontSize=12
``` to ~/.config/Google/GoogleEarthPlus.conf as suggested somewhere else, but this didn't work either.

Does anyone else have any ideas?

---

