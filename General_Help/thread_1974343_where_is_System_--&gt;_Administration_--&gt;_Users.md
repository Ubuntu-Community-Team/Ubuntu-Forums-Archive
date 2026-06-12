---
title: "where is System --&gt; Administration --&gt; Users and Groups in Unity"
date: 2012-05-05
forum: General Help
---

### Post by jlh68 on 2012-05-05
I need to find > System --> Administration --> Users and Groups in Unity (12.04LTS)

In fact I would like to find all those old menus.

---

### Post by anejo on 2012-05-06
```
sudo apt-get install gnome-system-tools
```

---

### Post by shashanksingh on 2012-05-06
Are you looking for 
Dash->Applicatons->System Settings->User Accounts ?

---

### Post by bogan on 2012-05-06
Hi!, **jih68**.

If you install the '**ClassicMenuIndicator**' you can have all the traditional Menus, only slightly re-arranged - Preferences and Administration are at the bottom of Applications.

It runs equally well with Ubuntu 2 & 3D, Gnome Classic or Classic with no effects, from an Icon installed in the top bar.

Chao!, **bogan**.

---

### Post by jlh68 on 2012-05-09
Where do I find **ClassicMenuIndicator**?  I tried the Ubuntu software Center, Synaptic and apt-get.

---

### Post by jerome1232 on 2012-05-09
Just click on the cog on the right, System Settings, User Accounts.

See, that wasn't hard.

---

### Post by fballem on 2012-05-09
The problem with the User Accounts is that you cannot administer groups. You need to install the gnome-system-tools in order to be able to administer groups.

---

### Post by jerome1232 on 2012-05-09
> **fballem said:**
> The problem with the User Accounts is that you cannot administer groups. You need to install the gnome-system-tools in order to be able to administer groups.

Ah, good point, and somehow I never actually read the title, just the OP and posts. So I thought the OP's beef was with the new menu arrangements.

Silly me.

---

### Post by bogan on 2012-05-10
Hi!,** jih68,**

You Posted: > Where do I find **ClassicMenuIndicator**?  I tried the Ubuntu software Center, Synaptic and apt-get.Ever heard of "GOOGLE"?? or the Forum 'Search' function.??

Try this one:[http://www.liberiangeek.net/2012/05/install-classic-menu-indicator-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/05/install-classic-menu-indicator-in-ubuntu-12-04-precise-pangolin/)

Chao!,** bogan.**

---

### Post by zombifier25 on 2012-05-10
> **bogan said:**
> Hi!,** jih68,**

You Posted: Ever heard of "GOOGLE"?? or the Forum 'Search' function.??

Try this one:[http://www.liberiangeek.net/2012/05/install-classic-menu-indicator-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/05/install-classic-menu-indicator-in-ubuntu-12-04-precise-pangolin/)

Chao!,** bogan.**
That still wouldn't solve his problem. Ubuntu 12.04's User Manager removed the ability to manage groups. Install gnome-system-tools to have that functionality.

---

### Post by kurt18947 on 2012-05-10
> **zombifier25 said:**
> That still wouldn't solve his problem. Ubuntu 12.04's User Manager removed the ability to manage groups. Install gnome-system-tools to have that functionality.

Correct.  Part of my "after installing 12.04" checklist.  Also create a desktop launcher  for the old style printer configuration app.

---

### Post by bogan on 2012-05-10
**Hi!**,

Just Posted: > That still wouldn't solve his problem.I was not offering a solution to his problem: rather directly answering his query.

Chao!, **bogan.**

---

### Post by grashdur on 2012-06-04
I was also looking for a way to manage groups, but wasn't sure whether installing the gnome thing would mess up my Unity interface. So I found the app KUser in the Software Center. It can administer both users and groups. Once I saw who's in which group, I ended up not making changes to any groups after all.

---

### Post by Easy Limits on 2012-06-04
This feature would have been a good one to leave in 12.04.

---

### Post by jlh68 on 2012-06-06
I found IT.  Using the Unity, click on the Dash Ubuntu icon.  Then click the three bars at the botom of the page, which will bring up ALL the applications.  Look for "Main Menu"  that will show the standard main menu set up.  That might help.

---

### Post by sdowney717 on 2013-02-01
just run 
"users-admin"

---

