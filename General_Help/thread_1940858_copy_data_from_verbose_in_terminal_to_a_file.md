---
title: "copy data from verbose in terminal to a file"
date: 2012-03-14
forum: General Help
---

### Post by prathmeshg90 on 2012-03-14
hey can any one pls tell me how to copy data generated from the following command, ran on a terminal,into a file
# snort -i wlan0 -c snort.conf -A console 

Basically it generates a lot of alert which are shown in the terminal, I want to know how do we copy all those alerts into a file ?

---

### Post by sudodus on 2012-03-14
Any text in a terminal window is marked by holding down the left mouse button and moving the mouse, 'painting'. Then it can be pasted into an editor by clicking the middle button.

If you are using gnome-terminal, you can also use the Edit dropdown menu.

---

### Post by lisanels47 on 2012-03-14
Highlight text with the mouse, and middle-click elsewhere to paste it.

---

### Post by lisanels47 on 2012-03-14
# snort -i wlan0 -c snort.conf -A console > mylogfile.txt

Maybe this is what you mean?

---

### Post by prathmeshg90 on 2012-03-14
Thanks for the replies, but the thing is the command some times generates upto 500 alerts in a single session, so how can i copy the data then in that case?

---

### Post by sudodus on 2012-03-14
> **prathmeshg90 said:**
> Thanks for the replies, but the thing is the command some times generates upto 500 alerts in a single session, so how can i copy the data then in that case?
```
# snort -i wlan0 -c snort.conf -A console [COLOR="Red"]>>[/COLOR] mylogfile.txt
```

where >> means append (add line(s) at the end of the file)

---

### Post by prathmeshg90 on 2012-03-14
@lisanels47 and @sudodus does the command which u wrote actually copy all data to the specified file and where is this file stored
Thanks for replies:)

---

### Post by sudodus on 2012-03-14
> **prathmeshg90 said:**
> @lisanels47 and @sudodus does the command which u wrote actually copy all data to the specified file and where is this file stored
Thanks for replies:)
Maybe you should specify the full path for example /home/$USER/mylogfile.txt to get it in your home directory.

It should copy all data. But maybe there is another possibility. I don't have snort installed so I cannot check, but I suggest that you run ```
man snort
``` and/or ```
snort --help
``` and find out if there is a direct option to write a log file.

---

### Post by prathmeshg90 on 2012-03-14
thanks a lot it works really well

---

