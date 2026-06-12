---
title: "Transmission Gtk to Cli problems"
date: 2010-11-08
forum: General Help
---

### Post by HitmanNumber86 on 2010-11-08
Transmission Gtk has a tendency of blowing up my processor, so I decided, in light of my taking terminal tutorials, that I should switch to Cli. I followed the steps on the transmission website to use the Gtk configuration.

Code:
hitmannumber86@Faptop-357:~$ transmissioncli -g ~/.config/transmission
Transmission 1.93 (10621) - [http://www.transmissionbt.com/](http://www.transmissionbt.com/)
No torrent specified!

I then discovered that there was no ~/.config/transmission-cli at all. So I 

Code:
cp -r transmission transmission-cli

That didn't do anything. I can't seem to get all the torrents to start. I also can't seem to start where I left off.

Code:
[email]hitmannumber86@Faptop-357:~/.config[/email]/transmission-cli/torrents$ transmissioncli -v ~/.config/transmission-cli/torrents/Pink\ Floyd\ -\ Discography\ CDRip\ \[Cov+23CD\]\[Bubanee\].fca25e4fe2c92ccd.torrent
Progress: 0.0%, dl from 0 of 11 peers (0 KB/s), ul to 0 (0 KB/s) [No^Z]

...and I know I had more then 0.0%

I'm probably doing something really stupid. Help me out guys. Thanks in advance.


Transmission 1.93
Ubuntu Lucid Lynx 10.04

---

