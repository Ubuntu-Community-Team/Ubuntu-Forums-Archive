---
title: "Managing PodCast Subscriptions With amarok"
date: 2006-01-25
forum: General Help
---

### Post by edwin11 on 2006-01-25
Hi all, i'm starting to use amarok to manage my podcast subscriptions, and having some difficulties and questions. Kindly advise, thanks very much!

1. As i'm using GNOME, i do not have kMail installed (use Thunderbird). At times, amarok tries to launch kMail. e.g. i subscribe to this ByteTalk podcast, and whenever i try to play an episode (i always download the MP3 instead of streaming), it will try to launch kMail. Why does it do that? And how can i stop it from trying to launch kMail? (Or should i just install kMail?)

2. How do i configure or even find out where the podcasts are downloaded to? (As mentioned above, i always download the MP3s instead of streaming, but this downloading is also rather automated, i.e. just right-click and choose "Download Media".

3. I understand (or assume, rather) that once a podcast is downloaded, the "Download Media" option is greyed out. In other words, if the "Download Media" is greyed out, it means the media is already downloaded. (Please correct me if my assumption is wrong.) But i have two problems with this:

a) For one of my podcast, the "Download Media" is greyed out, but it seems like the file is corrupted or not downloaded.

b) For another of my podcast, the "Download Media" is greyed out, but it seems like the file is incomplete.

So is there anyway to force a re-download? (Or do i have to locate the downloaded file and delete it?)



TIA and Regards,
Edwin

---

### Post by fireandlight27 on 2006-08-12
I'm having the first problem as well (with amarok attempting to launch kmail) .  Did you figure out how to keep it from doing that?

---

### Post by stormoog on 2006-08-16
2) Files are stored in /home/USERNAME/.kde/share/apps/amarok/podcasts/data

at least on my system...

---

### Post by fireandlight27 on 2006-08-16
I believe Amarok is trying to launch KMail to allow you to send an error report to the maintainers.  If Amarok is attempting to load KMail, I believe it means that it has already crashed.  I don't believe that installing KMail will keep Amarok from crashing, it will simply allow you to send an error report.

---

### Post by thedude98 on 2006-08-18
I don't think Amarok is crashing when attempting to start Kmail.  I think it is a cookie trying to relay back to the author to count that particular download.

I have many of the same issues with Amarok.  One not mentioned is a playcount, so I can keep track/delete old podcasts.

---

### Post by meanmrmustard on 2007-10-22
OP also asked how to configure where podcasts are stored.
Is there a way to change the default location?

---

### Post by meanmrmustard on 2007-10-22
> **edwin11 said:**
> Hi all, i'm starting to use amarok to manage my podcast subscriptions, and having some difficulties and questions. Kindly advise, thanks very much!



2. How do i configure or even find out where the podcasts are downloaded to? (As mentioned above, i always download the MP3s instead of streaming, but this downloading is also rather automated, i.e. just right-click and choose "Download Media".


Edwin

Right click on Podcasts in the Playlists tab and choose 'configure podcasts'

---

### Post by Bennett2005 on 2007-10-22
> **meanmrmustard said:**
> Right click on Podcasts in the Playlists tab and choose 'configure podcasts'

I'm actually stuck at this part right here.  For some reason I don't get anything when I select "Configure Podcasts."  No menu comes up.

I'm using Gnome right now, but I threw in a Kbuntu live CD and tried it there too, and nada.  Anyone know what might be causing this?

---

### Post by dakuran on 2007-10-23
same problem here =[

---

### Post by Bennett2005 on 2007-10-23
> **dakuran said:**
> same problem here =[

Well, at least I'm not nuts. :)

Anyone know of a fix?

---

### Post by meanmrmustard on 2007-10-23
Is this Feisty or Gutsy and is there a problem with R click menus elswhere?

---

### Post by Bennett2005 on 2007-10-23
> **meanmrmustard said:**
> Is this Feisty or Gutsy and is there a problem with R click menus elswhere?

For me it's a problem with Gutsy, I'm running Ubuntu 7.10.  I don't recall any other problems with Right-Click menus in Amarok, but I'll have to double check.  (I'm at work right now so I can't verify until later tonight)

---

### Post by dakuran on 2007-10-24
I'm on Gutsy too, and I have not had any R click problems thus far. its weird because amarok crashes when I try to get it to handle my ipod as well =[ =[ =[

---

### Post by Bennett2005 on 2007-10-25
> **dakuran said:**
> I'm on Gutsy too, and I have not had any R click problems thus far. its weird because amarok crashes when I try to get it to handle my ipod as well =[ =[ =[

I actually figured this out by accident last night.  I subscribed to a couple podcasts and created some sub-folders to sort them by subject just to play around a bit.  Here's what I discovered:

If I click on an actual podcast subscription or a sub-folder in the podcast directory I can access the "Manage Podcasts" option.  Even though I'm given this same option if I right click on the "Podcast" directory in the Playlist menu I still get no response, it has to be done either from right clicks on the podcast or a sub folder.

Basically it's working great, and in my opinion handles podcast subscriptions in a much more intuitive fashion than iTunes does.  It's more complicated to set up though for sure.

I didn't have much trouble getting it to work with my Ipod though, could that be a bad format on the device?  No idea.

---

### Post by Javier FdelR on 2008-01-22
Maybe 
you dont get the configure menu because you dont have any podcast

---

