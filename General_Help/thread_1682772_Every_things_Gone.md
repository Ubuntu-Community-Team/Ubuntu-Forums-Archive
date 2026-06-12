---
title: "Every things Gone"
date: 2011-02-06
forum: General Help
---

### Post by baqar on 2011-02-06
HEy i am using ubuntu for last 2 months.
But now recently while i was running it some sort of code error occur and then when i rebooted my Pc my all thing
i.e. in
/home 
is gone....

But modifications are charged to zero again. As if i had installed a fresh version of ubuntu..
Please help what shall i Do ... ???? !!!!!

---

### Post by wojox on 2011-02-06
What was the error code?

---

### Post by baqar on 2011-02-06
I dont knwo it was like (could not generate xml ..... )
While i was using file zilla, the only change which i had donw was add eyes and force quit to the panel..
Thats quite absurd... :(

---

### Post by Krytarik on 2011-02-06
Check with root rights if your home directory is still there. Does it remember your settings, when you change something in your fresh environment?

---

### Post by baqar on 2011-02-06
> **Krytarik said:**
> Check with root rights if your home directory is still there. Does it remember your settings, when you change something in your fresh environment?
How to check ???
While further more
i had only 16Gb free space left now its back again 85Gb ....!!!

---

### Post by jroa on 2011-02-06
```
sudo cd /home
ls
```

See if your directory is still listed.

---

### Post by Krytarik on 2011-02-06
> **baqar said:**
> How to check ???

- press Alt+F2
- enter "gksudo nautilus"
- enter your password
- check if any of your previous files are there, i.e. in Pictures
> **baqar said:**
> 
While further more
i had only 16Gb free space left now its back again 85Gb ....!!!
That sounds weird.

How about my question?
> Does it remember your settings, when you change something in your fresh environment?

---

### Post by baqar on 2011-02-06
> **jroa said:**
> ```
sudo cd /home
ls
```See if your directory is still listed.

When this happened at instant all my directories were gone that are 
/downloads
/videos
/documents 
etc 
each and every thing.
When i restarted
Ubuntu seemed to be as it was freshly installed...

---

### Post by baqar on 2011-02-06
> **Krytarik said:**
> - press Alt+F2
- enter "gksudo nautilus"
- enter your password
- check if any of your previous files are there, i.e. in Pictures

That sounds weird.

How about my question?

Your first Q.....
I checked and it shows only empty root directory
2nd Q....
Yeah....
It seemed to me as completely fresh, as if i am running from liveCD. coz i had changed my display setting added compiz changeg my desktop to Mac/OS type....

---

### Post by Krytarik on 2011-02-06
> **baqar said:**
> Your first Q.....
I checked and it shows only empty root directory
2nd Q....
Yeah....
It seemed to me as completely fresh, as if i am running from liveCD. coz i had changed my display setting added compiz changeg my desktop to Mac/OS type....
I already got that, but what I was asking is: Does it remember your NEW settings after a relogin?

What do you mean by "empty root directory"? A directory with your username that is empty, or the "home" directory of root?
Hint: Click at "View", then at "Show Hidden Files".

---

### Post by baqar on 2011-02-06
> **Krytarik said:**
> I already got that, but what I was asking is: Does it remember your NEW settings after a relogin?

What do you mean by "empty root directory"? A directory with your username that is empty, or the "home" directory of root?
Hint: Click at "View", then at "Show Hidden Files".

Thanks for the link sire...
But i have already told u that the free space has increased means i had lost my data :(
If it would have been hidden the space would be shouting at me that the file is here :D
But it isnt....
And for your question
No he has almost forgot each and everything, even my firefox has lost my facebook saved password :lolflag:

---

### Post by Krytarik on 2011-02-06
1. It's not usual for a users home directory to have the size of some 70 GB. So the point, that you are referring tells us nothing, of course unless you can confirm that your home directory was 70 GB big.

2. You still didn't answer my question.

---

### Post by baqar on 2011-02-06
Look i am totally noob here Ok .. :(
I have 500GB hard disk and taught to create ubuntu system that is (/)
on 80GB ok ????

And please ask me the question more simpler way thanks ...

---

### Post by jroa on 2011-02-06
He is asking that if you make changes now, do they stay when you reboot or does your system go back to default when you reboot?

---

### Post by sdowney717 on 2011-02-06
sounds like you logged in as another user.

I have several users.

all user names are under the filesystem home directory
so you can look at each user click places home folder
then select filesystem home

see what is there

---

### Post by baqar on 2011-02-06
> **sdowney717 said:**
> sounds like you logged in as another user.

I have several users.

all user names are under the filesystem home directory
so you can look at each user click places home folder
then select filesystem home

see what is there

But i am the only user ...

---

### Post by baqar on 2011-02-06
> **jroa said:**
> He is asking that if you make changes now, do they stay when you reboot or does your system go back to default when you reboot?

No the changes are saved ....
but my old one are gone x(

---

### Post by sdowney717 on 2011-02-06
[http://ubuntuforums.org/showthread.php?t=229143](http://ubuntuforums.org/showthread.php?t=229143)

is anything in the lost and found directory?
If it reboots, runs fsck and finds corrupted files, they go there.

---

