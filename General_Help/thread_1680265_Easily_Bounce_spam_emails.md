---
title: "Easily Bounce spam emails?"
date: 2011-02-02
forum: General Help
---

### Post by KonfuseKitty on 2011-02-02
I can't find the answer to this question... I switched to Ubuntu from Mac OS X and I miss the easy way in which Apple Mail would let you click on a spam message and run the Bounce command to return the message as if it had been sent to a non-existent email address. For genuine spam it was useless, but it proved effected with some of the companies who insist that you're subscribed to their mailing list unless you unsubscribe. I currently use Gnome Evolution which doesn't offer this feature. Is there a way of doing this in Ubuntu relatively painlessly, without switching to some kind of command-line email system?

---

### Post by ajgreeny on 2011-02-02
That is one of the **worst** possible things to do with spam!

It just lets the originator know you got it and it also just clogs up the mail system generally.

Just let your spam-killer or thunderbird rules, or whatever you use, deal with it and then delete it, if it is not deleted automatically by your rule.  Never send them back, or even ask the originator to stop sending, unless it is something you signed up to and now wish to stop, which means it is not strictly spam.

---

### Post by Grenage on 2011-02-02
> **KonfuseKitty said:**
> I can't find the answer to this question... I switched to Ubuntu from Mac OS X and I miss the easy way in which Apple Mail would let you click on a spam message and run the Bounce command to return the message as if it had been sent to a non-existent email address. For genuine spam it was useless, but it proved effected with some of the companies who insist that you're subscribed to their mailing list unless you unsubscribe. I currently use Gnome Evolution which doesn't offer this feature. Is there a way of doing this in Ubuntu relatively painlessly, without switching to some kind of command-line email system?

Not really; if it's a newsletter, you can either unsubscribe or blacklist them.  Most companies won't see the NDR you might return, it's an automated process.

---

### Post by elliotn on 2011-02-02
Just mark em and delete em, I am anoyed with them

---

### Post by srs5694 on 2011-02-02
> **ajgreeny said:**
> That is one of the **worst** possible things to do with spam!

It just lets the originator know you got it and it also just clogs up the mail system generally.

Not just that, but a lot of spam uses forged From: headers, so you'll end up either having your bounce message bounced back at you or some innocent party (whose e-mail address was used in the forgery) will receive your bounce message. I've received such bounces, not to mention irate complaints from spam recipients, in the past; for some reason about five years ago some spammer was using my e-mail address in From: headers. (Maybe I annoyed him by complaining to his ISP or something; a few years ago I still bothered to do such things, but the spam flood is just too great to bother with that today.) I haven't seen this lately, but I'm sure it still happens.

That said, it sounds like KonfuseKitty wants to do this for just a few selected mailing list type spams. The problems with bouncing mail in this way are less likely to apply to that case, so it might not be so awful. Nonetheless, using an official unsubscribe option or blacklisting the sender are probably preferable options in this case. (I'd only use an official "unsubscribe" link for mailing list messages from otherwise legitimate businesses with whom I've done business, though; sometimes such links are just a way for the bottom-feeder spammers to verify that an address is still valid.) Offhand, I don't know of any Linux mail client that provides a manual bounce option.

---

### Post by KonfuseKitty on 2011-02-02
I agree that a Bounce feature generally shouldn't be used on spam, but I find I'm mostly spammed by companies I've bought from, who then assume that buying from them is equal to being subscribed to their mailing list. I would rather Bounce their messages than go through the bother of trying out their Unsubscribe link, which in my experience is not always a straightforward procedure, sometimes it's a thinly disguised advertising attempt. So I prefer to get even: "You send me spam, I send you Bounce... we're even." To my surprise, this seemed to work about half the time - the spam would stop after one or two bounces.


> **srs5694 said:**
> Offhand, I don't know of any Linux mail client that provides a manual bounce option.


Yeah, it does seems there isn't one. How about a quick and dirty scripting solution? Then again, I'm not hoping for much, as the responses here show there isn't much appetite for this feature on Linux.

---

