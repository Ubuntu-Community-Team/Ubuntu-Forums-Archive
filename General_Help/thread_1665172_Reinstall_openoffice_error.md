---
title: "Reinstall openoffice error"
date: 2011-01-11
forum: General Help
---

### Post by pljehyun on 2011-01-11
So I tried out Libreoffice and want to revert back to Openoffice for the time being. I uninstalled Libreoffice from ubuntu software center and now I can't reinstall openoffice from USC. i get this error:

" Package dependencies cannot be resolved:
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time. "

does anyone have a way of fixing this? thanks in advance

edit: i've tried sudo apt-get install openoffice.org in terminal but it didn't work as well (i'm total noob)

---

### Post by JohnnyBDallas on 2011-01-16
I'm with you. My brother said to download Libreoffice, so I did and it wouldn't load so I tried to go back to Openoffice and now I'm stuck. Complete nood with like a week of Ubuntu knowledge. 

Bump

---

### Post by Hagar Delest on 2011-01-16
In Synaptic, make sure that all the OOo and LibO packages have been removed. Then, install the vanilla version, it's usually better: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by twlaaas13 on 2011-03-22
This is what I did sudo apt-get autoremove openoffice*.*
The sudo apt-get autoremove libreoffice*.*
Open Synaptic type in libreoffice there should be three listed that pertain to Libreoffice check for complete removal. After that I went and typed in openoffice and checked for install and it worked. It installed Open office 3.2

This was done on a Laptop HP nc6230 running Ubuntu 10.10

---

### Post by sub_acoustic on 2011-06-24
thanks, very helpful, OO seems to be more reliable for the moment...

---

### Post by DGRE6133 on 2012-05-08
For those who are interested. If you have a broken package and want to reinstall it, type "sudo aptitude install (package name) and hit enter. 
worked for me. I had broken packages in open office that restricted it from installing and this worked around those problems. Hope this helps someone.

---

### Post by cmr77 on 2012-10-07
Sorry to drag this one out of the woodwork, but have tried all of the above and still not getting anywhere.

I am a complete newbie, any help would be much appreciated.

Cheers

---

### Post by overdrank on 2012-10-07
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

