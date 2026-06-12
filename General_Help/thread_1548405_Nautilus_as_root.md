---
title: "Nautilus as root"
date: 2010-08-08
forum: General Help
---

### Post by dpwilson on 2010-08-08
I have downloaded fonts to install.  I normally use the terminal and **sudo mv /*name of font*  /usr/share/fonts ** 

 1) Can I move more than one file at a time using the terminal?  If so, how? I tried to add a space between each file, but it only took the first one listed.

2) Since I couldnt figure out how to do that using the terminal, I ran nautilus as root and opened two windows and dragged from one to the other.  Is there any harm in doing it this way?

Thanks for any answers and help :D

---

### Post by agnes on 2010-08-08
*mv filename1 filename2 destination* should work okay...

It is best to run nautilus as root with the gksudo command (*gksudo nautilus*), there is no harm to that.

---

### Post by WorMzy on 2010-08-08
Why do you need to install them that way? Just move them into ~/.fonts.

---

### Post by deostroll on 2010-08-08
hi even *mv path/*.extn path-to-destination* will work

---

### Post by chopinhauer on 2010-08-08
> **agnes said:**
> 
It is best to run nautilus as root with the gksudo command (*gksudo nautilus*), there is no harm to that.


That is, except thousands of lines of code running as root.

---

### Post by NFblaze on 2010-08-08
dpwilson,

You can get a root nautilus by:
Alt+F2
Type in *gksu nautilus*
done

Shouldnt be a problem at all.

The commandline version of *mv* should also work, I laways have to move particular fonts into /usr/share/local/ or whatever.

---

### Post by dpwilson on 2010-08-08
> **WorMzy said:**
> Why do you need to install them that way? Just move them into ~/.fonts.

Worked like a charm, never knew to do that, I guess that is the easiest way.  Thanks  :D

---

### Post by dpwilson on 2010-08-08
> **agnes said:**
> *mv filename1 filename2 destination* should work okay...

I tried to  do that, but perhaps was doing it wrong.  I am guessing I need to use the full path to each filename? ie; [I]/home/wilson/Desktop/file1 /home/wilson/Desktop/file2 /destination
[/I]


I think the safest/easiest way as suggested by WorMzy is to creat the ~/.fonts folder and move them there.  That worked great.

---

### Post by WorMzy on 2010-08-08
Glad I could help.

For the mv command, you'd either need to provide the full (or relative) paths to each file. For relative paths, first use cd to get to the most common path for all the files you want to move, then write the files as though you were continuing the path from just after the preceding slash.

e.g. say you wanted to move three files ([COLOR="Red"]~/Downloads/abc/file1.txt[/COLOR], [COLOR="Blue"]~/Downloads/def/file2.txt[/COLOR], [COLOR="Green"]~/Downloads/def/file3.txt[/COLOR]) to [COLOR="Orange"]~/destinationfolder[/COLOR], you'd first run ```
cd ~/Downloads
```
to change the directory that your shell is looking at to the Downloads folder. Then you'd just need to write
```
mv [COLOR="Red"]abc/file1.txt[/COLOR] [COLOR="Blue"]def/file2.txt[/COLOR] [COLOR="Green"]def/file3.txt[/COLOR] [COLOR="Orange"]~/destinationfolder[/COLOR]
```

Bash (your shell) is smart enough to know that it needs to prepend "~/Downloads/" to the start of all the file's locations. It also knows that "~" is the path to your home directory (e.g. /home/wilson).

You can also use TAB to auto-complete paths as you're typing.

---

### Post by soldier1st on 2010-08-08
running nautilus as root is just asking for trouble.

---

### Post by dpwilson on 2010-08-08
> **soldier1st said:**
> running nautilus as root is just asking for trouble.

That's why I was looking for a different method to move them.  Didn't want to do that anymore.

---

### Post by Ginsu543 on 2010-08-08
Moving/copying fonts to the .fonts folder makes those fonts available only to the user in whose home folder the .fonts folder resides. If you move/copy fonts to /usr/share/fonts, those fonts are available to every user.

When I do move/copy operations using Terminal, I actually like to go to the folder I want the files to be in and then go get them from their source folder using the "." command. For example, let's say that the truetype fonts I want to install are in my Downloads folder. I will then navigate to the destination folder, in this case /usr/share/fonts, and type:
```

sudo cp /home/suhheuge/Downloads/*.ttf .  <-- notice this "." which means "current location"

```I prefer this method because I know instantly if I did it right since they will show up in my destination folder as soon as I give the command. Second, if something goes wrong, I don't have to worry about which folder I moved/copied my files to by accident. I don't have to go hunting for it all over my directory tree to find them so I can delete them.

---

