---
title: "Fonts?"
date: 2006-02-26
forum: General Help
---

### Post by jbennett on 2006-02-26
Is there a way to install more fonts for Linux (namely, Windows fonts)?  I was chatting with a friend using gaim in ubuntu the other day, and then I rebooted into Windows to do some schoolwork and chatted with the same friend and noticed that their font was completely different.

Does anyone know where I can find Windows fonts for Linux?

Thanks for any help.

---

### Post by Xian on 2006-02-26
[QUOTE=jbennett]Does anyone know where I can find Windows fonts for Linux?[/QUOTE]

That's a little vague and could mean a lot of things.
Do you have some particular fonts in mind?

You can install some via APT:
$ sudo apt-get install msttcorefonts

---

### Post by jbennett on 2006-02-26
[QUOTE=Xian]That's a little vague and could mean a lot of things.
Do you have some particular fonts in mind?[/QUOTE]

I didn't have any particular ones in mind.  I guess the answer I was looking for was the vague one, just whether or not it was possible.  Is there other ways that I could go about obtaining some more Windows fonts?

Again, probably just looking for the vague answer, but, if you wanted to pick a font that wasn't included in the msttcorefonts package and describe to me how you might go about getting it for Linux, that would be helpful to me in the future if I wanted to get more fonts.

Thanks for the help.

Edit:  For instance, Book Antiqua or Comic Sans MS (both Windows fonts).:)

---

### Post by Xian on 2006-02-26
[QUOTE=jbennett]Again, probably just looking for the vague answer, but, if you wanted to pick a font that wasn't included in the msttcorefonts package and describe to me how you might go about getting it for Linux, that would be helpful to me in the future if I wanted to get more fonts.[/QUOTE]

I would just grab what I wanted from /WINDOWS/Fonts on an XP install. Install them in either /usr/share/fonts for global availability, or /home/<username>/.fonts for individual use. Update your font cache, run 'mkfontdir' and 'mkfontscale' in the applicable directory, and you should be good to go. You could also add them to a path like /usr/share/X11/fonts/TrueType and append that dir to the 'Section "Files"' category in your xorg.conf.

---

### Post by z_diver on 2006-02-27
I would suggest you intstall Automatix and the truetype fonts that are available through that.  If the font you are looking for is still unavailable, you can copy that font directly from your XP over and put it in a folder inside usr/share/fonts/truetype directory and then run 'sudo fc-cache -f -v' which rebuilds the font cache.

---

### Post by jazzgossen on 2006-02-27
Like Xian said, copy the files you want to some subdirectory under /usr/share/fonts/truetype/, run mkfontdir in the directory where you put the files, then run fc-cache and then you should hopefully be done. Now, the files should show up if you go to fonts:// in Nautilus, for example.

But note that the fact that the fonst look different when you chat can also be because your chat programs work differently.

---

### Post by nanotube on 2006-02-27
this wiki page: [https://wiki.ubuntu.com/FontInstallHowto](https://wiki.ubuntu.com/FontInstallHowto)
has all the info on how to install fonts. check it out.

---

### Post by jbennett on 2006-02-27
Thanks for the help everyone.  I followed a combination of everyone's suggestions and installed several new fonts.:)

---

### Post by Xian on 2006-02-27
Another good terminal command for font configuration:

$ sudo dpkg-reconfigure fontconfig

---

