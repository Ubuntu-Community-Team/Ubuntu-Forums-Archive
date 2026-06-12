---
title: "Help with a script?"
date: 2010-01-28
forum: General Help
---

### Post by lefty_lou on 2010-01-28
First of all i'm hoping i put this up in the right section and second i hope someone can help me with this.

I've had a little package of scripts for a while now and decided to use one that i had not used so far it's called

check md5 sum  by  Tony Mattsson

Well I used it and it says put name of file I put the name of the iso and for some reason the script turn my 4.06 Gb .iso to a 54k .iso


I tried contacting the maker with th email provided but had no luck the email is no longer good or never existed.

Please anyone who know's about this kind of thing help as the iso is super important and i need to try and recuperate it.

Is there anyway to reverse this?

Here is a copy of the script.

```
#!/bin/bash

# AUTHOR:	(c) Tony Mattsson <tony_mattsson@home.se>
# VERSION:	1.0
# LICENSE:	GPL (http://www.gnu.org/licenses/gpl.html)
# REQUIRES:
# NAME:		Make md5
# DESCRIPTION:

# Check that the user didn't select directories
for File in "$@"
do
if [ -d "$File" ]; then
zenity --error --text="'$File' is a directory.
Make md5 cannot handle directories."
exit
fi
done

#Enter the checksum filename to create
CheckName=`zenity --entry --title="Make md5" --entry-text "checksum.md5" --text="Enter the name of your md5 checksum file"`
if [ "$?" == 1 ] ; then exit ; fi

# 1 Check the md5 file
(md5sum "$@" > "$CheckName") 2>&1 | zenity --progress --title "Make md5" --text "Making: $CheckName" --pulsate --auto-close
```

I will be really thankful to who ever can help me andi will keep my computer on until i get some help just in case.

ps by the way anyone knows of a program to do this in a easier way?

Using karmic 9.10 x64

Thanks!

---

### Post by john_spiral on 2010-01-28
```
md5sum filename.iso
```

---

### Post by Leppie on 2010-01-28
> **lefty_lou said:**
> ps by the way anyone knows of a program to do this in a easier way?

Using karmic 9.10 x64

Thanks!
you can use the md5sum command: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by lefty_lou on 2010-01-28
Thanks guys ! Leppie thanks for the link that looks safer lol.


But is there any way to reverse what that script did?! I really need to rescue that iso.

---

### Post by john_spiral on 2010-01-28
if the lost .iso is ultra important, shutdown the system and boot off a live CD that way you won't be over writting the data from the lost .iso.

Try [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) I'm not sure it will be able to recover a .iso

---

### Post by Leppie on 2010-01-28
hopefully you still have the cd/dvd.
the script seems to have overwritten your to be checked file with the md5 checksum file.

---

### Post by lefty_lou on 2010-01-28
Thanks john! I will give it a try if i have no other choice.

The thing is just to make it clear the script was the one who did it when it asked me to put the name of the iso i did then it converted it from a 4.06 GB iso to a 53k iso i guess it changed or over wrote it not sure.

That's why i'm trying to see if there is a way to reverse what the script did.

@leppie 
no I don't that's why it's so important!!

---

### Post by falconindy on 2010-01-28
You can't reverse what the script did. Also, I suspect what you did to "break" it that you passed the name of the .iso file when the zenity popup box prompts you to enter the name of the **checksum file to generate**. This is the output file, **not** the iso file, which you're supposed to pass as an initial argument to the script. If you were to open the "iso" after running the script, I suspect you'd see an md5 checksum and some other nonsense in there.

It's a poorly written script, with error checking in all the wrong places. Zenity doesn't belong here at all, either.

tl;dr: +1 to the people who suggest just running `md5sum` on its own without this terrible wrapper.

---

### Post by lefty_lou on 2010-01-28
> **falconindy said:**
> You can't reverse what the script did. Also, I suspect what you did to "break" it that you passed the name of the .iso file when the zenity popup box prompts you to enter the name of the **checksum file to generate**. This is the output file, **not** the iso file, which you're supposed to pass as an initial argument to the script. If you were to open the "iso" after running the script, I suspect you'd see an md5 checksum and some other nonsense in there.

It's a poorly written script, with error checking in all the wrong places. Zenity doesn't belong here at all, either.

tl;dr: +1 to the people who suggest just running `md5sum` on its own without this terrible wrapper.


So in other words...I'm screwed and lost it? no way to rescue it? or undo what the script did?

that program suggested above recognizes .iso extension for rescue you think it can work??

---

### Post by john_spiral on 2010-01-28
I hope you are now using a live CD? The longer you use your current system the higher the probability you will overwrite data from the lost .iso file.

---

### Post by lefty_lou on 2010-01-28
Nope but i will now all i have is the browser open so far.

---

### Post by Leppie on 2010-01-28
> **lefty_lou said:**
> So in other words...I'm screwed and lost it? no way to rescue it? or undo what the script did?

that program suggested above recognizes .iso extension for rescue you think it can work??
what filesystem are you using?

you may have a better chance with debugfs.

---

### Post by lefty_lou on 2010-01-28
ok now i'm on live cd and ext4

---

### Post by lefty_lou on 2010-01-28
well i'll leave this on and brb have to go to walmart and get some milk and what not, thanks for any suggestions while i'm gone.

---

