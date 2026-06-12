---
title: "how to hide paid apps from software-center?"
date: 2012-01-09
forum: General Help
---

### Post by blueberries on 2012-01-09
hello,

since i have no ability at the moment buy applications, i want to hide "for purchase" apps from the software center. i did some digging online about it and so far found no solution..

 - software-sources have multiverse entry, but that will hide non open source apps that distributed for free
 - in the software-center, under "All Software" button, there are several option. even if i choose to stay only with "provided by canonical" i loose the ability for filter by category, and its valid only for current session. (like [here]("http://askubuntu.com/questions/85534/how-to-disable-hide-paid-apps-from-ubuntu-software-center"))
 - solution proposed [here]("http://askubuntu.com/questions/47997/is-it-possible-to-remove-the-commercial-programs-section-from-the-software-cente") no longer works - chanel.py no longer contains code they suggest to comment.

any ideas?

thx,
bb.

---

### Post by 1clue on 2012-01-09
I don't really have a happy answer for you, but rather a few questions.  I'm not trying to be rude, but it's probably going to be interpreted that way:

What's wrong with looking at the license terms and see if they're agreeable to you?  You really should do that no matter if it's "free" or not.

Why is it so painful to see all available options?  Does Google have an "only free" button, and do you use it anyway?

Ubuntu's mission is to make a distribution which works well with other computers in a business environment, and in order to do so some commercial options are a really good idea.  This is one of the major decisions a distribution makes:  Whether or not to allow non-free software to be easily installed.  There are lots of distributions which decide against, Ubuntu decided for it.  I use Ubuntu because it allows easy installation of non-free software.

---

### Post by Azdour on 2012-01-10
Hi,

If I understand what the OP is saying is that they have:

> no ability at the moment buy applications

To me that that means they have no objections to non-free software but for one reason or another cannot pay to use them.

I believe the actual request is to ask if it is possible to filter out paid applications from the list the software centre presents. 

On my Ubuntu 11.10 it looks like they read the available channels from a database in the method _get_channels_from_db (in channel.py), but without reasonable knowledge of how the software centre works I cannot suggest what code to alter or change. 

A code change is what I believe you need because the Software Centre does not seem to have any options in it via the UI to filter out channels.

So unless someone with more knowledge comes along and proposes a code solution you may have to live with it.

---

