---
title: "facebook chat in empathy"
date: 2010-03-03
forum: General Help
---

### Post by sHoIoKs on 2010-03-03
i got my facebook chat working in empathy, but for some reason i can not add my friends from this protocol into a custom group.  I have my gmail contacts in a group, and my aim buddies in a group, allowing them to be minimized, but i cannot get my facebook friends to go into a facebook group for some reason.  I can right click the friend, and create a new group called "Facebook", but the friend will not move to the group when i hit close.
Anyone know of a fix?

---

### Post by Pessulus on 2010-03-14
Same problem here.

---

### Post by CharlesJWelsh on 2010-03-14
How do you get facebook chat on empathy anywho? That would be very helpful :)

---

### Post by jdorenbush on 2010-04-11
Same problem here.

Using Empathy 2.30.0.1 on Ubuntu 10.04

---

### Post by skyeric on 2010-04-11
> **CharlesJWelsh said:**
> How do you get facebook chat on empathy anywho? That would be very helpful :)
same question here!

---

### Post by polki@mac.com on 2010-04-12
Try this link:

[http://www.facebook.com/sitetour/chat.php]("http://www.facebook.com/sitetour/chat.php")

---

### Post by skyeric on 2010-04-12
worked perfectly thanks a lot :)

---

### Post by jdorenbush on 2010-04-13
> **polki@mac.com said:**
> Try this link:

