---
title: "unable to remove Rhythmbox 0.12.6"
date: 2010-05-02
forum: General Help
---

### Post by neilh67 on 2010-05-02
For a reason I cannot remember, some months ago I installed Rhythmbox 10.0.6 as an upgrade to the standard version in Karmic ( I think it was in an attempt to get Ipod working).
Now that I have upgraded to Ubuntu 10.0.4 LTS with Rhythmbox 10.0.8 installed, I have a problem that when I try to start Rhythmbox, the old (unwanted) version starts, even though I have checked and the later version is installed.

I am unable to find a way to remove 10.0.6 as in the terminal when I use command

remove --purge rhythmbox-0.12.6

the message I get is "Couldn't find package rhythmbox-0.12.6" but I know it's there as the folder is in filesystem/usr/local/src/rhythmbox-0.12.6

Can anybody suggest a way I can remove this old, unwanted version soI can use the new version with all its lovely benefits?

Thanks

---

### Post by Karmic Alice on 2010-06-05
> **neilh67 said:**
> For a reason I cannot remember, some months ago I installed Rhythmbox 10.0.6 as an upgrade to the standard version in Karmic ( I think it was in an attempt to get Ipod working).
Now that I have upgraded to Ubuntu 10.0.4 LTS with Rhythmbox 10.0.8 installed, I have a problem that when I try to start Rhythmbox, the old (unwanted) version starts, even though I have checked and the later version is installed.

I am unable to find a way to remove 10.0.6 as in the terminal when I use command

remove --purge rhythmbox-0.12.6

the message I get is "Couldn't find package rhythmbox-0.12.6" but I know it's there as the folder is in filesystem/usr/local/src/rhythmbox-0.12.6

Can anybody suggest a way I can remove this old, unwanted version soI can use the new version with all its lovely benefits?

Thanks



That's because you are using the wrong command.

 ```
sudo apt-get remove --purge rhythmbox*
``` should do it.

---

