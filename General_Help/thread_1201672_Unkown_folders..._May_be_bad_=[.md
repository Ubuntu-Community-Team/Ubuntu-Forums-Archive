---
title: "Unkown folders... May be bad =["
date: 2009-07-01
forum: General Help
---

### Post by CharlesWelsh on 2009-07-01
Umm... I have a folder on my computer located in  /tmp/pulse-PKdhtXMmr18n... And im just curious. Is that supposed to be there? It willl not allow me to view the folder and the permissions are all set to ROOT. Sorry if this is a minor problem... or not a problem at all. But im a little uneasy with me not understanding this OS to well. Any input would be nice. Thank you -CJ

---

### Post by scrooge_74 on 2009-07-01
Those are temp folders created by the system, if you want to see what is in there (but don't erase anything)

open a terminal and type gksudo nautilus 

this will let you browse as root, so be carefull dont you go erasing something and breaking havok on the system ;)

---

### Post by CharlesWelsh on 2009-07-01
I'm a little afraid to mess with the terminal... However as long as I dont have like a virus or something... Because my computer has been slowing down so i cleared the temp folder. And i didnt know why that one wouldnt delete. As long as its supposed to be there... Then I am a little less worried...

---

### Post by DeMus on 2009-07-01
> **CharlesWelsh said:**
> Umm... I have a folder on my computer located in  /tmp/pulse-PKdhtXMmr18n... And im just curious. Is that supposed to be there? It willl not allow me to view the folder and the permissions are all set to ROOT. Sorry if this is a minor problem... or not a problem at all. But im a little uneasy with me not understanding this OS to well. Any input would be nice. Thank you -CJ

Isn't it like in Windows where you can just delete everything in the /tmp folder? Or am I completely wrong now?

---

### Post by c0mput3r_n3rD on 2009-07-01
Yes demus you can delete everything in the tmp directory... nothing of substance actually goes in there

---

### Post by scrooge_74 on 2009-07-01
> **CharlesWelsh said:**
> I'm a little afraid to mess with the terminal... However as long as I dont have like a virus or something... Because my computer has been slowing down so i cleared the temp folder. And i didnt know why that one wouldnt delete. As long as its supposed to be there... Then I am a little less worried...


First of all it aint a virus, trust us on that one.

What are your specs? And what are you running that is causing you to slow down.

You can open a terminal and type top and it will let you know what is running.

For example I had issues the other day with firefox because somehow wine started each time I used firefox because it wanted to use the Windows version of flash.

Maybe you did not configure enough disk space for the system to use.

the command line is your friend, you can config stuf from there, or shutdown programs that are not responding, I used to always have a terminal open to config stuff or shut down things, but with each passing version of Ubuntu I do that less and less

---

### Post by 3rdalbum on 2009-07-01
> **c0mput3r_n3rD said:**
> Yes demus you can delete everything in the tmp directory... nothing of substance actually goes in there

The tmp directory contains temporary files for other users too, not just your own user account.

Tmp gets erased on shutdown (or on bootup, the end result is the same).

DON'T REMOVE ANYTHING IN THERE THAT YOU DON'T UNDERSTAND. You can potentially crash your system by doing that, or you could more likely crash one of your programs and lose unsaved changes.

Please, get out of the mindset of "I don't understand this, it must be a virus". There are no viruses on Linux. None. Zero, zip, zilch. Maybe in the future, but not now.

---

### Post by CharlesWelsh on 2009-07-01
I'm a little afraid to mess with the terminal... However as long as I dont have like a virus or something... Because my computer has been slowing down so i cleared the temp folder. And i didnt know why that one wouldnt delete. As long as its supposed to be there... Then I am a little less worried...

---

### Post by scrooge_74 on 2009-07-01
open a terminal and type ps -ax and copy paste that list in here so others can see what is running and maybe slowing you down

---

### Post by t0p on 2009-07-01
> **CharlesWelsh said:**
> I'm a little afraid to mess with the terminal

That's understandable if you've never used it before.  But if someone here wants you to put a command in the terminal, all you need to do is copy it and paste it into the terminal, then copy the output and paste it into a forum post.  If you don't do it, we won't be able to help you fix anything.  So don't worry - just do it! :)

> **CharlesWelsh said:**
> 
my computer has been slowing down so i cleared the temp folder

Hmm.  I wouldn't do that if I were you.  Your system creates all sorts of temporary files, to do with all sorts of processes.  Deleting these files could cause processes to crash.  And deleting temporary files won't make your computer go faster.

---

### Post by -kg- on 2009-07-01
> Isn't it like in Windows where you can just delete everything in the /tmp folder? Or am I completely wrong now?

Actually, no...you can't delete *everything* in the Windows /tmp directory.  I know...I've done it over and over.

Any .tmp file that is currently open and being used by Windows or software/running processes cannot be deleted until whatever is accessing it closes it.

I don't know about Ubuntu or Linux in general, but I would think that would be included as a safety feature so someone couldn't inadvertently crash their system by deleting a file that was being used.

---

