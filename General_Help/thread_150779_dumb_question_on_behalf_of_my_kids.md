---
title: "dumb question on behalf of my kids"
date: 2006-03-26
forum: General Help
---

### Post by m.musashi on 2006-03-26
I got my kids (5 and 9) set up with Ubuntu running KDE (and gnome). Although the machine is a dual boot with XP they have been using Ubuntu nearly 100% for the past month or so. Actually, they don't even know XP from Ubuntu. They just play games and send grandma email and lately choose Ubuntu - all on their own.

Anyway, their favorite pasttime seems to be downloading pictures for wallpaper. I set them up with a wallpaper folder and they can do the "change desktop background" thing and all but I can't seem to figure out how to "import" all the pictures. On the gnome side they can add them to the wallpaper dialog and then scroll through as they wish. On the KDE side, only the preinstalled wallpapers stay in the list. How do you get new wallpaper to stay added to the list so you don't have to browse each time?

Hope that makes sense.

Thanks.

---

### Post by mindspin on 2006-03-26
KOntrol center-> Backgrounds->download new backgrounds 

its on the right side of the window...

---

### Post by Specialsauce on 2006-03-26
hey! its another colorado user! good to see ya!
anyways, shouldnt it be in the configure desktop window, and then click the little folder icon? is that what your looking for? im not fully understanding.

---

### Post by m.musashi on 2006-03-26
Okay, let me try and clarify. I found the little folder in the configure desktop window and that lets you find a new background and will add it to the list of available backgrounds. However, if you view several, only the one you actually choose to use will get added and not permanantly either. As soon as you choose a different background it too will be gone from the list. What I'd like to do is add all the backgrounds they downloaded to the list of available backgrounds. Also, they should be able to add additional backgrounds as they find them. That is how it works on the gnome side but in KDE there doesn't seem to be any easy way to add backgrounds to a central location.

Hope that is a bit more clear.

Specialsauce - where in CO are you? I'm in Fort Collins.

---

### Post by m.musashi on 2006-03-26
[QUOTE=mindspin]KOntrol center-> Backgrounds->download new backgrounds 

its on the right side of the window...[/QUOTE]
The "get new wallpapers" option only takes you to kde-look.org. It doesn't let you add backgrounds from a local folder (unless that is an option I'm not seeing).

Thanks.

EDIT: did a bit more looking and I found the folder with all the default backgrounds /usr/share/wallpapers. For each background there is also a .desktop file. I have no idea what that is for. I could just copy all the backgrounds here but would need root access. Also, I don't know if the .desktop file is necessary.

I can probably figure this out but since I want my kids to be able to do it it needs to be a simpler process - like on the gnome side. I like KDE a bit better and for them I think it's a good choice, but the dumb backgrounds (and themes in general) could be a bit more user friendly.

---

### Post by arcanistherogue on 2006-03-26
Hmm... I don't know. 

I have a folder for all my wallpapers (/home/john/Wallpapers), and it has about 40 or so I like.  When I want to switch I just hit browse, and since I always choose wallpapers from this folder it opens the browse window there by default.  KDE even shows a nice little preview of the one you select.  

This works fine for me, but it might not work for your kids.  I think though that there is a thing in the Configure Desktop part that switches wallpapers every now and then like that mac effect, but it is a straight transition with none of those neato effects.  It works nicely though, you might want to let them try that out.  As I recall what it does is selects wallpapers from the same folder to switch too.

BTW, if they are into games, I suggest Neverball.  It is one of my favorite Linux games, its where you guide a ball to the exit by tilting the level and gathering coins as you go along.  Sorry, I have been suggesting this game to everyone :mrgreen:

---

### Post by arcanistherogue on 2006-03-26
Sorry to double post, But I know for a fact that the themes and icons are just as easy to configure as the GNOME wallpapers.  When you drag the *.tar.bz2 icon archive (granted that it is setup right, but most full sets are) into the icon list window, it stays there forever.  same with Window decorations, but alot of win decos I have came across need to be configured from source.

---

### Post by m.musashi on 2006-03-27
[QUOTE=arcanistherogue]Hmm... I don't know. 

