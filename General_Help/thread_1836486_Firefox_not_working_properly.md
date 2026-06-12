---
title: "Firefox not working properly"
date: 2011-08-31
forum: General Help
---

### Post by markmb on 2011-08-31
Hi everybody!

I've been using Xubuntu for a while and I didn't have any problem until today,
In my computer, there are two HDD, the master one, where Windows is installed, and the slave one, where Xubuntu is installed.

To have Firefox always synchronised, I linked the Windows profile to Xubuntu profile, which was simple, and didn't make problems.

Yesterday, I wanted to play something, and I found a PSOne emulator (I had that console, and I've got games of it). I tried ePSXe, which I wasn't able to make it work (I had to install some libraries and download a bunch of archives). Then, I tried pSX, which works perfectly.

Then, today, when I wanted to open Firefox, I saw a few strange things:

[LIST]
[*]Back button doesn't work
[*]I don't have bookmarks
[*]Read It Later app doesn't have any bookmark
[*]"Normal" links doesn't get blue and underlined (I don't know this for sure, I've only tried google)
[*]Mouse doesn't change over a link (It puts the "text" cursor, not the "hand" cursor)
[*]URLs on the direction bar, doesn't change when you click a link (If I write "ubuntuforums.com", and then I click on a subforum, The written direction is ubuntuforums.com, not the subforum)
[*]When I write a direction in the direction bar, there aren't suggestions
[/LIST]
Thank you in advance! I expect you can help me with this mess!!

---

### Post by markmb on 2011-08-31
After using Firefox a bit, Hotmail webmail works awfully, and, in general, Firefox goes veeeery slow

---

### Post by lovinglinux on 2011-09-05
I don't know if that application has anything to do with Firefox, but looks like you have a problem with your bookmarks database.

Close Firefox, open ~/.mozilla/firefox/<profilename> folder and delete the file *places.sqlite*. Open Firefox, then open the Bookmarks manager and use the "Import and Backup >>> Restore" feature to restore your bookmarks.

---

### Post by markmb on 2011-09-05
I finally changed to Google Chrome. It's faster and great!

Thanks

---

