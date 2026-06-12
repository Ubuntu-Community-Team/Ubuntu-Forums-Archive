---
title: "Error moving file: Permission denied"
date: 2010-11-22
forum: General Help
---

### Post by ToxicDoom420 on 2010-11-22
Hey guys! Well, i'm **NOT **new to Ubuntu, but i have actually just installed 10.10 AGAIN - after going back to vista. Don't even get me started on why i bothered LOL. 

Anyways - i'm trying to write a theme folder to usr/share/pixmaps/pidgin/guifications/themes ....and, it keeps giving me that error. Saying that i don't have the permission.

Now, it's been awhile since i've used Ubuntu....so, how do i go about enabling permissions for folders again? Preferably that folder....but, also....any other, because i have a feeling i'll run into this again.

I don't know if this might make a difference....but, the **ENTIRE **drive is dedicated to ubuntu. No windows, no partitions, no...nothing. Just 10.10 - and, my external drive :)

Any help ASAP would be [B]GREATLY APPRECIATED! :)

[/B]Thanks! :D

---

### Post by beew on 2010-11-22
I would have just used the command "sudo mv original_folder/file destination_folder/file"

Sorry if this sounds too obvious since you said you are not new to Ubuntu, but just in case since you also said you have forgotten quite a bit.

---

### Post by ToxicDoom420 on 2010-11-22
hmmm....yea, beew, that's not obvious LOL. See, for me....i don't play around too much with the console. The only thing i really know how to do in the console are the sudo commands **LOL** the last time i played around too much in the console, i screwed versions up. I've been using ubuntu off and on since version 8 - but, got the idea yesterday that since everything i did on windows was with free software, that i'd give it a go again :)

There's gonna be a bit of a learning curve for me...but, i **HOPE **to have it all figured out soon....since i am that much of a geek, and will figure out stuff on my own as i go too :)

Thanks for the reply! I'll try that now! :)

---

### Post by searchfgold6789 on 2010-11-22
Or you could change the ownership of the folder, which tends to work better for other people.
```
sudo chown -R <your user name> <name of file/folder>
```
Once you have collected enough ways to do what you wish to do please mark this thread as Solved :)

---

### Post by ToxicDoom420 on 2010-11-22
YAY! Now i have 2 things to try! Thank you so much searchfgold for the reply! Hopefully one of these things works for me. Well, i'm sure they will....i just have to get all geeky for a few minutes and figure out how to do it right where i don't mess things up.

might help if my cat wasn't crawling all over me **LOL**

---

### Post by ToxicDoom420 on 2010-11-22
[COLOR=Black]i did talk to a friend, and he suggested "sudo nautilus" - which opens a new window for root. So, i tried that, and it WORKED! :D 

He also suggested that i try the cp -R ...which i TRIED...but, i screwed up. So, the nautilus thing worked the first time with opening a root folder, and then i could drag and drop from there. :D
[/COLOR][SIZE=3][COLOR=Black][/COLOR][/SIZE]

---

