---
title: "Possible Problem with Computer Janitor/Wireless"
date: 2010-06-05
forum: General Help
---

### Post by left 4 shred on 2010-06-05
Alright this I want to label this as "Mystery" because I'm not sure exactly what happened. The other day I ran Computer Janitor for the first time ever in the time that I've used Ubuntu. I'm still slightly new to Linux, I've only been with Ubuntu since 9.10 So like I've said I'm fairly new but have been catching on.

Here's what happened...

I was installing Ubuntu 10.04 64bit(which I now regret) onto my girlfriend's computer. She's been seeing me use Ubuntu for the last few months and she was wanting something new for her computer so I talked to her about it and converted another being to the world of Linux. Now I tell you this here because it will be relevant later in the post.

I opened Computer Janitor on my laptop just to see what it was, I read the "This application helps you find and remove software packages you might not need anymore. It also suggests configuration changes that might benefit you." disclaimer thing in the help tab and thought "hey this could be useful." Well by default everything was automatically selected and I didn't realize it. I clicked on the thing I wanted fixed/gone or w/e and applied the change and it wiped everything on the list. Of these items included Guitar Pro 6 and Virtual Box, two apps I use frequently and the first of which I paid $60 dollars for. Now this isn't a problem in the sense that I can and have simply reinstalled them but here is where the problem lies.  After this my wireless crapped out on me. It wouldn't see anything, it was automatically disabled and everything. I finally got it "enabled" which helped a lot (sudo apt-get install sarcasm-here) considering it still wouldn't see anything or even pick up my wireless connection after doing it via connect to hidden connection (I've used this before to connect when it couldn't see anything)

By this time I had Ubuntu installed on the Desktop and since I configured the connection on Vista, I thought it might have had something to do with my wireless not working but I ruled that out after thinking to my self "If this was the problem then wouldn't I have run into it when I turned that PC off?" So I checked that off the list. (I def ruled this out whenever my Wii and the Desktop computer still picked up the connection.)

Next I thought it was due to me turning off the function that makes the screen locking after every time it goes idle since it was tedious to type my pass in all the time. I thought it could be this because every time I'd turn on my computer I'd have to type in my password on start up with keyring. Before doing this my wireless wouldn't connect and this stopped coming up so I was wondering if this had anything to do with it.

Last I put a firm belief in that w/e I did in Computer Janitor is what killed me. I also believe this after seeing that other people have had trouble with their wireless after running Computer Janitor as well. People replying to those people usually say it's rubish and that it wouldn't do such a thing but I think all of us this has happened to use 10.04 and it could just be some sort of bug or a really big coincidence, idk.

I'm going to list a few things I did to try to solve the problem:

1.I found a code from a site (unfortunately I don't remember the site so I can't credit the poster at the moment I'll post a link once I find it again.)

	```
sudo apt-get install linux-headers-$(uname -r)
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
sudo mv madwifi-hal-0.10.5.6-current.tar.gz /usr/local/src/
cd /usr/local/src/
sudo tar -zxvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-r4016-20090429/scripts/
sudo ./madwifi-unload 
```

I just copied and pasted that into the terminal and w/e it was doing it said it would take like 39,800 (around like 9 hours) seconds to finish for some reason but the OP of that forum said it ended up working for him.

2.I went to the System/Admin/Synaptic Package Manager and typed wireless into the search bar. I marked everything in the list that was installed for re-installation and clicked apply. It took a short bit but it didn't take too long. This was my own method I thought about doing. I think this is what fixed it but I'm not sure. Because my wireless just randomly popped back up a little bit after I did this. Like close enough I'd consider it but long enough after to make me wonder if it turning back on was just random.

The whole reason for this post if for input on the methods I used, advice for better tactics, solved solutions, etc. from experience Linux users and those familiar with Gnome or anyone who knows what to do in this situation. I just wanted to make people aware of this problem since I've seen it pop up a few times on the web without very useful help or positive (not that it was negative) input. This way anyone having problems with their wireless, experienced or not, and confused to no end can hopefully save time searching for hours on end for a way to fix it and coming up with similar vague to useless answers.

I would also like simple guidelines for keeping your wireless from crashing in Ubuntu to also try to prevent this problem from happening in different situations in the future.

---

### Post by ajgreeny on 2010-06-05
That, I'm afraid is one major criticism of computer janitor, and one which really ought to be flagged up more obviously when it's used.  It will find things that have been installed manually, ie without the use of synaptic or software center, and list them as un-needed on the system,because to ubuntu, of course, they are not needed, even if they are for you.

A lesson learned the hard way, I think, and one mistake that you will not repeat.  Use computer janitor with great caution in future, if you use it at all, and note carefully all the listed applications before you allow it to remove anything.

Personally, I looked at it once and have not bothered since; it appears to be a waste of space for me.

---

### Post by left 4 shred on 2010-06-05
Like I said I just didn't realize everything was checked at first. Fatal careless mistake on my part that I'm sure I won't make again, with Computer Janitor at least. I'm pretty sure I won't use it again either and I don't advise it due to my experience.

---

