---
title: "Evolution contact account corrupted - how do I delete it"
date: 2012-05-11
forum: General Help
---

### Post by Jonners59 on 2012-05-11
I have had an issue with Evolution for the past year, since the release of Ubuntu 10.04.  I now realise that it is then that the Evolution team changed the file structure.  I have been able to fix all the issues I had: Calendar not working properly and contact accounts not syncing up, all that is, bar ONE account.  One contact account, the most important does not work.  I get the following messages:

[HTML]
UNABLE TO OPEN ACCOUNT
This address book cannot be opened.  This either means that an incorrect URI was entered, or the server is unreachable.

Detailed error message: Cannot open book: Source already loaded![/HTML]

I use one more account for contacts, and that works fine.  Both are google hosted, though one is a business addressbook and has our business URL.  That is the faulty one.

I am assuming that it is the config that is corrupted.  If I can purge/delete it I can start all over.  But where is it?????

---

### Post by kuifje09 on 2012-05-11
I want say I can help you, but you should tell which version of ubuntu and evolution you use.
The latest evolution uses SQLite to keep all the data. So you need to be a database administrator too to get through these problems I think.

But if you give some more info on the versions, I am shure someone can help you out.

---

### Post by Jonners59 on 2012-05-12
Sorry on a couple of accounts:
Should have put the details. I had in an earlier thread, but just got lazy. And I am away for the weekend, so doing this via my mobile and can't test. Any sugggestions until Monday.


Any way, the Ubuntu is latest. 12.04 64-bit. And the Evolution is also the latest on the distro, I think 3.2.??
I am assuming the account is corrupted in some way as it will not load.  I use two. Off mine and one works,   the other does not.

---

### Post by kuifje09 on 2012-05-13
Do I understand you well, Contacts can't be opened at all ?
Else, you could try to export them as vCards, edit it with vi i.e. , then import it back?

If it can't be opened at all, you need some SQL experience I think. Which I donot have this moment.

( I will give it a try at my system... )


Well, I did a test but I cannot get any info from evolution by using the sqlite manager.
The evolution developers are poking me in the back. ( very very sad )

