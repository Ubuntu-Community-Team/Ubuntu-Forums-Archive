---
title: "DSL Internet connection problem in Ubuntu 9.10"
date: 2009-11-18
forum: General Help
---

### Post by chrislionheart on 2009-11-18
[CENTER][SIZE=4][COLOR=Sienna]Getting problems in connecting to the internet in Ubuntu 9.10[/COLOR]

[/SIZE][LEFT]I just got a clean installation done of the latest Ubuntu 9.10 Karmic Kaola -- But after the new installation, when I tried connecting to the Internet,,, it just didn't work.

I mean that I went to the 'Edit connections' option, went to the 'DSL' tab, and then created a new connection. Then later when I tried connecting to the Internet, it just doesn't get connected, it always keeps telling that 'Internet disconnected'. 

I never had this problem in the 9.04 version. Everything went good in that version, I got this problem only in 9.10. 

A buddy from the forums told me that there was a bug in the newer Network Manager of 9.10. So he gave me his older Network Manager files. 

But they weren't getting installed, since the newer version was already installed, so I uninstalled the newer Network Manager and tried installing the files that he gave me. But I still got problems, they again didn't get installed. 

Now I don't have any Network Manager in my computer, since I uninstalled the Manager and the other files that he gave didn't get installed. I got a lot of problems..... 
[SIZE=4]**[FONT=Trebuchet MS][COLOR=Red]Please Help me!!!!![/COLOR][/FONT]** [/SIZE] 

Here are the screen-shots below of when I was trying to install the new files that I got from a buddy on the forum....

[IMG]http://cosmicmarshall.com/Screenshot1.png[/IMG]

[IMG]http://cosmicmarshall.com/Screenshot2.png[/IMG]

**[SIZE=5]Please help me out!!![/SIZE]** 
[/LEFT]
[/CENTER]

---

### Post by AlexZaim on 2009-11-19
Other than this : [http://ubuntuforums.org/showthread.php?t=1330641](http://ubuntuforums.org/showthread.php?t=1330641)
Can't help you with anything. The link is my problem (similar).

---

### Post by ashwindatye on 2009-11-30
Same problem on my acer 6930. I was trying it on live CD. I hope there is a fix for this soon. I was really excited about Karmic but cant use it :-(

---

### Post by jamesisin on 2009-11-30
Please don't post huge images in your threads; it makes it difficult to read your posts because the images torque the page formatting.

The easiest way to attach an image is to use the attach button (the paperclip) in the editing window (it's just to the right of the smiley face).  The site will then create thumbnails for your images, your pages will load faster, and your formatting will be correct.

---

### Post by ssj6akshat on 2009-11-30
Alternate Method:Via the Command Line
Just Type 
$ sudo pppoeconf

---

### Post by 71GA on 2009-12-07
ssj6akshat i used same command, and my DSL connection is working flawlesly.... but because of this sudo pppoe comand my Wireless (secure 802.1x connection) istnt working anymore. 
 
Anyone has an idea how can i enable my Wireless (secure 802.1x connection) again?:popcorn:

---

### Post by jamesisin on 2009-12-07
What happens when you attempt to connect to your wireless?

---

### Post by 71GA on 2009-12-08
Well... nothing .... but if i right click on Network manager taskbar icon it says "Device not managed" under Network. And i have no connections listed there... so i cannt connect any :)
 
Is there any way to start Wired conection out of a terminal?

---

### Post by jamesisin on 2009-12-08
If you right-click on the Network Manager icon (in the notification area) can you confirm that it shows a check before "Networking Enabled"?

This sounds like a very different issue if you are not showing any network devices at all.  You should be able to choose "Edit Connections..." from the right-click menu and make several changes and additions.  For instance, you should be able to edit your wired connection here.

I'm not familiar with that command and the man page is a bit sparse, so I'm afraid I can't offer much advice relating to that.  However, the man page suggests that after you run pppoeconf there will be a dialog.  Do you have the text of that dialog available?

Finally, you may want to try (if you haven't already) unplugging your network cable to see if the wireless kicks itself into action.

---

