---
title: "Odd Issues with 10.04"
date: 2010-04-30
forum: General Help
---

### Post by GSF1200S on 2010-04-30
First of all, allow me to say this is not a rant thread. Ive been around awhile and Im very happy with the 10.04 release and how far Ubuntu has come. 

I do want to ask though of a few problems Ive discovered that are very odd, and see if anyone else can duplicate/replicate these issues. Ill file a bug report, but considering it could just be my system, Id like to see if others can confirm these bugs.

1) I went to burn a copy of Netbook Edition which I currently have seeding. The first time I used Gnomebaker, after placing in my external DVD drive, it informed me that I had the wrong nomenclature (64bit) and that I needed to use i386. Ok, I figured I must have selected the wrong one. I then used brasero and went to select the Netbook ISO. I double-triple checked I had the proper one selected, and clicked open. I then see that Brasero has my DesktopAMD64 version selected as the version to burn- somehow it seems to me the file open GTK dialog is selecting a different file than I do. Eventually it decided to select the one I wanted, including the GTK open dialog not responding to any interaction other than Cancel or Open. I then was reminded of having the same issue with pidgin- if I try to send a buddy a file, it sends them the wrong one UNLESS I drag and drop the file into the pidgin file. Im on XFCE, so can anyone on Gnome replicate this issue? This leads me to number

2) With deluge downloading a file, especially as the rates approach 1MB/sec, my UI (desktop- all of it) gets extremely slow on both screens. Upload effects my web browser page loading speed, despite the upload total being under 100K/sec (I suspect my ISP throttles bittorrent upload speed, and my upload speed sucks as it is). This is despite my being able to download at well over 1.5MB/second. My web pages take at least 4 times longer to load under this condition.

3) Specific to Thunar: Drag and Drop causes a TON of crashing. To be fair, this is likely a thunar problem; Ive had the same issue with Arch and Sidux. Im not sure if this is as a result of Thunar not appreciating my dual head setup or what- I never have an issue with Thunar when Im running on one screen. This issue is just as prevalent on 10.04 as it was 9.10. 

I would appreciate if anyone having these issues would post here so I can file the appropriate bug reports; I dont want to burden the devs with crap that is due to something specific on my system when they are trying to sort through inevitable bugs that come with release day.

Thank you..

---

