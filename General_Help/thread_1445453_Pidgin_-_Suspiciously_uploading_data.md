---
title: "Pidgin - Suspiciously uploading data?"
date: 2010-04-02
forum: General Help
---

### Post by MidBSD on 2010-04-02
I wasn't sure if this should go in the networking sub-forum but figured as it wasn't specifically related to the network.

I've been noticing that when I'm not doing anything on my PC, there's sometimes network activity going on.

I have System Monitor in my system tray so I can see CPU and network activity and randomly, there is a sustained 5Kb upload.

Using iftop, I can see there's a sustained upload to xxxxxxxx.gateway.edge.messenger.live.com. Nothing is downloaded, just data sent.

It can last about 2 minutes and at 5KBs that could be my entire compressed log history.

Has anyone else noticed this or is this normal for the MSN protocol?

---

### Post by MidBSD on 2010-04-02
I've noticed there's a lot of data going up to xxxxxxx.phx.gbl too.

This also seems to be owned by Microsoft.

I found out a little more info on this page but it's old info:
[http://www.zenatode.org.uk/ian/internet/hotmail.xhtml](http://www.zenatode.org.uk/ian/internet/hotmail.xhtml)

Still digging...

---

### Post by MikeHa on 2010-04-02
Have you asked the Pidgin developers for their comments?

---

### Post by MidBSD on 2010-04-02
> **MikeHa said:**
> Have you asked the Pidgin developers for their comments?

I've not tried that yet but I will do once I make sure it's not me doing something stupid :)

---

### Post by Sharft 6 on 2010-05-04
I don't think it's you doing something stupid. when i log into my msn account with pidgin it uploads about 4.6KB/s for ages. I was about to go back to empathy but i can't block people :(

---

### Post by MidBSD on 2010-05-08
> **Sharft 6 said:**
> I don't think it's you doing something stupid. when i log into my msn account with pidgin it uploads about 4.6KB/s for ages. I was about to go back to empathy but i can't block people :(

I've not managed to do anything about this yet but I noticed just now that Pidgin is uploading again.

I thought I was the only one but glad it's not just me.

Do you have any details of where it's uploading to?

---

### Post by Linuxforall on 2010-05-08
Pidgin would knock my friend's MSN account and would reset his router from time to time, he would find it very hard to stay connected, this only happens when I log on via Pidgin MSN and he is on, strangely other friend's on MSN don't suffer the same fate, this behavior goes away once I change my client to Empathy and log on to MSN via that.

---

### Post by MidBSD on 2010-05-10
> **Linuxforall said:**
> Pidgin would knock my friend's MSN account and would reset his router from time to time, he would find it very hard to stay connected, this only happens when I log on via Pidgin MSN and he is on, strangely other friend's on MSN don't suffer the same fate, this behavior goes away once I change my client to Empathy and log on to MSN via that.

I didn't notice any uploading from Empathy but I removed it a few months ago. I will try and do some testing if I have time this weekend.

---

### Post by Sharft 6 on 2010-05-23
> **MidBSD said:**
> Do you have any details of where it's uploading to?

wireshark says i'm sending and recieveing lots of msnms packets between me and 207.46.124.52 which will lookup to by2msg4010605.phx.gbl.

I receive 76 bytes then send 916 bytes over and over until I've sent at least a megabyte and often much more i think.

---

### Post by lazyr78 on 2010-05-23
I've posted a message to the pidgin support mailing list about this, since I'm also affected. The thread can be found in the link below, but so far there's no definitive reply.

[http://pidgin.im/pipermail/support/2010-May/thread.html](http://pidgin.im/pipermail/support/2010-May/thread.html)

---

### Post by Sharft 6 on 2010-05-23
oh yea i guess we're all using pidgin from the ubuntu apt repository? maybe the ubuntu people need to look at this.

edit: installed pidgin 2.7.0 from the website and it uploads less than 100KB when logging in to msn now.

---

### Post by lazyr78 on 2010-05-24
The data being sent is due to this bug, fixed in 2.7.1:

[http://developer.pidgin.im/ticket/11532](http://developer.pidgin.im/ticket/11532)

It was triggered by having upper case letters in the email addresses of msn buddies, if I understand it correctly, and caused pidgin to send repeated malformed requests for that buddys icon.

---

### Post by Soul-Sing on 2010-05-24
I thought there was a pidgin PPA via launchpad, it is much more easy to use this and get the latest pidgin version.

---

