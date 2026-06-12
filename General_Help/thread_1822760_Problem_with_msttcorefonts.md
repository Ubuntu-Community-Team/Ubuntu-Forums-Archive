---
title: "Problem with msttcorefonts"
date: 2011-08-11
forum: General Help
---

### Post by SteezMcGee420 on 2011-08-11
Hello, I've recently been installing Steam on Ubuntu (11.04), and during the installation, I needed to install the Microsoft font package, msttcorefonts. I'm pretty sure that I need this font package in order to run the programs properly, so I don't think I can get rid of it. However, I've noticed that when I have it installed, all my fonts in firefox look different, and I don't quite like it. Is there a way that I can have the package installed, but keep certain other program's fonts the same?

---

### Post by mcduck on 2011-08-11
> **SteezMcGee420 said:**
> Hello, I've recently been installing Steam on Ubuntu (11.04), and during the installation, I needed to install the Microsoft font package, msttcorefonts. I'm pretty sure that I need this font package in order to run the programs properly, so I don't think I can get rid of it. However, I've noticed that when I have it installed, all my fonts in firefox look different, and I don't quite like it. Is there a way that I can have the package installed, but keep certain other program's fonts the same?

Do you mean that the font in Firefox application itself is different (which would be very strange) or that the fonts on web pages are different?

The latter case would be normal, web pages don't have any fixed fonts or direct control over such things, they only have a list of preferred fonts and order for them. The browser checks if the first listed fotn is available on your system, if it is ten it's used, if not then the browser checks if the next listed font is available, and so on until finally using the default font as configured in your browser's settings.

As the world *is* quite windows-centric, it's pretty common that web pages are built to use Microsoft fonts. Which is what you'll see if you just have the fonts installed.

You can define a default font you like in the browser's settings, and then tell it to not to allow web pages to use any other fonts. To do that in Firefox go to Edit/Preferences/Appearance, then click the Advanced-button in the Fonts & Colors-section. Set the fonts you want and then disable the "Allow pages to choose their own fonts"-option.

This may break some pages, though, if they were badly designed and the designer didn't understand that the fonts and font sizes might change depending on who is viewing the page, what fonts he has installed and how he has configured them. 

(Another option is to use some Firefox extension like Stylish to make your own font definitions on each site you'd like to change, but that might be a lot of work and also requires a fair knowledge of CSS)

---

### Post by CatKiller on 2011-08-11
As I understand it, the MS fonts are only Recommended by the Wine package, not Required, so you should be able to remove them if you don't want them.

I believe it's also possible to configure the Linux font system to use something other than those fonts even if they're there, but I'm quite hazy on the details.

---

### Post by SteezMcGee420 on 2011-08-11
Thank you all very much for your help. I think I know where I can go from here.

---

