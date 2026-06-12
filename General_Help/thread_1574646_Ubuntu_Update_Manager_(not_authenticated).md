---
title: "Ubuntu Update Manager (not authenticated)"
date: 2010-09-14
forum: General Help
---

### Post by ep1centre on 2010-09-14
Hello, 


As per title, i installed ubuntu on a machine but had no internet access for a few days, now i have internet access but when i went to update ubuntu, it says "Warning - You are about to install software that cant be authenticated?



Also for some reason even when i go ahead and install the updates anyway this particular file wont download and it generates this error message:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/m/mountall/mountall_2.15.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/m/mountall/mountall_2.15.1_i386.deb)
  404  Not Found


Any ideas?

Thank you.

---

### Post by ep1centre on 2010-09-14
And to add to that, i just tried to install gnucash using the ubuntu software center and it did it again, wont allow me to install software from there either aparently its an unathenticated source!

---

### Post by sikander3786 on 2010-09-14
Just change the server form System >>> Administration >>> Software Sources and select Main server preferably. Now do

```

sudo apt-get update

```

and

```

sudo apt-get install whateversoftware

```

---

### Post by mc4man on 2010-09-14
While you're in 'Software Sources' make sure the first 4 are checked under Ubuntu Software tab and the first 2 under the 'Updates' tab (security and updates.
(if a reload button shows up then click on it

---

### Post by ep1centre on 2010-09-15
i must have just missed your replies last night, today when i came in, booted the computer the update manager kicked in and all was fine as if nothing happened... go figure ubuntu can be odd... in windows when something isnt right you bloody well know about it as the whole thing packs up, in ubuntu it just acts odd...

anyway yes i had restarted the computer several times yesterday and i did quickly check said options in software sources but no luck...today i just started the computer and it was as if nothing happened so even without understanding why i guess this one's solved.

Thank you!

---

### Post by OrangeVixen on 2010-09-30
I get the same thing too and sometimes waiting a few hours and clicking on Reload in Update Manager works too.

---

### Post by sikander3786 on 2010-09-30
> **OrangeVixen said:**
> I get the same thing too and sometimes waiting a few hours and clicking on Reload in Update Manager works too.
It can be caused by a problem with the update server, mirror or even your own internet connection. You can always try to change the server from Software Sources and see if it works straight away. No need to wait for a few hours :-)

---

### Post by frodowiz on 2011-04-20
im really getting tired of this crud.  note to the fine folks with PPA's - if you have a key you better start making it available regardless of any condition.. my problem is that with ppa's issuing keys that , for whatever reason, arent available at the time of addition, you can still grab the software and  go on your merry way. then next week you go to update and poof- here comes the not authenticated sources message. 

why on earth would you NOT make darn sure that key downloaded?

i have some nice software that  is holding back updates because the key wasnt available atthe time of addition to  sources, or the server is down and cant get verified bla bla bla.

if you want your stuff used, make darn sure it can get updated.

sure i can disable the ppa's but that kinda  kills the point of updating everything..

i love  ubuntu,linux,and the fine folks who contribute and share this opertunity. why muddle the waters?


if there is a fix, other then removing the ppa stuff and just using the standard repos i would be glad to hear it.

---

### Post by sikander3786 on 2011-04-21
> **frodowiz said:**
> im really getting tired of this crud.  note to the fine folks with PPA's - if you have a key you better start making it available regardless of any condition.. my problem is that with ppa's issuing keys that , for whatever reason, arent available at the time of addition, you can still grab the software and  go on your merry way. then next week you go to update and poof- here comes the not authenticated sources message. 

why on earth would you NOT make darn sure that key downloaded?

i have some nice software that  is holding back updates because the key wasnt available atthe time of addition to  sources, or the server is down and cant get verified bla bla bla.

if you want your stuff used, make darn sure it can get updated.

sure i can disable the ppa's but that kinda  kills the point of updating everything..

i love  ubuntu,linux,and the fine folks who contribute and share this opertunity. why muddle the waters?


if there is a fix, other then removing the ppa stuff and just using the standard repos i would be glad to hear it.
Sometimes you need to manually refresh you repository index by running the apt-get update command or by clicking the 'Check' button in update manager and then you won't see the not authenticated message. Update Manager should refresh the index automatically but the case is a bit different till now.

For a better answer to you question, we need to see the complete output of this command please.

```
sudo apt-get update
```

---