### Post by SeijiSensei on 2011-02-02
> **srs5694 said:**
> Offhand, I don't know of any Linux mail client that provides a manual bounce option.

As you say, when headers are forged, to whom should the bounced message be sent?  The From?  Probably forged.  The SMTP envelope sender?  Perhaps, but often that's not even a person.  There really isn't any way to reliably bounce spam, and as others have said, if you manage to do so successfully, it just paints a target on your back.

My email virus scanner doesn't notify virus senders any more, either.  Again most of these are coming from robots; there's usually no one there to notify.  One case where it might make sense is if someone you know sends a Word document with a macro virus.  That's why I notify the recipient when messages are quarantined, but not the sender.

> **KonfuseKitty said:**
> I agree that a Bounce feature generally shouldn't be used on spam, but I find I'm mostly spammed by companies I've bought from, who then assume that buying from them is equal to being subscribed to their mailing list.

If all you want to do is delete annoying commercial messages from your inbox, I recommend using message filters like those found in Mozilla Thunderbird.  I'm assuming you have no control over your mail server, or at least not enough control to be able to blacklist senders at the server level.  If you can maintain a blacklist at your mail server, that's by far the preferable approach.

Remember that once you've signed up with a commercial entity, messages they send you really can't be considered spam.  Spam is "unsolicited" commercial messages; the types of messages that concern you aren't really unsolicited.  The simplest solution is to route them to the Trash upon arrival with your mail client.

---

### Post by KonfuseKitty on 2011-02-03
> **SeijiSensei said:**
> Remember that once you've signed up with a commercial entity, messages they send you really can't be considered spam.  Spam is "unsolicited" commercial messages; the types of messages that concern you aren't really unsolicited.  The simplest solution is to route them to the Trash upon arrival with your mail client.
Seiji, you're usually very helpful, but not this time. I've already explained that I'm talking about a) known sources of the spam, therefore no forged headers and b) I'm not subscribed, they subscribe me automatically. This happens often enough, even if they provide a box you can untick. And as I've said, the Bounce method has in the past on the Mac proven effective and it takes less time than setting up filters.


So, I'm still looking for a reasonably user-friendly Bounce solution.*

---

### Post by QLee on 2011-02-03
Kmail previously had the feature you're looking for KonfuseKitty, I don't know if recent version still have it because I haven't used it for a couple of years. The version in Debian Lenny still has it, I still have an installation of that and I don't know why they might drop that feature so recent version probably still can bounce email from the client. It might be a good idea to ask at a forum where KDE is used routinely.

---

### Post by KonfuseKitty on 2011-02-04
Thanks for trying, but unfortunately Kmail doesn't have this feature any more, presumably because people were using it incorrectly, bouncing spam with forged headers.


In doing more research I came across some discussions about how a bounced message is basically a redirected message, with headers and 'envelope' being set a particular way. So I tried Message->Forward->Redirect in Evolution, but that sets the message as coming from me, which I don't think is how it should be.


Still looking for a solution...

---

### Post by Grenage on 2011-02-04
> **KonfuseKitty said:**
> Thanks for trying, but unfortunately Kmail doesn't have this feature any more, presumably because people were using it incorrectly, bouncing spam with forged headers.

It was dropped because it's useless in the current e-mail world, and because kmail gained anti-spam filtering.  Back in the 90's, it might have had an impact, but these days you're more likely to end up on a black list because of it.

I appreciate that you personally like and want the feature, but your in a very small minority.

---

### Post by KonfuseKitty on 2011-02-04
I'm surprised at how motivated people are to tell me the feature is useless instead of helping. Even when I've explained how I use the feature and that it has been effective. Maybe I should make it clear that I do have the ability to set filters on the server, which I guess do catch much of the spam from unknown sources. The spam that *gets through is from companies I've dealt with, as explained before. It's too laborious to either set a filter for each such company or go through the unsubscribe feature which is usually hit and miss. So you could say the Bounce feature is just one of the tools in my arsenal. I do understand why it is deprecated, people mostly aren't so careful.


If anyone can help, please post.

---

