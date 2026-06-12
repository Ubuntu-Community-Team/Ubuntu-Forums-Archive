---
title: "Connecting SABnzb to bt internet news groups"
date: 2011-01-15
forum: General Help
---

### Post by brynellis on 2011-01-15
Hi

I'm using SABnzbd and it looks like it's actually working which is cool because I've been struggling with PAN always thinking every file I download is corrupt!

However, in the log messages when something is downloading I get this scrolling up every 20 - 30 seconds:


2011-01-15 11:40:28,081::INFO::[downloader:721] Thread [email]4@news.btinternet.com[/email]:119: Server news.btinternet.com:119 requires user/password
2011-01-15 11:40:57,776::INFO::[downloader:465] [email]1@news.btinternet.com[/email]:119: Initiating connection
2011-01-15 11:40:57,836::INFO::[downloader:465] [email]2@news.btinternet.com[/email]:119: Initiating connection
2011-01-15 11:40:57,900::INFO::[downloader:465] [email]3@news.btinternet.com[/email]:119: Initiating connection
2011-01-15 11:40:57,960::INFO::[downloader:465] [email]4@news.btinternet.com[/email]:119: Initiating connection
2011-01-15 11:40:58,068::INFO::[downloader:654] Connecting [email]1@news.btinternet.com[/email]:119 finished
2011-01-15 11:40:58,151::INFO::[downloader:654] Connecting [email]4@news.btinternet.com[/email]:119 finished
2011-01-15 11:40:58,211::INFO::[downloader:654] Connecting [email]3@news.btinternet.com[/email]:119 finished
2011-01-15 11:41:01,262::INFO::[downloader:654] Connecting [email]2@news.btinternet.com[/email]:119 finished
2011-01-15 11:41:01,288::INFO::[downloader:721] Thread [email]2@news.btinternet.com[/email]:119: Server news.btinternet.com:119 requires user/password
2011-01-15 11:41:30,932::INFO::[downloader:465] [email]1@news.btinternet.com[/email]:119: Initiating connection
2011-01-15 11:41:30,992::INFO::[downloader:465] [email]2@news.btinternet.com[/email]:119: Initiating connection
2011-01-15 11:41:31,054::INFO::[downloader:465] [email]3@news.btinternet.com[/email]:119: Initiating connection
2011-01-15 11:41:31,116::INFO::[downloader:465] [email]4@news.btinternet.com[/email]:119: Initiating connection
2011-01-15 11:41:31,286::INFO::[downloader:654] Connecting [email]3@news.btinternet.com[/email]:119 finished
2011-01-15 11:41:31,336::INFO::[downloader:654] Connecting [email]4@news.btinternet.com[/email]:119 finished
2011-01-15 11:41:31,438::INFO::[downloader:654] Connecting [email]2@news.btinternet.com[/email]:119 finished
2011-01-15 11:41:34,445::INFO::[downloader:654] Connecting [email]1@news.btinternet.com[/email]:119 finished
2011-01-15 11:41:34,474::INFO::[downloader:721] Thread [email]1@news.btinternet.com[/email]:119: Server news.btinternet.com:119 requires user/password
2011-01-15 11:42:04,099::INFO::[downloader:465] [email]1@news.btinternet.com[/email]:119: Initiating connection
2011-01-15 11:42:04,159::INFO::[downloader:465] [email]2@news.btinternet.com[/email]:119: Initiating connection
2011-01-15 11:42:04,219::INFO::[downloader:465] [email]3@news.btinternet.com[/email]:119: Initiating connection
2011-01-15 11:42:04,281::INFO::[downloader:465] [email]4@news.btinternet.com[/email]:119: Initiating connection
2011-01-15 11:42:04,342::INFO::[downloader:654] Connecting [email]1@news.btinternet.com[/email]:119 finished
2011-01-15 11:42:04,351::INFO::[downloader:654] Connecting [email]2@news.btinternet.com[/email]:119 finished
2011-01-15 11:42:04,412::INFO::[downloader:654] Connecting [email]3@news.btinternet.com[/email]:119 finished
2011-01-15 11:42:07,468::INFO::[downloader:654] Connecting [email]4@news.btinternet.com[/email]:119 finished
2011-01-15 11:42:07,493::INFO::[downloader:721] Thread [email]4@news.btinternet.com[/email]:119: Server news.btinternet.com:119 requires user/password

Now, as you can probably see I'm on BT Total broadband which is why I'm using news.btinternet.com and all the places I've found for the settings of this it says you don't need to use your username and password because you're already authenticated through you broadband router connection (BT home hub v2).

Anybody any idea what the problem is here?  It seems to be downloading the files but doing it a lot slower than I remember when I've done this using Newsleecher on a Windose box.  I'm wondering if each iteration of this sequence of messages is my session logging out, back in again, downloading a bit then getting kicked off again hence making the download slower.

Any ideas please?

Ah, forgot to mention I'm using Ubuntu 10.10 Maverick Meerkat 64-bit.

---