I have doubt you need SqLite, see this other thread.
[http://ubuntuforums.org/showthread.php?t=1975626](http://ubuntuforums.org/showthread.php?t=1975626)

---

### Post by Jonners59 on 2012-05-14
OK, now i am back, maybe I can be clearer.
First what I use:
Running CPU: Intel(R) Core(TM) iS-2500K CPU @ 3.30Ghz and 15.7GB RAM
Dist is Ubuntu 12.04 x86_64 and Desktop is UNity with xfce4
Evolution is 3.2.3-Oubuntu6

I, like you, have used Evolution for a long time, though, unlike you I prefer Outlook, but that won't work with gmail as it needs SSL certs and WINE can't cope in some way, so I use Evolution, the next best....

I have used it successfully for a few years.  I have 4 eMail accounts. One is a gmail and the others are on my private domain but hosted by google, so the settings are the same.

I use all 4 accounts, plus my wife's account for the calendar - again hers is in our private domain.

And I use 2 of the accounts for the contacts.  One I call PERSONAL = gmail account and one I call WORK = my private domain.

A couple of Ubuntu upgrades ago, I think it was 10.04, I could not get my contacts to work.  Lots of error messages and the same with calendars.  There were lots of bugs being reported.  In this build - 12.04 after removing Evolution and reinstalling the calendars started to work and my PERSONAL contacts.  My WORK contacts refuses to.  I get the error message as per below.  I get the impression it sees "something" of the contacts account, but can not load it or sync with it, so I thought IF I could completely remove all traces of the account, then reinstall the account settings it may work.  In the past that was easy, just deleted the appropriate file in /etc/.EVOLUTION.......

The problem is JUST the one contact account will not display.

Hope that is clearer

---

### Post by dcstar on 2012-05-15
In 12.04 various components that older releases are not installed by default. In Evolution this was the Ubuntu One part that if you upgraded from 10.04 to 12.04 then there would be an error in Evolution because the Couchdb packages were not installed. This caused an error in the Contacts because the old configuration came across but the back-end was not there for it to work.

[https://bugs.launchpad.net/ubuntu/+source/evolution-couchdb/+bug/955673](https://bugs.launchpad.net/ubuntu/+source/evolution-couchdb/+bug/955673)

I don't know if this has any relevance to your issue, but there may be something else missing?

---

### Post by Jonners59 on 2012-05-15
Thank you, but I doubt it.  I did a complete new install, though it seemed to pick up my old settings.  That may be the issue, as I believe the old settings may have been broken.  It would be easier to delete the settings for the faulty account and start over.

That bug ends in it being the way the upgrade was carried out by the user, not the upgrade itself too.

I thought Ubuntu One was part of Evolution for a couple of years, so would have been in 10:xx to date????????

Cheers any way.  Any other ideas to try?

---

### Post by chrismou on 2012-05-15
I've had a similar (or maybe identical) problem.  Had to wipe my Ubuntu 11.10 install after something went horribly wrong, but managed to save my home directory (live CD, copied to USB drive).

Managed to set up all email/calendars again without a problem.

Contacts it's pulled the my "Personal" contact list (the one under "On this computer") and it'll pulling my work contacts from exchange (set up using MAPI, I think).

But Google apps for domains contact list won't load.  Same error as the OP mentioned:

```
This address book cannot be opened.  This either means that an incorrect URI was entered, or the server is unreachable.

Detailed error message: Cannot open book: Source already loaded!
```

I went as far as trying to delete all evolution folders in the .config, .local and probably others - pretty much every directory called "evolution" I could find in the home directory.  But the personal contacts have remained, and I still can't add my gmail contacts.

Is the contact data stored in it's own sqlite instance, or is it in some sort of generic, glocal sqlite db? If it's the former, where is it so I can just delete it and start over?  If it's the latter, what would I need to do to get access to that data and delete what the saved contacts?

The thing is, I copied the files I *thought* I needed back into the home directory from the USB stick, so I at least know it's somewhere in the home dir, and it's something I'm sure I can safely delete - if I can find it.  So any help tracking it down would be appreciated!

---

### Post by kuifje09 on 2012-05-15
Well, Also I would like to know how one and other is working now ( or stored )
Used evolution for years, but now its killing me. 
( making things better is not the same as changing a lot, as always. Keep it simple. )

---

### Post by Jonners59 on 2012-05-15
> **kuifje09 said:**
> Well, Also I would like to know how one and other is working now ( or stored )
Used evolution for years, but now its killing me. 
( making things better is not the same as changing a lot, as always. Keep it simple. )

It is all done on databases, I believe.  All the old folders and directories changed at about 10:04, that's when I started getting problems and all the bugs started getting filed.  The new structure is:

The user's data files
$HOME/.local/share/evolution

Various configuration and state files
$HOME/.config/evolution

Disposable data caches
$HOME/.cache/evolution Configuration settings in GSettings$HOME/.config/dconf
But I can't make head nore tail of it.  I tried taking out some of the files but it made no difference.  I have now deleted all the Contacts account addressbooks.

---

### Post by chrismou on 2012-05-16
> **Jonners59 said:**
>  I tried taking out some of the files but it made no difference.  I have now deleted all the Contacts account addressbooks.

Have you actually managed to fix the issue then?  I tried wiping all evolution folders in .cache, .config and .local and it removed my email accounts, but I'm still getting the gmail contacts issue.  :(

---

### Post by Jonners59 on 2012-05-16
> **chrismou said:**
> Have you actually managed to fix the issue then?  I tried wiping all evolution folders in .cache, .config and .local and it removed my email accounts, but I'm still getting the gmail contacts issue.  :(

No, nothing and no help either.  I raised a bug a year ago, and had no help then either....

Interesting:
I downloaded all my contacts (1,900) from one of my Google accounts, and then loaded them in to the "On This Computer" -> "Personal" accounts yesterday.  Worked fine.  Just started up Evolution today and the account is empty!

I have started another thread with a slightly different title.  Hopefully that shall attract someone who can help us.

---

### Post by chrismou on 2012-05-16
> **Jonners59 said:**
> No, nothing and no help either.  I raised a bug a year ago, and had no help then either....

Interesting:
I downloaded all my contacts (1,900) from one of my Google accounts, and then loaded them in to the "On This Computer" -> "Personal" accounts yesterday.  Worked fine.  Just started up Evolution today and the account is empty!

Seems I made a mistake with my post.  I just tried deleting evolution folders from .local, .config and .cache again, booted up evolution and my mail accounts are still there. I can't actually remember how I managed it last time (though last time it only deleted the mail accounts, not contacts, so it wasn't really a solution).

This is ridiculous.  There must be a way of just deleting everything from evolution at file level and starting again?  I'm not particularly up for wiping my entire OS again just so I can have a synced contact list in Evolution.

---

### Post by Jonners59 on 2012-05-16
And we are not alone.  I have seen similar in other forums and on Evolution's forum/bug reporting.  Someone one must be able to assist us.  This is when you feel helpless  :(

---

### Post by javierpv on 2012-07-19
I found in [https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/1010349]("https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/1010349") a partial solution. It works for me but must be done every time you turn on your computer.

---

