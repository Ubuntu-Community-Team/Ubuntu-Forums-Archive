---
title: "Evolution contact problems"
date: 2012-05-16
forum: General Help
---

### Post by Jonners59 on 2012-05-16
First what I use:
Running CPU: Intel(R) Core(TM) iS-2500K CPU @ 3.30Ghz and 15.7GB RAM
Dist is Ubuntu 12.04 x86_64 and Desktop is Unity with xfce4
Evolution is 3.2.3-Oubuntu6

I have used Evolution for a long time, but since circa 10:04 when Evolution changed the way it worked, Directories and Data bases, etc, I have had trouble with Calendar and Contact accounts.  The Calendar issues seemed to have resolved with the new 10:04 build and  complete reinstall, but the contacts is a different issue.

After setting up the accounts in Contacts using my Google account details I get the following messages:

```
This address book cannot be opened.  This either means that an incorrect URI was entered, or the server is unreachable.
Detailed error message: Cannot open book: Source already loaded!
```

I have tried exploring and even deleting files in the following Directories, but to no avail.

```
The user's data files
$HOME/.local/share/evolution

Various configuration and state files
$HOME/.config/evolution

Disposable data caches
$HOME/.cache/evolution Configuration settings in GSettings$HOME/.config/dconf
```

Yesterday I thought I would take the simple route of just using the "On This Computer" -> "Private" account and just manually uploading my contacts.  It worked yesterday, but today on restarting Evolution the account is empty.

I have tried reinstalling and purging Evolution, but it makes no difference.  I also think that even with purging the account data is not removed completely so if there is an incomparability between the old and new Evolution then that is reused again.

I have raised other Threads, but not had the desired support/responses to get this fixed, so I am trying another Title in the hope of attracting someone who may have the answer....

---

### Post by apochry on 2012-05-16
Hi,
are you using any contact sync or only locally stored contacts?
If it's the second, you could try to set up U1 or google sync and see happens.

- Christo

---

### Post by Jonners59 on 2012-05-16
> **apochry said:**
> Hi,
are you using any contact sync or only locally stored contacts?
If it's the second, you could try to set up U1 or google sync and see happens.

- Christo
I have 4 x Google hosted accounts.  One is a gmail and the other 3 are a personal domain hosted by Google.

I started finding the error message below some time ago and have reduced the number of accounts I try and sync to just the personal account (gmail) and one of the personal domain.  But I still get the errors.  I have deleted the accounts and started fresh and I have un-installed Evolution and started fresh, and purged Evolution and started fresh, no method works.  I have then to get some form of list for keeping contact downloaded the contacts from my private domain account and installed in to the "On This Computer" "Private" account.  It worked until I rebooted, when there was NOTHING in the account.

---

### Post by Derek Karpinski on 2012-05-16
I have the same problem too.  Someone should file a bug.  If I was at my Ubuntu box, I would.

---

### Post by Jonners59 on 2012-05-16
> **Derek Karpinski said:**
> I have the same problem too.  Someone should file a bug.  If I was at my Ubuntu box, I would.
I have filed three over the past year or so.  They just don't get looked at, there's no point.

---

### Post by apochry on 2012-05-16
I had an issue with the google sync of contacts several releases ago (in 11:04 or 10.10), but the problem was solved by changing the Network Preferences in Evolution to "Direct Connection".
Since than I have no problems at all (with the contact sync particularly).
I'm sticking to the 32bits, this might make difference. But I guess it's not an option for you, with 16G RAM.

- Christo

---

### Post by Jonners59 on 2012-05-30
It worked yesterday, for no reason.... today back to error messages.
Anyone willing to help out, please????

---

### Post by Jonners59 on 2012-10-23
Fixed in new build 12:10....  Only taken 2 years.

---

