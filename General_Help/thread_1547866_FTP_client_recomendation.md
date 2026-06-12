---
title: "FTP client recomendation?"
date: 2010-08-07
forum: General Help
---

### Post by Bernie Gallagher on 2010-08-07
Can someone recommend an FTP client for my Ubuntu Machine?   I use FTP very rarely, and when I do I only need minimal finctionality to upload manuscripts to a few publishers' web sites.  Software Center offers a number of FTP clients, but I'm not sure which one is best.  I use Cute FTP on my Windoze machine, but that's not an option on Ubuntu.  I see that FileZilla is available for both platforms, so I'm leaning on installing that on my Ubuntu machine, and replacing CuteFTP on my Windoze machine with it.  Any advice or recommendations?  Again, I'm a relative newcomer to Linux and am still learning my way around Ubuntu before I burn my bridges and trash Windoze completely.

---

### Post by stinkeye on 2010-08-07
Filezilla is very easy to use and will suit your purpose.
Worked out of the box for me.
Just had to enter host, username and password.

---

### Post by Bernie Gallagher on 2010-08-07
Thanks!  Sounds good.  Some time ago, someone ripped me a new one for marking a thread Solved prematurely, so I'll wait for a few more replies before I do so...

---

### Post by xXxBlender3DxXx on 2010-08-07
I just use Nautilus. Just open the file browser, click Places (or something like that, I'm not on Ubuntu right now) and "Connect to server...".

It works quite nice. I also recommend FileZilla if you want a program specifically for FTP.

---

### Post by Bernie Gallagher on 2010-08-07
> **xXxBlender3DxXx said:**
> I just use Nautilus.

Cool!  Thanks.  I already installed FileZilla, but I just tried your way and it works nice, too.  It's nice to know about to use as a backup.

---

### Post by stinkeye on 2010-08-07
> **xXxBlender3DxXx said:**
> I just use Nautilus. Just open the file browser, click Places (or something like that, I'm not on Ubuntu right now) and "Connect to server...".

It works quite nice. I also recommend FileZilla if you want a program specifically for FTP.

I didn't know you could connect to FTP like that.
I just tried it and you can delete, copy and paste through nautilus.
Too easy, thanks.

---

### Post by WorMzy on 2010-08-07
I've had nautilus hang on large/multiple file transfers with remote ftp servers before, so I prefer Filezilla for transferring things to and from; never had any problems with that yet.

Mounting the ftp server through nautilus is great for website coding though. You can access the files through gedit, and it's almost the same as having the file on the local machine.

---

### Post by Jose Catre-Vandis on 2010-08-07
If you use Firefox, try the **FireFTP** add-on, an ftp client that's runs under the firefox code. You can run it inside the browser itself (it's listed in the Tools section), or as a separate app by running:
```
firefox -chrome chrome://fireftp/content/
```

What's nice about this add-on is that all your sites and passwords are stored inside Firefox, just like all your other saved logins, and by operating inside your browser, which you probably have open anyway most of the time, you don't need to go and open another program.

Alternatively, another suggestion:

If you are running **Xubuntu** (therefore no Nautilus :)), you can use **Gigolo** to mount the remote location and then use **Thunar** to browse, add and delete files

---

### Post by sideaway on 2010-08-07
I love nautilus and hate windows explorer for the ftp and ssh capapbilities. Ubuntu suprises me every day :)

---

### Post by Bernie Gallagher on 2010-08-07
> **WorMzy said:**
> Mounting the ftp server through nautilus is great for website coding though.

Yes, that is convenient to be able to mount a remote directory to my local filesystem via FTP.   The best advantage of that is that it doesn't time out with inactivity the way normal FTP does.

---

