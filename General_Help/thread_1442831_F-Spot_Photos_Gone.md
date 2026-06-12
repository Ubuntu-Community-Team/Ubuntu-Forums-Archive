---
title: "F-Spot Photos Gone"
date: 2010-03-30
forum: General Help
---

### Post by JugglinPhil on 2010-03-30
It only happened a few minutes ago, and it really annoyed me:
I had all my photos in F-Spot, a few thousand all nicely tagged and tidied up. 
Now I open F-Spot and everything is gon - no more pictures, no more custom created tags, just the way it looks after installation. 
The picture files are still there in the ~/Pictures/Photos folder that F-Spot created, but I really can't be bothered recreating all those tags.
Is there any way I can rescue my tags?

---

### Post by switch10 on 2010-03-30
I have no idea if F-spot saves the tags to the actual files, but have you tried to re-import all the files back into F-spot and see if it kept all of the tags, etc..

---

### Post by JugglinPhil on 2010-03-30
There is an option to save the tags directly to the files, but I am afraid I chose to save them separately. I will try to reimport them, see what happens.

---

### Post by JugglinPhil on 2010-03-31
I reimported everything, but the tags are gone. Is there maybe an option to change profiles like in thunderbird or firefox that might be responsible for the sudden emptiness of my photo library? I am really confused as to why this happened and I'm afraid it'll happen again, so it would be great to find the answer to this.

---

### Post by JugglinPhil on 2010-03-31
Okay, not only do I have to rewrite all my tags, F-Spot didn't even rotate the actual files, so I have to rotate all those photos again. Really annoying.
I'm just wondering if there is a decent alternative to F-Spot out there, because I am getting fed up with it. Anybody an idea?

---

### Post by JugglinPhil on 2010-04-03
Just for the record, I've given it up and I switched to Digikam, which in my eyes looks quite a bit better.

---

### Post by strabomx on 2011-03-10
Now, one year later, you will not need that information anymore. 

But maybe someone else encounters 
similar problems like Mr. JugglinPhil and me.

After an hour of anger i read the f-spot faq and found out:
The only problem was that they moved user-databases etc from ~/.gnome2/f-spot to ~/.config/f-spot
without any notification. Even in their faq they (conf-)use both paths.

you have to stop any running f-spot session and type  
rm -rf ~/.config/f-spot 
mv  ~/.gnome2/f-spot ~/.config/
and restart f-spot. After that everything should look like before updating

mfg strabomx max
I

---

