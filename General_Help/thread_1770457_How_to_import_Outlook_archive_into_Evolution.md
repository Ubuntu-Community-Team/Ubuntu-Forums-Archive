---
title: "How to import Outlook archive into Evolution?"
date: 2011-05-29
forum: General Help
---

### Post by r2d211 on 2011-05-29
I set up my email accounts in Evolution and I would like to import all emails, contacts, calendar, etc. from my outlook archive into evolution. Is it possible and how to do it?

---

### Post by r2d211 on 2011-05-29
Okay, someone posted that you must use thunderbird installed in windows and then import its files into thunderbird on ubuntu and from there to evolution. I downloaded thunderbird for ubuntu but how to install it?

---

### Post by lightstream on 2011-05-29
just install the one from the repos. Open Software Center and search for thunderbird

---

### Post by r2d211 on 2011-05-29
Oh, I forgot to tell you that I don't have internet connection yet in ububntu. May I download it from windows as a .deb from somewhere?

---

### Post by linuxinstalledfromhdd on 2011-05-29
I don't recommend doing it that way. I think it has dependencies, and you are making this much harder than it needs to be.

Wait for internet.. or get internet first.

---

### Post by r2d211 on 2011-05-29
Well, are you talking about waiting for internet in order to download thunderbird or for direct migration outlook-evolution? I think you're talking for thunderbird. Okay, what can I do...

I am now trying to install barry4all for Blackberry tethering but no success so far. I'll wait...

---

### Post by lightstream on 2011-05-29
> **r2d211 said:**
> I am now trying to install barry4all for Blackberry tethering...

is this how you get the internet in windows?

---

### Post by linuxinstalledfromhdd on 2011-05-29
> **r2d211 said:**
> Well, are you talking about waiting for internet in order to download thunderbird or for direct migration outlook-evolution? I think you're talking for thunderbird. Okay, what can I do...

I am now trying to install barry4all for Blackberry tethering but no success so far. I'll wait...

You don't have an Ethernet cable that you can hook to a router in your location instead?

---

### Post by r2d211 on 2011-05-29
Nope, my only way to get to the internet is by using Tether for Blackberry in Windows or just surf on the Blackberry.

---

### Post by linuxinstalledfromhdd on 2011-05-29
I know, do you have a college nearby that you can take it to, and hook it into their network to get this installed?  Pretend you are working on a class project.

---

### Post by LordNeo on 2011-05-29
IIRC Evolution already has the option to import your old PST file to recover your mails

---

### Post by r2d211 on 2011-05-30
I tried this option and after 20 minutes of hard work it crashed.




Linuxhdd, I live in a very remote area with people out of the grid.

---

### Post by linuxinstalledfromhdd on 2011-05-30
Try using the PST import plugin for Thunderbird instead, and then you can migrate the data natively to evolution eventually in Ubuntu. 

[http://lifehacker.com/340521/import-outlook-pst-files-into-thunderbird-with-pst-import](http://lifehacker.com/340521/import-outlook-pst-files-into-thunderbird-with-pst-import)

---

### Post by r2d211 on 2011-05-30
Okay, I've just downloaded and I'll keep you update!

---

### Post by r2d211 on 2011-05-30
So, tomorrow I'll install Thunderbird in Windows XP, then use the migration tool to get all emails, contacts and everything from MS Outlook and then I'll try to copy everything from the TB's profile folder in Windows to the Evolution folder in Ubuntu.

Then I'll let you all know the result.

---

### Post by r2d211 on 2011-05-31
Hey, I installed the thunderbird on windows today and imported all my emails and hierarchy folders and archive, and also all my contacts from MS Outlook, amazing! The next thing to do is to transfer all this from the windows profile of the TB to the evolution folder.

One thing disappointed me: it didn't import calendar entries, notes and ToDo list! Seems that TB doesn't even have calendar and such, but only mail and contacts.

Is there any way to import the calendar, notes and todos from MS Outlook?

---

### Post by r2d211 on 2011-06-01
I've been searching all day but just couldn't  find where the evolution folder is located!

---

### Post by lightstream on 2011-06-01
> **r2d211 said:**
> I've been searching all day but just couldn't  find where the evolution folder is located!
Look in ~/.evolution

As for your question about importing calendar etc, I would start a new thread for that question. Good luck!

---

### Post by Rebelli0us on 2011-06-01
Evolution's import function is weak or useless.

Thunderbird can import everything from Outlook and will also let you share a profile between Linux & Windows. Start with command Thunderbird -profilemanager and create a "new" profile pointing to an existing profile.

---

### Post by r2d211 on 2011-06-01
Hey, you, rebel, are you talking about using thunderbird in ubuntu instead of evolution? Then how to import calendar and other stuff?

---

### Post by Rebelli0us on 2011-06-01
> **r2d211 said:**
> Hey, you, rebel, are you talking about using thunderbird in ubuntu instead of evolution? Then how to import calendar and other stuff?

I've never tried calendar but Thunderbird will import mail accounts, settings, mail, etc. There's even a Mozilla addon than will import Mail filters. The best thing is that you can use the **same** account from **both** Windows and Linux, so there's no need to synchronize anything.

---

### Post by r2d211 on 2011-06-01
Teach me, my friend, how to accomplish this.

---

### Post by Rebelli0us on 2011-06-01
> **r2d211 said:**
> Teach me, my friend, how to accomplish this.

The Mozilla people already have step-by-step instructions 

[http://forums.mozillazine.org/viewforum.php?f=39&sid=1cbefba48206197569b53c2c73ccce4b](http://forums.mozillazine.org/viewforum.php?f=39&sid=1cbefba48206197569b53c2c73ccce4b)

you can use the same profile from Linux & Windows. See my reply above or do a google search for "thunderbird -profilemanager". You don't have to import anything, you can use your exiting profile from its present location from another OS!  Firefox can do the same, it makes switching to Linux easy and painless.

---

### Post by r2d211 on 2011-06-02
That's great Rebellious! I will try to implement it.

By tje way, I used today the evolution's import command and it did it! Emails and folders were imported good.

But anyway I'm interested of having the same account on two OS so I'll check your advice.

Okay, because the main goal of this thread was accomplished, with your permission, I will declare our thread as SOLVED!

---

### Post by r2d211 on 2011-06-02
That's great Rebellious! I will try to implement it.

By the way, I used today the evolution's import command and it did it! Emails and folders were imported good.

But anyway I'm interested of having the same account on two OS so I'll check your advice.

Okay, because the main goal of this thread was accomplished, with your permission, I will declare our thread as SOLVED!

---

### Post by r2d211 on 2011-06-05
I cannot believe it! My evolution email was working these days but starting with yesterday I am not able to receive or send anything? The popup says: Route to host not found.

All of a sudden?

:(

---

