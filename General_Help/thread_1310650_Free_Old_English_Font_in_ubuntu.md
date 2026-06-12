---
title: "Free Old English Font in ubuntu?"
date: 2009-11-02
forum: General Help
---

### Post by Johndo1 on 2009-11-02
I want to create a cool desktop background with my alias written in Old English Font. Preferably i'd like to have the font installed but I can handle an online font generator. The only problem with online font generators is that I can't take a downloaded or copied .gif image and put it into gpaint to make my wallpaper...
Thanks in advance.
--Dawn.

---

### Post by stinger30au on 2009-11-02
these may interest you
i went a googling

[http://www.fontspace.com/category/old+english](http://www.fontspace.com/category/old+english)

[http://www.eyetricks.com/oldenglishfonts/](http://www.eyetricks.com/oldenglishfonts/)

---

### Post by Johndo1 on 2009-11-02
Thanks. The first link is pretty helpful. I'm having a bit of trouble downloading the .tff file I downloaded. I tryed to download it useing the info from this post. [http://ubuntuforums.org/showthread.php?t=275202]("http://ubuntuforums.org/showthread.php?t=275202")

---

### Post by ricardisimo on 2009-11-02
You are having trouble downloading them, or installing them?

As far as installing, probably the quickest way is to create subfolder of your home folder named ".fonts" (just right-click in your home folder and choose "Create _F_older"). Then drag and drop (or copy and paste) your fonts there.

Some applications (like OpenOffice) require a reboot to make use of these new fonts.

---

### Post by ricardisimo on 2009-11-02
P.S. - I've found most fonts you find on the web are packaged within zip files, so make sure you have extracted them before handling.

---

### Post by Johndo1 on 2009-11-02
Due to my earlier tinkering ther's already a directory named .fonts that I cannot see. I'm tryint to move the .tff file into there but in the file browser I can't even see the file and i'm not sure how to in the terminal.

---

### Post by Unchqua on 2009-11-02
> **Johndo1 said:**
> Due to my earlier tinkering ther's already a directory named .fonts that I cannot see. I'm tryint to move the .tff file into there but in the file browser I can't even see the file and i'm not sure how to in the terminal.
Man, you're on Linux forum so don't say you can't work in terminal :-) .

# cd ~/.fonts
# mv your_download_directory/downloaded_fonts.zip ~/.fonts
# gunzip downloaded_fonts.zip

That's if you have your downloaded fonts in zip format; if not, you don't need 3rd command -- just use "mv" to move files into .fonts directory.

---

### Post by gwpritch on 2009-11-02
FYI...the '.' infront of .fonts makes it a hidden file so it doesn't show up immediately in nautilus or other gui file managers. To see these files click on view in the menu bar and then view hidden files. You will then see how many directories and files are really in your home directory...lol.

---

### Post by Johndo1 on 2009-11-02
> **Unchqua said:**
> Man, you're on Linux forum so don't say you can't work in terminal :-) .


I guess your right lol. I know how to work in the terminal but I guess i'm being lazy. Back to the Unix for dummies book hehe.

Anyway I got it now that it's not 4:00 am.

---

### Post by ricardisimo on 2010-01-13
> **Johndo1 said:**
> Due to my earlier tinkering ther's already a directory named .fonts that I cannot see. I'm tryint to move the .tff file into there but in the file browser I can't even see the file and i'm not sure how to in the terminal.

This has been a long time, so it's probably not necessary any longer, but just in case...

Whatever file browser you're using - nautilus, dolphin, thunar, etc. - <CTRL>H toggles "Show hidden files" in it. So, you open your Home folder, and the first time you hit Control and "H", it will show them, and the next time they will be hidden again.

Like I said, just in case you were interested.

---

