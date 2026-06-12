---
title: "Messed up big time I think"
date: 2011-09-22
forum: General Help
---

### Post by Stewart54 on 2011-09-22
Upgraded from 10.10 to Natty about 1 month ago. Fairly new to linux so have been experimenting with programs,what I like and what works for me. A number of programs downloaded and removed. Last evening was reading a blog about Ubuntu Tweak and cleaning system The rest of the story, tweak is doing its thing and than Terminal pops open and I am supposed to mark packages to purge. Blog suggested all but those starting en. Well I only have 4 choices all begining with aa. Can't do anything in popup box but close and than I get a message:

W:GPG error:http//ppa.launchpad.net natty Release: The following
signatures couldn't be verified because the public key is not available:
NO_PUBKEY E4010F076C2225A4
E:Could not get lock /var/lib/dpkg/lock 1 open (11: Resource temporarily
unavailable)
E: Unable to lock the admi

Figured that I had a problem, so being the genius that I am, I shut down for the night and figured that it would go away. This morning I booted up and tried to run update manager and ended up at the same purge package screen. Closed out, shut down and restarted, without running update manager. Basic programs, Chormium, T bird, Libre appear to work properly altho a little slower. Tried to download Deja Dup through the software center, but am unsure if it installed properly.

Bottom line, any thoughts on how to "fix" Natty, or what do I do from here. Biggest concern is GNUcash or whatever it is called, have 3 years of data on it which due to my own stupidity have had to enter 3 times, and I really do not wish to go thru that exercise for a 4th time.

Thoughts, suggestions, solutions and any thing else would be greatly appreciated. Thanks for your time and expertise.

Linux has an article #48910 but site is down for maintenance

---

### Post by SpatryX on 2011-09-22
I am still consider myself a newbie when it comes to using Linux. One thing that I have learned is that it is usually best to backup anything you want to save and do a fresh install of an updated system. 

For Example I used 10.04 and instead of upgrading from the update manager, I downloaded a fresh 11.04 ISO and installed from a usb key. There were a lot of changes that came with the release of Natty. I was reading on other forums that this is usually the best way to upgrade.

---

### Post by Enigmapond on 2011-09-22
Well seems that the PPA doesn't have a  public key on your computer. Not knowing what PPA it is, I can't give it to you so you'll have to figure out what PPA it is. I would uncheck all third party ppa'a and try to update again.

The other error happens when you are trying to update with two applications. You can't have Synapsis or Update manager open and run an update from the terminal.

If you don't know what PPA is unsigned, I have attached a small .sh file that when run in therminal will go through and update all the keys to your launchpad ppa's. Good Luck.

---

### Post by Stewart54 on 2011-09-22
Enigmapond,

Thanks for the response.  Not sure if this makes any sense but I seem to recall something about the public key missing in Ubuntu 11.04.  When I installed Natty, I did the upgrade using the update manager.  I thought that every was working fine.

Thanks

Stewart

---

### Post by patryk77 on 2011-09-22
In Terminal, try:
```
sudo apt-key update
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com E4010F076C2225A4
```

If that doesn't work, run:
grep -i launchpad /etc/apt/sources.list

And post the output here.

Edit: If it did work:
sudo apt-get update

Edit 2:
If it still says: E:Could not get lock /var/lib/dpkg/lock 1 open (11: Resource temporarily unavailable), then
sudo rm /var/lib/dpkg/lock

---

### Post by quasimodo69 on 2011-09-22
Stwart54...,
the bad news is the best way to solve the problem is to back up and re-install...back up being the key words.
yes there are MANY articles telling you how to micro solve this problem...but it takes forever..and not for a novice...only the GREAT GODS who are experts..LOL
Plz back up.If those records on Gnucash are so important..save them.You now see why.
If you want to remove a program...Synaptic Package Manger is the easiest (not fastest) to remove what you want to remove....program by program.
I still do not know why Ubuntu does not off a streamlined install...and let you chose what you want to add to it.I know 40% of the programs that are installed with a new install..I don't want or need.
Any other problems you run into...use Google to do a common question query on the problem..and it will point you to a resolution.Just make sure you check out ALL the resources listed in the search...and read a few from sites you trust..or try some of the solutions.
You will soon find who you can trust for online answers.

---

### Post by patryk77 on 2011-09-23
I don't see any reason to reinstall just yet.

I provided you with a solution to NO_PUBKEY and to the "could not get lock", neither of which is a *Critical* Error.

Purging packages is not really necessary, it is like saying "I never needed my spare wheel, and since I never used it and even though I don't need the space in the bottom of my trunk, I will throw it out."

It might seem like a good idea at the time, but then it might do more harm than good, but if you don't mess up the system (or get stuck in the middle of the desert with no spare) you can always put it back.

Ubuntu's package manager is actually one of Ubuntu's strongest features as far as I'm concerned, and while yes, you *can* foobar it, it can take a great beating and still give you the tools to fix its problems.

Moral of the story: Don't try to purge packages just because you can before you understand the consequences, and don't give up on a system because of some unimportant errors ;)

---

### Post by Stewart54 on 2011-09-23
patryk77

Again sorry for the delay in getting back on this.  Rolled the dice and attempted your "fix" number 1, copy and pasted in terminal.  I guess terminal did its thing because I did not see any error messages.Closed out of all programs and ran Update Manager which appeared to work just like it used to.

I have to assume that we are running OK again, till my next screwup.  Thanks to all for your time and suggestions. Very much appreciated.

A Great weekend to all

Stewart

---

