---
title: "evolution download gal"
date: 2010-08-24
forum: General Help
---

### Post by bacardiandwatermelon on 2010-08-24
Hi guys, can't for the life of me find where this is in Evolution. Basically I have Evolution 2.30.3 installed with exchange-mapi. Everything works fine and I can access the addresses in the gal fine with no issues. What is a problem is though is it isn't downloading the latest address list and all the new starters which have since started aren't showing up. In Outlook you can force it to download the address book, can you do a similar thing in Evolution?

---

### Post by bacardiandwatermelon on 2010-09-02
bump

---

### Post by dcstar on 2010-09-02
> **bacardiandwatermelon said:**
> Hi guys, can't for the life of me find where this is in Evolution. Basically I have Evolution 2.30.3 installed with exchange-mapi. Everything works fine and I can access the addresses in the gal fine with no issues. What is a problem is though is it isn't downloading the latest address list and all the new starters which have since started aren't showing up. In Outlook you can force it to download the address book, can you do a similar thing in Evolution?

So what happens when you select the list in Contacts?

---

### Post by eclay on 2011-04-27
I am experiencing a similar issue where the GAL doesn't update no matter what I try when new email accounts are added to exchange.  The only method I've found that works is to remove the following directory.

/home/usernam/.evolution/cache/addressbook/mapigal_emailid@IP/servername*

this directory will have two files in it.

cache.summary
cache.xml (contains the actual address entries).

I tried to change the address book from cache locally to not but then it wouldn't actually see any addresses.  When I deleted this directory and then restarted evolution it recreated the directory and files but I couldn't see the addresses.  I had to close evolution and pkill -9 evolution from a shell prompt then restart evolution and I could see the addresses in the GAL address book.

I'm using evolution 2.28.3 in ubuntu 10.04 but have run 10.10 and had the same problem.

hth

---

