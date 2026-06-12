---
title: "Adding programs for automatic startup?"
date: 2009-12-21
forum: General Help
---

### Post by Amzo2 on 2009-12-21
I have a server running ubuntu, and want to know how to add program to start automatically, there is no GUI, and everything is done via ssh? 

Thanks.

---

### Post by s.fox on 2009-12-21
Hello,

I think [this]("http://ubuntuforums.org/archive/index.php/t-300296.html") is what you are after.  Hope this helps.

-Silver Fox

---

### Post by Amzo2 on 2009-12-21
ssh starts automatically, but I need some other programs to run after a reboot, so I don't have to go start them all manually after a reboot.

Would I have to to write some sort of script for /etc/init.d?

Or how what I do it via crontab?

---

### Post by StuartN on 2009-12-21
> **Amzo2 said:**
> ssh starts automatically, but I need some other programs to run after a reboot, so I don't have to go start them all manually after a reboot.

Would I have to to write some sort of script for /etc/init.d?

Or how what I do it via crontab?

There is a really nice shorthand: @reboot command. There are others like @yearly and @midnight. Full details are in man 5 crontab.

---

### Post by Amzo2 on 2009-12-21
Lol yeah I figured it out, but here is what I did jsut incase anyone needs it.

'crontab -u user -e'

and just added 
'@reboot command'

---

