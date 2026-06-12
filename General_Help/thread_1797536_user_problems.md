---
title: "user problems"
date: 2011-07-05
forum: General Help
---

### Post by imadman on 2011-07-05
Hi,

I got into some weird situation on my xubuntu which makes that i have to use windows and i don't like it so please help me to get back...

What my situation was before the problems:
-I dualboot win(xp) and xubuntu(11.04)
-No problems whatsoever except for the fact that power consumption was higher on xubuntu.

Then i read something that said that the kernel i was using was effectively having power issues and that it could be fixed so in went into the terminal and nano'd the grub config file and update-grub'd with the addition i had read all over the internet.
When i rebooted it seemingly had worked but once i opened a youtube video it didn't react to anything(i'm 99% sure kernel panic since there was no hdd movement). So i forced it to shutdown and when i got back in again i nano'd the file again but for some reason i didn't only remove the power stuff but I also removed the quiet splash. Once i had rebooted it would suddenly ask for username and password twice(: once the older looking menu an then the newer looking one with the fancy bg). The first time i got in okay but afterwards i could only get in as root. I thought i had simply forgotten my password but i ran passwd myusername as root and it didn't work(only when i typed something random it gave the wrong password message). As root i also can't edit the users and groups(when i open it it stays grayed out).


What happened and how do i fix this. If i will lose my account anyways then how do i get my files/bookmarks/... of of it

thanks in advance,

imad

---

### Post by mikejonesey on 2011-07-05
ohh dear... you'll need to live boot, edit ur grub config back to remove the option you added install n update grub... 

ps u only messed up ur grub, no biggie, but i wouldn reccomend changing props without a little more info next time... (i read a post on this power issue but there is no way i would add a prop to my grub without knowing what it does from either more sources or a direct source...)

---

