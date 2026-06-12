---
title: "computer freezing in ubuntu and windows 7"
date: 2010-01-20
forum: General Help
---

### Post by stldirty on 2010-01-20
this is happening pretty often.  when in ubuntu, usually while i'm browsing the web, my browser will go dim then a box will come up saying something along the lines of missing resources.  the thing is, all my desktop icons will then turn to red x's and no text characters on any further boxes will show.  when i restart it says grub error and takes one more restart to finally come on.  i got fed up with it and switched over to windows 7 where my browser also froze and my computer froze up.  any help diagnosing this will be EXTREMELY appreciated.

hp dv6000

---

### Post by mk1w86 on 2010-01-20
If your computer is crashing in Ubuntu and Windows then it sound like you might have a hardware problem. :(

Somewhere you can start is checking your RAM using Memtest, you should be able to boot Memtest from Grub when your computer starts. ;)

---

### Post by stldirty on 2010-01-20
> **mk1w86 said:**
> If your computer is crashing in Ubuntu and Windows then it sound like you might have a hardware problem. :(

Somewhere you can start is checking your RAM using Memtest, you should be able to boot Memtest from Grub when your computer starts. ;)

i just ran that and my computer shut off before it finished...

---

### Post by synapsys on 2010-01-20
Ram or overheating. Check for dust.

---

### Post by stldirty on 2010-01-20
i'll plug it in to my cooling pad and see.  but there doesn't seem to be too much dust.  not any that i can get to without opening it up anyway. i'll look at getting an aircan tomorrow.

---

### Post by wkulecz on 2010-01-20
If the memtest crashes, my first replacement would be the power supply assuming all the fans are working and heatsinks still attached.

> i'll look at getting an aircan tomorrow Don't!  Get a vacuum cleaner.  Stirring up the dust can cause the hard drive vents to clog with it later, leading to premature hard drive failure.

---

### Post by stldirty on 2010-01-20
oh.  ok.  thanks lol.  i'll try that now then. :)

---

### Post by kerry_s on 2010-01-20
try running from live cd, if it crashes it's ram, if it runs fine it's hd.

---

### Post by stldirty on 2010-01-20
alright i'll try that too.  it hasn't crashed since i've had my cooling pad running though so this i'm still on the first diagnosis.  bout to vacuum it in a second just to make sure.

---

### Post by stldirty on 2010-01-26
ok so i just got an error message that forced a restart so i took a picture of it.  and while i was coming to post it the missing resources thing happened again and i had to restart...again.  here's the photos of the first error.

---

### Post by kerry_s on 2010-01-26
> **stldirty said:**
> ok so i just got an error message that forced a restart so i took a picture of it.  and while i was coming to post it the missing resources thing happened again and i had to restart...again.  here's the photos of the first error.

the error don't help, that can be caused by bad ram or disk. for example say it can't find the directory cause the drive just froze, but you can get the same error from ram, for example the drive read fine but the data was corrupted when it went to ram. ram is the middle man all go's through there.

you try the live cd?

---

### Post by stldirty on 2010-01-26
i need to get a live cd burned for me.  there's something wrong with my burner.  this happens about once a day though and usually when i'm on the web.  i can't get my internet connection going through a live cd however. i might end up spending a week trying to reproduce a problem.

---

### Post by eddier on 2010-01-26
Is it a Sony Laptop by any chance?

eddie

---

### Post by stldirty on 2010-01-27
nope an hp dv6000

---

### Post by stldirty on 2010-02-16
finally figured it out guys.  i had a bad stick of ram in there.  replaced it and everything has been working smooth since.

---

