---
title: "This Has Been Bothering Me for Too Long..."
date: 2012-03-30
forum: General Help
---

### Post by w201 on 2012-03-30
I'm  curious about that box that pops up at the bottom right hand corner of the desktop when I type something. What is it for? 

Thanks

---

### Post by Paqman on 2012-03-30
Can you take a screenshot and show us?

---

### Post by Frogs Hair on 2012-03-30
I know what you are writing about because I have seen another thread describing the same thing in the Gnome Shell . I do not know the cause or if that thread was resolved  but it is not normal . 

If you are using the Gnome shell make sure all updates are installed and try restarting the shell using the  following command in the command prompt . ```
r
``` Enable the command prompt in the shell from keyboard > shortcuts > system . Use Alt + F2 as the shortcut .

---

### Post by w201 on 2012-03-30
Frogs Hair- I'm updated.

This is what I'm talking about. Look at the lower right hand corner:

[IMG]http://wguayan.comuv.com/images/righthand_corner_box.png[/IMG]

---

### Post by Frogs Hair on 2012-03-30
Try restarting Nautilus ```
nautilus -q
``` This issue has been posted at Ask Ubuntu also . [http://askubuntu.com/questions/71292/right-bottom-corner-textbox-in-desktop-whats-it-for](http://askubuntu.com/questions/71292/right-bottom-corner-textbox-in-desktop-whats-it-for)

---

### Post by Henkdroid on 2012-03-30
The Desktop is sort of a Nautilus (the file manager) window, so when you type it begins looking for files / folders on the Desktop that start with those letters as if out were looking in a folder.

---

### Post by w201 on 2012-03-30
The post in your link isn't clear whether or not this is abnormal.

Are you saying that box shouldn't pop up?

---

### Post by w201 on 2012-03-30
> **Henkdroid said:**
> The Desktop is sort of a Nautilus (the file manager) window, so when you type it begins looking for files / folders on the Desktop that start with those letters as if out were looking in a folder.

wow, okay. THAT works. I typed the name of a file on my desktop, it selects it, then you can hit enter to open the file. Pretty cool. 

I guess if I had typed an actual file instead of asdf every time I would have figured that out :lolflag:

Thanks!

---

### Post by winh8r on 2012-03-30
You should be able to launch it by typing ```
Control + F
```

(It could be opening because you are accidentally pressing the control key as you type the letter F in a document, this happened to me ;) )

On the desktop it will search for files there but it should also search text within a web page too.

This is the behaviour in 10.04LTS and I cannot check on anything newer at the moment but I think it is still the same.

---

### Post by matt_symes on 2012-03-30
Hi

O/T

I like your desktop wallpaper. Very nice indeed.

Kind regards

---

### Post by stinkeye on 2012-03-30
If you have nautilus drawing the desktop (default) then you are doing a search
in your ~/Desktop folder.
Start typing "bulk" and your **bulk_rename_files** folder will be highlighted.

---

### Post by w201 on 2012-03-30
> **matt_symes said:**
> Hi

O/T

I like your desktop wallpaper. Very nice indeed.

Kind regards

Glad you like it. I found it  here, they have very nice wallpapers.

[http://www.dream-wallpaper.com/photography-wallpaper/nasa-wallpaper/1440x900/index.html](http://www.dream-wallpaper.com/photography-wallpaper/nasa-wallpaper/1440x900/index.html)

---

### Post by Frogs Hair on 2012-03-30
> **w201 said:**
> The post in your link isn't clear whether or not this is abnormal.

Are you saying that box shouldn't pop up?

Yes, the box should not appear.

---

### Post by w201 on 2012-03-30
Are you positive? It seems to have a purpose e.g., to search and select files stored in the desktop folder.

---

### Post by Frogs Hair on 2012-03-30
I has not appeared in 5 months of using 11.10 weather there are desktop folders in use or not . It does not appear on the my desktop while searching for files weather using either Unity desktop , Classic , or the Gnome Shell. I have let nautilus handle the desktop enabled in advanced settings also.

---

### Post by w201 on 2012-03-30
Hmmmm. Okay, if I try your suggestion...

```
nautilus -q
```man pages says -q quits nautilus. Do I have to issue another command to restart it or does it restart automatically?

---

### Post by matt_symes on 2012-03-31
Hi

> **w201 said:**
> Glad you like it. I found it  here, they have very nice wallpapers.

[http://www.dream-wallpaper.com/photography-wallpaper/nasa-wallpaper/1440x900/index.html](http://www.dream-wallpaper.com/photography-wallpaper/nasa-wallpaper/1440x900/index.html)

Thanks.

Kind regards

---

