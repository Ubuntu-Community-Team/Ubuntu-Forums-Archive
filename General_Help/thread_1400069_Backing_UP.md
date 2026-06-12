---
title: "Backing UP"
date: 2010-02-06
forum: General Help
---

### Post by Amrobadr on 2010-02-06
Hello Guys,

I was wondering if I can backup **_ONLY_** "Installed softwares, Firefox settings and fonts", then re-install uBuntu 9.10 and restore them back !!

Is that Possible !!

---

### Post by Amrobadr on 2010-02-06
Anyone !!

---

### Post by blueshiftoverwatch on 2010-02-06
You could make a copy of your entire /home/YourUserName directory and just replace your current /home/YourUserName directory with it. That's where all (or atleast 99%) of the settings for applications are stored. I made a [thread]("http://ubuntuforums.org/showthread.php?t=1052105") dealing with that awhile ago.

Just make sure that your username on your new Ubuntu installation is exactly the same (case sensitivity matters) as on your old installation. Or else you'll run into the minor problem of applications trying to by default save into a non-existent /home subdirectory based on your old name and having to manually redirect it to your existing one.

Also, calm down a little. It's only been an hour and you've already bumped the thread. Wait at least a day before bumping. People who browse the forums will go back several pages to look for unanswered threads.

---

### Post by Enigmapond on 2010-02-06
Well if you mean software YOU installed, most of that is in your /user directory...so are your fonts in user/share/fonts. Your FF settings are in your home directory so by backing up /user and /home this should accomplish this.

---

### Post by Amrobadr on 2010-02-06
Well, Thanks Guyz

Now, which folders exactly shall I move !!
Only : /user and /home

and Can I Copy them to another Partition !!

and yes, I'll create the username exactly like the previous one ;)

---

### Post by ushills on 2010-02-06
search for dpkg --get-selections, this will record your installed applications.  the hidden file .mozilla in you home directory holds you firefox settings, just bakup .mozilla and the output od dpkg --get-selections and you can reinstall.

---

### Post by warfacegod on 2010-02-06
[http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

---

