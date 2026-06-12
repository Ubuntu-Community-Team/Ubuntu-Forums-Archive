---
title: "SSH Session Hangs After Shutdown Command"
date: 2011-02-01
forum: General Help
---

### Post by clevertomato on 2011-02-01
After I issue the shutdown command (ie. sudo shutdown -h +20) in an ssh session on another ubuntu machine on my LAN at home, I receive the "system will shutdown in 20 minutes" message and then can no longer type anything into the session, leaving me unable to logout.

When I searched the web for answers, I found one suggestion to try pressing ENTER then ~ (tilda) then . (period) to end the ssh session. It did, but I should be able to type after issuing the delayed shutdown command in an ssh session.

Solutions?

---

### Post by hwttdz on 2011-02-01
What happens if you background the shutdown command on issue?
sudo shutdown -h +20 &
And then you might need to nohup it if you're going to logout before the shutdown.

---

### Post by Habitual on 2011-02-01
```
sudo shutdown -h +20 && exit
```

---

### Post by clevertomato on 2011-02-01
Neither solution works. Still hangs.

Even if it worked, those wouldn't allow me to keep using my session. Maybe I want to shutdown -h +120 and then keep using my session for a few things. Shouldn't that be possible, or is it designed to be this way? Surely it's not supposed to hang when the shutdown command is issued. It happens on Lucid, Lubuntu, and other releases of Ubuntu.

---

### Post by clevertomato on 2011-03-25
bump

---

### Post by morean51 on 2011-03-25
thank you for the code it works for me appreciate

---

