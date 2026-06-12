---
title: "Un F-Spot-ing a photo collection"
date: 2010-05-14
forum: General Help
---

### Post by Ozor Mox on 2010-05-14
I maintain a computer running Ubuntu 10.04 for my family which contains our entire photo collection. I was using F-Spot to manage it but, to be honest, I'm not massively keen on F-Spot. Every time I remove all the duplicates, a few weeks later a load more seem to have appeared.

Anyway, F-Spot imports photos in to the /home/<user>/Photos folder, and puts them in Year/Month/Day directories, presumably for its date slider thing across the top to work properly. Can anyone think of a good way to remove all the photos from their sub, sub-sub, and sub-sub-sub directories and put them all in one big directory? I guess a nice bash script would do the job, anyone willing to get me started?! :)

---

### Post by nothingspecial on 2010-05-14
```
find ~/Photos -name *.jpg -exec mv '{}' ~/one_big_folder \;
``` 

That assumes all your photos end with .jpg.

You have to create ~/one_big_folder (or whatever) first.

If the are all different file extentions but you have no other type of files in you Photos directory an downwards

```
find ~/Photos -type f -exec mv '{}' ~/one_big_folder \:
```

That will mv any file to one big folder, without moving the directories

---

### Post by Ozor Mox on 2010-05-14
Thanks very much nothingspecial, very helpful.

---

### Post by Dragonbite on 2010-05-14
> **Ozor Mox said:**
> I maintain a computer running Ubuntu 10.04 for my family which contains our entire photo collection. I was using F-Spot to manage it but, to be honest, I'm not massively keen on F-Spot. Every time I remove all the duplicates, a few weeks later a load more seem to have appeared.

Anyway, F-Spot imports photos in to the /home/<user>/Photos folder, and puts them in Year/Month/Day directories, presumably for its date slider thing across the top to work properly. Can anyone think of a good way to remove all the photos from their sub, sub-sub, and sub-sub-sub directories and put them all in one big directory? I guess a nice bash script would do the job, anyone willing to get me started?! :)

Yeah, I've never like that structure either.  Plus, it looks like [Shotwell ]("http://yorba.org/shotwell/")is gaining momentum and is to be the default in future Ubuntu releases (at least the Netbook I think).

---

### Post by cariboo on 2010-05-14
Moved to General Help, as this doesn't belong in the Cafe.

---

### Post by Dragonbite on 2010-05-14
> **nothingspecial said:**
> ```
find ~/Photos -name *.jpg -exec mv '{}' ~/one_big_folder \;
``` 

That assumes all your photos end with .jpg.

You have to create ~/one_big_folder (or whatever) first.

If the are all different file extentions but you have no other type of files in you Photos directory an downwards

```
find ~/Photos -type f -exec mv '{}' ~/one_big_folder \:
```

That will mv any file to one big folder, without moving the directories

Can you break the command down?  I want to understand what it's doing and everything.

So **find ~/Photos -name *.jpg ** means find in the Photo's directory (off the /home/<username>/ directory) all files with name ending in .jpg.

And **-exec mv '{}' ~/one_big_folder \;** means to execute the mv (move) command, but what is the **'{}'** for?  Is that a placeholder for the file the **find** found? 

I know the **~/one_big_folder** is the destination, and what is that last **\;** for?

---

### Post by nothingspecial on 2010-05-14
> **Dragonbite said:**
> Can you break the command down?  I want to understand what it's doing and everything.

So **find ~/Photos -name *.jpg ** means find in the Photo's directory (off the /home/<username>/ directory) all files with name ending in .jpg.

And **-exec mv '{}' ~/one_big_folder \;** means to execute the mv (move) command, but what is the **'{}'** for?  Is that a placeholder for the file the **find** found? 

I know the **~/one_big_folder** is the destination, and what is that last **\;** for?


Yep '{}' means everything that find has found

; ends the exec command the escape \ stops the shell as interpreting it as the the end of the find command. You could type  ```
'{} ;' 
``` instead of '{}' \; in the same way as you cd into a directory wiyh a space in it`s name.

I don`t actually know why you have to end the -exec, I just know you have to.

While we are on the subject, it is advised to run the command without the -exec bit first just to check which files exec is going to manipulate.

For example, the op wanted to move every photo into his ~/Photos folder
he could have done 
```
cd ~/Photos
find ./ -type f -exec mv '{}' ./ \;
```

./ means "this directory"

if he forgot to cd into the Photos directory he would have moved every file (Videos, mp3s, configs, icon pngs --- the lot) into his home directory. Find is recursive by default although you can specify how many levels it will traverse through the file system.

If he`d done it from / .......:shock:

---

### Post by nothingspecial on 2010-05-14
**_[SIZE="5"][COLOR="Red"]DO NOT PUT THIS IN A TERMINAL, IT IS FOR ILLUSTRATION ONLY[/COLOR][/SIZE]_**

Thinking about it abit more, the next step would be

```
find ./ -type d -exec rm -r '{}' \;
```

Which would find and remove all the (now empty) directories.

Of course, if you`d already done the first bit from the wrong directory, you'd have stuffed up your installation already and I don`t suppose that it would matter.

---

### Post by StuartN on 2010-05-14
> **Ozor Mox said:**
> Can anyone think of a good way to remove all the photos from their sub, sub-sub, and sub-sub-sub directories and put them all in one big directory?

If you do this kind of thing too infrequently to remain familiar with the command line, then a regular search and move is effective:

Using Places -> Search for Files, find all your images. Select them in the list (click the first and shift-click the last to select all) and drag them to another location - press shift when dragging to actually move rather than copy them.

Using a dual-pane file manager like Krusader, select all the images into a list-box and move them.

Using gThumb, run a search and move them from the image browser.

---

