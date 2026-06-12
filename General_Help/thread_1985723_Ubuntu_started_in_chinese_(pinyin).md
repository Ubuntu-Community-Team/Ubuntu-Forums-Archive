---
title: "Ubuntu started in chinese (pinyin)"
date: 2012-05-23
forum: General Help
---

### Post by MasterZ on 2012-05-23
Hi,

I booted my ubuntu 12.04 today and the whole interface changed to chinese (pinyin apparently...)
I didn't change it on purpose and I can't find a way to go back to the default english... Could someone help me ? 

Here are some screenshots of my system now: 

-Upon login I'm greeted with a prompt window to change all my folder names:
[[img]http://s14.postimage.org/u35ade9od/Update_Language.jpg[/img]](http://postimage.org/image/u35ade9od/)
It says "you have logged in to a new language" is this some option from the login screen ?? 

-I tried to go to the Language configuration (the blue icon) but when I select 'English' and click the first button below (which should be 'apply system wide' nothing changes. 
[[img]http://s13.postimage.org/6ukeq54nn/Lang_Config.jpg[/img]](http://postimage.org/image/6ukeq54nn/)

-On the second tab of the language configuration, the selected language is also English(U.S)
[[img]http://s17.postimage.org/ed0qx5gh7/Second_Tab.jpg[/img]](http://postimage.org/image/ed0qx5gh7/)


I really do not understand how the system language could change like that as I did not do it on purpose... 
How can I switch back ? 

Thanks

---

### Post by MasterZ on 2012-05-24
I still can't find a way to change the language. 

I've seen that something had changed my /etc/default/locale settings to zh_CN; so I changed that manually: 
```
$ cat /etc/default/locale 
LANG=en_GB.UTF-8
LANGUAGE="en_GB.utf8:en"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"

```

Same thing for /etc/environment I changed it back too: 
```
$ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANGUAGE="en_GB.UTF-8:en"
LANG="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"

```

Still after a reboot my X session continues to displays system messages and other stuff in chinese...

I do not know where this setting comes from, but when I check my session locale from a terminal I get: 
```
$ locale
LANG=zh_CN.UTF-8
LANGUAGE=zh_CN:en
LC_CTYPE="zh_CN.UTF-8"
LC_NUMERIC=en_GB.UTF-8
LC_TIME=en_GB.UTF-8
LC_COLLATE="zh_CN.UTF-8"
LC_MONETARY=en_GB.UTF-8
LC_MESSAGES="zh_CN.UTF-8"
LC_PAPER=en_GB.UTF-8
LC_NAME=en_GB.UTF-8
LC_ADDRESS=en_GB.UTF-8
LC_TELEPHONE=en_GB.UTF-8
LC_MEASUREMENT=en_GB.UTF-8
LC_IDENTIFICATION=en_GB.UTF-8
LC_ALL=

```

The only thing I can do now is try to backup and delete all the contents of my Homedir and pray that it goes back to normal... Otherwise I'll have to reinstall the whole system.

or if anybody has an idea ?

---

### Post by wojox on 2012-05-24
did you try ```
sudo dpkg-reconfigure locales
``` and a reboot?

---

### Post by MasterZ on 2012-05-24
Hi, 

Yes I tried that, I had a message about all en_* locales being up to date but it did not change anything. 

I removed ALL files and directories from my home dir and now I'm back to english. :popcorn:
I will copy back my important files in the home dir and redo the compiz configurations and all that stuff manually. 

Something had changed my files in /etc that's for sure, so it must be something I installed, because this requires root privileges... 
Everything I installed came from the repositories, except for actkbd, a keyboard mapping driver, which I had to compile and make install... 

I'll still try to track whatever did this and report my findings here, if any. 

I hope it won't happen again though...

---

### Post by Tamalin on 2012-05-24
From the language configuration screen, drag English to the top of the list, then click Apply System Wide.  I think this is how you reset the language.

P.S., though not relevant, I think I see simplified chinese characters, not pinyin :)!

---

### Post by Siak on 2012-08-20
Hi guys,

I had the same bug. I went to ~/.pam_environment file and changed this two variables:
LANGUAGE="en_GB:en"
LANG="en_GB.UTF-8"
And everything went back to normal.

Hope that helps

---

### Post by dewdrop_world on 2012-10-11
I had the same problem, but it was resolved using the system settings panel. Of course it was rather challenging to figure out *which* panel to use, since the name was in CHINESE...

I am simply gobsmacked that anything in a modern OS would (expletive deleted) up the user's language preference with no action from the user, and no warning. Has this been logged as a bug?

Seriously, what's up? If it happened only to me, I'd just chalk it up as a fluke. But it happened to me once in 10.04, once in 12.04 and I'm stunned to see other people are affected too.

---

### Post by svtguy88 on 2013-01-12
I just ran into this problem.  I hadn't even installed anything or updated.   I was using my Windows partition, rebooted into Ubuntu and found a lot of Chinese characters.

Luckily, I stumbled through the language selection dialog and got English back.

But what's the cause of this?  Is there any sort of log of when/how the language got changed in the first place?

---

### Post by AlexanderDGreat on 2013-02-24
I got this working by launching the System Settings.

1. Just click on blue flag
2. Popup window, can't remember what I clicked.
3. Click on the red circles for your guide.
4. Finally LOGOUT.

PS DON'T EVER EVER RENAME YOUR FOLDERS if it prompts you. UNTIL YOU'VE CHANGED Your Language back to ENGLISH, JUST LEAVE IT THERE HANGING.

Seriously Ubuntu, cmon!

---

### Post by svtguy88 on 2013-02-25
No one knows the cause of this?  It's concerning that something as important as the system language can get changed without user interaction....

---

### Post by lindara on 2013-05-15
You need to be root to follow the steps in AlexanderDGreat's post.

---