[http://www.facebook.com/sitetour/chat.php]("http://www.facebook.com/sitetour/chat.php")

Didn't work for me.

[email]myusername@chat.facebook.com[/email]/
Pidgin disconnected
Unable to connect

---

### Post by skyeric on 2010-04-14
I'll give it a go on Pidgin now

---

### Post by skyeric on 2010-04-14
Follow these instructions --> [http://www.omgubuntu.co.uk/2010/02/facebook-chat-in-pidgin-empathy-with-no.html](http://www.omgubuntu.co.uk/2010/02/facebook-chat-in-pidgin-empathy-with-no.html)

It says you don't need the plugin but I got that anyway (just search 'pidgin facebook' in symaptic package managaer).

> 
For the protocol type, select XMPP.
For the username, use your Facebook username. (see [http://www.facebook.com/username/](http://www.facebook.com/username/))
For the domain, use "chat.facebook.com"
For the password, use your Facebook password.

Now in advanced settings set the following:
Uncheck Require SSL
Set connect port to 5222
Set connect server to chat.facebook.com


---

### Post by jdorenbush on 2010-04-14
> **skyeric said:**
> Follow these instructions --> [http://www.omgubuntu.co.uk/2010/02/facebook-chat-in-pidgin-empathy-with-no.html](http://www.omgubuntu.co.uk/2010/02/facebook-chat-in-pidgin-empathy-with-no.html)

It says you don't need the plugin but I got that anyway (just search 'pidgin facebook' in symaptic package managaer).

Following those steps, which were different in that it said to uncheck SSL, still didn't work though.

---

### Post by skyeric on 2010-04-14
> **jdorenbush said:**
> Following those steps, which were different in that it said to uncheck SSL, still didn't work though.

Im on a different computer now so cant check my settings, tomorrow i will upload a print screen of all the settings i have and you can compare. Perhaps its an issue at facebooks end with your account. 

As i said i'll upload tomorrow.

Eric

---

### Post by jdorenbush on 2010-04-14
> **skyeric said:**
> Im on a different computer now so cant check my settings, tomorrow i will upload a print screen of all the settings i have and you can compare. Perhaps its an issue at facebooks end with your account. 

As i said i'll upload tomorrow.

Eric

Installing the plugin via Synaptic seemed to do the trick. :)

---

### Post by skyeric on 2010-04-15
Oh sweet, it say's that's not needed but I got it too so clearly they're getting something wrong.

Have to say since you encouraged me to use Pidgin i've been using that instead it seems far easier, as a solution to the original thread poster asking for facebook contact grouping in empathy - use pidgin it works perfectly fine and I prefer the UI too.

---

### Post by jdorenbush on 2010-04-15
> **skyeric said:**
> as a solution to the original thread poster asking for facebook contact grouping in empathy - use pidgin it works perfectly fine and I prefer the UI too.

Exactly. I switched over simply because of that minor flaw. My buddy list was out of control w/o being able to group Facebook contacts.

---

### Post by skyeric on 2010-04-15
I only have the once account on it at the moment, are you using multiple accounts? can you group contacts from different accounts into the same groups? so rather than having one group for facebook and one for msn or something can I have groups like: work, school, family and have contacts from a variety of accounts in each?

---

### Post by jdorenbush on 2010-04-15
> **skyeric said:**
> I only have the once account on it at the moment, are you using multiple accounts? can you group contacts from different accounts into the same groups? so rather than having one group for facebook and one for msn or something can I have groups like: work, school, family and have contacts from a variety of accounts in each?

Currently I am accessing AIM, MSN, Gmail, and Facebook account all via Pidgin.

I am able to rearrange contacts/groups however I want. It appears to be very flexible.

---

### Post by skyeric on 2010-04-15
Wow definitely changing to pidgin then. Starting to think that it should be installed by default rather than Empathy which I was getting annoyed with.

Thanks,
Eric

---

### Post by nucleuskore on 2010-05-06
For those still struggling with empathy and facebook chat
[http://ubuntuforums.org/showthread.php?p=9211014#5](http://ubuntuforums.org/showthread.php?p=9211014#5)

---

### Post by Grone1985 on 2010-05-06
For everyone struglin with the lack of groups for facebook on Empathy there is this workaround... Go to facebook's chat and move all contacts into a list you create. Call it "Facebook" and on empathy you will then have a group called "Facebook". This of course allows you to have your contacts divided in different groups...

The problem is basically related to the contacts that don't belong to any list, if you name the list or lists the same as your other protocol groups it will put the contacts in the same groups... hope that helps

Cheers!

---

### Post by DomesDKG on 2010-05-06
I had no problems getting the account set up in empathy, but I'm having the same issue of not being able to move friends around in groups.  Hope someone has an answer for it?

---

### Post by Grone1985 on 2010-05-06
> **DomesDKG said:**
> I had no problems getting the account set up in empathy, but I'm having the same issue of not being able to move friends around in groups.  Hope someone has an answer for it?

Last post on page two ;)

---

### Post by birdy on 2010-05-10
Doesn't work for me. 

I have my Facebook contacts on Facebook sorted in various standard groups (Friends, Coworkers, ...). When I opened the Facebook account in Empathy, Facebook contacts were sorted nicely in these groups. However, any changes I have done on Facebook since then (e.g. adding a custom group Old friends) does not reflect in Empathy. I even tried to remove and add the Facebook account in Empathy to get the new groups to register. Didn't work.

---

### Post by Grone1985 on 2010-05-11
> **birdy said:**
> Doesn't work for me. 

I have my Facebook contacts on Facebook sorted in various standard groups (Friends, Coworkers, ...). When I opened the Facebook account in Empathy, Facebook contacts were sorted nicely in these groups. However, any changes I have done on Facebook since then (e.g. adding a custom group Old friends) does not reflect in Empathy. I even tried to remove and add the Facebook account in Empathy to get the new groups to register. Didn't work.

That's weird... It works perfectly for me... It takes a few seconds to reflect on empathy but it works... what you could try is to hide and then show the lists on the "friend lists" tab on FB chat... I thought I had that same problem but then realized that it just took some time... Good luck!

---

### Post by nmfralich on 2010-05-26
For clarity, I followed the link to the facebook chat page.  There it says that you cannot edit Friend Lists outside of facebook, but if you edit them in facebook, they will be reflected in you client.  I don't recall having had this problem in Pidgin/Karmic, but having upgraded to Lucid I now am running Empathy and there this definately [[COLOR="Blue"]seems to be the case...[/COLOR]]("http://www.facebook.com/sitetour/chat.php#!/help/?faq=16743")

---

### Post by dasy2k1 on 2010-05-26
looks like i will be swiching back to pigin

more than the groups being a bit dodgy is that i cant merge contacts who are the same person but on more than one network!

---

