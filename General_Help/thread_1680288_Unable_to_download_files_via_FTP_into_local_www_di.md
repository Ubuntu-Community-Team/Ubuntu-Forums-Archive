---
title: "Unable to download files via FTP into local www directory"
date: 2011-02-02
forum: General Help
---

### Post by dv310p3r on 2011-02-02
When I try to transfer files from my remote web server into my local www directory it doesn't let me. I imagine it has something to do with permissions but I can't seem to figure out what the issue is.

I'm using Filezilla to try and transfer them. I can transfer them into my home directory though.

---

### Post by irv on 2011-02-03
Yes it is a rights issue. I have a scrip file I will attach which will allow you to open the var folder with root right and allow you to change the www folder rights.
Here is what you need to do: copy the script file into a hidden folder in your home folder. The folder name is .gnome2. Don't forget the dot before the name.
When you go the var folder, right click on the www folder and you will see a popout menu goto the scripts and choose “root-nautilus-here”. You will be asked for your password and then will be able to change the rights on the folder www. When you are done I would change it back.
By the way I use fireFTP right out of Firefox. Once you set it up it is easy to transfer files.
[ATTACH]182641[/ATTACH]  [ATTACH]182642[/ATTACH]  [ATTACH]182643[/ATTACH]
```
#!/bin/sh
# root-nautilus-here
# opens a root-enabled instance of a nautilus window in selected location
# requires sudo priviledges and gksudo, which may involve security risks.
#Install in your ~/Nautilus/scripts directory.
#
# Placed in the public domain by Shane T. Mueller 2001
# Fixes provided by Doug Nordwall
#
# 2004.04.18 -- keith@penguingurus.com - Added gksudo usage to provide popup
#               password window if sudo has expired.  Line only echos got
#               root to std output.  But gksudo updates your sudo access
#               privs, so running nautilus with sudo will succeed
#               without asking for a password.


foo=`gksudo -u root -k -m "enter your password for nautilus root access" /bin/echo "got r00t?"`
sudo nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI
```
If you are interested in other scripts for this purpose, here is a link on my server. [http://wabasha-server.net/Nautilus%20Scripts/]("http://wabasha-server.net/Nautilus%20Scripts/")

---

### Post by kukker32 on 2011-02-03
or the simple way..

sudo nautilus in terminal.
navigate to var/www/ right click and set permissions.. ;)

---

### Post by irv on 2011-02-03
> **kukker32 said:**
> or the simple way..

sudo nautilus in terminal.
navigate to var/www/ right click and set permissions.. ;)

I will agree with you it is the simple way, but I like to find ways to do things via the GUI so I can show people you can do things just like you do in Windows. Most people are spoiled because of using Windows. That's why I show them the long way, but I am glad you posted the simple way so others can see the great advantage of using Linux.
Thanks

---

### Post by dv310p3r on 2011-02-09
Just wanted to thank everyone.

---

