---
title: "ubuntu cannot display an photo type files"
date: 2006-04-05
forum: General Help
---

### Post by jbrown101st on 2006-04-05
okay as the title describes. this happens to me on every photo i try to open. this is the error message:

ERROR

The filename "example.jpg" indicates that this file is of type "JPEG image". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

______________

Does anybody know how i can fix this???

thanks, 
     jbrown101st

---

### Post by Kevinator on 2006-04-06
As far as I can tell, this is a very lame feature of Nautilus that seems to be minimally useful. Renaming the files as it suggests is not a reasonable option. Instead, try the other suggest (use the Open With menu option), or launch the program you want to use then open the file from that program's menu.

There is a chance the the files in question are not actually valid image files, but actually text files with unfortunate names. If they fail to open using these suggestions, that may be the reason.

---

### Post by jbrown101st on 2006-04-06
I know they are valid photos because i jus transfered them from my windows PC to ubuntu. and I have tried every photo related app i have to open them :(

---

### Post by taurus on 2006-04-06
How did you transfer those files because according to Ubuntu, they are not image files?  If they were an image files, then you can open them with gqview, gimp, etc....

---

### Post by engla on 2006-04-06
Nope, this is a bug I've run into also, with images that I used to watch in ubuntu that suddenly threw that message after some package upgrades.

I sadly referred to fixing this problem manually :(

Like this:
1. Put this in the file ".local/share/mime/packages/custom.xml"
```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
  <mime-type type="image/jpeg">
         <comment xml:lang="en">JPEG bild</comment>
         <glob pattern="*.jpg"/>

  </mime-type>
</mime-info>

```
2. Ran 'update-mime-database ~/.local/share/mime'

---

### Post by jbrown101st on 2006-04-06
[QUOTE=engla]Nope, this is a bug I've run into also, with images that I used to watch in ubuntu that suddenly threw that message after some package upgrades.

I sadly referred to fixing this problem manually :(

Like this:
1. Put this in the file ".local/share/mime/packages/custom.xml"
```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
  <mime-type type="image/jpeg">
         <comment xml:lang="en">JPEG bild</comment>
         <glob pattern="*.jpg"/>

  </mime-type>
</mime-info>

```
2. Ran 'update-mime-database ~/.local/share/mime'[/QUOTE]


thanks, but one other problem... my folders dont go any deeper than "/share"
i have no option for mime. :(... so... WHat now??? :(
sorry and thanks!

---

### Post by Ramses de Norre on 2006-04-06
It's ~/.local/share/mime/packages/custom.xml, so in your home folder.

---

### Post by jbrown101st on 2006-04-06
[QUOTE=Ramses de Norre]It's ~/.local/share/mime/packages/custom.xml, so in your home folder.[/QUOTE]

i told you... i dont have anything after share. my only folder option is-

"~/.local/share/applications/"
applications is the only folder in share folder.

thanks tho

---

### Post by Ramses de Norre on 2006-04-06
Guess you should just create the folders then.

---

### Post by jbrown101st on 2006-04-06
okay i just tried creating the folders and that doesnt work.

---

### Post by Ramses de Norre on 2006-04-06
What's the output of ```
update-mime-database ~/.local/share/mime
```

---

### Post by engla on 2006-04-06
Hmm, that was probably a bad idea by me to bring this topic off-topic. Yes, offtopic as that lazy/stupid fix is nothing really.

We have a real problem here.

1. Nautilus has some kind of security measure where it tried to be smart but fails horribly eventually. This shouldn't be possible.

2. Right, this shouldn't be possible. So why do mime hiccups happen all the time?

---

### Post by jbrown101st on 2006-04-06
okay, so where does this leave us? sorry for all of the trouble!

---

### Post by Kevinator on 2006-04-09
[QUOTE=jbrown101st]I know they are valid photos because i jus transfered them from my windows PC to ubuntu. and I have tried every photo related app i have to open them :([/QUOTE]

If they are valid JPEG images I don't know of any reason that the apps would fail to open them. Do they give you any error messages? If so, what do they say? Can you post one of the images somewhere for us to test?

---

### Post by jswakefield on 2008-01-29
Cool, cheers Engla I had the same problem suddenly happen to all my jpegs,  tried the code you suggested:

<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
  <mime-type type="image/jpeg">
         <comment xml:lang="en">JPEG bild</comment>
         <glob pattern="*.jpg"/>

  </mime-type>
</mime-info>

ran: 

update-mime-database ~/.local/share/mime

And it worked, although I had to re-boot my PC as well. :)

---

