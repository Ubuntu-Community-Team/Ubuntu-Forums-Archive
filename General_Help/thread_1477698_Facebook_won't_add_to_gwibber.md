---
title: "Facebook won't add to gwibber"
date: 2010-05-09
forum: General Help
---

### Post by joe&amp;nidhi on 2010-05-09
I am having a problem getting my facebook account to add to gwibber. I have searched the forum for the last couple of days and found several others with an identical problem but to date no solution is offered other than keep trying.

I have run gwibber in terminal and attempted to add the account. Below is the output. For information I am trying to add an existing account not create a new account.

Thanks for any help offered.

joe@Joe-nidhi:~$ gwibber

** (gwibber:1986): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:1986): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:1986): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Updating...
Updating...

** (gwibber-accounts:2022): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber-accounts:2022): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber-accounts:2022): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Updating...
Saving...
Could not identify preference: username
Could not identify preference: session_key
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/accounts.py", line 184, in on_edit_account_save
    self.get_account_data()
  File "/usr/lib/python2.6/dist-packages/gwibber/accounts.py", line 353, in get_account_data
    aId = "%s-%s" % (self.account["protocol"], self.account["username"])
KeyError: 'username'

---

### Post by joe&amp;nidhi on 2010-05-10
anyone out there willing to help

---

### Post by mahela007 on 2010-05-10
I have the same problem.

---

### Post by derrick81787 on 2010-05-15
I have the same problem, too.  I'm still looking for a solution.

- Derrick

---

### Post by torrentialrain3 on 2010-05-18
Also having this issue. Any help?

---

### Post by mahela007 on 2010-05-19
The issue seems to have worked itself out on my PC.. I didn't do anything to fix this.. weird.

---

### Post by JAPHacake on 2010-05-25
Same problem here....and with my twitter account, no errors, just simply doesn't do anything.

It seems a bug report has been made for this and a work around suggested open DNS has worked for some people, although not me :(

Worth a try though...

```
$ sudo apt-get install bind9
```

Then follow instructions here.. [https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/571858/comments/10](https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/571858/comments/10)

---

### Post by meldroc on 2010-05-27
Having problems too - Facebook stopped updating on Gwibber yesterday.

---

### Post by tamias on 2010-05-29
Try the fix at [https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/552227/comments/70](https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/552227/comments/70) -- it worked for me and allowed me to add the Facebook account, as Gwibber was not waiting long enough for Facebook to respond each time. Increasing the timeouts means Gwibber waits long enough for Facebook to respond.

However I'm still not getting anything actually showing in the Gwibber main window... but that's another story.

---

### Post by t3h_g3n3r4l on 2010-05-31
> **tamias said:**
> Try the fix at [https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/552227/comments/70](https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/552227/comments/70) -- it worked for me and allowed me to add the Facebook account, as Gwibber was not waiting long enough for Facebook to respond each time. Increasing the timeouts means Gwibber waits long enough for Facebook to respond.

However I'm still not getting anything actually showing in the Gwibber main window... but that's another story.

I did the change mentioned in the bug comment and was then able to get my facebook account working.  I only set my timeouts to 30 seconds each, however.

---

### Post by joe&amp;nidhi on 2010-06-01
Something interesting happened to my gwibber. It goes like this.
I was playing around with some settings in grub to try and resolve the issue with Plymouth and the proprietary drivers for Nvidia and managed to break my grub. Sorry but I keep having these illusions that I am a Linux expert when at best I am a well meaning amateur.

Anyway I took an image of my system using Umarks (congratulations to Lovinglinux for this a brilliant add on that saves a lot of heartache) , backed up my home folder before restarting and as expected grub wouldn't load. 

I set about reinstalling Ubuntu. However on this occasion I used the DVD I got with Ubuntu User magazine instead of the original iso image I downloaded from the internet.
Anyway after the process was finished suddenly I can easily get my facebook profile to load into gwibber without any tweaking.

I can only assume the original iso image downloaded from the ubuntu website had a bug in it. As usual after burning onto a CD I did a MD5 check and this was OK but issues with gwibber that did not occur using the DVD from Ubuntu User.

Maybe someone in the know can shed light on this.

Anyway now I only need to do something about Plymouth but this is another issue.

---

### Post by aaqiln on 2010-06-09
fb on gwibber worked perfectly on my lucid, until i re-installed  lucid....:p so i knew it wasn't lucid...hehehe all i did was remove  gwibber, reinstalled it, n installed some gtk libs something on the line of libgtkmm i guess n all dependencies n  voila. it worked again!!!! hope it helps....:-)

---

### Post by rudysuryanto on 2010-06-11
I have the same problem too, can not add facebook to Gwibber since I reinstall ubuntu use remastersys, but at first installation I can add facebook to Gwibber. Now I reinstall ubuntu use original live CD. But still can not add facebook to Gwibber, I will try the above explanation. Thank's.

---

### Post by calexbg on 2010-06-26
I had the same problem and increasing the timeouts for facebook at /usr/share/pyshared/gwibber/microblog/util/facelib.py worked like a charm.

---

### Post by vsh3r on 2010-11-01
I noticed with a recent update manager run that Gwibber was updated.  However, this still doesn't fix the problem.  I looked at my facelib.py file and I noticed that someone removed the code for 
         c.setopt(pycurl.CONNECTTIMEOUT, 80)
Is there a reason this is removed... It might be a mistake?


I still have the problem even after using the new TIMEOUT settings.



V$H.
:(

---

### Post by vsh3r on 2010-11-01
SOLUTION: gksu gedit /usr/share/pyshared/gwibber/microblog/util/facelib.py

ADD: just after c.setopt(pycurl.TIMEOUT, 150) ADD the following...
c.setopt(pycurl.CONNECTTIMEOUT, 80)

Works now... 

V$H.

:KS

---

### Post by derrick81787 on 2010-11-02
> **vsh3r said:**
> SOLUTION: gksu gedit /usr/share/pyshared/gwibber/microblog/util/facelib.py

ADD: just after c.setopt(pycurl.TIMEOUT, 150) ADD the following...
c.setopt(pycurl.CONNECTTIMEOUT, 80)

Works now... 

V$H.

:KS

I'm glad to hear that.  I was just about to post that I never did get it to work in Lucid but that it worked in Maverick right out of the box.  I did a clean install though.  I don't know what happens if you just upgrade.

---

### Post by ConchX on 2012-02-07
Sorry to bump the thread guys, but in case anyone is having problems with Gwibber, this is how I fixed it in 11.10.

> sudo mv /usr/share/pyshared/gwibber/microblog/util/facelib.py /usr/share/pyshared/gwibber/microblog/util/facelib.py.BAK

Makes a backup of the Facebook account Python thingy.

Then..
> sudo apt-get purge gwibber gwibber-service
Then..
> sudo apt-get install gwibber
This will install gwibber again, gwibber-service and all the other gwibber stuff.

Works for me 100% :popcorn:

---

