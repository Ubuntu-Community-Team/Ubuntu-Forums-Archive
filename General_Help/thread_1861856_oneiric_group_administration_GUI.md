---
title: "oneiric group administration GUI"
date: 2011-10-16
forum: General Help
---

### Post by MartinusEx on 2011-10-16
Hi Folks,

I just upgraded from 10.10 to 11.10.
I have several issues but the most disturbing currently is the user and group administration.

I'm not used to admin groups from the terminal (somewhat lazy :) )
So I looked for the "Group" button in the "User"-Admin Window, but there is none..
System settings only lead to user admin, no group admin to bie found.

Who can tell me how to admin groups in oneiric using unity.


THX

Martin

---

### Post by bauwan on 2011-10-16
I'm having the same problem and question! Created a new user on 11.10 and attached USB-hdd is not shown. I guess it is something with the groups the new user isnt member of.

---

### Post by bloodorange on 2011-10-16
You could install "gnome-system-tools".  This will give you access to the old "Users and Groups".

---

### Post by Derek Karpinski on 2011-10-17
Should we really have to?  Ironically, in striving for an easier to use system, you have to google for 30 minutes to find the missing users and groups settings menu, you either end up doing it in terminal, or installing a package to do what used to be there OOTB.

To make matters worse, after you install this package, it still won't show up in the settings menu.

And CCSM doesn't show up in the settings menu either.  I don't know if these are bugs, or they will be fixed, but it seems like a regression of usability to me......

---

### Post by MartinusEx on 2011-10-17
@Bloodorange:
THX :)
Will try tonight.
As it reads, (hopefully)these are all the system  tools I knew from 10.10?
I will report back if so.


I was also looking for the utility to admin harddisks (gome-disk-utility) which IS installed.
If you do not know the wonderfull name "Palimpsest" (see Wikipedia for the historic background of this name :) ) you might not find it in the "Dash".
Like Derek stated it's nowhere hooked to (used to be in the "systems menu") and the new systems menue GUI does not show half of all necessary tools.

@Derek: 
In terms of discussing oneirics usability:
It reminds me a bit of Windows Vista Home;
An OS for Dummies with all the importand things hidden so far
away, no one can do any harm.

I really think about changing to a different LINUX distro.
Don't need no MS LINUX. Lets see where this leads to. 12.04 is coming and I'll give Mark a chance to show that he knows better.

I will state further findings besides the "group admin GUI" in the sticky thread re onerirc bugs


THX so far @ all

Martin

---

### Post by MartinusEx on 2011-10-20
Folks,

i installed the gnome-system-tools and the user and group daministration was available

THX a lot

Only trade of is:
All these programs have been available from the systems menu in 10.10 and one has to find out the names of the programs to look the up in the dash.

Martin

---

### Post by antojk on 2011-12-04
Ubuntu's usability is going down the drain. I mean why should they remove essential functionality like full desktop configuration support, users/group admin etc..

I mean Unity is the most horrible, partially complete solution they are ditching on the head of users. Its integration with Compiz is the most half - hearted solution that has come out of Canonical till now.. The CCSM manager was not designed for this kind of abuse..

How do they differ from M'soft if this is their approach and attitude? Looks like Mark is yearning to join the Bill gates camp, this time on the back of open source devs. How can they justify their human theme?

Open source or not, usability cannot be argued away.. 
No way to admin services other than to use the cli.
No way to add and set user rights and access levels other than to revert back to old well tested tools


Sorry I have to flame..

The boot speeds are going back to the pre-natty days.
A decent UI for OS level functionality is the least they are expected to do.. Thinking seriously of falling back to Debian Squeeze.. Atleast they have no pretension of usable computing and  you get a well footed repo system at no cost.

To prove a point, I just booted my old centrino lappy with ubuntu 9.10 and was productive to the boot. Felt faster than my current 4core Ubuntu setup. and I feel saddened by the direction Ubuntu is taking now..

---

### Post by AbdRahim on 2011-12-13
I agree. Every new task that used to be simple in previous versions now takes me a half hour to several days to find out how to accomplish. This is terrible!!

---

### Post by LewisTM on 2011-12-13
For administration, nothing beats [Webmin]("http://www.webmin.com").

If you want a sane, fast desktop and still stay in the game, Xfce/Xubuntu should fit the bill and then some.

Just my 2¢

---

### Post by xadder on 2011-12-16
Thanks for the gnome-setup-tools tip. Solved my problem after I also wasted half an hour.

---

