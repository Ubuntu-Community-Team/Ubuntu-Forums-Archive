---
title: "Scripts Related Help"
date: 2010-02-15
forum: General Help
---

### Post by Coldness on 2010-02-15
Hi. I wanted to make a simple script that would trigger on certain environment events. For instance, I want the script to trigger whenever a new file gets copied or placed on the Desktop, and cut that file and place it somewhere else. Sort of cleaning the Desktop process. Here's the thing: I want to trigger on it's own, not requiring me to open shell and invoke it from there.

Thanks.

---

### Post by geirha on 2010-02-15
I suggest you write a script that is started when you log in (System -> Preferences -> Startup Applications), that listens to inotify event using the inotifywait command (man inotifywait). Something like:

```

#!/bin/bash

inotifywait -m -e moved_to -e close_write --format "%w%f" ~/Desktop |
while IFS= read -r file; do
    case $(xdg-mime query filetype "$file") in
        video/*) mv "$file" "/path/to/video/" ;;
        audio/*) mv "$file" "/path/to/audio/" ;;
        image/*) mv "$file" "/path/to/images/" ;;
        *) mv "$file" "/path/to/unknown/" ;;
    esac
done

```

---

### Post by Coldness on 2010-02-15
Thanks for your kindly reply. I tweaked the code you gave me (I don't extensive knowledge in shell scripting) but I did my best to tweak it to my needs:
```
#!/bin/bash

inotifywait -m -e create --format "%w%f" ~/Desktop |
while IFS= read -r file; do
    case $(xdg-mime query filetype "$file") in
        video/*) echo "Enter the Path: "; read path; mv "$file" "$path";;
        audio/*) echo "Enter the Path: "; read path; mv "$file" "$path";;
        image/*) echo "Enter the Path: "
		read path
		mv "$file" "$path";;
    esac
done
```
Now, the code runs and displays the message "Enter the path: ", but it doesn't do anything after that; the file stays put. I've tried a slightly different arrangement, but ended up only copying the file to the destination folder. Any help would be appreciated :)

---

### Post by geirha on 2010-02-15
You have set inotifywait to listen to the create event only. I agree that that sounds logical, but the create event occurs when a new file is created in that directory; NOT when it's completely copied. If you are copying a large file to the directory, it may take seconds or minutes for the copy to complete, and if you move it before it is completely copied, you risk only moving the first part of the file, meaning you lose the rest of the data..!

That's why I used the close_write event in my example. While the program that is copying the file to your desktop is transfering the data, the file will be open in write mode, and when it's done, it will close the file for writing, emitting a close_write event.

However, that won't leave the file on the desktop. Didn't mv give you an error message?

Also, if you move a file to ~/Desktop, from the same filesystem, neither a create event nor close_write event will occur, you'll only get a moved_to event, since it doesn't have to create a new file and transfer data, it just changes the path.

BTW, instead of read path, you can do path=$(zenity --file-selection --directory) to select directory graphically.

---

### Post by Coldness on 2010-02-15
Thanks a lot! By the way, do you know where I can find great tutorial on shell scripting? I'm a programmer (well, if you could call programming in C# a programmer) and I have slight knowledge in both Java and C++. So, a lot of the programming concepts I already understand, so I need something that will teach me shell scripting properly. Also, how would I know that libraries for specific tasks exist? E.g. the inotifywait library.

After your next reply, I'll mark this topic as resolved. Thanks a lot :)

---

### Post by djurny on 2010-02-15
> **geirha said:**
> I suggest you write a script that is started when you log in (System -> Preferences -> Startup Applications), that listens to inotify event using the inotifywait command (man inotifywait). Something like:

```

#!/bin/bash

inotifywait -m -e moved_to -e close_write --format "%w%f" ~/Desktop |
while IFS= read -r file; do
    case $(xdg-mime query filetype "$file") in
        video/*) mv "$file" "/path/to/video/" ;;
        audio/*) mv "$file" "/path/to/audio/" ;;
        image/*) mv "$file" "/path/to/images/" ;;
        *) mv "$file" "/path/to/unknown/" ;;
    esac
done

```
a bit off topic, but this is a really nice one! 
IFS/read to handle whitespace and the mime type query..

---

### Post by geirha on 2010-02-15
> **Coldness said:**
> Thanks a lot! By the way, do you know where I can find great tutorial on shell scripting? I'm a programmer (well, if you could call programming in C# a programmer) and I have slight knowledge in both Java and C++. So, a lot of the programming concepts I already understand, so I need something that will teach me shell scripting properly.

There's really only one good guide on bash that I know of, and that is [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) and the accompanying FAQ [http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ). Moreover I urge you to stay away from the Advanced bash-scripting guide. It teaches bad practice. Also, about 90% of the shell scripting hits on google are junk. So make sure you check that guide/faq before you try googling.

> **Coldness said:**
> Also, how would I know that libraries for specific tasks exist? E.g. the inotifywait library.

That's hard. Mostly you'll know by experience that it either exists, or that such a tool likely exist. You have the same problem in Java and C++ and similar, you need to know what libraries are available. 

Asking about what tools you can use for a particular task here at the forums will likely give you some answers though.

Oh, and btw, the Programming Talk (under Development & Programming category) forum is the best place to put questions about programming (which includes shell scripting).

---

### Post by Coldness on 2010-02-15
> **geirha said:**
> There's really only one good guide on bash that I know of, and that is [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) and the accompanying FAQ [http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ). Moreover I urge you to stay away from the Advanced bash-scripting guide. It teaches bad practice. Also, about 90% of the shell scripting hits on google are junk. So make sure you check that guide/faq before you try googling.



That's hard. Mostly you'll know by experience that it either exists, or that such a tool likely exist. You have the same problem in Java and C++ and similar, you need to know what libraries are available. 

Asking about what tools you can use for a particular task here at the forums will likely give you some answers though.

Oh, and btw, the Programming Talk (under Development & Programming category) forum is the best place to put questions about programming (which includes shell scripting).

Thanks for the reply :) It really helps. I'll be sure to post more programming related threads in the proper place ;)

---

