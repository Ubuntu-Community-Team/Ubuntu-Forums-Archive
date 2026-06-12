---
title: "Evolution: How to remove  / disable &quot;Ubuntu one&quot; ?"
date: 2011-02-25
forum: General Help
---

### Post by tredegar on 2011-02-25
Hello,

I am handling email with evolution 2.28.3, on 10.04.2 LTS. It is up to date.

I do not wish to use "ubuntu one", so I removed it by following the instructions on their [launchpad page]("https://answers.edge.launchpad.net/ubuntuone-client/+faq/778").

However, I still cannot stop evolution trying to use "ubuntu one". For example if I R-click an address in evolution and choose **Add to address book**, it defaults to adding it to "ubuntu one", not my local address book which I have to select every time.

I have been through all the configuration options in evolution, and de-selected "ubuntu one" wherever I see it.

Evolution is still defaulting to saving addresses to "ubuntu one".

Any ideas as to how I can stop this unneeded, unwanted, and unnecessary behaviour will be most gratefully received.

---

### Post by howefield on 2011-02-26
Is you address book set to Personal in both...

Evolution > Edit > Preferences > Contacts

and 

Evolution > Edit > Preferences > Mail Preferences > Automatic Contacts.

---

### Post by tredegar on 2011-02-26
My thanks for your reply.

I did not have **Evolution > Edit > Preferences > Mail Preferences > Automatic Contacts** set to **Personal**, so I set it, and restarted evolution.

Now when I R-click an email address and choose **Add to address book** the **Select Address Book** box is blank, and the OK button is greyed out. I have to select **Personal**, and wretched ubuntu one is still there as the first choice offered.

So the problem isn't solved yet.

Meanwhile I have been trying to compile evolution 2.26.3 (a slightly older version, so it *should* work) from source (not ubuntu's source, obviously). It has been quite difficult, and **./configure** now gives me this error:
```
checking for CAMEL... configure: error: Package requirements 
(camel-provider-1.2) were not met:

No package 'camel-provider-1.2' found
```
**dpkg -S camel-provider** suggests that I need the source for **evolution-data-server-1.2** but this is not in the ubuntu repositories, so this is turning into a major headache.

This is a pity, because I have been using ubuntu since 6.06, and now have a group of 6 OS naiive users who are all running 10.04 and rely on me entirely for support. I am getting complaints for the first time in 4 years, and I can't fix this issue.

It reminds me of [this thread]("https://bugs.edge.launchpad.net/ubuntu/+source/evolution/+bug/642839") on launchpad when evolution was patched to append to the users sig "Sent from Ubuntu". This did _not_ go down well with the testers, and was reverted.

It is good for ubuntu to offer "enhancements", but I wish they would not force them down our throats in ways we cannot easily decline or disable.

Perhaps I should report this as a bug? Or maybe move my supported group to another distro? But ubuntu has mostly "just worked". I am linux literate, and can usually fix problems, but not this time.

If you have any further advice, I'd really like to hear it.

Thanks for your time.

Best wishes.

---

### Post by howefield on 2011-02-26
How about if you click on the Contacts icon, and then right click on the Ubuntu One address book and select delete. 

That should leave only the address book that you want to use, if you created more than one address book, right click on the one you want to default to, and mark it so, via properties.

---

### Post by tredegar on 2011-02-27
I thank you for your continued support.

I have tried **evolution**  - **contacts** (it's under "couchBD") **ubuntu one** R-click and choose delete. I am prompted that ubuntu one  will be removed permanently. YES.

But it does not go, it is still listed, even after a restart of evolution and logout. The thing is back there again.

A week ago, when I tried this, it used to seem to disappear (it was not listed any more)  but it was restored when evolution was restarted. Now it does not even say it has gone, because it is still listed there.

I have tried the GUI with "Purge / Remove completely" **evolution** and then reinstalling it [My email is safely backed up elsewhere, on a trusted 6.06 machine, 100% reliable for emails, but not trusted for anything else]. 

10.04 is still "testing" at home for me, but one of my support group has new hardware, and 8.04LTS would not work for them . So I upgraded all of them to 10.04.2LTS.

Apart from this issue, they, and I, are happy.

Your post made complete sense to me, but U1 is still clamped to our heels, like a terrier.

Any other ideas?

Thanks for your help &

Best wishes.

---

### Post by howefield on 2011-02-27
Hmm.. that is strange.

This seems to work on my system but that is with 10.10. I'll try a VM with 10.04 and let you know how it goes.

---

### Post by drewstew on 2011-04-05
I too have been frustrated by this, even delving into the cache and disabling the folder - and guess what - restart, and a new cache has been created!  So I've decided to make it work for me instead.
As set up, the Ubuntu One address book is held on the computer, not online (this facility needs to be enabled.  What I've done then is to move all my "subscription" senders to the Ubuntu One address book - they are the ones who generally send HTML-rich emails I want to enable - and only keep my [I]really[I]personal contacts in my Personal folder.  Has stopped me cursing the machine.

---

### Post by tredegar on 2011-04-05
> What I've done then is to move all my "subscription" senders to the Ubuntu One address book 
So you are still connected to that damn thing?

I still do not want my personal data, or my address book "shared" with ubuntu or anyone else.

---

### Post by drewstew on 2011-04-06
Yes, and you'll never guess what, having reconciled myself to live with its "fault", I stumbled across the solution last night-open Contacts, then Edit, Preferences.  Change to "Personal" et voila!  Couldn't believe it when I went to save an address and had Personal as default. (I'm sure you found all the others from the Main Preferences menu, which may all need to be ticked as Personal).

And I'll keep all my (invited) mail-shot email addresses in Ubuntu One - they are welcome to them!

---

### Post by tredegar on 2011-04-06
Thanks for the additional information.

But I have opened Preferences -> Contacts and unchecked "Ubuntu One", under the  CouchDB, while leaving "Personal" checked.

It still asks me to "Select Address book", where I am offered "Ubuntu One" or "Personal". I cannot get it to default to Personal.

Ubuntu seem to be adopting MS & Apple's marketing strategies, and I do not like it.

I have used synaptic to remove all references to ubuntu one. I am still asked where to store my contacts. I would like Ubuntu One to be gone. Forever.

No joy yet, but thanks for your input.

---

### Post by drewstew on 2011-04-06
Sorry, I misled you - it was late at night when I stumbled across the solution, and I just found it again.  The answer is on the Contacts page, Actions, Address Book Properties - change to Personal.  That should do it!

---

### Post by tredegar on 2011-04-07
Thank you!!

At last, Ubuntu One is gone!

---

### Post by drewstew on 2011-04-07
Good to out-flavour a Master Roaster! (Sorry Howefield).

---

