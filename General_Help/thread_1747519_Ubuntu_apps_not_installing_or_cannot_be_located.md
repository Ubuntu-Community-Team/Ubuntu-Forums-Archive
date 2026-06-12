---
title: "Ubuntu apps not installing or cannot be located"
date: 2011-05-02
forum: General Help
---

### Post by southafricanguy on 2011-05-02
Hi guys,
 
Just installed Ununtu 11.04 (on a dual boot system) and can't seem to install a thing. I opened terminal and when I try to install a package it says it can't be located.
 
Also, Firefox seems to be behaving a little oddly as it won't let me visit certain links via google. Strange indeed?
 
Am I missing something? :(
 
Cheers.
 
Jas.

---

### Post by oldos2er on 2011-05-02
Which packages are you trying to install? Is your internet connection working ok otherwise?

---

### Post by Throne777 on 2011-05-02
> **southafricanguy said:**
> 
 
Just installed Ununtu 11.04 (on a dual boot system) and can't seem to install a thing. I opened terminal and when I try to install a package it says it can't be located.
 

Are you in the right directory when you issue the command to install? When you first run the terminal, you are in the Home directory by default. You need to navigate to the folder the files you want to install are in in order to run the install commands successfully.

---

### Post by southafricanguy on 2011-05-03
Hi,
 
Thanks for the posts.
 
Internet connection seems okay. 
 
I was trying to install Docky but can't find it in the list of packages. Also tried installing aircrack-ng but no luck in finding the package or installing it via terminal.
 
I will see if navigating to the directory helps though where do I need to put the files if I can't download them? 
 
Also, when checking for updates it seems to constantly get stuck towards the end of the the process.
 
When I installed Ubuntu I never had my laptop connected to the web. Would this cause problems?
 
Sincere thanks.
 
Jas.

---

### Post by imigueldiaz on 2011-05-03
> **southafricanguy said:**
> Hi,
 
When I installed Ubuntu I never had my laptop connected to the web. Would this cause problems?
 
Sincere thanks.
 
Jas.

You should revise the contents of the file

```

/etc/apt/sources.list

```

To see enabled (uncommented) repositories.

Could be that off line installation only enables CDROM source... 

Best

---

### Post by oldos2er on 2011-05-03
apt-get doesn't care which directory it's run from. Can you run this command in a terminal, and post all the text output here? ```
sudo apt-get update && sudo apt-get install docky
```

---

### Post by southafricanguy on 2011-05-03
Oh my word! This is going horribly wrong!
 
I checked /etc/apt/sources.list and that seemed okay so I tried to reinstall Ubuntu but it seemed to hang on the first screen (the locale). I then rebooted and now my laptop seems completely dead! Nothing coming up on the screen at all!
 
Not good at all. Any ideas?

---

### Post by southafricanguy on 2011-05-03
Okay, took the battery out of the laptop and it's started working again... wtf.

---

### Post by tech7 on 2011-05-03
What laptop model and hardware configuration are you using?  (HD, RAM, Processor, etc)

---

### Post by wittzi on 2011-05-03
I had exactly the same issue, but in my case my wifi would be connected but for some reason no network connection could be established (even though I had been assigned an IP, etc ...).

My fix was less bizarre than yours, which was to plug in a cable instead of using wireless then subsequently when I disconnected the cable and went back to using WiFi again it worked (and has done ever since).

I'm afraid I've noticed Natty have a few 'weird' things happen over the past few days.  There was a bunch of updates yesterday ... maybe they'll increase the stability?

__________________________________________________________________
[http://www.astonishedape.com](http://www.astonishedape.com)
Where primates come to be amazed by technology &#8230;

---

### Post by southafricanguy on 2011-05-03
Odd indeed.

It's Packard Bell Easynote with 2GB RAM and a Core 2 Duo processor.

All seems okay now though. I reinstalled Ubuntu with a internet connection and that seems to have solved it.

---

