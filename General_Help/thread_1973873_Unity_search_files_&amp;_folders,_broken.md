---
title: "Unity search files &amp; folders, broken?"
date: 2012-05-05
forum: General Help
---

### Post by 8Kuula on 2012-05-05
So doing a test.
```
$ mkdir ~/tmp ; cd ~/tmp; echo "buuu" > testfile.txt
```

super+f 
write: testfile.txt
"Sorry, there is nothing that maches your search."

What is in ~/tmp directory then?
```
$ ls ~/tmp/
testfile.txt
```

In "privacy > files" I have nothing checked and no folders in "Don't record activity in the following folders"

So why testfile.txt do not show up?

---

### Post by grahammechanical on 2012-05-05
I would not say - broken.

I notice this

> mkdir ~/tmp

Did you allow "Unity" to update its database of folders?

You make a directory but the Dash database engine does not yet know it is there.

That is my explanation.

The Dash is designed to bring back what we recently opened. Perhaps you are expecting it to operate outside of its design parameters.

It is a bit late to start testing something that has been under development for more than a year.

If you truly are interested in Ubuntu/Unity work better than have a look at this link.

[http://unity.ubuntu.com/getinvolved/]("http://unity.ubuntu.com/getinvolved/")

and this

[http://unity.ubuntu.com/getinvolved/testing/]("http://unity.ubuntu.com/getinvolved/testing/")

Regards.

---

### Post by 8Kuula on 2012-05-05
I expect it to "search files & folders" like it says in search field.
Maybe it should be changed then to "search accessed files & folders" since it do not find, until user have found them first.

How long it takes to dash/unity database to find new directory? In home directory there is alot directories/files in home directory that have been in there since 28.04.2012, and dash do not find them.

How I can add in dash database directories so dash would find files/folders in them?

---

### Post by philinux on 2012-05-05
> **8Kuula said:**
> I expect it to "search files & folders" like it says in search field.
Maybe it should be changed then to "search accessed files & folders" since it do not find, until user have found them first.

How long it takes to dash/unity database to find new directory? In home directory there is alot directories/files in home directory that have been in there since 28.04.2012, and dash do not find them.

How I can add in dash database directories so dash would find files/folders in them?

You need to run ```
sudo updatedb
``` It will then show up.

I'm just trying to find out how often it runs automagically and thus how to increase it frequency.

I think it runs daily.

---

### Post by philinux on 2012-05-05
If you create a document normally e.g. via an app or right click create then it will show up in Dash without the need for updatedb.

---

### Post by Vaphell on 2012-05-05
> I expect it to "search files & folders" like it says in search field.

it's a tradeoff. Either you get not so current data instantly (stored in a database, refreshed from time to time) or you mow through your whole disk every time

try this
```
locate some_file
```
vs
```
find ~ -name '*some_file'
```

locate uses said db (i guess unity does the same under the hood) and you get results instantly while find physically goes into the every corner which means quite a lot of disk thrashing and much slower response. Users usually don't want that.

---

### Post by 8Kuula on 2012-05-05
> **philinux said:**
> You need to run ```
sudo updatedb
``` It will then show up.

I'm just trying to find out how often it runs automagically and thus how to increase it frequency.

I think it runs daily.

Nice, it runs daily, /etc/cron.daily/mlocate, or atleast looks like it is that. And yes testfile shows up after sudo updatedb :)

Need make it little more frequent. Hourly maybe is fine.

So I think this issue is solved. :)

Thanks ppl :)

---

### Post by philinux on 2012-05-05
> **8Kuula said:**
> Nice, it runs daily, /etc/cron.daily/mlocate, or atleast looks like it is that. And yes testfile shows up after sudo updatedb :)

Need make it little more frequent. Hourly maybe is fine.

So I think this issue is solved. :)

Thanks ppl :)

Post the fix to run it hourly. Cheers

---

### Post by 8Kuula on 2012-05-05
Just linked cron.daily one in cron.hourly.
cd /etc/cron.hourly
sudo ln -s ../cron.daily/mlocate

---

