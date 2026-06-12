---
title: "File Sharing Assistance"
date: 2010-06-03
forum: General Help
---

### Post by NibbleAbit on 2010-06-03
I'm new here, so please excuse me if this is the wrong place to seek assistance.

I bout a new computer about a month ago and thought I would try to avoid the MS tax, so I thought I would install Ubuntu instead.  It has been going well, except I can't for the life of me figure out how to share folders with my family the way I want to.

We all share the same network (192.168.1.x) some wired, some wireless.

I want to set up one folder that we all can use (/home/public) and each of us have our own private folder (/home/firstname) even if the private folder is only private because we just know to keep out of someone else's folder.

I tried right clicking on /home/public and going to share, but it told me that I needed samba running.  So after about 2 weeks, I now have just about every samba tool in existence loaded.  It finally allows me to share, but the windows systems can't mount it.

Please, any help would be appreciated.  After upgrading, I am now running Ubuntu 10.04 LTS

---

### Post by SnickerSnack on 2010-06-03
Have you read any samba tutorials?  I found this by googling: [http://www.iamjacksdesign.com/blog/a-decent-samba-tutorial-for-ubuntu/](http://www.iamjacksdesign.com/blog/a-decent-samba-tutorial-for-ubuntu/)

---

### Post by sgosnell on 2010-06-03
Open Nautilus, the file manager, navigate to /home, right-click on /public, select Sharing Options, set the options as you want them, and click on Create Share.

---

### Post by NibbleAbit on 2010-06-04
Thank you so much for the link.  I followed the samba installation instructions, and the windows connection instructions and it now works well enough for me.

I think the moral of the story is that for samba, use the command lines and manually edit the config files and leave the gui interface for the experts who know what they are doing.

---

