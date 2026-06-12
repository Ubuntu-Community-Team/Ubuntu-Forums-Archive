---
title: "Ubuntu 11.10 update broke server?"
date: 2011-10-14
forum: General Help
---

### Post by xioSlayer on 2011-10-14
I was running 11.04 server with the desktop gui installed. I upgraded to 11.10 and it mentioned that it mucked with sources.list

I noticed it also had the side effect of making it so I could no longer view my LAMP website even from the server itself. It can't connect to localhost.

I then tried to fix sources.list by uncommenting the lines I previously added for webmin.

(i'm a new linux user so things were starting to look grim at this point)

I restarted the server and now it takes a while to boot and mentions it couldn't bind to the SMBus or something as well as that it cannot obtain the network configuration.

Then it takes me to an solid black screen with an X for a cursor.



Firstly, is this possible to fix? And if not, I guess I need to boot in with a live CD and back up everything up and start over? :/

In the case that I have to start from scratch again, should I just use the 11.04 release instead of 11.10? Or is this some sort of 'upgrade' error that I won't experience if I install 11.10 from scratch?


Any help would be really appreciated. Thank you.

---

### Post by JohnE1 on 2011-10-21
The links below should help you:

[http://www.reddit.com/r/Ubuntu/comments/kmfv0/latest_1110_oneiric_update_can_break_networking/]("http://www.reddit.com/r/Ubuntu/comments/kmfv0/latest_1110_oneiric_update_can_break_networking/")


Apparently, updating 11.10 left networking incomplete by removing rather than replacing file: libnss3.so

This is one source I found for it:

[http://packages.ubuntu.com/oneiric/net/libns3-3]("http://packages.ubuntu.com/oneiric/net/libns3-3")

I downloaded and tried to install the package above and ran into a snag during the installation of it. It refused to install certain files and the entire package installation failed due to version and non-supported lib warnings. So, meanwhile, I'm still looking for libnss3.so that will work (going under the assumption that that is indeed what's broken my networking during an update of 11.10). Both Firefox and Thunderbird have a copy, but the size of each libnss3.so is different; bout 5K bigger in Firefox than it is in TB.

HTH!

JohnE1

---