I have a folder for all my wallpapers (/home/john/Wallpapers), and it has about 40 or so I like.  When I want to switch I just hit browse, and since I always choose wallpapers from this folder it opens the browse window there by default.  KDE even shows a nice little preview of the one you select.[/quote]
That is how we have it set. You can easily pick a new wallpaper from the folder but I was kind of hoping to add to the original default list so they wouldn't have to browse. On the plus side, they will learn a bit more this way. I'm actually quite amazed by how comfortable they have become in a very short time (not that they were very computer savy before so not much to unlearn). 

> This works fine for me, but it might not work for your kids.  I think though that there is a thing in the Configure Desktop part that switches wallpapers every now and then like that mac effect, but it is a straight transition with none of those neato effects.  It works nicely though, you might want to let them try that out.  As I recall what it does is selects wallpapers from the same folder to switch too.
I set this up to try. It's called slide show. You can add whatever backgrounds you want and they cycle through changing every x minutes. It's a cool option they may like. I'm not a mac person so I'm not sure about the effects you mentioned. Is it more of a smooth transition rather than just a switch?

The help menu mentions that you can also replace the background with a program and gives the example of "kdeworld". Are there other cool apps for this? The one preloaded is called kwebdesktop but I don't see what it actually does.

> BTW, if they are into games, I suggest Neverball.  It is one of my favorite Linux games, its where you guide a ball to the exit by tilting the level and gathering coins as you go along.  Sorry, I have been suggesting this game to everyone :mrgreen:
Thanks for the suggestion. Always good to hear about new programs. I'll give it a try.

EDIT: grammar/spelling

---

### Post by Randomskk on 2006-03-27
[QUOTE=arcanistherogue]
BTW, if they are into games, I suggest Neverball.  It is one of my favorite Linux games, its where you guide a ball to the exit by tilting the level and gathering coins as you go along.  Sorry, I have been suggesting this game to everyone :mrgreen:[/QUOTE]
..wow XD
you just got me hooked to that game ><

---

### Post by Jucato on 2006-03-28
m. musashi: I'm not sure if I'm too late for this info but:
/usr/share/wallpapers is the place to put wallpapers that you want to become available to all present and future users, that is, system wide wallpapers. 
There's a folder in your /home/user/.kde/share directory for wallpapers that will only be available to the user that puts them there, and doesn't need root access (you just need to be the owner of that home directory). I'm not exactly sure if the exact directory is /home/usr/.kde/share/wallpapers or /home/usr/.kde/share/config/wallpapers (I'm not in Kubuntu right now :D).

---

### Post by aysiu on 2006-03-28
/home/username/.kde/share/apps/kstyle/themes/original/wallpapers
/home/username/.kde/share/apps/kthememanager/themes/original/wallpapers

Another solution would be to create a symlink to /usr/share/wallpapers and change permissions on the /usr/share/wallpapers directory so that everyone can access it: ```
sudo chmod -R 777 /usr/share/wallpapers
ln -s /usr/share/wallpapers ~/wallpapers
```

---

### Post by m.musashi on 2006-03-28
[QUOTE=Fenyx]m. musashi: I'm not sure if I'm too late for this info but:
/usr/share/wallpapers is the place to put wallpapers that you want to become available to all present and future users, that is, system wide wallpapers. 
There's a folder in your /home/user/.kde/share directory for wallpapers that will only be available to the user that puts them there, and doesn't need root access (you just need to be the owner of that home directory). I'm not exactly sure if the exact directory is /home/usr/.kde/share/wallpapers or /home/usr/.kde/share/config/wallpapers (I'm not in Kubuntu right now :D).[/QUOTE]
Not too late at all. I still haven't figured this out. My first thought was to put everything in the system folder /usr/share/wallpapers but I'd have to change permissions and since it's for my kids I didn't want them to be able to mess anything up. I was not aware of the .kde folder so thanks. If I just move wallpapers there will they show up in the change desktop app? There is also another folder level or two. One is "desktop" and has the image for the current desktop. Do I add them there or up a level? I guess I can play around. Thanks.

