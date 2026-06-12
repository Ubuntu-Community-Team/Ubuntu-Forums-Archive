---
title: "Finding and Copying codes"
date: 2009-08-27
forum: General Help
---

### Post by Guyik on 2009-08-27
Hello

I have two questions that I think they are not very difficult.

The first one is: Could I make a code to find every folder which name is the same and to copy them (and the files and folders which are in it) into another folder? I know about find command, but I don't know much about neither variables nor loops.

The second question is: Could I make a code to copy every folder (and the files and folders which are in it) which are in another one except a specified folder?

Thank you very much

---

### Post by Liolikas on 2009-08-27
Yes you could and you could do this with one simple command.
here similar explained example:
> 
find /mnt/music -iname "*.mp3" -exec cp '{}' /mnt/music ';'

FInd all ot the .mp3 files in the music directory (doesn't matter that they are in subfolders)
copy (or mv) every found one '{}' to the root /mnt/music directory

I hope you manage to adapt it to your situation if not ask for more help.

---

### Post by Guyik on 2009-08-27
Thank you very much Liolikas

I have tried it and it works fine.

---

### Post by Guyik on 2009-09-11
Ok, I am trying this:
> find /path -type d -name Name -exec mv '{}'/. '{}'/.. ';'It says "Dispositivo ó recurso ocupado" which means - in Spanish - something like "Device or resource are busy".
It works fine if I use cp instead of mv. What is happening? :confused:

---

### Post by DaithiF on 2009-09-11
Hi,
where are you trying to move the directory?
It looks like you are saying move <somedirectory> to <somedirectories> parent directory.  But every directory is already *in* its parent directory, so it doesn't really make sense.

if you give an example of your directory structure and show what you want to move where, that would help
thanks

---

### Post by Guyik on 2009-09-11
I need this code because I am doing a kind of Backup. I have files in my PC that I want to copy into my external HDD for backup, but I have other files (like most of videos, images and music) I want to move into my HDD, and not to keep them in the PC.

So I had this idea: "I can put the files I want to copy into directories like Music, Images, etc. -as it is usual- and the files I want to move into a directory called 'Move' which would be in the directories I said before."
That is why I have "/home/guyik/Images" with the images I want to save in both my internal and external HDD, and I have "/home/guyik/Images/Move" with the images I want to save only in my external HDD.

Now, I made the code:
> #!/bin/bash
cp -R -i -v -P /home/guyik/* /media/MyHDD/
find /media/MyHDD -type d -name Move -exec mv '{}'/* '{}'/.. ';'
And it says something like > I cannot do 'stat' on <</media/MyHDD/Images/Move/*>>: The file or directory does not existI tried this: > find /media/MyHDD -type d -name Move -exec cp '{}'/* '{}'/.. ';' without success, it says the same.

So I tried: > find /media/MyHDD -type d -name Move -exec cp '{}'/. '{}'/.. ';' and It worked! And it works!!

And I think it worked with mv once, but it doesn't now. It says: "Device or resource are busy".

WHY!!?? I don't know, and my PC doesn't answer me.

---

### Post by DaithiF on 2009-09-11
ok, i think i understand.
i would do it this way:

```
find -type f -path '*/Move/*' | while read file
do
  echo mv "$file" "${file%%/Move/*}"
done

```

(take out the 'echo' part once/if you're happy its doing what you want.)

---

