---
title: "PureFTP damage - user no longer can log into Ubuntu"
date: 2010-07-27
forum: General Help
---

### Post by CraigFoote on 2010-07-27
I'm a newbie. I was attempting to set up PureFTP on my server using GAdmin-ProFTP. I'm thoroughly disappointed in how vague the tool is. I stumbled through it over and over again and could not get it right. I tried a virtual "ftp" user and then I created a normal "ftp" user account. It fared no better so I deleted it and rebooted. Now my regular "craig" account no longer works!

Grub starts up but no longer displays my "craig" user account - just a login button. Entering "craig" and my password gives an "Authentication failure". I started in recovery mode with just a root prompt and I see the /home/craig encrypted folder is still there. I tried "sudo adduser craig" and got an error stating "group craig" already exists.

I swear I deleted only the "ftp" account, not my "craig" account before rebooting and getting this mess. I don't really think PureFTP or Gadmin-PureFTP caused the problem but it sure didn't help.

Anyway, I don't really want to reinstall Ubuntu and all the stuff I had running on that machine, or decrypt the home folder and somehow move data to a safe place. It is my backup machine so it is not itself backed up properly (noob). Is there any way I can undo this damage and log in as "craig" again?

Poisoned by it all,
Craig
](*,)

---

### Post by byStanderone on 2010-07-27
...seems like, there had been a binary clutter, don't know if a sudo apt-get autoclean would do the trick, haven't personally encountered this situation. also try a sudo update-grub, just guessing,tho... lol.

---

