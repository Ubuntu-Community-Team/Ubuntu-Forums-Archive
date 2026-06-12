---
title: "How can I make sure that Computer Janitor didn't delete anything important?"
date: 2010-04-16
forum: General Help
---

### Post by TheNerdAL on 2010-04-16
So I ran Computer Janitor and I thought it deleted things I don't use anymore so I deleted those things and I read somewhere that Computer Janitor does delete important things, how can I be sure that I didn't delete anything important?

---

### Post by gavinjb on 2010-04-16
Hi,

I have never used Computer Janitor, but my first thought would be to check to see if it creates a log file.

Also to note form looking on google, I can see several people with problems where it has deleted apps that were wanted, it seems that on Ubuntu/Mint it will remove anything that was not installed with synaptic (unless you untick the options).

not sure if this helps.


Gavin,

---

### Post by TheNerdAL on 2010-04-16
> **gavinjb said:**
> Hi,

I have never used Computer Janitor, but my first thought would be to check to see if it creates a log file.


How do I do that?

---

### Post by gavinjb on 2010-04-18
Most logs are usally stored inside /var/log/ have a look inside there to see what you can find

but if you cant find anything there you could check to see if Computer Janitor has a manual orr a website (I cant see one).

From googling I have seen a lot of people complaining about it deleting all sorts of apps on Ubuntu (seems to be buggy), including print drivers, dropbox and other apps.

---

### Post by 3rdalbum on 2010-04-18
Computer Janitor sometimes deletes programs that you use, that are not in the repositories or were automatically installed to satisfy a dependency for a program you have removed. In other words, if you don't notice anything missing from your system, then CJ has not done anything wrong.

My rule of thumb is: If there's anything that wants to get removed in Computer Janitor or Synaptic, you need to check the list carefully before allowing the removal.

---

### Post by rudihawk on 2010-04-18
My honest answer? Don't use it. 

Janitor removes 3rd party repo's and the software associated with them, which is unacceptable.

---

### Post by Mark Phelps on 2010-04-18
> **TheNerdAL said:**
> ...how can I be sure that I didn't delete anything important?

Basically -- you can't.  I used that (by mistake) a while back and had to do a complete reinstall to get a working system back.

Recommend strongly AGAINST using Computer Janitor.

---

### Post by Arand on 2010-04-18
Look at [menu]System &#8594; Administration &#8594; **Log File Viewer**

The log **dpkg.log** contains all packaging actions done on the system.

One way is to simply look through this one and check all packages that were removed at that particular point.


Alternatively:```
cat /var/log/dpkg.log | grep remove
```will output a list of only the package removal actions done on the system, again matching the time you should be able to find out what, if anything, was removed by computer janitor.

- Arand

---

