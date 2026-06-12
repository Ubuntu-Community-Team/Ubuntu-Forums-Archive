---
title: "Firefox and webmail"
date: 2010-11-09
forum: General Help
---

### Post by riseringseeker on 2010-11-09
I am having a frustrating problem with trying to use firefox for webmail.  There are several complaints to be found about firefox and yahoo mail, or gmail, and seemingly no one has a solution (other than one thread here marked "solved" that suggests upgrading from 8.04)

The problem I am having started in yahoo mail.  When I go to delete a read mail, nothing happens.  It just sits there, no progress of any type showing.  I can switch to contacts, or go back to the in-box view (where the mail I had just read showed as unread), but the only way I can delete it (and then not always) is to put a check next to the mail and then delete it "unopened".  Sometimes this happens with the first e-mail I tried to delete, other times it would be the second or third...

Also, just often enough to be a real pain, when answering or forwarding an e-mail it would again just sit there, doing nothing.  I could again open contacts, or go back the the in-box view (in doing so losing my composed e-mail), but could not send!

Now I am having a similar problem with gmail.  If I compose a message (or try to forward) it just sits there saying "loading".  I have let it sit like that for as long as a half an hour, and it was still "loading".

I have tried clearing the cache, closing and reopening firefox, even rebooting, but the problem persists.

I can switch to epiphany, and everything works fine, so it is not an Ubuntu problem per se, but at least a problem with the Ubuntu version of firefox.  I do not have a non-Ubuntu machine to try it out on, but if it were a wider spread problem, there would be more hits come up with a google search.

I will try and see if 10.10 has any problems with this off the live CD, and may well upgrade, but was not in a hurry this time.  I only have a few rather innocuous plugins/extensions, so I don't think that is the problem, but if **anyone** can give me a clue as to what to try, I sure would appreciate it!

---

### Post by CharlesA on 2010-11-09
Yahoo and gmail work fine for me on FF in Maverick and Lucid.

Do you have any add ons installed?

---

### Post by riseringseeker on 2010-11-09
> **CharlesA said:**
> Yahoo and gmail work fine for me on FF in Maverick and Lucid.

Do you have any add ons installed?

A few, but I have not added any before I began having problems.

<Update>

I found that I was not having problems on the desktop install.  I have deleted the .mozilla folder from the laptop, then copied over the desktop setup.  No problems yet, but will keep you advised.

---

### Post by CharlesA on 2010-11-09
Corrupted profile would do it.

---

### Post by riseringseeker on 2010-11-10
> **CharlesA said:**
> Corrupted profile would do it.

Agreed, but if it was, it was corrupted in a way that it wasn't an every time thing.  I would expect a corrupted profile would be more consistent, but then again it may not.

I did consult a highly skilled IT guy, and he said that he had a very similar problem both with his linux setup and his wifes W7 machine.  In his case upgrading directly from the mozilla site solved the problem, so that points to it being a firefox issue more than an ubuntu implementation problem.

Googling for "gmail (or yahoo mail) stuck on loading" or yields quite a few hits, and gmail and yahoo even have possible fixes for it (though they did not work for me).

Anyway, so far so good, will keep seeing if the problem rears it's ugly head.  If it doesn't after a few days, I will marked this solved.

---

### Post by andymorton on 2010-11-10
Have you thought of using an desktop email client? Thunderbird, Evolution etc. 

andy

---

### Post by CharlesA on 2010-11-10
> **riseringseeker said:**
> Agreed, but if it was, it was corrupted in a way that it wasn't an every time thing.  I would expect a corrupted profile would be more consistent, but then again it may not.

I know what you mean. I've had it happen where I had to recreate the profile due to it getting stuck at "crash recovery" and never actually recovering. It only happened a few times but it would never recover. Stupid but it wasn't happening all the time.

> **andymorton said:**
> Have you thought of using an desktop email client? Thunderbird, Evolution etc. 

andy

IMAP would work for that, I suppose, since it syncs the mail with the server.

---

### Post by riseringseeker on 2010-11-16
> **andymorton said:**
> Have you thought of using an desktop email client? Thunderbird, Evolution etc. 

andy

It's not really practical for me to do so.  Two of my e-mail addresses would not work.  AFAIK, unless using yahoo plus, which I don't have, and don't want, one cannot use such a client at all, and with my cox address, I *must* be on a cox connected machine to retrieve (or send, forget which) any e-mail at all.

Since I am literally all over the place (e.g. now writing this from Adana, Turkey, will be in Morbach, Germany come morning), web based e-mail is the best solution for me.

Copying over the profile from the desktop seems to have solved the problem, and another problem with flash on certain site as well, for that matter!

---

