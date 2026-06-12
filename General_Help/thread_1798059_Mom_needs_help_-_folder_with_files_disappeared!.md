---
title: "Mom needs help - folder with files disappeared!"
date: 2011-07-05
forum: General Help
---

### Post by Gidget2 on 2011-07-05
So I have this FOLDER on my desktop - I named it DESKTOP ITEMS and I use it like a 'junk drawer" and when I take pics or have files I stash them in there till I am ready to file them properly.  (lazy)

So today was the day I was going to file them all away - or at least start.  I was right in the middle of organizing files in the folder and possibly multitasking - checking emails, listening to my husband, etc... and POOF I swear, it disappeared - I didn't delete it or put it in my trash - it was just GONE.
SO I thought maybe it slid off my desktop and I did check that by opening up the desktop file and nothing.  Then I searched for files - DESKTOP ITEMS and the names of other files and folders within that folder - nothing!  I searched for files modified today - NOTHING - it is gone I tell you lol.

Now, I do use Ubuntu but I am NOT computer savvy and certainly have to be told everything like you were explaining to a child.  So if you have any suggestions please keep that in mind.

Thanks for any suggestions!!!

Gidget2 :D

---

### Post by seawolf167 on 2011-07-05
Welcome to the Forums!

Hopefully we can help you out - could you by any change have added a period '.' in front of the folder name? This would make it "invisible". You can check by turning on displaying of hidden folders and files by selecting "Show Hidden Files/Folder" under the Tools? menu (not on a *nix computer atm) in Nautilus (i.e. a standard folder)

Other suggestions - maybe its in the trash? or inside another folder on the desktop? If you open Nautlius and browse to your home you can hit [CTRL][F] to search for folders/files

---

### Post by Gidget2 on 2011-07-05
> **seawolf167 said:**
> Welcome to the Forums!

Hopefully we can help you out - could you by any change have added a period '.' in front of the folder name? This would make it "invisible". You can check by turning on displaying of hidden folders and files by selecting "Show Hidden Files/Folder" under the Tools? menu (not on a *nix computer atm) in Nautilus (i.e. a standard folder)

Other suggestions - maybe its in the trash? or inside another folder on the desktop? If you open Nautlius and browse to your home you can hit [CTRL][F] to search for folders/files

Thanks so much.  I did check for hidden folders and files and found nothing and I also checked the trash and found nothing.  

I was wondering, is it possible for a file name to change and therefore make it difficult to search for??  My son suggested:  "open a terminal and type "cd Desktop; ls -a"  If it doesn't show the file, it got deleted somehow."  And I did that and it showed no file by that name.  SO that makes me wonder if the name has been changed somehow - I certainly didn't do that.  UGH.  THANKS again!!

---

### Post by Frogs Hair on 2011-07-05
I had a document disappear once and I knew it was not deleted . When I checked desktop in nautilus the document was there even though it was not visable on the desktop . It may be worth checking .

---

### Post by seawolf167 on 2011-07-05
> **Gidget2 said:**
> open a terminal and type "cd Desktop; ls -a"  If it doesn't show the file, it got deleted somehow.

This would only show if the folder in question were still on the desktop (and you recognized it under the same name). There is nothing I know of that would spontaneously change the folder name, though it could easily happen with the wrong keystrokes, say you hit [F2] with the folder selected and started typing, you would be changing the folder name, but this would typically be pretty easy to spot.

You can also try 

```
sudo find / -type d -iname '*some.part.of.the.name.you.remember*'
```

if that gives too many results to wade through in the terminal, you can either run it again being more specific, or redirect the output to a file and look through the file

```
sudo find / -type d -iname '*some.part.of.the.name.you.remember*' > ~/Desktop/find-output && gedit ~/Desktop/find-output
```

---

### Post by Rasa1111 on 2011-07-05
> **Frogs Hair said:**
> I had a document disappear once and I knew it was not deleted . When I checked desktop in nautilus the document was there even though it was not visable on the desktop . It may be worth checking .

 Yeah same here. 
Wasnt on my desktop where it previously was, 
but when I opened the "desktop folder" in Nautilus, there it was. 
Definitely worth a check. 

Good luck Gidget.

---

### Post by Gidget2 on 2011-07-06
> **seawolf167 said:**
> This would only show if the folder in question were still on the desktop (and you recognized it under the same name). There is nothing I know of that would spontaneously change the folder name, though it could easily happen with the wrong keystrokes, say you hit [F2] with the folder selected and started typing, you would be changing the folder name, but this would typically be pretty easy to spot.

You can also try 

```
sudo find / -type d -iname '*some.part.of.the.name.you.remember*'
```if that gives too many results to wade through in the terminal, you can either run it again being more specific, or redirect the output to a file and look through the file

```
sudo find / -type d -iname '*some.part.of.the.name.you.remember*' > ~/Desktop/find-output && gedit ~/Desktop/find-output
```


I COULD HUG YOU!!!!!!!!!!!!!!!!!!  This worked!!!  I have to say, I had to get my husband to help me but he used the find command and it showed that the file was actually in the trash but not seen - it couldn't be seen maybe because it was so large.  It did not show up in Nautilus which was weird.  

But all is right with the world now lol and I THANK YOU GUYS for helping me!!!!

You rock :guitar:

---

### Post by seawolf167 on 2011-07-06
> **Gidget2 said:**
> I COULD HUG YOU!!!!!!!!!!!!!!!!!!  This worked!!!  I have to say, I had to get my husband to help me but he used the find command and it showed that the file was actually in the trash but not seen - it couldn't be seen maybe because it was so large.  It did not show up in Nautilus which was weird.  

But all is right with the world now lol and I THANK YOU GUYS for helping me!!!!

You rock :guitar:

Glad you got it working! Now that this panic is fresh in your mind... make sure to keep backups of all your important files/folders! 

Please mark the thread as solved under "Thread Tools". :P

---

### Post by Gidget2 on 2011-07-06
I will!!  I had a backup from May 24 - but of course there were some new things I didn't want to have done forever.  The main lesson for me is to file things away in their proper spot to start with.  No more being lazy.  

Thanks again.  Now to figure out how to mark this as solved.

---

### Post by Habitual on 2011-07-06
> **Gidget2 said:**
> ...The main lesson for me is to file things away in their proper spot to start with.  No more being lazy.

At least it wasn't a "destructive" lesson. ;)

---

### Post by Rasa1111 on 2011-07-06
Good call seawolf!! :D

---

