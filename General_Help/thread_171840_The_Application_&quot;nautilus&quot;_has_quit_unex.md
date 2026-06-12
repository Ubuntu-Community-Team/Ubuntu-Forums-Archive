---
title: "The Application &quot;nautilus&quot; has quit unexpectedly."
date: 2006-05-07
forum: General Help
---

### Post by wiggie on 2006-05-07
I'm not sure how I got to this but now I'm constantly getting this message
[B]
The Application "nautilus" has quit unexpectedly.

You can inform the developers of what happened to help them fix it.  Or you can restart the application right now.
[/B]

I tried restarting the application and closing it, but nautilus doesn't restart and instead the message keeps appearing. I removed nautilus, and reinstalled it, to no avail.

I thought automatix was at fault. So I removed everything that I installed with it and purged the configuration files. I thought that the MS true type fonts were the cause. But now they're all gone and so is automatix. After a fresh install of nautilus (again), I get the same error message.

I`m not sure what to do. I think I will have to reinstall ubuntu, or gonme.:-( 

Cheers,

wiggie

---

### Post by jrib on 2006-05-07
does it happen with a new user?

---

### Post by wiggie on 2006-05-07
No, it does not!

Ok, what now? What does it mean? I'm really curious!!!

Thanks _jason

---

### Post by wiggie on 2006-05-07
Ok, so I restarted Ubuntu altogether and it doesn`t happen anymore. Very interesting, but I would like to know what exactly happened, if anyone knows.

Thanks

wiggie

---

### Post by lorenzo on 2006-05-23
I'm having the same problem after some dist-upgrade (non always). Does anyone has any clue?

---

### Post by insub2 on 2006-09-02
this is happening on my machine too.

i'm looking around the forums.  i'll post what i find.

---

### Post by Jeremiah478 on 2006-10-29
Yeah I get the same error when I am browsing folders that are mapped to a network drive...

Seems like it can happen for a bunch of different reasons

---

### Post by Suavsilk on 2006-11-10
i too am getting this error, it dosnt stop poping up :/ no matter what i click.

it happen after i ran the update tool, to update from ubuntu 1.06 to 1.10.
i also updated all the recomended stuff
i then restarted my computer and it began
i did a full shutdown then started my pc up again and its still happening

everything seems to be the same as before the update, except i dont have my custom wallpaper anymore, nor any desktop items ... (could this clue in someone as to what might be happening somehow?)

i cannot open the Rubish Bin. I click the bin icon, nothing happens, i then  click "Restart Application" or "Close " in the error dialogue and the basic frame  of the Rubish Bin app pops up for a second but then freezes and the Error shows itself again

---

### Post by jasonsim on 2007-03-18
Hi pals,

I get the same message anyway! I tried to reboot my pc many times and the problem still remain there... I am very upsad and fed up with Nautilus + Gnome now... Please some one assist me to resolve this problem! thanks ASAP...

---

### Post by jgriffi6 on 2007-05-15
When attempting to upgrade from dapper dandy to edgy eft I also had the same problem.

I changed every instance of dapper to edgy in  "/etc/apt/sources.list"

ran  "apt-get update"

ran "apt-get dist-upgrade"

The last command only downloaded the new edgy files, but did not install them.  That is why, I believe, I had the nautilus has quit unexpectedly problem.  

My solution was to restart my computer, where I still had the problem, open a terminal and run

"apt-get dist-upgrade"  again.

This time it installed everything and had me restart my computer and edgy began working fine with no problems.  I have since done a similar procedure to upgrade to feisty fawn and now everything is working great!

Hope this could help someone.

justin

---

