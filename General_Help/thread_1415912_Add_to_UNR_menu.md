---
title: "Add to UNR menu?"
date: 2010-02-25
forum: General Help
---

### Post by uRock on 2010-02-25
I would like to add a network folder to the UNR Files & Folers menu screen. Can someone please tell me how to do this?

Thanx,
Ronnie

---

### Post by uRock on 2010-02-26
I really like the UNR menu screen. Adding a Network folder will make it super awesome, being I send and receive files multiple times a day from this machine to my desktop/server.

Thanks again for any and all help,
Ronnie

---

### Post by Aduntu on 2010-02-26
I do not have my UNR machine in front of me at the moment.  I'm guessing you've already tried the menu settings screen?

---

### Post by uRock on 2010-02-26
I took a look at it and it doesn't show the Files & Folders selection that is in the above screenshot.

---

### Post by Aduntu on 2010-02-26
Oh, I see.  Sorry I can't help.  I'm a fairly new Linux user myself.

I love that wallpaper by the way. Looks great.

---

### Post by bluelamp999 on 2010-02-26
See here - [http://ubuntuforums.org/showthread.php?t=1349543](http://ubuntuforums.org/showthread.php?t=1349543)

Just tried it and it works...

---

### Post by uRock on 2010-02-26
No problem, thanks for trying. I found the picture when I Googled Lynx. There are a lot of good pics.

---

### Post by derrick81787 on 2010-02-26
> **bluelamp999 said:**
> See here - [http://ubuntuforums.org/showthread.php?t=1349543](http://ubuntuforums.org/showthread.php?t=1349543)

Just tried it and it works...

That might work.  Alternatively, you can edit the hidden file .gtk-bookmarks that is in your home directory.

The format is
```
file_uri optional_label_name
```

For example, to add a folder that goes to your network drive that is mounted in /media/network and name it "My Network Drive" add the line:

```
file:///media/network My Network Drive
```

You can probably try other types that are not just files (for instance http:// maybe [ftp://)](ftp://)) but I've never done that.

I hope this helps.

- Derrick

---

### Post by uRock on 2010-02-26
I tried both ways mentioned above. Both ways will work, but this is the code that has to be added to the .gtk-bookmarks file.

```
network:/// Network
```

Thank you to all who contributed.

Sincerely,
Ronnie

---

