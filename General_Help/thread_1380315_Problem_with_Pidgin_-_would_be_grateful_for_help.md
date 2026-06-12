---
title: "Problem with Pidgin - would be grateful for help"
date: 2010-01-13
forum: General Help
---

### Post by Angelic_fruitcake on 2010-01-13
Hi, 

I hadn't logged into Pidgin for about a month, but on trying yesterday it came up with this message:

"disconnected,
Our protocol is not supported by this server"

The server it has always listed is: messenger.hotmail.com

my protocol is set to MSN as I use a hotmail.com email account.


If there is any advice anyone could give, it would be greatly appreciated.

I hope this is a simple one, but just to warn you I am fairly lousy with computers, so be gentle with me if it's complicated please.

---

### Post by howefield on 2010-01-13
Nothing has changed since you last used pidgin ?

What version are you using, you might need an update.

---

### Post by Angelic_fruitcake on 2010-01-13
Hello!

Sorry, I meant to say: I thought that I needed to update, so I installed all available updates yesterday, but to no avail. I'm afraid I don't know how to find out which version I'm using. *embarrassed face*

---

### Post by howefield on 2010-01-13
Is there a Help menu option on the Pidgin window, select About Pidgin from it, should tell you there what version it is.

Do you know which version of Ubuntu you are using ?

---

### Post by roadtripdave on 2010-01-13
To find the version of Pidgen your using you can click Help and then About.  Maybe try deleting that old account and try recreating it again?

---

### Post by Angelic_fruitcake on 2010-01-13
Of course, thanks. It's version 2.4.1

and I'm on 8.04 Hardy Heron

---

### Post by Angelic_fruitcake on 2010-01-13
I tried the delete + recreate, but that didn't work. Thanks for the suggestion though.

---

### Post by howefield on 2010-01-13
It's a bit of an an old version, if it were me, I'd update to the latest.

If you feel up to entering two commands into a terminal window and then applying the updates, go to this website and follow the instructions.

[http://pidgin.im/download/ubuntu/](http://pidgin.im/download/ubuntu/)

---

### Post by Angelic_fruitcake on 2010-01-13
My computer is old and rickety, I don't know if it would cope with the Koala! I am planning a new laptop in the not too distant though.

Thanks I'll give that a go.

---

### Post by howefield on 2010-01-13
Just to clarify, I am talking about updating to a newer version of Pidgin, not your Ubuntu version :)

---

### Post by Angelic_fruitcake on 2010-01-13
Hi again, 

I copy/pasted the commands into the terminal and the last line of text now reads:

gpg: keyserver receive failed: keyserver error

As you can probably tell, I have no idea what this means. Should I give it another try?

---

### Post by howefield on 2010-01-13
> **Angelic_fruitcake said:**
> gpg: keyserver receive failed: keyserver error

Try again.

I have just tried and although it took a bit of time, it did come through.

---

### Post by Angelic_fruitcake on 2010-01-13
I repasted the commands. It hasn't come up with the previous message at the end, but in the middle this time. The end now says the following:

 echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
>     sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu)   hardy main

 I'm not quite sure how to tell whether it has 'come through'. I opened my update manager, but it's still telling me that my system is up-to-date, so I'm guessing not yet. (Haha, I did think you were saying that hardy was too old before, oh well...)

---

### Post by howefield on 2010-01-13
Bring up the update manager and press the Check button.

See if any updates appear.

---

### Post by Angelic_fruitcake on 2010-01-13
aha! one thousand years later and I'm downloading the latest Pidgin - just in time, as I was about to threaten to turn it into a tasty, virtual pie. - I hope this works :)

---

### Post by howefield on 2010-01-13
Great :)

I suspect it will, however if it doesn't, then at least you have the latest Pidgin (version 2.6.5) and we will move on to the next go.

PS. Hardy is old, (in Ubuntu terms) but I'd never suggest you update the whole operating system just for an instant messenger :)

---

### Post by Angelic_fruitcake on 2010-01-13
Thank you so much for your help - :D Everything is sorted. Right - I can now talk to people again. :D

---

### Post by Angelic_fruitcake on 2010-01-13
PS. Hardy is old, (in Ubuntu terms) but I'd never suggest you update the whole operating system just for an instant messenger :)[/QUOTE]

Ah... but the boyfriend and friends are too cheap to use the phone like normal people, so it might have been worth it! ;)
Cheers, and have a good evening. I'd better mark this one as solved now.

---

### Post by howefield on 2010-01-13
> **Angelic_fruitcake said:**
> Everything is sorted.

Lovely Jubbly :)

Every so often, the different IM providers change the protocols and settings in order that we can't use "aggregators" like Pidgin. So the Pidgin developers need to release an update.

Now that you have the repository in your sources.list (the result of the terminal commands you executed) every time Pidgin release an update, you will get it through the update manager automatically.

---

