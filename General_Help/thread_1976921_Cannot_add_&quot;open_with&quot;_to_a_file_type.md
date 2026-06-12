---
title: "Cannot add &quot;open with&quot; to a file type"
date: 2012-05-09
forum: General Help
---

### Post by Paddy Landau on 2012-05-09
[LIST]
[*]I have an application (not available from the Repositories).
[*]I use a specific extension to identify data files for that program.
[*]In Nautilus,I right-click the file > Properties > Open With > Show other applications
[*]The program in question is not listed, so I cannot add it.
[/LIST]
In Natty 11.04 and earlier, I remember there being a button to add a new program to the list so that I could assign the program as the default application.

But, in Precise 12.04, there is no such button.

How can I add the program to assign it to the extension?

---

### Post by Vaphell on 2012-05-09
what program would that be?

---

### Post by Alpyre on 2012-05-09
I experience the same problem with Guitar Pro 6

---

### Post by Paddy Landau on 2012-05-09
> **Vaphell said:**
> what program would that be?
Well, you can test this with *any* program not listed; for example, zenity. In this particular case, I am using Truecrypt, and I want to associate it with files ending in [FONT=Lucida Console].tc[/FONT].

---

### Post by Enigmapond on 2012-05-09
The problem there is that TC doesn't use or need file-type suffixes to work in fact they sway against that for additional security.

---

### Post by Paddy Landau on 2012-05-09
> **Enigmapond said:**
> The problem there is that TC doesn't use or need file-type suffixes to work in fact they sway against that for additional security.
That's not a problem. I don't use TC for illegal or immoral use; I use it against data theft, and I use a standard suffix for all TC files.

