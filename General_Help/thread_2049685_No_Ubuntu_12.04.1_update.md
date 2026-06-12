---
title: "No Ubuntu 12.04.1 update?"
date: 2012-08-29
forum: General Help
---

### Post by techbuntu27 on 2012-08-29
Hello been using ubuntu for a while. I've done a fresh install on my 80GB IDE HD which runs smoothly and comfortable on using it as my secondary OS. But I'm no expert on tinkering its terminal and minimal knowledge on its cli commands. So I have this problem, why is that I don't receive the Ubuntu 12.04.1 LTS update? even-though I have chosen the "Long term support" notification on update software settings with security and recommended updates are checked. Need help on this matter guys.

[IMG]http://i.imgur.com/7kE41.jpg[/IMG]

[IMG]http://i.imgur.com/fbTYW.jpg[/IMG]

---

### Post by taras.kuzyo on 2012-08-29
Please run it in terminal:
```
lsb_release -a
```

---

### Post by zombifier25 on 2012-08-29
> **taras.kuzyo said:**
> Please run it in terminal:
```
lsb_release -a
```

This.

Also, 12.04 and 12.04.1 are not different from each other; the latter is simply the former applied all the updates up to the date. The System Monitor will not show 12.04.1, it simply shows 12.04 (like on my setup)

---

### Post by ajgreeny on 2012-08-29
I have an alias set up for the command ```
lsb_release -dc && echo "Desktop:    $DESKTOP_SESSION" && uname -a
``` so I type "version" in terminal and get 
```
$ version
Description:    Ubuntu 10.04.4 LTS
Codename:    lucid
Desktop:    gnome
Linux Lucid 2.6.35-32-generic #68~lucid1-Ubuntu SMP Wed Mar 28 17:09:33 UTC 2012 i686 GNU/Linux
``` which gives much more information to me about everything.

System monitor never shows the point versions of the ubuntu OS, just the base, eg, in my case, 10.04 (Lucid), but as you can see I am running 10.04.4.

---

### Post by techbuntu27 on 2012-08-29
Hello guys, thank you very much for helping me out with this problem of mine...

I think I'ts fine now??? Right? Because it says 12.04.1 so is my system up to date now?

[IMG]http://i.imgur.com/9Zzri.jpg[/IMG]

---

### Post by beboylips on 2012-08-29
As said above, 12.04.1 is just a release designed for fresh installs and contains all the updates released for 12.04 up to the date of the release of 12.04.1 . It's just an updated version of 12.04. You "get" it by simply updating regularly.

---

### Post by techbuntu27 on 2012-08-30
> **beboylips said:**
> As said above, 12.04.1 is just a release designed for fresh installs and contains all the updates released for 12.04 up to the date of the release of 12.04.1 . It's just an updated version of 12.04. You "get" it by simply updating regularly.

Sorry for not getting the point. Because I'm very new to Linux Environment and using its features confuses me a lot. Nevertheless I want to thank you all guys for assisting me.

---

### Post by lotharmat on 2012-08-31
Thanks for this! - Very useful for me - I was wondering about the point 1 update and this has confirmed that my 'up to date' system is 12.04.1!

Thanks again! :)

---

