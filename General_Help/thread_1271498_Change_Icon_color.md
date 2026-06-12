---
title: "Change Icon color"
date: 2009-09-20
forum: General Help
---

### Post by mju4t on 2009-09-20
Hello,

I have an icon set "Shiki-Mint" installed.  I want to continue using these icons but I want to change the color to blue.  How can I do this?

Thanks
Alex

---

### Post by blackened on 2009-09-21
If you're wanting to recolor one icon, say the folder icon, then this is pretty easy. If you want the entire palette of the icon set changed, then you're dealing with a whole different animal and should look closely at what you're trying to undertake.

As an example, the Eikon set has about 1000 individual icons (+ or - some duplicates) that would have to be recolored one at a time.

---

### Post by Megrimn on 2009-09-21
to physically change them yourself, you need to go to /usr/share/icons, and **copy** the "shiki-mint" folder to your desktop.  

once you do that, open the folder, open the file index.theme in a text editor.  I had to open the text editor and then drag the file into the editor, or you can just 'sudo gedit index.theme' from the command line if you prefer that way.  

So, change the word in the "Name" line from 'Shiki-Mint' to Shiki-Mint Blue or something other than plain 'shiki-mint'.  then save it and quit.  On a note, you may want to change the name of the folder, too, to what ever you name your theme.

next is the tedious part.  Browse through all the other folders in the "Shiki-Mint" folder and open the icons in gimp.  in there you can change the colors using the 'hue-saturation' thing under the colors menu.  Then save each icon when you are finished.

If you are looking to change only the folder colors, they are located in the 'places' folder in each of the first folders.  If a folder doesn't have a 'places' folder, don't worry about it.  

It's all pretty self explanatory once you get working on it, and it's tedious, so get ready to buckle down with a nice cold beverage.

When you are done, there are two ways you can install your theme.  

You can right-click the folder of your theme, hit 'create archive', and make a tar.gz out of it, and open the appearance preferences, where you can install the theme under the 'Theme' tab (just hit the install button and navigate to your Shiki-Mint-Blue.tar.gz or what ever you decided to call it.)

The second way is to just paste the folder back where you found it, in usr/share/icons.  It will show up the appearance preferences where you change the icon theme.  If you already have appearance preferences open, you will have to close it and open it again before it shows up.

The 'out' to this situation is to browse for a different theme on gnome-look.org or deviantart.com.  But that's just an easy way out if you get fed up.  I already tried looking for the specific theme you have in a blue flavor and didn't find any, just letting you know.  You could probably submit yours when you're done though, if you wanted to.

So have fun with your little project :)

---

### Post by mju4t on 2009-09-21
Thanks for the feedback!  I decided to just download some new icon sets (i'm not down with the tedious work haha) but thank you anyways :-)

---

### Post by CatKiller on 2009-09-21
> **Megrimn said:**
>  next is the tedious part.  Browse through all the other folders in the "Shiki-Mint" folder and open the icons in gimp.  in there you can change the colors using the 'hue-saturation' thing under the colors menu.  Then save each icon when you are finished.

Actually, if you only want to apply the same tint to each image, you may be able to use [ImageMagick]("http://www.imagemagick.org/script/command-line-processing.php") to change the colours of all the icons in one batch process.

---

