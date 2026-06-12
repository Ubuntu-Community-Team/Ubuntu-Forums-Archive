---
title: "How to View Hidden Files"
date: 2010-03-30
forum: General Help
---

### Post by shikhar_sharma on 2010-03-30
Hi guys,

I have a ubuntu 9.10 on my aspire one.previously i had windows and through it i burned a few dvd's with hidden files on it.Now i cant view it in ubuntu.CTRL+H shows me all the hidden files of the ubuntu system but it does not show me the files on the disc.When i tried running nautilus as a root then in the media folder it doesnt show the dvd as mounted.I really need these files.I know the files are in dvd as i can view it in my dad's XP laptop.
Any help would be appreciated

---

### Post by lisati on 2010-03-30
In a regular file browser, you can click on View->Show hidden files

---

### Post by the yawner on 2010-03-30
Ubuntu typically always shows the files that are marked hidden in a Windows system. Ctrl+H only works on files that were hidden the Linux way (prefixing a dot on the filename).

That said, it would appear that your Ubuntu system is unable to read your disc. Can you confirm if this happens on any DVD? Or just that particular DVD with that file?

---

### Post by shikhar_sharma on 2010-03-30
This is happening on all the 15 DVD's.I know that ubuntu by default shows u all the hidden files of windows.but its just not showing these files.is there any way to browse the dvd as a root.because when i tried running nautilus as a root then it is not showing my dvd as mounted in /media.

---

### Post by sitex on 2010-09-28
if you want to display hidden files on your computer you can do it like this
    
    1.) if you want to display some hidden files in a folder
         check the checkbox "view ==> Show Hidden Files" (or Ctrl + H)
        
    2.) if you want to display your hidden files always you can do it with gconf-editor like this
        2.1 -goto Terminal or Run Application (Alt + F2)
        2.2 -type "gconf-editor" and press Enter
        2.3 -goto desktop => gnome(or something else) => file_views
        2.4 -then Check the check box "show_hidden_files"

[**[COLOR="DarkGreen"]To read this with related Screenshots come to solutionz.yolasite by clicking here...[/COLOR]**]("http://solutionz.yolasite.com/linux")

---

