---
title: "remastersys restore - How to do it?"
date: 2010-06-26
forum: General Help
---

### Post by arapaho on 2010-06-26
I have remastersys backup on DVD but I have no idea how to restore. There is install option when I boot from DVD but it doesn't install anything to hard drive. It looks as if my system was loaded to memory or was run as LiveCD. In Nautilus I can see my original root and home partitions (I mean these on hard drive) as separate drives, not partitions.
On remastersys website I didn't find any information.

---

### Post by realzippy on 2010-06-26
yep,remastersys seems to be broken since Lucid...

---

### Post by giddyup306 on 2010-07-06
I know this post is a week old, but I am looking for the answer as well.  I've been searching all afternoon for a way to fix this. I've been searching Google, Ubuntu Forums and I even subscribed to the remastersys forums.  I was going to break down and ask a question, however it turns out that unless I pay $50 USD (well he'd settle for $25) he won't help with any distro copies.  

> If you want support for remastersys dist mode you will need to become a  special member.

To become a special member, just donate $50US  from my website and provide me with your username on the forum here in  the paypal info before you submit the payment.  This will give you 1  year of access to the Priority Distribution Mode Support area that is  not available to any other members except for paying Distribution Mode  members.

If you can only afford $25US then you will get 6 months  of support for questions related to the dist mode and have full access  to the area during that period of time.

This ensures that I  continue to work on remastersys and gives you access to more information  and support for distribution mode.

I have in no way crippled  remastersys or have any plans on crippling it and want to make that very  clear.

The subscription mentioned above is only for access to  the dist mode support area.  All dist mode questions will be answered  regardless of how simple or complicated.

If you can't afford  either but would still like access please PM me and we can discuss it. 

I can't afford it, nor am I going to PM him.

When someone else asked him about it here's what he posted...

> Godaddy was hacked.  I wasn't hacked personally.

In reality, if  you want to create a distro and had the necessary skills you really  wouldn't need to ask something so basic.

With that comment you  don't need to come back here at all.  Good luck.

If you want  support from Ubuntu, you have to pay for it.
If you want support from  Mandriva, you have to pay for it.
If you want support from Redhat,  you have to pay for it.

See the pattern.

If you want me to  continue releasing my work you'll help me continue it.  If not, no big  deal.  I'm only asking for dedicated support from those that are using  remastersys to create their own distro.  If you feel this is unfair then  please feel free to create your own backup tool, support it, etc.

That's not the Linux or Ubuntu spirit.  [-X

---

### Post by arapaho on 2010-07-30
Finally I discovered simple solution. You mast have ubiquity and  ubiquity-frontend-gtk or ubiquity-frontend-kde installed, depending on your desktop environment. When you boot from remastersys backup dvd it really doesn't matter whether you chose install or run as LiveCd because both these options works the same. That is a bug of the install option of remastersys, I suppose . Anyway, after you run it go to menu -> administration (or wherever you have it) and chose install (I have Install linux mint). It is the installer that you already know from installation livecd. It allows you to install your backup the same way as a clean liveCd.

---

### Post by giddyup306 on 2010-07-31
> **arapaho said:**
> Finally I discovered simple solution. You mast have ubiquity and  ubiquity-frontend-gtk or ubiquity-frontend-kde installed, depending on your desktop environment. When you boot from remastersys backup dvd it really doesn't matter whether you chose install or run as LiveCd because both these options works the same. That is a bug of the install option of remastersys, I suppose . Anyway, after you run it go to menu -> administration (or wherever you have it) and chose install (I have Install linux mint). It is the installer that you already know from installation livecd. It allows you to install your backup the same way as a clean liveCd.


Thanks for the update!  I've been searching for hours on how to get this program to work!  It turns out that I didn't have ubiquity-frontend-gtk installed in my system.  I just bought a new HD, and  literally in a few hours I will be needing to re-install Ubuntu.  This will save me countless hours of re-installing all the programs (and hopefully) tweaks that I spent months perfecting. 

Kudos!

---

### Post by arapaho on 2010-08-03
Nice to hear that it helped. 
The problem with remastersys is that it has image size limitations, which means your system cannot be larger than about 12GB (check on remastersys site). In that case, good solution for making a backup or move from one disk to another is to use partimage. It can be found on:
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
or with other useful disk maintenance tools on Parted magic, or Hiren's Boot CD iso's.
Partimage makes a compressed copy of partition, not a livecd. Personally I use it only to backup partition and save image on the same hard disk but on another partition. I didn't try to save it on DVD, but I guess it is possible.
Maybe it is not so convenient as remastersys livecd but much faster.
Just the second alternative option.

---

