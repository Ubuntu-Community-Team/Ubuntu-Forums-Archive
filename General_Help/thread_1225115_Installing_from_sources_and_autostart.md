---
title: "Installing from sources and autostart"
date: 2009-07-28
forum: General Help
---

### Post by alpha_lt on 2009-07-28
Hello,

Recently I've installed proftpd FTP server from sources. It didn't produce any startup scripts and put nothing in /etc/init.d
So I wrote startup script and called it proftpd.sh and put it into /etc/init.d and then enter command *update-rc.d ./proftpd.sh defaults*.
My question is it everything I did was corectly ? Some people in other forums suggested to use *sysvconfig* or *upstart*. Do I really need them ?

---

### Post by justleen on 2009-07-28
No, not really. This way accomplishes exactly the same. Its just that some people (me included) cant get the hang off the update-rc.d way, and want to stick with sysvconf (it has some other functions that updaterc is missing).  

All updaterc does is create symlinks in the correct rc.d folder, with a correct priority. You could even do it manually if you'd really want to..

---

