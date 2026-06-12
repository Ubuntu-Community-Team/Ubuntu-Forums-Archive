---
title: "can not add facebook to gwibber"
date: 2010-06-10
forum: General Help
---

### Post by rudysuryanto on 2010-06-10
I can not add facebook to gwibber, help.:p

---

### Post by x-shaney-x on 2010-06-10
Is it not appearing or not connecting?  Any errors?

Speaking personally, I would forget gwibber altogether.
I have found it one of the worst and buggiest apps I have ever used.

Having tried it on ubuntu, mint, PCLinuxOS, Mandriva, openSUSE and Fedora 13, it hasn't worked properly on ANY of them.

Even if you do get it working there will be no notifications so you will need it open to see any changes.
May as well have a tab open in a browser or use prism-facebook.

---

### Post by rudysuryanto on 2010-06-10
First I click add facebook, then click authorize, I login to my facebook account, but then facebook did not added at the left column.

---

### Post by aaaantoine on 2010-06-11
I have the same problem.

---

### Post by avaughan585 on 2010-06-14
ok, I had the same problem but I managed to fix it.
First I went into Synaptic package manager and did a complete removal on gwibber, gwibber-service and gwibber-themes.

Then at the terminal I entered the following command:
```
ls -aR ~ | grep "gwibber"
```This gives me a list of everything in my home directory associated with gwibber, which looks something like this:


```
$ ls -aR ~ | grep "gwibber"
gwibber
~/.gconf/apps/gwibber:
~/.gconf/apps/gwibber/client:
gwibber_accounts.couch
 .gwibber_accounts_design
gwibber_messages.couch
.gwibber_messages_design
gwibber_preferences.couch
.gwibber_preferences_design
~/.local/share/desktop-couch/.gwibber_accounts_design:
~/.local/share/desktop-couch/.gwibber_messages_design:
~/.local/share/desktop-couch/.gwibber_preferences_design:

```From this, I ascertained the location of gwibber's config files associated with my user account. I suspected that it was the ~/.gconf/apps/gwibber directory which might be holding a corrupted config file so I proceeded to delete that one.

Then I reinstalled gwibber and it seemed to work again; I successfully added my Facebook account to gwibber.

Hope this helps.

---

### Post by avaughan585 on 2010-06-17
ok now the problem has reoccurred for me.  I tried my previous solution which I posted above, but it did not work this time. 

Does anyone out there have any ideas?  Or is it just that gwibber is completely hopelessly useless?  I might go with the advice of the first poster and just not use it at all until a decent release comes out.

---

### Post by SushiR on 2010-06-17
Have a look at /etc/hosts. The first part should look like this:
> 127.0.0.1       localhost
127.0.0.1       YOURHOSTNAME

If it doesn't, open /etc/hosts via ```
gksu gedit /etc/hosts
``` and change it. Then try again with gwibber.

---

### Post by x-shaney-x on 2010-06-17
> **SushiR said:**
> Have a look at /etc/hosts. The first part should look like this:

Could you expand on this?
My /etc/hosts is like this: ```
127.0.0.1    localhost
127.0.1.1    MYHOSTNAME
```
It's like that on both my ubuntu installs.

---

### Post by SushiR on 2010-06-18
> **x-shaney-x said:**
> Could you expand on this?
My /etc/hosts is like this: ```
127.0.0.1    localhost
127.0.**1.**1    MYHOSTNAME
```
It's like that on both my ubuntu installs.

Do you see the difference?

It should be
```
127.0.0.1    localhost
127.0.**0.**1    MYHOSTNAME
```

---

### Post by x-shaney-x on 2010-06-18
> **SushiR said:**
> Do you see the difference?

Indeed I did. That is why I asked you to expand :)
I mean if it is meant to be the same address for both lines why is the second line that way by default?
Also, how might changing this affect other things?
As it happens, I don't have any problems connecting to facebook with gwibber with my /etc/hosts the way it is.
Only problem I have with gwibber is that it's rubbish.

---

### Post by bgryderclock on 2010-06-24
avaughan585's and SushiR's suggestions worked for me.

---

### Post by luttman on 2010-06-30
Hi there i have done both of the "helps" without any results.
Here is a picture of my problem
i got no add button

[img]http://data.fuskbugg.se/skalman01/gwibber.png[/img]

---

### Post by hobbsc on 2010-07-05
I'm having the same problem.  I don't have an "add" button.

---

### Post by peejay1977 on 2010-10-18
Hi all,

I'm using Ubuntu 10.10 (Maverick) and am having this same issue, I tried removing and reinstalling as per the original mentions but this didn't work, also the hosts file was fine.

What did work for me was renaming the following file :

```
/home/pj/.gconf/apps/gwibber/preferences/%gconf.xml
```

Obviously in this case "pj" is the name of my user account. If you don't do it from a command line you will need to enable hidden files in the file browser.

Before renaming it the file was 110bytes as I had managed to add my Twitter account fine. After renaming it though the Twitter account has remained intact but it let me add the Facebook account as well. The new file is 667bytes.

Both accounts seem to work fine so on my machine at least this is sorted. Hope this might work for others.

Paul.

---

### Post by mozi on 2010-10-18
please login with your nick on the facebook page and in the same time in gwibber (also with nick instead of email) should work :)

---

### Post by gunashekar on 2010-10-29
> **mozi said:**
> please login with your nick on the facebook page and in the same time in gwibber (also with nick instead of email) should work :)

Thank you Mozi. This worked finally!

---

### Post by x-shaney-x on 2010-10-30
> **mozi said:**
> please login with your nick on the facebook page and in the same time in gwibber (also with nick instead of email) should work :)

Does that not make gwibber completely pointless though?
If you are going to login via a browser may as well just keep it open or a tab open on facebook and bypass gwibber altogether?

Or even just use prism as a lighter option to having a full browser open.

---

