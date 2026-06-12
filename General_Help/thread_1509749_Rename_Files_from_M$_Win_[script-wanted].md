---
title: "Rename Files from M$ Win [script-wanted]"
date: 2010-06-14
forum: General Help
---

### Post by AlphaLexman on 2010-06-14
I have been looking for a bash or nautilus script that will rename all my old M$ Win directories and files to Linux filename standards. No spaces, no special characters, and do it smartly. In other words replace [FONT=DejaVu Sans, sans-serif]è with e, instead of deleting [/FONT][FONT=DejaVu Sans, sans-serif]è[/FONT] [FONT=DejaVu Sans, sans-serif]etc. Also, if the extension is in CAPS, change to lowercase.
[/FONT]

---

### Post by skooter1121 on 2010-06-14
try Renamer 1.4, does it all.

[http://gnome-look.org/content/show.php/Renamer?content=87601](http://gnome-look.org/content/show.php/Renamer?content=87601)


-SKooter

---

### Post by AlphaLexman on 2010-06-14
Thanks, not quite a one-step solution, but VERY easy to use.

Nice!

---

### Post by u-slayer on 2010-06-14
> **AlphaLexman said:**
> I have been looking for a bash or nautilus script that will rename all my old M$ Win directories and files to Linux filename standards. No spaces, no special characters, and do it smartly. In other words replace [FONT=DejaVu Sans, sans-serif]è with e, instead of deleting [/FONT][FONT=DejaVu Sans, sans-serif]è[/FONT] [FONT=DejaVu Sans, sans-serif]etc. Also, if the extension is in CAPS, change to lowercase.
[/FONT]

Linux filenames can handle any special characters including [FONT=DejaVu Sans, sans-serif]è[/FONT] and space.

---

### Post by AlphaLexman on 2010-06-14
> **u-slayer said:**
> Linux filenames can handle any special characters including [FONT=DejaVu Sans, sans-serif]è[/FONT] and space.

I know, but typing them in on a terminal from a standard US keyboard can be tricky!

---

### Post by u-slayer on 2010-06-14
> **AlphaLexman said:**
> I know, but typing them in on a terminal from a standard US keyboard can be tricky!

Just use stars for the characters you can't type. (It saves typing time anyway"

Example:

cd Tyrannosaurus

becomes

cd T*s

It's much easier.

---

### Post by AlphaLexman on 2010-06-14
> **u-slayer said:**
> Just use stars for the characters you can't type. (It saves typing time anyway"

Example:

cd Tyrannosaurus

becomes

cd T*s

It's much easier.

I welcome your advice, but I feel like you are offering a short-term solution opposed to moving windows files to a linux system. I am truly looking for a long-term solution to get rid of the problems associated between dos standards and linux standards.

However, thank you.

---

### Post by skooter1121 on 2010-06-14
RE: Renamer

I've searched high and low for scripts that actually convert from UNIX to windows format. My users (Attorneys!) have issues reading filenames with '.' or '_'. Go figure.

The best I've found is Renamer I referenced above. I've successfully renamed thousands of files. In recursive mode it can go through a complete drive. You might need to run it a couple of times to get all your changes. Other than Renamer would would need to create some custom scripts.

I have corresponded with the author and he has incorporated some of my suggestions. He might have a better solution for your needs. If I remember correctly he was looking into a method of retaining custom settings, so you could run them again easily.

-Good Luck

-Skooter

---

### Post by AlphaLexman on 2010-06-14
If I can be more specific... I have folder/files like this:

> /media/ntfs/Documents and Settings/User Name/My Documents/My Music/Artist Name/Year - Album Name/01 - Song Title Name.mp3

and I want to move or copy to

> ~/Music/Artist_Name/Year.Album_Name/01.Song_Title_name.mp3

AND, if any folder/directory or filename has any special characters...

> Mötley Crüe
Queensrÿche
Santana/Best of Santana (Disc2)/09 Flor D' Luna (Moonflower).mp3

gets renamed like this:

> Motley_Crue
Queensryche
Santana/Best_of_Santana_Disc2/09.Flor_D_Luna_Moonflower.mp3


---

### Post by tom.swartz07 on 2010-06-14
> **u-slayer said:**
> Just use stars for the characters you can't type. (It saves typing time anyway"

Example:

cd Tyrannosaurus

becomes

cd T*s

It's much easier.

What about tab completion? You hit the TAB key and it finished the name.

Example:

cd Tyrannosaurus

becomes
cd Ty[TAB]
cd Tyrannosaurus

---

### Post by skooter1121 on 2010-06-14
Do you want to rename or copy/move?

Rename the files where they are. Then move/copy if you want.

With just a quick look at your file structure, and if you are careful you can do everything in Renamer.

For example use Renamer to complete one substitute at a time:

Rename \My Music to \Music
Replace Recursively Substitute ' - '(space dash space)to'.'(period)
Replace Recursively Substitute '' (space) to '_' (underscore) 
and so on..

Yer on your own from here!

-Skooter

---

