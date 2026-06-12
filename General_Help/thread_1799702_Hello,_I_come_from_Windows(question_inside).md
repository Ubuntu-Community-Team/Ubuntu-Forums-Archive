---
title: "Hello, I come from Windows(question inside)"
date: 2011-07-08
forum: General Help
---

### Post by DEdesign57 on 2011-07-08
I finally got Ubuntu after my recent interest in programming. I've up to now always used windows, but even in windows I was never very involved with it. I use to game on windows but that about it. I never used the command line, or really learned about file extensions ect..... But I've added Linux to my PC now so the leaning officially starts.
So far I like Ubuntu alot but it does not feel like home because all of my documents, favorites, and main files are in windows.
Is there a way to migrate those documents over to Ubuntu?

---

### Post by hawthornso23 on 2011-07-08
The most straightforward way would be to copy them onto a USB key in windows and read them off the USB key into ubuntu.

It is also possible to mount your windows partition so you can directly access your windows files from inside ubuntu. That is a little bit trickier, especially for someone just starting out so I'd suggest go with the USB key unless we are talking about an awful lot of stuff.

---

### Post by wildmanne39 on 2011-07-08
> **DEdesign57 said:**
> I finally got Ubuntu after my recent interest in programming. I've up to now always used windows, but even in windows I was never very involved with it. I use to game on windows but that about it. I never used the command line, or really learned about file extensions ect..... But I've added Linux to my PC now so the leaning officially starts.
So far I like Ubuntu alot but it does not feel like home because all of my documents, favorites, and main files are in windows.
Is there a way to migrate those documents over to Ubuntu?
Hi, all you have to do is open file manager and your windows drive should be there if it is not mounted mount it and click copy then paste it to the location in ubuntu that you want the files, this is only with files not applications.

---

### Post by mastablasta on 2011-07-08
> **wildmanne39 said:**
> Hi, all you have to do is open file manager and your windows drive should be there if it is not mounted mount it and click copy then paste it to the location in ubuntu that you want the files, this is only with files not applications.
 
 
andf you dont' really even need to copy them. as mentioned befor eoyu can just access them. Linux can read windows file system while windows can't read linux file system without additional tools

---

### Post by DEdesign57 on 2011-07-08
O cool, I did not know about file manager, so I went ahead and downloaded it form the software center. Seems to work :), I can play music files from windows, and access some C++ source code but I cant seem to make it compile. When I try to open it and run it in codeblocks, which is btw the same IDE I use on windows, it says that the "project has not been built, do you want to build it?" But when I press yes it doesn't work. Granted I can always copy and paste, but If anyone knows how to do this let me know.
Btw thanks so much for your help guys.

---

### Post by wildmanne39 on 2011-07-08
> **mastablasta said:**
> andf you dont' really even need to copy them. as mentioned befor eoyu can just access them. Linux can read windows file system while windows can't read linux file system without additional toolsHi, true but he asked about migrating his files over like he wanted them in ubuntu not just to access them from ubuntu that is why I told him he could copy and paste them.:)

---

### Post by lisati on 2011-07-08
> **DEdesign57 said:**
> O cool, I did not know about file manager, so I went ahead and downloaded it form the software center. Seems to work :), I can play music files from windows, and access some C++ source code but I cant seem to make it compile. When I try to open it and run it in codeblocks, which is btw the same IDE I use on windows, it says that the "project has not been built, do you want to build it?" But when I press yes it doesn't work. Granted I can always copy and paste, but If anyone knows how to do this let me know.
Btw thanks so much for your help guys.

You might have to install the C++ compiler. Try this from the terminal before you retry compiling:
```
sudo apt-get install build-essentials
```

---

### Post by kanishkdudeja on 2011-07-08
> **DEdesign57 said:**
> Osome C++ source code but I cant seem to make it compile. When I try to open it and run it in codeblocks, which is btw the same IDE I use on windows, it says that the "project has not been built, do you want to build it?" But when I press yes it doesn't work. Granted I can always copy and paste, but If anyone knows how to do this let me know.
Btw thanks so much for your help guys.

Can you tell us what error does it show when you try to build it?

---

