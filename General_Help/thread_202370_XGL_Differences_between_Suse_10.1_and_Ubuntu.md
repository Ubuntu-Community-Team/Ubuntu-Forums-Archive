---
title: "XGL Differences between Suse 10.1 and Ubuntu"
date: 2006-06-23
forum: General Help
---

### Post by Devilotx on 2006-06-23
I run Suse 10.1 on my laptop and Ubuntu 6.06 on my desktop, now knowing XGL originated from Novell, I figured there would be some differences, but I was amazed at what really appears to be lacking in XGL on Ubuntu.

Things that seem to be missing in XGL on Ubuntu:

the "Page Peel" effect  when you grab the edge of the window and pull away, this effect shows whatever is beneath the window.  

The windows also bounce and flux as you expand them from a smaller window to a full screen window and vice versa.  This is difficult to explain, but the windows appear to explode or implode as you click.

Drag Transparency,  when you click the titlebar of 

a window, the window turns transparent as you move it around.

Rain Drops,  A key combo make it appear that your desktop is liquid and rain drops are causing ripple effects across your screen.  there is another command that lets the mouse pointer ripple across the screen with the same effect.

Are these available to put into Ubuntu? or is this a novell configuration?

in the flight stages of dapper, I had intended to put Dapper on my lappy to enjoy the XGL, but the missing effects are glaring to me, maybe it's a simple config change, but it's a big difference.

---

### Post by no1wantdthisname on 2006-06-23
All of those things have been there for a while now.  Which packages are you using?

---

### Post by nik on 2006-06-23
well, first this isn't xgl, but compiz... and I have the effects you mentioned. did you try QuinnStorm's compiz packages?

---

### Post by Devilotx on 2006-06-23
I just grabbed the ones from Apt, I didn't get any additional packages from anywhere...

I followed the guide that is here on these forums,  can you point me twords where I can get the updated packages?

*EDIT*

So I added the [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) stuff to my sources.list and did an apt-get upgrade and made sure to install compiz, compiz-gnome and compiz-kde

so far, it's looking good, but now the menu's are lacking that "pop" that they had before...where both the Gnome menu and the K-Menu would appear to "pop" onto the screen.

other then that, it looks good,  is there a configuration area where you can tweak things for XGL in Ubuntu? kinda like in Suse's Gnome Control Panel?

---

### Post by zitch on 2006-06-23
I've followed [this wiki](https://help.ubuntu.com/community/CompositeManager/Xgl) to get XGL/Compiz working on my laptop, and I have all of the effects that you've described available.  I'm using Quinn's repository ([http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) when you get to the second page of the above linked wiki).

---

### Post by nik on 2006-06-23
[QUOTE=Devilotx]
other then that, it looks good,  is there a configuration area where you can tweak things for XGL in Ubuntu? kinda like in Suse's Gnome Control Panel?[/QUOTE]
Did you get gset-compiz installed? Try running it... if not, you can use gconf-editor, but it's a bit hard to understand what everything does there...

---