But anyway, what if I wanted to do the same thing with a different program (such as the [post=11920717]Alpyre's Guitar Pro[/post])? There needs to be a way to add programs to the list, just as there used to be.

---

### Post by ingramproductions on 2012-05-09
Same problem [here]("http://ubuntuforums.org/showthread.php?t=1976923") with rdp files

---

### Post by Enigmapond on 2012-05-09
> **Paddy Landau said:**
> That's not a problem. I don't use TC for illegal or immoral use; I use it against data theft, and I use a standard suffix for all TC files.

But anyway, what if I wanted to do the same thing with a different program (such as the [post=11920717]Alpyre's Guitar Pro[/post])? There needs to be a way to add programs to the list, just as there used to be.

I wasn't implying any immoral activity...just was stating what TrueCrypt states. It's not hard to figure out that .tc are TC files with sensitive data.  Yes I agree that there should be a way to link to an executable not on the list. Right now they've done away with that feature.

---

### Post by Vaphell on 2012-05-09
i've seen claims that some apps refuse to show in the other apps dialog if their .desktop file lacks %u in their Exec= line.

---

### Post by mc4man on 2012-05-09
If you can describe how you run TrueCrypt such as a launch command, (or Alt+F2 comm.), then it's pretty easy to create & register a new mimetype & a .desktop to launch an app from r. click on this 'new' mimetype.

(gotta go out but post what you can if inclined

Screens show I made this up (don't actually have TrueCrypt installed & the 1.tc is just empty but if I had TC installed ect. it would likely be good.

---

### Post by Paddy Landau on 2012-05-10
> **ingramproductions said:**
> Same problem [here]("http://ubuntuforums.org/showthread.php?t=1976923") with rdp files
Solution found! I'll post in your thread.

> **Enigmapond said:**
> I wasn't implying any immoral activity...
Sorry, I didn't intend to sound abrupt. I was trying to say that in my case, secrecy is not important; only protecting the data from unauthorised eyes.

> **Vaphell said:**
> i've seen claims that some apps refuse to show in the other apps dialog if their .desktop file lacks %u in their Exec= line.
That solved the problem! I added %u to the end of the Exec line in truecrypt.desktop (in folder /usr/share/applications), and rebooted. It was there and it works now. Thank you.

> **mc4man said:**
> ... it's pretty easy to create & register a new mimetype
That would be a great idea for aesthetic purposes, but I don't know how to do so. Can you give me a pointer, please?

---

### Post by mc4man on 2012-05-10
> **Paddy Landau said:**
>  I added %u to the end of the Exec line in truecrypt.desktop (in folder /usr/share/applications), and rebooted. It was there and it works now. Thank you.


That would be a great idea for aesthetic purposes, but I don't know how to do so. Can you give me a pointer, please?

Didn't know that truecrupt installed a .desktop, so adding a %<letter> is all you needed to do, at least as far as r.click menu
(In gnome3 only .desktops whose Exec= line ends with a %<letter> will be available in the r. click > Properties > open with menu
(typically %U or %f

The reason for creating & registering a new mime/filetype would be to be able to set truecrypt as default for that type, .tc & have another app as default for text/plain

Maybe I'll grab TC & then show you exactly, otherwise post the .desktop. Also this can be done locally per user or system wide, which?

---

### Post by Alpyre on 2012-05-10
Adding the "%u" phrase to the end of the Exec line in the file: "/usr/share/applications/Guitar Pro 6.desktop" solved the issue for me too!

Thanks! ^^

---

### Post by Paddy Landau on 2012-05-10
> **mc4man said:**
> Maybe I'll grab TC & then show you exactly, otherwise post the .desktop. Also this can be done locally per user or system wide, which?
Well, system-wide would make sense, I suppose. But I have no clue as to how to go about registering a mime-type. If you happen to know, that would be great, otherwise I'll use Google.

---

### Post by mc4man on 2012-05-10
Didn't grab TC yet but for system-wide something like this (I tend to do stuff locally, if anyone has any corrections please do so

First create an .xml, I did so in ~/Documents, named it truecrypt.xml

```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
    <mime-type type="application/x-true-crypt">
        <comment>TrueCrypt files</comment>
        <glob pattern="*.tc"/>
    </mime-type>
</mime-info>
```

Then add, locally no sudo is used

```
sudo xdg-mime install --novendor  ~/Documents/truecrypt.xml
```

Locally this isn't needed, probably is for system-wide
```
sudo update-mime-database   /usr/share/mime
```

After that if using a custom .desktop I'd use xdg-desktop-menu install --novendor /path to .desktop  but no need here. Instead you open the current .desktop & add to the end of the MimeType= line  this

application/x-true-crypt; 
or if there is no such line then create it

```
MimeType=application/x-true-crypt
```

Then do a log out in

---

### Post by Paddy Landau on 2012-05-12
mc4man, that's excellent, thank you!

---

### Post by Finn bjerke on 2012-05-12
I would really like to open Guitar pro 6 with files with the extension .gpx or .gp5 or gp4. (.gp?) However I cannot make Ubuntu 12.04 do that. 

This hint is probably very good I must confgess I dont understand it :

> Adding the "%u" phrase to the end of the Exec line in the file:  "/usr/share/applications/Guitar Pro 6.desktop" solved the issue for me  too!
Thanks! ^^

---

### Post by Paddy Landau on 2012-05-12
> **Finn bjerke said:**
> This hint is probably very good I must confgess I dont understand it :

[LIST]
[*]Press Alt-F2 and enter the following command:```
gksudo gedit '/usr/share/applications/Guitar Pro 6.desktop'
```
[*]Find the line that starts with [FONT=Lucida Console]Exec=[/FONT].
[*]At the end of the line add a space and then [FONT=Lucida Console]%u[/FONT]
[*]Save the file and exit.
[*]Log out and log in again (or just reboot).
[/LIST]

---

### Post by Finn bjerke on 2012-05-12
thanks for the kind answer . 
F2 dims the light on the laptop, so i use terminal instead is that OK?

It seems I can only find this file 

in 

./usr/ Share/applications/ guitar pro 6

 I can not see the extension

right click / properties i get this

/opt/GuitarPro6/launcher.sh

type skrivebordskonfigurationsfil (application/x-desktop)

I understand that Ill need to add %u after  /opt/GuitarPro6/launcher.sh  ??

---

### Post by Finn bjerke on 2012-05-12
Using the text editor from terminal I solved the problem Im very gratefull, now I can open guitar pro with a .gp? file which is wonderfull. I had to open guitar pro 6.desktop directly from the text editor. Learned a lot from that actually

gksudo gedit '/usr/share/applications/Guitar Pro 6.desktop'
is almost correct this works in terminal
gksudo gedit '/usr/share/applications/GuitarPro6.desktop'  
thx again.

---

### Post by Paddy Landau on 2012-05-13
> **Finn bjerke said:**
> F2 dims the light on the laptop...
Sorry, that was my mistake. The correct keystroke is Alt-F2. I have corrected [post=11930070]my post[/post].

> **Finn bjerke said:**
> ... this works in terminal
gksudo gedit '/usr/share/applications/GuitarPro6.desktop'
Again, my bad; I though the file had spaces in (I don't have Guitar Pro, so I was following on from [post=11923585]a previous post[/post]).

I'm pleased you got it solved.

---

