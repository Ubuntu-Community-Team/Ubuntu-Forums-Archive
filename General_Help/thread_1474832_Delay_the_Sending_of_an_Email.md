---
title: "Delay the Sending of an Email"
date: 2010-05-06
forum: General Help
---

### Post by ciamele on 2010-05-06
Does anyone know of a way to delay the sending of an email to a specific time? For example, compose an email at 8 PM and have the client send it at midnight?

I don't believe it can be done in Evolution or Thunderbird, unless I'm mistaken. Thunderbird has two add-ons (SendLater and SendTools), but they are not supported on the latest release of T-bird.

I use Gmail, but I don't see an option there either.

Do you know of a mail client that can do this? Or a way to perform that task with one of the above? Thanks!

---

### Post by dcstar on 2010-05-07
> **ciamele said:**
> Does anyone know of a way to delay the sending of an email to a specific time? For example, compose an email at 8 PM and have the client send it at midnight?

I don't believe it can be done in Evolution or Thunderbird, unless I'm mistaken. Thunderbird has two add-ons (SendLater and SendTools), but they are not supported on the latest release of T-bird.

I use Gmail, but I don't see an option there either.

Do you know of a mail client that can do this? Or a way to perform that task with one of the above? Thanks!

[http://www.lettermelater.com/forum.php?id=2](http://www.lettermelater.com/forum.php?id=2)

Google is an amazing thing.

---

### Post by ciamele on 2010-05-07
Thanks, DCStar, that looks like a nice option. I admit I was looking for something that didn't involve using a third party. Something like a client that has a native feature or an add-on. I'm going to keep your suggestion in mind in case no one else responds. Thanks, again!

---

### Post by ciamele on 2010-05-08
bump

---

### Post by narnie on 2010-06-03
Bump

Surely a plugin could do this. There isn't one? Wish I new how to code (something other than scripting) and I'd write one.

Narnie

---

### Post by Andrew_P on 2010-10-25
I, too, would like to see a mail client for Ubuntu with this capability, even if it isn't my primary mail client (SeaMonkey suite in my case).  The last time I encountered a mail system with delayed send capability was when I worked for a company that used Microsoft Exchange with Windows 95/98/NT systems. Running with an internal Exchange Server, it also had the capability of recalling messages that had already been sent within the company, so long as the recipient hadn't opened the message yet.  Microsoft Outlook is the successor to Exchange, and it still features delayed send capability, but, alas, it isn't available for Linux.

The SeaMonkey Suite, and, I believe the Mozilla Suite and Netscape Suite before it, have a Send Later feature (Ctrl+Shift+Return), which puts the message in the Unsent Messages folder under the Local Folders.  There's no way to specify when the messages in that folder will be sent, but when the mail client is restarted it checks for the presence of messages in that folder and optionally asks whether you want to send them now, or immediately sends the messages without asking, depending on the settings selected in the email Preferences dialog under "Offline & Disk Space".  To do this unattended would require a plug-in that checks the folder periodically while the client is running and sends whatever it finds there.  With SeaMonkey 1.1.18, the version I now have installed, there is no way to tag the individual messages uniquely with a send time, as far as I know.  This may have been a feature that the Mozilla team was contemplating years ago, but never fully implemented.  Searching in the Mozilla/SeaMonkey help screens for "Unsent Messages" yields no results.

:idea:If one only needs to send a delayed message *occasionally*, it may be possible to make it work as a [FONT="Fixedsys"][SIZE="+1"]cron[/SIZE][/FONT] job, by selecting automatic sending of Unsent Messages when the mail client starts, have [FONT="Fixedsys"][SIZE="+1"]cron[/SIZE][/FONT] start the mail client, let it run for a few minutes to ensure that the message(s) have been sent, then shut down, i.e., "kill" the client automatically.  It also suggests the possibility of copying new unsent message files into the program's Unsent Messages folder under the control of a script, and having the [FONT="Fixedsys"][SIZE="+1"]cron[/SIZE][/FONT] job send successive messages or batches of messages using the mechanism described above.  This wouldn't be an elegant solution, but might just work if you didn't need the feature regularly.

---

### Post by Andrew_P on 2010-10-25
> **dcstar said:**
> [http://www.lettermelater.com/forum.php?id=2](http://www.lettermelater.com/forum.php?id=2)

Google is an amazing thing.

LetterMeLater is not free.  It would be preferable to be able to do what ciamele wants to do without having to pay extra, if one already has the expense of maintaining a computer and an Internet service.

There is another service that is free (but happily accepts donations), called Time Cave ([http://www.timecave.com/](http://www.timecave.com/)).  Being free, it tacks an ad onto the bottom of each message and one is limited to two messages per day.  A $12/year subscription option removes the two-message limit and the ads.

The problem with using third-party mailers such as these is that even though the message appears to come from you, a legitimate sender, the recipient's mail service or mail client may perform deep analysis of the message header and conclude that the sender address was spoofed (it was) and simply discard the message or send it to the spam folder.

---

### Post by SeijiSensei on 2010-10-25
I can imagine a way to build a system like this on the server side, but making it convenient for the client is something else again.  sendmail has a mode where it queues up mail rather than delivering it immediately as is the default.  You could run one of these queueing versions of sendmail on a non-standard port.  Mail sent to this listener would get queued.  Then you'd run the "sendmail -q" command out of cron to despool the queue.  The user would have to switch email identities to use something like this; probably not very easy.

Another method would be to use something like Squirrelmail to talk to the queueing sendmail.  Then you'd just use the web interface for messages you want to send on a delayed basis.

It would still be hard to implement the message recall function though.  As I understand Exchange, all messages are stored in an SQL database which makes it easier to implement things like delays and recalls than it is with mbox or even maildir.

---

### Post by jikamens on 2012-06-05
I know this is an old thread, but I just stumbled upon it, so on the off chance that this might be useful to someone...

The "Send Later 3" Thunderbird add-on does what you are looking for. The next version, which is currently in beta, supports SeaMonkey as well as Thunderbird.

See [https://addons.mozilla.org/thunderbird/addon/send-later-3/](https://addons.mozilla.org/thunderbird/addon/send-later-3/)

---

