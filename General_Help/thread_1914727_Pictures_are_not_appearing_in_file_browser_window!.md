---
title: "Pictures are not appearing in file browser window!"
date: 2012-01-24
forum: General Help
---

### Post by linuxuser12345 on 2012-01-24
I am trying to upload some .JPG pictures to a website and every time I go to upload the pictures using the file browser tool in Ubuntu, none of the pictures are shown! Of course, the pictures are on my computer, as I clearly see them when I go to my desktop. Can someone help me here?

---

### Post by bluexrider on 2012-01-24
You didn't specify what file browser you are using so if using Nautilus 

File Management Preferences, under preview, show thumbnails, Always

---

### Post by linuxuser12345 on 2012-01-27
I am using Nautilus. I figured out the problem: When the file browser tool searches only for image files, it doesn't recognize the file if the ending label, like ".jpg" or something is in all caps. I have to literally go in an rename every single photo. This is ridiculous and needs to be fixed before the next Ubuntu version.

---

### Post by mcduck on 2012-01-27
> **linuxuser12345 said:**
> I am using Nautilus. I figured out the problem: When the file browser tool searches only for image files, it doesn't recognize the file if the ending label, like ".jpg" or something is in all caps. I have to literally go in an rename every single photo. This is ridiculous and needs to be fixed before the next Ubuntu version.

Actually when you are uploading the pictures to a web site, you aren't using Nautilus, or any other file manager. You are using *your web browser's file selection dialog* (which looks pretty familiar simply because it's using the file selection widgets from the same toolkit, GTK).

So, if you have problems with a file selection, you should report the bug to the developer of the program. Ubuntu devs aren't the ones who could fix it. Nautilus developers even less since they have absolutely nothing to do with it.

...furthermore, in this very situation it's actually the web site where you are uploading the images who decides what filetypes are allowed... So it's not even your web browser that has the issue, it's the site you are using that hasn't included all the possible variants of the file name extension for the allowed filetype. ;)

(this is assuming you are using a web browser to upload the images, insted of an FTP program for example. If you do use an FTP program, then the problem would of course be in that application. Although I've never heard of an FTP app that would care about filetypes at all, which is why I made the assumption that you are doing this through a web site instead)

---

### Post by jwbrase on 2012-01-27
> **linuxuser12345 said:**
> I am using Nautilus. I figured out the problem: When the file browser tool searches only for image files, it doesn't recognize the file if the ending label, like ".jpg" or something is in all caps. I have to literally go in an rename every single photo. This is ridiculous and needs to be fixed before the next Ubuntu version.

To the best I can determine, the website determines what file extensions get shown (no matter what operating system you're using). Try uploading a *.JPG to Facebook: when I do that, it does show files with uppercase names (because the Facebook people did it right). 

Windows stores files with case, but handles them internally without case, while Linux both stores and handles files case sensitively (the same goes for OS X), and Window's predecessor, DOS, ignored case completely, both for storage and internal processing. Many cameras and stuff use the old DOS filesystem for their memory cards, which is why you get a lot of photos with *.JPG extensions. 

So Web programmers that think the whole world runs Windows end up relying on Window's case insensitivity and specifying a set of extensions that only includes lower case. This works on Windows, but fails on any Unix-like system (including OS X and Linux). Contact the site you're using. If Facebook can get it right, so can they.

In the meantime, you don't need to rename things one by one. There are several mass renaming utilities available:

If you want a graphical utility, there's Metamorphose. I haven't tried it personally, but it's discussed in [this]("http://ubuntuforums.org/showthread.php?t=1500940") thread and available [here]("http://file-folder-ren.sourceforge.net/").

If you're not afraid of the command line, there's a package called mmv in the repositories.

I personally use zmv, which comes with the zsh package, if you prefer that to bash as your command-line shell.

---

