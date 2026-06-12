---
title: "Authentication Failure."
date: 2010-02-18
forum: General Help
---

### Post by Ash-Lee on 2010-02-18
My passwords never work.

I have set it to auto-logon but when it ask me for passwords, for example to install Adobe Flash it comes up Authentication Failure.

I tryed to reset the password by booting to the command prompt and using passwd but it never works.

I'm 100% sure the original password was correct anyway.

---

### Post by Ash-Lee on 2010-02-18
If i toggle the 'F Lock' key on the keyboard it seems to make a difference.

It's a Microsoft Wireless Multimedia keyboard, not sure if theres a known issue here?

---

### Post by nothingspecial on 2010-02-18
So does it work now?

---

### Post by Jackzor on 2010-02-18
[http://www.youtube.com/watch?v=AkENYv7kEhg&feature=player_embedded](http://www.youtube.com/watch?v=AkENYv7kEhg&feature=player_embedded)

Maybe?

---

### Post by Ash-Lee on 2010-02-18
It appears to be working fine now.

I went into system/preferences/keyboard and changed the keyboard model and the problem hasn't come back.

---

### Post by Ash-Lee on 2010-02-18
Spoke to soon.

Problem has come back. Why does it keep loosing my password?

---

### Post by nothingspecial on 2010-02-18
Might be total overkill here.

To reset your password

Reboot, and when you see the grub loading dialogue, press escape, quick.

Choose, recovery mode (or whatever they call it nowdays)

Then choose root console (again, I can`t remember what it is called - something like that)
```

passwd [COLOR="Red"]*username*[/COLOR]
```

Change the red username for your username and change the password.

```
reboot
```

---

### Post by Ash-Lee on 2010-02-18
I've already done this endless times. It still wont accept the passwords.

The computer is set to auto logon, it still does that after i change the password?

---

### Post by Ash-Lee on 2010-02-18
I created a new user from the command prompt from the grub screen. Same password problem there as well.

I appreciate the security but this is stupid.

---

### Post by jbird21 on 2010-02-18
I had this problem recently, after installing recommended updates to 8.10.
Unfortunately I cannot give detailed advice, but it turned out to be a problem with PAM. In my case, for some reason, it was using a different authentication & therefore had no idea who I was or recognise my password.

Good luck, it took my VERY linux savvy friend quite awhile to fix it & then my graphics were trashed & I had to reinstall the nVidia drivers & reboot several times

---

### Post by Ash-Lee on 2010-02-19
Thankyou, any little bit of info allows me to search some more.

This problem has come when updating 9.04 (which i d/loaded as a ISO) to 9.10.

I haven't really configured anything apart from Nvidia drivers so it's pretty much a 'fresh' install. If i get to frustrated i might just d/load a 9.10 ISO and try that.

---

### Post by Ash-Lee on 2010-02-19
I have downloaded 9.10.

Will install this and hopefully this issue will be no more.

---

### Post by Ash-Lee on 2010-02-19
Forget it, i've had enough.

Returned to 8.04 LTS where i know everything works for me. :D

---

