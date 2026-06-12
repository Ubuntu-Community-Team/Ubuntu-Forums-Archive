---
title: "need help backing up firefox  bookmarks/fav"
date: 2009-09-11
forum: General Help
---

### Post by hockey97 on 2009-09-11
Hi, I am going to reinstall my ubuntu server system. I still have access to the files. 

I want to backup the my fav or bookmarks that firefox does. I also did created folders for favs or bookmarks. I need to back those up. I saved urls on the main fav bookmark and then added about 20 folders for specific stuff like programming or engineering or bank or school stuff etc. I need to back them up. 

Where would this be located. I used the default setup. I didn't touch a thing in settings only added plugins like flash and java etc. Other then that I didn't touch the setup well just touched the dir where downalods were saved that and that's about it.

Where would the bookmars/fav would be stored on a ubuntu system?

I am trying to backup everything and making sure I got everything I needed.

---

### Post by imhotep59 on 2009-09-11
Your firefox profile is located in your home in .mozilla/firefox
You jus have to backup the folder called *something*.default

---

### Post by lovinglinux on 2009-09-11
See the Backup section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567) for additional methods of backing up Firefox profiles and bookmarks, including sync methods between different profiles.

---

### Post by gchand7 on 2009-09-11
bookmarks  /  Organize Bookmarks  /  Bookmarks Menu  /  Import Backup / backup and name file
to transfer same steps except import... good luck

---

### Post by shwallace on 2009-09-12
Firefox has a nifty addon called FEBE that will backup just about everything. I've used it often and it works great

---

### Post by chriskin on 2009-09-12
> **hockey97 said:**
> Hi, I am going to reinstall my ubuntu server system. I still have access to the files. 

I want to backup the my fav or bookmarks that firefox does. I also did created folders for favs or bookmarks. I need to back those up. I saved urls on the main fav bookmark and then added about 20 folders for specific stuff like programming or engineering or bank or school stuff etc. I need to back them up. 

Where would this be located. I used the default setup. I didn't touch a thing in settings only added plugins like flash and java etc. Other then that I didn't touch the setup well just touched the dir where downalods were saved that and that's about it.

Where would the bookmars/fav would be stored on a ubuntu system?

I am trying to backup everything and making sure I got everything I needed.

why not use [xmarks]("http://www.xmarks.com/")?

if i understood well enough, you want the bookmarks, that's what this plugin does. it uploads them into their servers and you can get them again after reinstall

---

### Post by mike555 on 2009-09-12
Firefox has changed the location of bookmarks and no longer has a file" bookmarks.html  " in your profile folder , if you want Firefox to make one from now on ;

you can automatically export bookmarks to bookmarks.html from Firefox 3. Here's how:
In the address bar of Firefox 3, type: about:config

A warning will appear: Click "I will care, I promise!"


In "Filter", type autoexport, then double-click the "browser.bookmarks.autoExportHTML" to pass the value to true.

Firefox now automatically export your bookmarks in the files bookmarks.html in your profile.


=== 1+ for xmarks , I use it all the time , makes live so much easier.

---

### Post by hockey97 on 2009-09-12
Well, right now I am locked out of my system well graphicly. I can only have access threw terminal or live cd. 

So I want to make backups of the firefox fav. I have some places that I saved in my fav or bookmark that are important. 

Is their any I can just backup a mozilla folder that will contain the book marks? and how would I import them when I reisntall the system?

---

### Post by P4man on 2009-09-12
just backup ~/.mozilla/firefox-yourversion/

Copy paste it in the new install, and it should work. Maybe you have to run ```
firefox --profilemanager
```
to pick the right (old) profile.

Oh and install xmarks next time :)

---

### Post by imhotep59 on 2009-09-12
As i said in post #2:
Just backup your directory *profile*.default located in your home in .mozilla/firefox. (*profile* is usually composed of 8 characters)
After your new install, copy this directory at the same place: /home/*user_name*/.mozilla/firefox
Then edit the file profile.ini and correct the line 'Path=....' to indicate the name of the directory you have previously backup.
I have use this method several times and it works fine. You will recover your bookmarks, your passwords and the addons that you had installed.

---

### Post by hockey97 on 2009-09-13
I do have a backup of firefox. I backed up both my root folder / and my home folder which is /home/user/ 

I looked on my external hd at my home folder. I can see .mozilla/firefox/bookmarkbackups. 

In the bookmarkbackups folder I see nothing but .jason files are these the raw files of the bookmarks? 

If so then it seems I got them backed up and I can safely start the reinstall.

I would also like to know how I can make sure I have my mysql databases backed up. 

The reason is that I won't remeber what I named them so it will be hard for me to edit every php file that I made of my website the correct the datatable names and rows etc. 

I used webmin as an interface with mysql etc. thanks for your time.

---

### Post by akakingess on 2009-09-13
+1 for FEBE plugin, I use it regularly and have used it to move profiles,bookmarks,themes,etc. from machine to machine with no problems.

---

