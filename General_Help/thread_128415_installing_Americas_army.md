---
title: "installing Americas army"
date: 2006-02-11
forum: General Help
---

### Post by njzillest on 2006-02-11
How do i install Americas army. I allready downloaded it to my desktop and extracted it to my desk top. I attempted to su armyops210-linux.bin
 and to sh armyops210-linux.bin Both said "no such directory" What can i do to install the game?


thanx for the help

---

### Post by Lord Illidan on 2006-02-11
> How do i install Americas army. I allready downloaded it to my desktop and extracted it to my desk top. I attempted to su armyops210-linux.bin
 and to sh armyops210-linux.bin Both said "no such directory" What can i do to install the game?

su armyops210-linux.bin won't work... su is used to change users.

Are you running from your home directory?
The desktop is located at /home/username/Desktop

cd to that location.
Then run ```
sh armyops210-linux.bin
``` HINT : while typing commands, press TAB. It will autocomplete the command for you.

---

