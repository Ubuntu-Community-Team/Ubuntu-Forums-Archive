---
title: "Cross-Platform Data Access / Setting Up An Office"
date: 2009-08-30
forum: General Help
---

### Post by Refrozen on 2009-08-30
Hi all,

This isn't a strictly Ubuntu question, so I hope you guys will humor me anyway. I'm a software developer working on designing my new office, with a (overpowered) desktop running a two-boot Windows XP/Ubuntu Latest (with Ubuntu being the primary - actually XP is mostly just for gaming) **AND** a MacBook Pro (2007 edition) mostly for "on the road" work. 

The majority of my work requires little more than a web server, a PHP interpreter and a text editor. So this isn't an issue. My design for this at the current time is going to be a push-pull strategy: when I get home, I'll have the Ubuntu machine pull any updates from the MacBook, when I leave, I'll have the Ubuntu machine push the up-to-date files to the MacBook. The only files I'll move at all are my todo list and current projects. Everything else will remain on the Ubuntu machine 100% of the time, never touching the MacBook.

Here's **question one**. This push-pull strategy, can I automate it? Can I have the Ubuntu machine running some sort of daemon / repeated-test to see if the MacBook has connected to the network? If it connects, I then run the pull? 

So far - all is well. I have a second drive in the Ubuntu machine which I intend to use entirely for media. Music, movies, and most importantly: graphics, videos and other content necessary for my business/work stuff. This is where it gets tricky.

I don't want to send all those files to the MacBook every time I leave, they're MOSTLY unnecessary. However, I need to be able to access them on the road. One (poor) solution of course would be to run an HTTP or FTP server - there'll be an HTTP server running for web development stuff, but I don't want to use it for this.

My preferred solution would be to have it as a networked drive when I'm in the house (easy, just enable sharing on SMB/AFP) **and** automatically re-mount itself on my MacBook as a remote drive of some sort (SMB again? can I do this? how do I do this?) if I'm not in the house. I want everything on LAN in the house for speed purposes (it'd be wifi on the macbook, but still plenty fast compared to outside connections) - particularly because in the house is when most of my use of this drive will take place*.

So here's **question two**. What is my best/recommended solution for sharing this media drive with my MacBook which may or may not be on the same network as the Ubuntu machine at any point in time?
 
**Question three** is a simple one: what is your recommendation for backup software - particularly from anyone who's implemented backups before. I'm looking at sbackup and Back in Time, currently. I have two 1TB external drives that I figured I'd use to backup my important data from the Ubuntu machine (preferably Time Machine-style backups - keeping a 24 hours worth of hourlies, 7 days of dailys, a month of weeklies, and monthies till full - or whatever strategy I can implement easily). On top of that, I intend to use JungleDisk to remote backup my data - the plan is to have the Ubuntu machine remote backup the important data every 6 hours, UNTIL the MacBook receives a push of data - once I push the data, I'll disable the JD backup, run one final JungleDisk backup and wait for the MacBook to come back (since at this point the MacBook should be trusted to have the "most up to date data"); the MacBook would then be set up to allow incidental backups to JD to overwrite existing backups.

**That's all for now, hopefully someone with some experience can comment on this, let me know what they think, etc. Thanks in advance**.

* The more I think about it, most of my development while in the house will be done on the Ubuntu machine. Perhaps I can just always mount it as a remote drive?

---

### Post by SoftwareExplorer on 2009-08-30
To clarify, what's the macbook running?

---

