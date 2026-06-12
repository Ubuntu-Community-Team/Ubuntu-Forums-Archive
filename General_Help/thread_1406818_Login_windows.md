---
title: "Login windows"
date: 2010-02-14
forum: General Help
---

### Post by agkq62 on 2010-02-14
When I boot up 9.10, very occasionally, I get a login screen directly after the page with the Ubuntu b&w symbol and before the colour page. It doesn't happen very often but usually when I am showing someone how good and quick  Ubuntu is.

Any ideas,

Thanks.

---

### Post by agkq62 on 2010-02-19
Still having problems with this. Any ideas/

Thanks

---

### Post by skarychinezeguie on 2010-02-19
sooooo, you're not supposed to get a login screen, but occasionally you catch a glimpse of a login screen?

---

### Post by agkq62 on 2010-02-19
Yup, i have to enter my login name and password and then usually enter sudo in desperation and eventually the boot up continues. This is dual boot with a partition.

---

### Post by skarychinezeguie on 2010-02-19
well i doubt your other OS would be causing it. if this was a mac i would say it sounds like your plist files got screwed up. but in this case i'm not sure. It could be a permissions problem, or disk error. try running a repair disk utility if there is one. it still sounds like whatever files deal with your login info are screwed up. idk. that's a bit over my head at the moment, but i would google various strings pertaining to auto login problems and see what you can do about resetting them. on a mac you just need to reset the PRAM. try makin a new account and see if the issue occurs with that one. though idk if you can set another account to auto-login over another. you may need to turn the auto-login off on your main account.

---

### Post by arnab_das on 2010-02-19
go to system > preferences >login screen and see which option is enabled (show login option or a login option with a particular username).

---

### Post by agkq62 on 2010-02-19
Doh, another senior moment, forgot all about the auto login setting. I'll try that, many thanks.

---

### Post by agkq62 on 2010-03-05
Still having problems with this. Firstly I forgot to say the login window that appears between the b&w Ubuntu symbol and the coloured Ubuntu window is a terminal for command prompts.

I have created a new user and deleted the original but the login window still appears every second or third bootup in the original name. Now of course I can't put in the password as it comes up incorrect so I have to reboot and then everything goes straight through.

Anything else I can try?

Thanks.

---

### Post by skarychinezeguie on 2010-03-05
backup your home folder and reinstall. here is an awesome tutorial on backing up your entire system for a full restore, but you could just as easily use it to back up your home folder rather than the entire system.

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

