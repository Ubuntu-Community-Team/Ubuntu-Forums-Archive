---
title: "need a good bittorrent client that can handle magnet links."
date: 2012-03-27
forum: General Help
---

### Post by silvama11 on 2012-03-27
Transmission,as far as I can tell,doesn't handle magnet links. TPB now only uses magnet links so... what is a fast,GUI based client that is stable and does? On the Win7 side of my rig I use and am  happy with utorrent but would prefer to use a Linux client on my Ubuntu 11.10 side (dual boot).

---

### Post by ccrs8 on 2012-03-27
Transmission handles magnet links flawlessly for me.  When TPB moved to them, Transmission handled them just like the old style links.

---

### Post by silvama11 on 2012-03-27
> **ccrs8 said:**
> Transmission handles magnet links flawlessly for me.  When TPB moved to them, Transmission handled them just like the old style links.
okay so how do u get it do that? Firefox doesn't recognize them and using "copy link location" is great if as with utorrent yoy have a way of getting it going. So if you can clarify the process of using magnet links with Transmission it would realy be aap.

---

### Post by colin.p on 2012-03-27
I use Deluge (in repos) and it handles magnet links just fine.

---

### Post by papibe on 2012-03-27
In case Firefox won't redirect the magnet links to transmission, or won't give you a chance to define the application to launch, you can do this:
[LIST]
[*]Right click on link containing the magnet link.
[*]Select 'Copy Link Location'.
[*]Open transmission and go to File -> Add URL.
[*]Paste the link.
[/LIST]
Hope that helps,
Regards.

---

### Post by ccrs8 on 2012-03-27
> **silvama11 said:**
> okay so how do u get it do that? Firefox doesn't recognize them and using "copy link location" is great if as with utorrent yoy have a way of getting it going. So if you can clarify the process of using magnet links with Transmission it would realy be aap.

I wish I could help you.  For me, Transmission handles magnet links exactly the same way it handles the traditional links.  I click on it, a dialog box opens asking me what program I want to open the link with, I pick transmission, and my file downloads.  I did nothing at all to make this happen.  I read that TPB was changing to magnet links and that users may need to update their client to handle them, but I personally had to do nothing.

I posted basically to let you know that you didn't have to get a new bittorrent application - more than likely you just needed to change something in the application or system configurations.

EDIT: FYI, I'm using Xubuntu 11.10, although I don't know why that would matter.

---

### Post by jerome1232 on 2012-03-28
When you click a magnet link, firefox should ask you what you want it to do, you then choose transmission as the default program to open the magnet link. Check under edit->preferences->Applications that you don't have some other application set to handle magnet links.


This is a firefox issue, not your bit torrent clients issue.

[http://support.mozilla.org/en-US/kb/Options%20window%20-%20Applications%20panel?as=u](http://support.mozilla.org/en-US/kb/Options%20window%20-%20Applications%20panel?as=u)

---

### Post by colin.p on 2012-03-28
I use Deluge on my download server and have never had any issues with it. However, I needed to download something on my laptop and tried to use Transmission but when I selected it to open magnet links (in FF), nothing happened. I "futzed" with it for a few minutes, then said screw it and installed Deluge. It worked perfectly. I don't know why Transmission wouldn't open magnet links, just that Deluge (at least for me) works.

edit: Interesting, I looked at the above link and in my FF "preferences-applications", Transmission was not listed at all to open Magnet links, even though, when I first tried to open a Magnet link, Firefox did have Transmission listed in the "open with" box, so I selected it and assumed since I was able to select it, it would work. I then figured it was going to work, but it still isn't listed in Firefox at all. I don't know what the problem is and am not going to bother manually selecting it from the filesystem, but since I installed Deluge, Firefox picked it up so it is the only torrent program that Firefox even sees to open Magnets.

---

### Post by B1U3SK13Z on 2012-07-20
[http://www.utorrent.com/downloads/linux](http://www.utorrent.com/downloads/linux)

utorrent is the best!


The other option is use wine and use the windows version. it works pretty sweet.

---

### Post by M!K3_$ on 2012-07-20
I use the transmission-daemon with the web interface and adding magnet links is as easy as copy/paste.

I'm sure, as our fellow forum-mates have pointed out, you can add them in the desktop application as well.

---

### Post by kelvin spratt on 2012-07-20
qbittorrent also handles magnet links. there is a firefox add-on to handle magnet links, tranmission also does the job.

---

### Post by sophie2cu2 on 2012-07-20
I've got uTorrent for Ubuntu set up, but I can't make it work. When I click on a magnet the only choice I get is Transmission.
What to do to get uTorrent going?
Thanks,
S

---

### Post by papibe on 2012-07-20
Hi sophie2cu2.

utorrent for Linux is web-interface only. You have to:
[LIST]
[*]copy the magnet link from the download page.
[*]open the utorrent web interface.
[*]click either add a torrent, or add from url (don't remember the actual option name).
[*]paste the magnet link.
[/LIST]
Regards.

---

### Post by sophie2cu2 on 2012-07-22
Gee Papibe,
It works. Thanks. You're a star.
S

---

### Post by sakamoto on 2012-07-29
transmission should be sufficient for torrents these days - never faced any issues with transmission

---

