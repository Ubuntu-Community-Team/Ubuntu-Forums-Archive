---
title: "Conky not taking new .conkyrc files"
date: 2011-09-13
forum: General Help
---

### Post by contumacious on 2011-09-13
Just installed conky and am trying to experiment with configurations using the .conkyrc file. I placed it in the home directory but even after using 

killall conky

and than restarting it, the different configuration changes don't take. Any ideas what I'm doing wrong?

---

### Post by Quackers on 2011-09-13
When killall conky is run the conky display should disappear.
To start it again run conky in the terminal and it should start up with the new config. Did you save the updated .conkyrc ?

---

### Post by contumacious on 2011-09-13
Yea I did the killall conky, than moved the new .conkyrc file to / than ran it again and its just the same as when it started.


:???:

---

### Post by Quackers on 2011-09-13
Your new .conkyrc should be in your home directory. How many .conkyrc files are in there?
Most times killall conky isn't required. When saving the amended .conkyrc conky should restart on its own.

---

### Post by contumacious on 2011-09-14
There is only one in there. I had just installed so I had just moved the first .conkyrc file in there and have had no such luck. Deleted the original and tried with some others still with no change.

---

### Post by Quackers on 2011-09-14
This is a hidden file, correct? You are pressing ctrl + h to see it?
If you double click on that file it should open for editing. When you click on File > save your conky display should close then re-open. If it isn't doing that I suspect your conky display is using a different file.

---

### Post by contumacious on 2011-09-14
Yea it's hidden, I just tried leaving it open, making a small change, and saving again and it did not reload the program from what I could tell. Any idea how to find out what other file it may be using?

---

### Post by Quackers on 2011-09-14
It's so long since I started with conky I can't remember. I don't remember moving a .conkyrc though.

---

### Post by contumacious on 2011-09-14
Found it hiding as conky.conf in /ect/conky

Thanks for the help.

---

