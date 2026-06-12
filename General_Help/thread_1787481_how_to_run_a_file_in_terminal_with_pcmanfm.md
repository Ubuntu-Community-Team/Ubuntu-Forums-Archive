---
title: "how to run a file in terminal with pcmanfm"
date: 2011-06-21
forum: General Help
---

### Post by mr.akik on 2011-06-21
I am using pcmanfm.I connect to internet using wvdial.I know that if I write a command in a text file and give it .sh extension and make it executable, then whenever I'll click that file the command will run.In nautilus you have the privilege that when you click a file you can select whether you will run it in terminal or display the contents or just run.But in pcmanfm or konqueror you do not get that option. I want that I will make a file named wvdial.sh and In the file the command wvdial will be written.When I will click it ,gnome-terminal will open and wvdial will run.Please tell me how I can do this with other file managers like pcmanfm or konqueror. I know that if I give this command in terminal:
./wvdial.sh  it will run. But I want to run it by clicking.

---

### Post by TeoBigusGeekus on 2011-06-21
Haven't used pcmanfm for a long time, but what does it do now when your double click it?

---

### Post by mr.akik on 2011-06-21
> **TeoBigusGeekus said:**
> Haven't used pcmanfm for a long time, but what does it do now when your double click it?It just runs but it doesn't run in terminal.suppose, I make a .sh file which contains a command like:
wget -c [http://.](http://.)...........
when I'll double click it , the file will be downloaded from the link but terminal won't open so I can't see what is happening.

---

### Post by TeoBigusGeekus on 2011-06-21
```
gnome-terminal -e ./wvdial.sh
```
Replace gnome-terminal with the terminal you use.

---

### Post by nothingspecial on 2011-06-21
Surely the contents of wvdial.sh should be changed to 

```
gnome-terminal -e wget blah blah blah
```

unless wvdial.sh is placed in the users $PATH in which case you would remove the ./

---

### Post by mr.akik on 2011-06-21
wow!!!! it works. thank you very much.thank u again.................... and again.

---