[QUOTE=aysiu]/home/username/.kde/share/apps/kstyle/themes/original/wallpapers
/home/username/.kde/share/apps/kthememanager/themes/original/wallpapers

Another solution would be to create a symlink to /usr/share/wallpapers and change permissions on the /usr/share/wallpapers directory so that everyone can access it: ```
sudo chmod -R 777 /usr/share/wallpapers
ln -s /usr/share/wallpapers ~/wallpapers
```[/QUOTE]
What is the difference between the two folders? I have both and they seem to be very similar. Also, could you explain a bit what a symlink is? Thanks.

---

### Post by aysiu on 2006-03-28
[QUOTE=m.musashi]My first thought was to put everything in the system folder /usr/share/wallpapers but I'd have to change permissions and since it's for my kids I didn't want them to be able to mess anything up.

What is the difference between the two folders? I have both and they seem to be very similar. Also, could you explain a bit what a symlink is? Thanks.[/QUOTE] The first command actually changes permissions so that anyone can read/write the /usr/share/wallpapers folder. The rest of /usr/share is protected, though--and the symlink will make it so that your kids won't even realize they're in /usr/share/wallpapers.

They'll think they're in /home/kidsname/wallpapers--that's where /usr/share/wallpapers is "symlinked" to.

A symlink is kind of like a Windows shortcut or Mac alias. When you click on ~/wallpapers, you'll see the contents of /usr/share/wallpapers.

---

### Post by m.musashi on 2006-03-28
[QUOTE=aysiu]The first command actually changes permissions so that anyone can read/write the /usr/share/wallpapers folder. The rest of /usr/share is protected, though--and the symlink will make it so that your kids won't even realize they're in /usr/share/wallpapers.

They'll think they're in /home/kidsname/wallpapers--that's where /usr/share/wallpapers is "symlinked" to.

A symlink is kind of like a Windows shortcut or Mac alias. When you click on ~/wallpapers, you'll see the contents of /usr/share/wallpapers.[/QUOTE]
Cool, that might actually be the fix I was looking for. I tried to put wallpapers in the .kde/.../wallpapers but the didn't show up in the list of wallpapers in the configure desktop dialog. I'll give this a try. Thanks again.

---

### Post by Jucato on 2006-03-28
[quote=m.musashi]Cool, that might actually be the fix I was looking for. I tried to put wallpapers in the .kde/.../wallpapers but the didn't show up in the list of wallpapers in the configure desktop dialog. I'll give this a try. Thanks again.[/quote]
 
Strange... that usually worked for me. Maybe I've given the wrong directory/folder. I'm just working from memory (the motherboard on my dual boot system has some problems, and I'm forced use my sister's XP system till it gets fixed :()
 
If there will be no security issues or any other problems with aysiu's suggestion, and if you find that it works, go for it. Just remember that it's still a "system folder" and that what you put in there will affect your entire system, no matter who the user is.

---

### Post by m.musashi on 2006-03-28
[QUOTE=Fenyx]Strange... that usually worked for me. Maybe I've given the wrong directory/folder. I'm just working from memory (the motherboard on my dual boot system has some problems, and I'm forced use my sister's XP system till it gets fixed :()
 
If there will be no security issues or any other problems with aysiu's suggestion, and if you find that it works, go for it. Just remember that it's still a "system folder" and that what you put in there will affect your entire system, no matter who the user is.[/QUOTE]
I've got the mobo blues too. Mine kind of works though. I'm trying this on my laptop though at the moment.

I found the folder alright but nothing I put in there showed up in the configure desktop dialog. I could be doing something wrong but I don't see what. Maybe there is a step missing.

aysiu: I did the symlink but it didn't do quite what I expected. Inside my /home/wallpapers folder I now have another folder called wallpapers. It's obviously the linked folder to /usr/share/wallpapers. I can drag and drop wallpapers from my folder to the linked one and they show up in the configure desktop dialog just fine. I kind of expected the opposite - i.e. my /home/wallpapers showing up in the /usr/share/wallpapers folder. As it is, anything saved into the /home/wallpapers will need to be moved for it to be usable. Of course that is an easy step.

---

