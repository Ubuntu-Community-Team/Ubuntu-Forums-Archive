---
title: "Howto escape a passwd in sbackup utility"
date: 2010-04-28
forum: General Help
---

### Post by olyander562 on 2010-04-28
This is prolly a quickee, but I not able to figure it out.

I am using sbackup installed on karmic 9.10.

I am using the gui driven sbackup, and the field below needs a passwrd:

ssh://username:password@192.168.1.201:/usr/home/username/BAK/

This is a remote backup to a backup storage server.

Nothing fancy, just need to know how to escape a :password@ were the real password uses non numeric/alpha characters.

my passwd includes an "@" so would i use quotes? backticks? backslashes?

Using a passwd like ab34f67 will not work, i use shift'd chars like ^&*@ so forth in my passwrds.

Can someone give me a clue?

Thanks, Oly

---

### Post by munky99999 on 2010-04-28
I havent tried sbackup before. However it might be an ssh issue. A recent patch made the ftp style cli like that stop working.

I had to setup entering the password and login through the cli options.

ssh://192.168.1.201/usr/home/username/BAK/ -p 2222 -l root

Then it prompts for password.

Could potentially be the issue you are discovering. Sorry if this doesnt help.

---

