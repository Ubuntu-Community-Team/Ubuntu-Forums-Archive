---
title: "Unable to update"
date: 2012-04-06
forum: General Help
---

### Post by Vladimir Pavic on 2012-04-06
[COLOR=#314004][FONT=Verdana, sans-serif][SIZE=2]**Dear Friends, **[/SIZE][/FONT][/COLOR] 
 

 [COLOR=#314004][FONT=Verdana, sans-serif][SIZE=2]**I use Ubuntu 10.04. When I try to install a program from Ubuntu Software Center, I get a message *“Requires installation of untrusted packages”*. I am sure you have heard of that one before. Right? Checking 'Source Code' in Update Manager – doesn't help. My system cannot properly update because of the following error. **[/SIZE][/FONT][/COLOR] 
 

 [COLOR=#800000][FONT=Verdana, sans-serif][SIZE=2][COLOR=#314004]**W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <[EMAIL="ftpmaster@ubuntu.com"]ftpmaster@ubuntu.com[/EMAIL]>**[/COLOR][/SIZE][/FONT][/COLOR]
 

 [COLOR=#314004][FONT=Verdana, sans-serif][SIZE=2]**What to do?**[/SIZE][/FONT][/COLOR]
 [COLOR=#314004][FONT=Verdana, sans-serif][SIZE=2]**Thank you.**[/SIZE][/FONT][/COLOR]
 

 [COLOR=#314004][FONT=Verdana, sans-serif][SIZE=2]**Vladimir**[/SIZE][/FONT][/COLOR]

---

### Post by raja.genupula on 2012-04-06
Hi Untrusted pkg's means you are trying to install third-party software and we can make this by selecting the canonical checkboxes in the Update Manager -> Settings -> other software Tab.

if you tried installing that particular from the terminal , then terminal prompts as same it prompts in GUI and here you can have the options as Yes/No . so you can install by giving Yes or Y . 

while coming to GPG issue , please paste this in your terminal ```

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

paste them one by one  and give a Enter strike in your terminal and that will solve . 

Hope that helps:)
All the best .

---

### Post by Vladimir Pavic on 2012-04-07
Dear Raja,
 

I have done what you suggested, but I haven' tot the desired result. Instead, I can't even go as far as getting the previous warning. The Ubuntu Software Center doesn't offer me possibility to download any software. 'Install' button is now replaced with 'Use This Source' button. But, when I click on it &#8211; I get this information:
 

```
To show information about this item, the software catalog needs updating. 
 Canonical does not provide update for GNOME Color Chooser. Some updates may be provided by the Ubuntu community.
```

 ???
 

Vladimir

---

### Post by raja.genupula on 2012-04-07
you sure that two checkbox's got checked in the settings of update manager ? 

whats the output of 
```
sudo apt-get update
```

---

### Post by Vladimir Pavic on 2012-04-10
I'd like to send you screenshots of my update manager, but, I don't know how to do it here. You could send some message to my e-mail address  , so I would have you e-mail address (to send you the images).

---

### Post by Ms. Daisy on 2012-04-10
> **Vladimir Pavic said:**
> I'd like to send you screenshots of my update manager, but, I don't know how to do it here. You could send some message to my e-mail address <snip>, so I would have you e-mail address (to send you the images).
Click reply
click "go advanced"
Click the paperclip
a new window will open, click "browse"
point to wherever your screenshot is saved.
Click "upload" and wait for it to show up under "current attachments"
click on "close this window"
now click on the paperclip again, you will get a drop-down menu showing your .jpg (or whatever kind of file it is). Click on it. The forum will include something like this in your post 
```
 [ ATTACH]215818[/ATTACH]
```but when you hit "submit reply" it places a nice thumbnail like this on your post.
[ATTACH]215819[/ATTACH]

---

### Post by nothingspecial on 2012-04-10
> **Vladimir Pavic said:**
> I'd like to send you screenshots of my update manager, but, I don't know how to do it here. You could send some message to my e-mail address  , so I would have you e-mail address (to send you the images).

This forum has a private message system. Also you can attach images to your posts using the paper clip at the top of the posting box.

Posting your email address on the forum will lead to your inbox getting spammed.

---

### Post by raja.genupula on 2012-04-10
> **Vladimir Pavic said:**
> I'd like to send you screenshots of my update manager, but, I don't know how to do it here. You could send some message to my e-mail address  , so I would have you e-mail address (to send you the images).

you can post that output code of terminal in pastebin and paste the link here . 

Thank you .

---

### Post by Vladimir Pavic on 2012-04-14
Thank you all for help.

So, on the attached images you could see what my update manager settings looks like.

---

### Post by Vladimir Pavic on 2012-04-14
Oh, yes. And this is what I get when I try to install a program. The 'Use this source' button leads to nowhere.

---

### Post by ronnieredd on 2012-04-26
bump:
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

