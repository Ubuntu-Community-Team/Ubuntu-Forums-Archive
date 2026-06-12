---
title: "Evolution"
date: 2009-07-29
forum: General Help
---

### Post by Howard Kaikow on 2009-07-29
I set up the POP and SMTP info in Evolution.

Sent a message to 4 diffferent addresses, including 3 to me.
Message was listed in the Sent mailbox.

I received all 3 messages on another computer. I may not know, for several daze, whether the 4th addressee received the message.

Since then I have not been able to Send any messages.

The next message I sent went into the Outbox, but did not get sent.

Subsequent messages were briefly listed in the Outbox, then are gone, but do not get listed in the Sent mailbox. Hmmm, maybe Evolution detected that some of the messages were duplicates?

Worse yet, the Send/Receive button on the Evolution toolbar is disabled.

Sound familiar?
How to fix?

Do I have to uninstall, then re-install Evolution?
If so, how does one do this?

---

### Post by Tamlynmac on 2009-07-29
One thought, is to check if Evolution is online.

At the bottom left corner of the Evolution window is an icon of a plug. If the plug is disconnected left click on the icon one time and it will attempt to re-connect. This plug icon should remain connected (I believe the account information must accurate or it will disconnect again).

Good Luck and Hope This Helps

---

### Post by t4thfavor on 2009-07-30
About every 10 minutes my Evolution will crash, if the actual Evolution app doesn't crash, I can be assured that one of the 3 backend processes will die, causing the frontend to lock up, and lose/not send emails. I mostly have to do:

```

sudo killall evolution
sudo killall evolution-data-server
sudo killall evolution-exchange-storage
sudo kill everything that says evolution

``` 

Then when I launch it again, I get another 15 minutes or so.

What you are describing is not out of the ordinary.

If you don't need the exchange/groupware features of Evolution, I recommend Thunderbird, as it's must more stable.

---

### Post by Howard Kaikow on 2009-07-30
> **Tamlynmac said:**
> One thought, is to check if Evolution is online.

At the bottom left corner of the Evolution window is an icon of a plug. If the plug is disconnected left click on the icon one time and it will attempt to re-connect. This plug icon should remain connected (I believe the account information must accurate or it will disconnect again).

Good Luck and Hope This Helps

Hey, are you looking over my shoulder?

That was indeed the problem.

My fat fingers carelessly clicked in that area when I received an indicator that a message had not be sent.

---

### Post by Howard Kaikow on 2009-07-30
> **t4thfavor said:**
> About every 10 minutes my Evolution will crash, if the actual Evolution app doesn't crash, I can be assured that one of the 3 backend processes will die, causing the frontend to lock up, and lose/not send emails. I mostly have to do:

```

sudo killall evolution
sudo killall evolution-data-server
sudo killall evolution-exchange-storage
sudo kill everything that says evolution

``` 

Then when I launch it again, I get another 15 minutes or so.

What you are describing is not out of the ordinary.

If you don't need the exchange/groupware features of Evolution, I recommend Thunderbird, as it's must more stable.

I just use straight mail, with fairly sophisticated filtering in Thunderbird in Windows, and filters also run on the mail server at my incoming mail ISP. I use a different ISP for SMTP> No need for any of that other stuff. If I had such need, I'd use Outlook. tHe filters at ny incoming ISP are in effect no matter what email prog I use.

For the issue I raised here, it was a fat finger problem.

When I had ubie 7.04, I did use Thunderrbird and, as this is a multiboot system, shared the address, filters and mailboxes with Windows on my desktop.

I have not yet decided whether to use Thunderbird in ubie 9.04. And, if I do, whether to share things again, as it is a pain in the back rank, to use polite chess terminology, to do so.

On my Vista notebook, I receive mail in Windows Mail in a single mailbox, but leave the mail on the server to be later read by my Windows desktop. I thought about sharing mailboxes over the network, but, thus far, I am not doing so.

In ubie, I just may opt to use Evolution the same way as I use Windows Mail in Vista.

I see no point in using Thunderbird in ubie unless I share mailboxes, etc.

---

### Post by dcstar on 2009-07-30
> **t4thfavor said:**
> 
.........
If you don't need the exchange/groupware features of Evolution, I recommend Thunderbird, as it's must more stable.

Funny then that I have been using Evolution since Ubuntu 4.10 with only a few issues with one or two of the versions, and many (many) others have been using it with no problems at all.

I really don't know why people "recommend" other things and jump to erroneous conclusions because **they** may have had an issue with a package.

---

### Post by Tamlynmac on 2009-07-30
Don't you just hate fat fingers - not to mention people looking over your shoulder.  Careful your paranoia may be showing, have you checked for cameras? :D

The truth is much simpler. I did it and it took me almost two hours to figure it out.  It's always the simple things that drive me nuts.

Not to mention, I probably could have resolved it in minutes had I been smart enough to post the question on this forum. #-o

Good Luck

---

