---
title: "I may have to go back to Breezy"
date: 2006-06-11
forum: General Help
---

### Post by welders4linux on 2006-06-11
At first I thought 6.06 was good, however I have noticed
apps dissapearing from the toolbars.  I check and they are onboard, I cannot even tick them on the Alacarte Menu editor.

Ive tried to reinstall them, to no avail.

Some other apps were a breeze <smile> to install in the last version, this one I follow all the instructions and nothing...

---

### Post by mlind on 2006-06-11
I have used Dapper since early flights and never had a problem like that.
What apps are disappearing precisely?

---

### Post by Computeruser on 2006-06-11
I tried upgrading to Dapper direct from Breezy using the upgrade function. I certainly lost some settings (OK, I can redo those). But I have no X, so VMware Tools don't work, and that means the machine is entirely useless to me. I will try to get X going (I have no idea yet how to do that), but at this point I am about 30 minutes away from deleting Dapper and copying Breezy back. Maybe I need to download the CD's and start all over (bummer, since my Breezy machine is only a few months old). I like my OS's to run several years with no breakage and being up-to-date at the same time.

Hmm, suspicions confirmed. Most all of my menu choices have gone. I no longer even have an Update application. The only menu left in System was Nmap FE. Dapper was deleted.

---

### Post by taurus on 2006-06-11
[QUOTE=welders4linux]At first I thought 6.06 was good, however I have noticed
apps dissapearing from the toolbars.  I check and they are onboard, I cannot even tick them on the Alacarte Menu editor.

Ive tried to reinstall them, to no avail.

Some other apps were a breeze <smile> to install in the last version, this one I follow all the instructions and nothing...[/QUOTE]
Did you upgrade from Breezy to Dapper or did you do a fresh install of Dapper?

---

### Post by mlind on 2006-06-11
If you upgraded, those problems are usually caused by some virtual package missing, like ubuntu-desktop or ubuntu-base.

---

### Post by adssse on 2006-06-11
I had a few problems when upgrading from breezy, such as open office being removed. But I was able to reinstall that without much difficulty.

---

### Post by welders4linux on 2006-06-12
Thanks to all who replied to this post.

Looks as if people are having different issues.  Ive tweaked a few things now.

My biggest problem (that Im aware of) is I cannot get my debian menu back.
Ive tried the instructions here:  [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

But its not working, I see Debian in the a la carte menu but I cannot <tick> select it.

cheers

---

### Post by Computeruser on 2006-06-14
I set up a new Dapper machine from scratch from the downloaded install CD. I set up root so I can log into it (sometimes I need to work there) and just like the upgrade, there are no useful menus in the System menu. No upgrades, no synaptic package manager - nothing useful at all.

Was root deliberately crippled? Or is there a way to bring the standard menus back? 

So far Dapper is a disappointed and I am still using Breezy.

---

### Post by scxtt on 2006-06-14
as far as i can tell, when a box predominately wants you to use sudo access to do "root" tasks (as ubuntu does) creating a root login to use graphically probably isn't going to contain the same configs that a normal user would ... how did you "set up root"?  and if you did it through "adduser" (or the gui) how does your /home/$user compare to /root?

---

### Post by mlind on 2006-06-15
[QUOTE=Computeruser]I set up a new Dapper machine from scratch from the downloaded install CD. I set up root so I can log into it (sometimes I need to work there) and just like the upgrade, there are no useful menus in the System menu. No upgrades, no synaptic package manager - nothing useful at all.

Was root deliberately crippled? Or is there a way to bring the standard menus back? 

So far Dapper is a disappointed and I am still using Breezy.[/QUOTE]

I'm not sure, but I think you must assign root user to necessary groups so you can
gain access to certain (desktop) resources. Just type 'groups' as normal user and assign root
to those groups too. Why would you login on desktop as root anyway?

---

### Post by Computeruser on 2006-06-15
[QUOTE=mlind]I'm not sure, but I think you must assign root user to necessary groups so you can
gain access to certain (desktop) resources. Just type 'groups' as normal user and assign root
to those groups too. Why would you login on desktop as root anyway?[/QUOTE]

I need to login as root in order to install VMware Tools. It won't work in the normal user (even if I su first). There are enough install steps that the Tools install loses the fact that it was once root (via su). 

I merely enabled the local administrator to log in to the GUI and logged it. This is what I did with Breezy, but it doesn't work with Dapper. 

Then, finally (for me), having installed the Tools, they don't work properly in Dapper and (again for me), without menu choices in the System tab, it is very difficult to manage.

---

### Post by mlind on 2006-06-15
[QUOTE=Computeruser]I need to login as root in order to install VMware Tools. It won't work in the normal user (even if I su first). There are enough install steps that the Tools install loses the fact that it was once root (via su). 

I merely enabled the local administrator to log in to the GUI and logged it. This is what I did with Breezy, but it doesn't work with Dapper. 

Then, finally (for me), having installed the Tools, they don't work properly in Dapper and (again for me), without menu choices in the System tab, it is very difficult to manage.[/QUOTE]

So, did you try to put root user in groups
adm dialout fax cdrom floppy tape audio dip video plugdev lpadmin scanner admin

?

---

### Post by Computeruser on 2006-06-15
I went to the Properties of 'root' in Users and Groups, and under User Priveleges, I checked off all the items. That has brought back a large number of menu items to the 'root' user. I guess that may have the default in Breezy because I didn't have to do it there. 

Now, if I can only get VMware Tools to work. I added all the source, headers and compiler. The Tools install, but the install is not complete (says it cannot find X installed), and they don't run at startup as they are supposed to. 

Still, I am making progress, and a clean install was clearly better than an upgrade.

---

### Post by eth on 2006-06-15
To activate **root** superuser instead of using the silly **sudo** every single line you type you've got two options:

. install fresh ubuntu in **expert** mode, that asks you if you want to activate a **root** user: this way your usual working account isn't a sudoer
. if you installed in a standard way, your account IS sudoer, so pick a console and type:

**sudo passwd root**

he'll ask you for YOUR password first, then he will ask you to enter a UNIX password, and there you put your root pwd. 2 times, of course.
Here you are your root s.u. account: type **su** to test and enjoy your Ubuntu-Debian-Way

---

