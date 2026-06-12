---
title: "CouchDB 0.11 - no views/useless CPU usage"
date: 2010-05-24
forum: General Help
---

### Post by tree_snake on 2010-05-24
Hello, experts

recently I installed CouchDB 0.11 from source. Everything seemed to be fine, but yesterday I found out, that I can not use CouhDB Views. There are two reasons:
1 - I get no response from CouchDB if I created a Views and tried to execute it. There's no response neither in futon non in terminal. Everything I get is an endless loading-circle (if I use futon)
2 - CouchDB immediately "eats" all free resource. CPU usage jumps to 99% right after I executed a (temp)view. Only restarting of the couchdb stops this useless CPU crap :mad:

Any Ideas ?! 

P.S. I'm using Ubuntu 10.04 via VmWare in Windows 7.
Sorry for bad english

---

### Post by tree_snake on 2010-06-14
Ok. I'll make another question....

**IS there a way to** completely remove couchdb (I guess, I have some "couchdb parts" in /usr/bin and in /usr/local/), so I could try to reinstall 0.11 version again ?!

---

### Post by tree_snake on 2010-06-14
The problem is [COLOR=Green]**solved**[/COLOR]


Solution:

To find out where the problem is, I decided to create another VirualMachine with Ubuntu 10.04 and try to install CouchDB 0.11 from source on pretty "fresh and naked" OS.
Installing (especially _./configure_ing) from source [COLOR=Red]_[wasn't simple]("http://tommy.chheng.com/index.php/2009/07/installing-couchdb-on-ubuntu-problems-and-fixes/")_[/COLOR]. I [had to install]("http://japhr.blogspot.com/2009/03/yak-shaving-is-new-dependency-hell.html") [FONT=Courier New]libicu-dev, libcurl4-openssl-dev, xulrunner-dev[/FONT] and [FONT=Courier New]erlang-dev[/FONT] first to be able to configure the SourceCode. After *make && sudo make install* I finally could start CouchDB und play with it via CURL and Futon UI. **BUT** after few second I realized, that in-front of me is the same issue as before: no working views, failed Test Suite and high CPU usage. 

As I thought, XulRunner was a headache-generator. After researching I found a [COLOR=Red]_[guide for CouchDB installation]("http://wiki.apache.org/couchdb/Installing_on_Ubuntu")_[/COLOR] 
To fix this:

```
sudo gedit /etc/ld.so.conf.d/xulrunner.conf
```and simply add :
```
/usr/lib/xulrunner-1.9.2.3
/usr/lib/xulrunner-devel-1.9.2.3
```Save and then:
```
sudo /sbin/ldconfig
```restart couchDB.
*Honestly, I do not understand how this xulrunner.conf did the trick*

After this I was finally able to use views and run test, but one of them (reader_acl) always has raised an Exception. 

[COLOR=Red]_[Workaround:]("http://mail-archives.apache.org/mod_mbox/couchdb-dev/201003.mbox/%3C20100324094049.GA5069@uk.tiscali.com%3E")_[/COLOR]
```
sudo chown couchdb:couchdb /usr/local/etc/couchdb/local.ini
```or (if local.ini wasn't found)
```
sudo chown couchdb:couchdb /etc/couchdb/local.ini
```Now, everything works fine

---

### Post by dxxvi on 2010-06-30
Thank you for this. In my case it's ```
/usr/lib/xulrunner-1.9.2.6
/usr/lib/xulrunner-devel-1.9.2.6
```

---

### Post by tree_snake on 2010-06-30
Yes, It seems that you _always need to update the xulrunner.conf_ if newer version of xulrunner was released. After updating you also need to restart the ldconfig too, otherwise you couldn't run the test suite

Hmm ..I think (and probably not only me) it would be great if we could automatize this process ....

---

