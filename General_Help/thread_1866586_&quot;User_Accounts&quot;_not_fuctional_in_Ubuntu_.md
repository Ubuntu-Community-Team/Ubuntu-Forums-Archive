---
title: "&quot;User Accounts&quot; not fuctional in Ubuntu 11.10"
date: 2011-10-21
forum: General Help
---

### Post by linuxinstalledfromhdd on 2011-10-21
Hey everyone. I just did the latest rounds of updates on my Ubuntu 11.10 system and I noticed that today "User Accounts" on the upper right hand corner of Unity is no longer working or fuctional. I switched to Gnome 3, and tried again, and it appears as if the application was going to run but closed. No crash notice either. It just disappeared.  Anyone else having trouble using "User Accounts" in Ubuntu 11.10 today???:(

As of right now I can't change my user. Any suggestions???

---

### Post by linuxinstalledfromhdd on 2011-10-21
BUMP BUMP BUMP

Can someone else please confirm that this is happening with their 11.10 after today's updates please besides myself???  Thank you:p

---

### Post by linuxinstalledfromhdd on 2011-10-21
Does anyone else have this issue after the latest updates this afternoon???  

It only takes 2 seconds for someone with an updated 11.10 (as of right now) to check this for me so I can know if it is my system, or a bug with User Accounts package.

---

### Post by Larkspur on 2011-10-21
I'm up to date and can open User Accounts.

---

### Post by haqking on 2011-10-21
yes it works fine

see attached

---

### Post by figure002 on 2011-10-21
I recently did a clean install of Ubuntu 11.10, and User Accounts doesn't work for me either. Exact same problem as the topic starter. If someone could give me the command to start this from the command line, then maybe I can find an error message.

If more people are having this issue, then someone should probably make a bug report.

---

### Post by crdlb on 2011-10-21
> **figure002 said:**
> If someone could give me the command to start this from the command line, then maybe I can find an error message.

```
gnome-control-center user-accounts
```

---

### Post by BBUCommander on 2011-10-21
> **crdlb said:**
> ```
gnome-control-center user-accounts
```

I am having the same trouble and the response to running the command in terminal is:

Segmentation fault

---

### Post by BBUCommander on 2011-10-22
This may be the buggiest release I have experienced since 8.10.  Where should I lodge the bug report?

After running gnome-control-panel -v and clicking on user accounts I received the following output:


** (gnome-control-center:5433): DEBUG: Enabling debugging
(gnome-control-center:5433): user-accounts-cc-panel-DEBUG: calling 'ListCachedUsers'
(gnome-control-center:5433): user-accounts-cc-panel-DEBUG: unhandled property XSession
(gnome-control-center:5433): user-accounts-cc-panel-DEBUG: Got 1 users

(gnome-control-center:5433): user-accounts-cc-panel-DEBUG: adding user User

(gnome-control-center:5433): user-accounts-cc-panel-DEBUG: user added: 1000 User

(gnome-control-center:5433): common-cc-panel-DEBUG: Ignoring 'zh_SG.utf8' as a locale, since it lacks translations
Segmentation fault

---

### Post by BBUCommander on 2011-10-22
The problem is solved in the next version of gnome-control-panel.  If you cannot wait for the update, you can download the new packages (verison 3.2.1) at the following URLs.  Note that you must install the packages in the following order: gnome-control-center-data, gnome-control-center1, gnome-control-center

Mind that gnome-control-center1 and gnome-control-center are NOT the same package and that both are needed.

[gnome-control-center-data]("https://launchpad.net/ubuntu/oneiric/amd64/gnome-control-center-data/1:3.2.1-0ubuntu1")

[gnome-control-center]("https://launchpad.net/ubuntu/+source/gnome-control-center/1:3.2.1-0ubuntu1/+build/2862831")

---

### Post by crdlb on 2011-10-22
Or just install it from oneiric-proposed: [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

Those links are for amd64 only, btw.

---

### Post by BBUCommander on 2011-10-22
Cool!  I didn't know about *-proposed.  I particularly like the ability to simply type:

sudo aptitude install packagename/natty-proposed

...and voila, upgrade to a proposed version!  

For anyone who wants to try this way of testing proposed packages, make sure you read the instructions about creating the preferences file to prevent Update Manager from trying to upgrade all your packages to proposed.

---

### Post by figure002 on 2011-10-23
> **BBUCommander said:**
> The problem is solved in the next version of gnome-control-panel.

Confirmed. I just enabled the repository for proposed, upgraded to version 3.2.1, and the problem is fixed. Thanks for the info guys!

I guess this thread can be marked "solved" now.

---

### Post by edkmho on 2011-11-06
hey guys,

I am up-date with v3.2.1 but still could not get "User Account" to work. Please help. 

Thanks.

---

