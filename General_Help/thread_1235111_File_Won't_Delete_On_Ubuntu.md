---
title: "File Won't Delete On Ubuntu"
date: 2009-08-08
forum: General Help
---

### Post by mikethedj4 on 2009-08-08
Well this is my first post here to hello everyone.

Well I downloaded the tarball for Flock, and when I extracted it I renamed the flock folder .flock so it could be hidden on my desktop, Big mistake. I then tried to delete both the tarball, and the .flock folder but the .flock folder won't delete.

What makes this weird is when I navigate to /home/speed/Desktop the folder isn't visible, but I still see it on my desktop.

I tried moving it to my documents, but I get something that says Error while copying "There was an error getting information about ".flock"."

More details:
Error stating file '/home/speed/.flock': No such file or directory

I get the same error while deleting, except it says error while deleting of course.

Screenshot:
[http://img34.imageshack.us/img34/1431/screenshotbmj.png](http://img34.imageshack.us/img34/1431/screenshotbmj.png)

I feel I've looked everywhere to get the answer, and I'm still stuck. So if anyone can help me out it'll be greatly appreciated.

---

### Post by michy99 on 2009-08-08
What do you get for these commands?```
ls -la /home/speed/Desktop
lsattr /home/speed/desktop/.flock
```

---

### Post by mikethedj4 on 2009-08-08
Nevermind I got it, thanks anyway bro.

---

### Post by mikewhatever on 2009-08-08
cd Desktop

rm -r .flock

You have to change to the Desktop directory first. You can also make the hidden files visible in the file browser with ctl+h, and delete .flock using GUI.

---

