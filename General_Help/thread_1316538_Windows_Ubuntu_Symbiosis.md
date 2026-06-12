---
title: "Windows Ubuntu Symbiosis"
date: 2009-11-06
forum: General Help
---

### Post by monkeyatwar on 2009-11-06
This is just an idea that has been going about in my head for awhile now but is there any way to make windows and ubuntu completely symbiotic as in connect your folders to each other such as you music folders would be linked together same as you documents and such. I know how to make certain aspects connected such as my firefox browser uses the same profile for both OS's and i have songbird set up to watch my windows itunes library, and a couple other thing but all i'm really concerned about here is ubuntu's home folder using windows (since i know you can't do it the other way around)

---

### Post by Martin_sensei on 2009-11-06
You could just use a common partition.

I have 3 partitions: Windows, Ubuntu, and Data.  My Personal Windows folders are pointing to places in the Data partition (Pictures, Mucis, Video, Documents etc) and the same parition is mounted on boot in Ubuntu.

Although I havent mounted my /home folder to this data partition, maybe this is possible I am not sure...

Sorry this is only half a solution!  Perhaps someon else could add to this?

---

### Post by monkeyatwar on 2009-11-06
that does sound like a good solution in fact at the moment i have my hard disk set into 4 partitions 47g Ubuntu 120g windows 73g pure storage and 9g encrypted however trying to move all my data to the storage and then resize windows and ubuntu os partitions down to a smaller size would be highly impractical at this point however as it turns out my linux partition doesn't really have to much data on it it's mostly on my windows or storage ones

---

### Post by P4man on 2009-11-06
open nautilus file manager. Go to bookmarks, edit bookmarks. Set the location of your music / documents / images etc to the windows partition where you have them. done

---

### Post by monkeyatwar on 2009-11-06
That works for me, thanks :D

---

### Post by HiImTye on 2009-11-06
or symlink your music folder to your music on your storage, etc

---

### Post by coffeecat on 2009-11-06
Oh yes, I did this once. With my data partition mounted at bootup courtesy of fstab, I created 'Video', 'Music', 'Correspondence' - usual sort of thing - folders in the data partition, and then created symlinks in /home: 'Video', 'Music', 'Correspondence', etc. Then, in Windows, I created shortcuts in 'My Documents' to the 'Video', etc folders in what Windows saw as E:. It all worked very nicely, except that I then very rarely booted into Windows. :) By then, Linux had taken over. :lol:

---

### Post by monkeyatwar on 2009-11-07
> **coffeecat said:**
> Oh yes, I did this once. With my data partition mounted at bootup courtesy of fstab, I created 'Video', 'Music', 'Correspondence' - usual sort of thing - folders in the data partition, and then created symlinks in /home: 'Video', 'Music', 'Correspondence', etc. Then, in Windows, I created shortcuts in 'My Documents' to the 'Video', etc folders in what Windows saw as E:. It all worked very nicely, except that I then very rarely booted into Windows. :) **By then, Linux had taken over.** :lol:

you say that last part like it's a bad thing ;)

---

### Post by coffeecat on 2009-11-07
> **monkeyatwar said:**
> you say that last part like it's a bad thing ;)

Eh!? :shock:

No, have another look. I'm laughing - with relief and joy. :wink:

---

