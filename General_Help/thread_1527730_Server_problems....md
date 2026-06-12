---
title: "Server problems..."
date: 2010-07-09
forum: General Help
---

### Post by fneergaard on 2010-07-09
My server have been down for some time and now I need it again!

Its supposed to run a site and an mysql server.

Since I took the server down I have changed ISP and IP number.

Well, Now I need it again and I I need some help!

If you take a look at 188.178.104.174 you see something imcomplete and I guess it could be mysql... 

I have been setting up port 21-22 and 80 in my FW! Is that sufficient?

Any idea? Please!

Regards,

Frank

---

### Post by GreenN00b on 2010-07-09
You are using carpuna.com as a domain however the dns point to the wrong ip:
> Your [www.carpuna.com](www.carpuna.com) A record is:
[www.carpuna.com](www.carpuna.com) -> carpuna.com -> [ 87.60.199.180  ] 
One solution will be to update dns settings to point to the new ip.
Also you should use relative paths for css and images that way will work with the ip as you are trying now.

You do not need port 21-22 in order for the site to work.

---

### Post by fneergaard on 2010-07-10
Hi Green,

Thanks for the help... The DNS settings did it!

Frank

---

