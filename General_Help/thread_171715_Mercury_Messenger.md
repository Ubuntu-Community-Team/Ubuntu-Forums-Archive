---
title: "Mercury Messenger"
date: 2006-05-07
forum: General Help
---

### Post by Smittey on 2006-05-07
I want to try using mercury messenger with Ubuntu, but I can't seem to get it installed
I downloaded the package mercury-messenger_1710_S7_i386.deb and ran sudo dpkg -i mercury-messenger_1710_S7_i386.deb but after that Mercury doesn't appear anywhere? Where did it go?

Remember I am a newbie when replying :P

---

### Post by Kimm on 2006-05-07
I never tried the latest version of Mercury

I'm gona work on it...
But you should be able to find the executable if you look in Synaptic

Edit: Just run 'mercury' in your terminal

---

### Post by damvcoool on 2006-07-12
try using the console to open it

if it displays an error that is related to a lax file the to one of the following commands

sudo chmod 777 /usr/lib/mercury/Mercury.lax

sudo chmod -R 777 /usr/lib/mercury/

if you are the only user you can use

sudo chown -R your_user:your_group /usr/lib/mercury/

example for above in my PC

sudo chown -R eddie:eddie /usr/lib/mercury/

eddie is my user and my group is usually like that when you are the only user

---

