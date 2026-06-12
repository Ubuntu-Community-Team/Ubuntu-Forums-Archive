---
title: "Symatic package Manager - error"
date: 2010-07-02
forum: General Help
---

### Post by SEAWolfpack on 2010-07-02
First off I new to Ubuntu, so bare with me...

I went to install a package, but when I clicked on the package manager this is the message I receive.

E: Type ',!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read. Go to the repository dialog to correct the problem.
E: _cache->open() failed, please repott

I have no idea what to do?
I am running 10.04, on gateway computer. Before this I was able to access the package manager...well, until my younger brother was missing around with the computer.

Any Help is appreciated.  Thanks

---

### Post by WorMzy on 2010-07-02
Can you post the output of the following terminal command:
```
cat /etc/apt/sources.list.d/playonlinux.list
```

---

### Post by SEAWolfpack on 2010-07-02
cat /etc/apt/sources.list.d/playonlinux.list
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">

<!--//////////////////////////////////////////////////////////////////////////
//
//    Copyright (c) 1996 - 2008, Websense, Inc.    All Rights Reserved
//    See WebsenseCopyright.txt for copyright information
//
///////////////////////////////////////////////////////////////////////////-->

<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
<title>Access to this site is blocked</title>
</head>
<body>

<!--[if lt IE 7]> <div style="width: 725px;"> <![endif]-->
<div style="border: 1px solid #285EA6;width: 95%; max-width: 700px; overflow: hidden; margin-left: 10px; background-color: #EEF2F7;">
    <iframe src="http://10.2.41.70:15871/cgi-bin/block_message.cgi?ws-session=1439851342" title="test" name="ws_block" frameborder="0" scrolling="auto" style="width:100%; height: 10em;">

    </iframe>
    <iframe src="http://10.2.41.70:15871/cgi-bin/blockOptions.cgi?ws-session=1439851342" name="ws_blockoption" frameborder="0" scrolling="auto" style="width:100%; height: 17.5em;">
        <p>To enable further options, view this page with a browser that supports iframes</p>
    </iframe>
    <div><img title="Websense" src="/Images/wslogo_block_page.png" alt="Websense Logo" style="float: right;clear: both;margin: 0px 10px 6px 0px; padding: 2px 0px;">
        <div style="clear: both; overflow: hidden; height:1px;"></div>
    </div>
</div>
<!--[if lt IE 7]> </div> <![endif]-->

</body>
</html>

---

### Post by WorMzy on 2010-07-02
Huh. Weird. You seem to have received a filter's warning message, rather than the sources list you were supposed to receive. Are you behind a firewall, or a parental block or something?

In any case, you can fix it by running
```
gksu gedit /etc/apt/sources.list.d/playonlinux.list
```
and replacing everything with a single line:
```
deb http://deb.playonlinux.com/ lucid main
```

Then run```
sudo apt-get update
```

---

### Post by SEAWolfpack on 2010-07-02
Thanks!  That did solve the problem, and I currently updating now.

---

### Post by WorMzy on 2010-07-02
Glad to hear it. Please mark your thread as solved by using the thread tools in the top left of your original post. :)

---

### Post by Vege 4wd on 2010-07-10
Hi , when I ran the code I got this ouput:

aaron@aaron-laptop:~$ cat /etc/apt/sources.list.d/playonlinux.list
cat: /etc/apt/sources.list.d/playonlinux.list: No such file or directory


Any Idea because I am unable to update as well.

---

### Post by WorMzy on 2010-07-10
What error do you get when you run 'sudo apt-get update'? The solution to SEAWolfpack's error was to modify that file, because that was the file that was causing the error, if a different file is causing your error, then we'll need to modify that file instead; but you can't use the same line that SEAWolfpack used in his file, because that line is purely for Play on Linux.

tl;dr: Post your error here, and we'll take a look. You'll need a different solution to the one SEAWolfpack used. :)

---

### Post by Vege 4wd on 2010-07-10
hi, thanks for taking a look.

The output is:

aaron@aaron-laptop:~$ sudo apt-get update
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_AU       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_AU   
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) lucid/non-free Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/dtl131/ppa/ubuntu/](http://ppa.launchpad.net/dtl131/ppa/ubuntu/) lucid/main Translation-en_AU   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_AU       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_AU
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_AU       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg                        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_AU     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_AU
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg                       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_AU
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid/non-free Packages           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Reading package lists... Done
aaron@aaron-laptop:~$ 


Seems like it cant reach anything.

---

### Post by WorMzy on 2010-07-10
That executed perfectly. Your package lists are up to date and there were no problems. Could you describe where you encountered your problem?

---

### Post by Vege 4wd on 2010-07-10
Well strange as it may seem last time I ran that code it came up with a lot of fails instead of hits. 

I tried some other codes from the forum so it must all be working now.

While it's a bit embarassing thanks heaps for the help.

---

### Post by WorMzy on 2010-07-10
No worries. If it starts happening again, the best thing to do is post here before you try random codes to try and fix it. The codes may have been purposely written to fix a problem which differs to your own, despite the symptoms being similar; and if you're not sure what you're doing, by running them you may do more harm than good to your system. Fortunately this doesn't seem to be the case this time. :)

---

### Post by Vege 4wd on 2010-07-10
Good point.  Thanks.

---

