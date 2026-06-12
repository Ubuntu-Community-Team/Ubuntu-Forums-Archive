---
title: "Remaster settings directories"
date: 2010-08-02
forum: General Help
---

### Post by iam2 on 2010-08-02
Remastery Question.  Re: Psychocats' Tutorial,  Make your own Ubuntu remix with Remastersys, at: 
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Psychocats posted a marvelous tutorial article on Remastering your own Ubuntu mix.  In the first part of the article he states:  "*In your /home/username directory, make sure hidden files are showing .. copy the appropriate settings directories to the /etc/skel directory.*"  However, he does not spell out exactly what setting directories to copy.  Frankly, I do not even know what "settings" to be looking for or how they work, exactly; only have a general idea. This is an important piece of the tutorial as far as I am concerned, because without the right directories the whole project fails.  Will someone please tell me what I should be looking for?  Perhaps give me some examples or a clue as to what folders I should be looking for in the */home/username directory*?   And while you are at it, will you tell me where the "/etc/skel directory" is?  Any help will be greatly appreciated. Thanks.

---

### Post by Paulgirardin on 2010-08-05
I found that comment vague too.Here is a better description:

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

"Some notes about using the dist option

   You should start with a clean install of Ubuntu or variant and use a single user to make all changes.  You should not install any proprietary video drivers like the nvidia or ati drivers as they will not be used on the livecd and users will have to reinstall them after installation.  Clean up history and cache and copy over the contents to /etc/skel but be sure to change the ownership of everything in /etc/skel to root.  While the livecd/dvd is being created, you should not open any other apps or windows. "

---

### Post by iam2 on 2010-11-01
[SIZE=5]Paul, I apologize for being absent from the keyboard for several months, and want to thank you for responding to my inquiry.  I have yet to try it, as I have to kind of get warmed up to the task again.  Again, Thank you.[/SIZE]

---

### Post by naidra on 2010-12-08
[SIZE=4]how to setup about visual effect (compiz) .... [/SIZE][SIZE=4]I often problematic when looking for drivers, definitely appears notification error[/SIZE]

---

