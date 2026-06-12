---
title: "syncing Evolution between multiple computers?"
date: 2010-04-14
forum: General Help
---

### Post by derande on 2010-04-14
I am beginning to use Evolution not for email, but for calendar and contact archiving.

I also use 3 different computers, all currently running Karmic.

Is it possible to have Evolution sync calendar and contacts on all 3 machines? Possibly by using Ubuntu One or another cloud service like Dropbox?

OR are there any other calendar/contact software programs that can sync between multiple computers besides an online service like Google?

Thanks!

---

### Post by duanedesign on 2010-04-14
Ubuntu One can sync contacts on CouchDB and replicate between desktops and the cloud. They have also [recently introduced]("http://fridge.ubuntu.com/node/2009") the ability to get those contacts from and to mobile phones.

---

### Post by Mr5o1 on 2010-06-21
I'm keen to give this a shot myself.. Having googled around a bit.. I havent found much info about this, everyone seems obsessed with syncing to google - which doesnt seem that helpful to me if it wont sync tasks as well as calendars.

As far as I can tell, evolution uses two folders for your 'profile':
/.evolution and /.gconf/apps/evolution

I was going to try moving both folders into /Ubuntu One, and then creating symlinks in their original positions (ln -s) then on another pc, create those same symlinks.

Does anyone know if this will work? I read that when moving these folders to a new machine on a thumbdrive or something, you need to have the same login & password on each machine, so I assume that would apply here also. Is that true??

Are there any problems I should watch out for?

Is there an easier way to do this?

---

### Post by pir on 2011-11-20
> **Mr5o1 said:**
> I'm keen to give this a shot myself.. Having googled around a bit.. I havent found much info about this, everyone seems obsessed with syncing to google - which doesnt seem that helpful to me if it wont sync tasks as well as calendars.

As far as I can tell, evolution uses two folders for your 'profile':
/.evolution and /.gconf/apps/evolution

I was going to try moving both folders into /Ubuntu One, and then creating symlinks in their original positions (ln -s) then on another pc, create those same symlinks.

Does anyone know if this will work? I read that when moving these folders to a new machine on a thumbdrive or something, you need to have the same login & password on each machine, so I assume that would apply here also. Is that true??

Are there any problems I should watch out for?

Is there an easier way to do this?

Have you tried yet? Or found a better solution?

---

### Post by drdos2006 on 2011-11-20
What you are looking for is Open Source Email & Collaboration Software

There is [http://www.zarafa.com/](http://www.zarafa.com/) and [http://www.zimbra.com/](http://www.zimbra.com/)

Zentyal server loads zarafa as an add-on.

regards

---

