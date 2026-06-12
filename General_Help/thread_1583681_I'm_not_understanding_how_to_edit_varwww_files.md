---
title: "I'm not understanding how to edit /var/www/ files"
date: 2010-09-28
forum: General Help
---

### Post by micha8l on 2010-09-28
Hello, I have lots of files I need to put in my /var/www/ folder (Apache http server). I thought I understood how to edit it:

For single files: sudo cp file /var/www/
For opening files: sudo gedit /var/www/file

But I can't use the above for a thousand files, and I really can't afford the learning curve of BASH scripting at this time. 

So if there a way I can do this the GUI way (drag and drop and all that) without having to add myself in the group permissions for the /var/www/ folder?

Kind Regards
Mike

---

### Post by mcduck on 2010-09-28
just press Alt-F2 and run "gksudo nautilus". That will open the file manager as root.

Remember to close it afterwards and don't mix it with file manager windows running as your own user. I recommend setting the background color for root nautilus to red or something (Edit/Backgrounds and Emblems) to make sure they stand out...

---

### Post by oopsie on 2010-09-28
I'm a linux newbie, so people who actually know what they're doing are probably gonna look at me in horror, but what I do is

sudo nautilus

---

### Post by lisati on 2010-09-28
What I do is maintain a copy of my website's files on my laptop, and use tools like gedit, [kompozer]("http://kompozer.net/") etc to maintain them. Then when I've made the changes I want, I copy them to the /var/www folder on my server. I've even been known to use [Windows-based site creation/editing software]("http://www.freeserifsoftware.com/software/webplus/") to manage groups of related files.

---

### Post by micha8l on 2010-09-28
Thanks guys, I like the idea of changing nautilus's background to red, I'll do that

Thanks again
Mike

---

### Post by JedMeister on 2010-09-28
I think editing files in a local user account (ie remote from the server) as lisati suggests is a good option. 

A GUI FTP client is another handy way to upload these updated files. I use FileZilla (cause I'm ex Win user and I was used to it). I prefer to use SFTP for transfers though for security.

@oopsie - I use whichever I feel like at the time. AFAIK the only difference between sudo and gksudo is that sudo asks for your password in the terminal window and gksudo uses a nice little GUI window. Although someone may correct me :)

---

### Post by mcduck on 2010-09-28
> **JedMeister said:**
> 
@oopsie - I use whichever I feel like at the time. AFAIK the only difference between sudo and gksudo is that sudo asks for your password in the terminal window and gksudo uses a nice little GUI window. Although someone may correct me :)
Sudo doesn't load target user's environment correctly for GUI apps, so it might cause the app to run with root's permissions but using your user's configuration files. Which may result in those files becoming owned by root and causing all kinds of issues from not being able to change some program's settings to not being able to log in at all as that user.

This doesn't happen with every program (nautilus and gedit both seem to be fine) but it's not something you'd like to ever happen so it's easier to just always use gksudo for GUI apps and sudo for terminal apps.

---

### Post by Tibuda on 2010-09-28
It is not a good idea to use nautilus as root for daily tasks like webdevelopment. Using a FTP client is overkill. I have two suggestions:

1. Change the Apache root dir to your home folder. [Rapache](apt://rapache) can help you.

2. Change the owner of /var/www to yourself
```
sudo chown $USER:$USER /var/www
```

---

