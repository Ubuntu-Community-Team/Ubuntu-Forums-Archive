---
title: "Newbie(ish) Help on Media Server"
date: 2006-04-09
forum: General Help
---

### Post by Lawrence Dudley on 2006-04-09
Hi there,
First post here so please be gentle!
Quick introduction: I'm a relative newbie to linux, but I know how to use a terminal and I know to read Man pages for a lot of stuff. I'm looking to set up a media server for the WISP that I own and work for.
We have 15 users or thereabouts, and a fast (30meg) connection. What I'm looking to do is to have a way for users to download movies using a web interface and bittorrent and then to have these downloaded movies appear in on a shared network drive. 
I've tried using TorrentFlux before on [ClarkConnect Home ]("http://www.clarkconnect.com"), but it was painfully slow, presumably due to various limitations in the PHP installation that it provides. It wasn't the downloading that was slow, it was the page loads, and strangely enough from time to time it would be really fast while at other times it was awfully slow. Because of this I decided to switch to using Ubuntu because it seemed to be the largest free distribution of Linux I could find, and Debian refused to install correctly (The GRUB bootloader failed every time, as did LILO.)
Anyways, here's what I'd like:

A box with apache, torrentflux, samba file sharing and an adminitration web interface (I was looking at [WebMin]("http://www.webmin.com/").)

It should also be possible to SSH into the machine for those things I can't do through the web interface.

I tried doing a base install of Ubuntu (The one where you type server when you boot from CD ), and then installing Apache and SSHD. While SSHD worked apart from failing to reverse map the IP address, meaning I had to change the grace time to 300 to get it to work with an irritating delay, Apache didn't seem to start at all, and a port scan of my box didn't show 80 as an open port.

I have now done a standard install of Ubuntu, as I would quite like to have the GUI to configure it all as it's easier than SSH'ing and using VI to edit the config files in /etc as I was previously.

I think I can figure most of the Apache stuff out, but if 

1) Anyone has any reccomendations on what web administration interface to use to fit my purpose, and

2) Anyone knows how to disable the reverse map ip address stuff in SSHD

I'd be really grateful.

Thanks a lot, and I look forward to having some success with Ubuntu. So far I am impressed! :-)

---

### Post by 123buyer on 2007-07-24
I am a Newbie Is the server working? How can I set up a server like this?

---

