---
title: "All files show as type plain text"
date: 2011-04-14
forum: General Help
---

### Post by Ralph L on 2011-04-14
I somehow managed to screw up my lucid lynx system so that all files show up under Nautilus properties as Type Plain Text.  When I double click a file, any file, the system tries to open it as plain text with gedit.  Everything worked correctly until yesterday when I tried to install a new version of PyQt4.  If I reboot with an old (karmic) version of Ubuntu and bring up Nautilus Properties on the same file (my data partition can be opened in other OS's) the files show up with the correct file type (PDF, ODT, etc)  So the problem is not in the file itself, but rather in the lucid OS, which is mis-interpreting the file type.  As I said I somehow messed it up when installing the new version of PyQt4.  I have restarted lucid several times and this does not help.  I don't know how the File Type system works in Linux.

Any help in fixing this would be appreciated.  

Thanks
Ralph

---

### Post by K_45 on 2011-04-14
Right click the file, choose open with another application and choose the right one for each file type. Make sure the option to set as default is ticked.

---

### Post by Ralph L on 2011-04-14
K-45

Thank you very much for responding.

However, I tried this.  It doesn't work.  If I change, say a pdf file, to be opened by Evince, then Nautilus attempts to open all files with Evince.  I believe this is because Nautilus thinks all files are of type plain text and whatever application I set to open plain text files is used to open all files.  As I see it my problem is that I've screwed up lucid/Nautilus so that it thinks all files are of type plain text.  But they aren't all plain text, because if I open the same files with an old karmic system I still have on my disk, they have the correct file type and open correctly.

Can you think of any way to get Nautilus to correct its thinking.

Thanks

Ralph

---

### Post by K_45 on 2011-04-14
This may provide an answer:

[http://www.dslreports.com/forum/r23836120-SOLVED-All-files-are-considered-text-plain-yikes-Help-](http://www.dslreports.com/forum/r23836120-SOLVED-All-files-are-considered-text-plain-yikes-Help-)

Run ```
sudo find /usr/share/mime -type f -exec chmod a+r '{}' \;
```

---

### Post by Ralph L on 2011-04-15
K_45

Your the best!!!!!  I was all set to reinstall my OS.  I ran what you told me to and right clicked and opened a few files with the correct application, lo and behold all the icons came back.  I right clicked and looked at properties and they were all correct.  Once again I can double click files and they launch in the correct application.

Thank you, Thank you, Thank you,

Ralph

---

### Post by K_45 on 2011-04-15
I'd write down that command for reference. Mark this as "solved". Enjoy Ubuntu!

---

### Post by Ralph L on 2011-04-15
I've never figured out how to mark something as solved.  How does one do that?

---

### Post by K_45 on 2011-04-16
Go to Thread Tools -> Mark this thread as solved.

---

