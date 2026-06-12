---
title: "what is the path to this folder"
date: 2010-06-23
forum: General Help
---

### Post by Jedit Ojanen on 2010-06-23
Hello, I hope this is a simple question. It is just hard to google.

I'm setting up MPD with ncmpcpp. I should point path to my music folder for MPD so it knows where to search. This works fine: /home/user/Music but what I want is it to point to a folder that is on another hard drive. I've tried  this: /media/D/Musika but that doesn't work.

So, to make it all simple what is the path to my music folder in other hard drive?

Thanks in advance

Edit: Solved! it was /media/D/Musika but there were some permission problems and that's why MPD couldn't find the files. I mounted the Musika folder to my /home/user/Music folder using command:

sudo mount --bind /media/Hive/Musika /home/user/Music

Found the info from here: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

Just in case if someone stumbles to same problem. I just wish I could mark this topic as solved:o

---

