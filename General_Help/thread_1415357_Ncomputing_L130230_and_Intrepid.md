---
title: "Ncomputing L130/230 and Intrepid"
date: 2010-02-24
forum: General Help
---

### Post by dyvid on 2010-02-24
I wanted to know anyone's experience with the new deb package ncomputing released for Intrepid.  I've used their products and fought my way through to make them work.

I was able to get ncomputing to work for a short while with intrepid, but upon installing the video drivers (and rebooting) the l230 hasn't been able to connect to any other host.  (With Intrepid running).

I've updated the firmware but the box still refuses to connect, for awhile it would say TS error (....).  The system log only showed,

Date  SystemName ncltsd [6198]: ERROR: NULL == video
 " "     "    "   "   "     "    " " " " " " " " " [18043]: ERROR: SrvCli.CreateSession () failed! (3211426, 1869984)

Any help I can get would be much appreciated.  If I forgot anything of I apologize, as you probably noticed it's my first time using the forum and I have only been using Ubuntu for a little less than a year.

Thanks for you time and support,
~Dyvid

---

### Post by jnyabicha on 2010-03-01
Today we have released our L-series vSpace software for Linux.  This Linux software runs on a standard installation of Ubuntu 8.10 and includes all the powerful desktop virtualization capabilities of our award-winning vSpace for Windows.  It also
includes all of our software protections and uses the same registration process as vSpace for Windows.


Also, this new version supports USB and microphone on the L230 (features not available)). Future versions of vSpace for Linux (both L-series and X-series) will normally have their initial releases available for installation on an Ubuntu distribution.


You can download this new Linux release and the documentation directly from the software download center in the support section of the NComputing website.

NComputing's multi-user technology enables greatly expanded computing capabilities by allowing up to 30 users to simultaneously access a single PC. This multi-user desktop experience supports simultaneous users at lower costs in an easy to use, set-up and maintain environment that is eco friendly. The result is a significantly lower cost of computing, on-going management and power usage that is many times better than a
traditional networked PC model.

Since most users only utilize a few percent of today’s powerful PCs, NComputing leverages this power with small access terminals and proven software that enables a single PC or server to support up to 30 users at once. The goal in the multi-user environment is to maintain the performance of the host computer across many users; and as long as the host CPU, memory or LAN performance is not constrained, each access terminal should operate at a speed similar to the host.

NComputing supports both Linux and Windows. From Windows 2000, Windows XP to Windows Server 2000 and Windows Server 2003. Linux distributions supported include Ubuntu/Edubuntu/kubuntu, SUSE, FEDORA, DEBIAN, CENTOS, REDHAT and others. What I like about the company is their R&D, they are always researching and improving on their products. Remember the Office Station L100? Then came the NComputing L100, and NComputing L1200, and now NComputing L130,NComputing L230. Not to forget the NComputing Xtenda X300.

In East Africa (Kenya, Uganda, Tanzania, Rwanda, Burundi, Congo, Ethiopia, Somalia) you can contact OPENCODE SYSTEMS at [www.opencodesystems.com](www.opencodesystems.com). Their telephone is +254-020-3560507/8, +254-722-681971, +254-721-219190

---

### Post by dyvid on 2010-03-01
Wow, just got to love those bots/crawlers.

Umm for anyone who is wondering.  I did get the ncomputing device to work.  I had to start from scratch adding one piece of software at a time.  I think adding the nvidia drivers from nvidia.com was the issue.  I am currently using the restricted hardware 177, and it seems to be running fine.

For anyone else wondering, I went to CES and spoke with one of the programmers of the L-series.  He informed me 10 days after the show there would be support with ubuntu 9.10....that would have been Jan 20...it took them until a week from last Friday to get out the 9.10 version, they also said it would support mic and usb....which I have yet to try, and I honestly don't believe it will work anyway.

---

### Post by jhun_jhaye on 2011-01-31
ncomputing on 8.10 works just fine. it just complicates on the video driver so better i guess let the it use the default. anyone might have other solution pls assist.

---

### Post by dyvid on 2011-01-31
I think you'll find that Ncomputing has stopped development in linux.  I got ncomputing working, but it's one of those things that you can't update the video card settings or else you break the installation of ncomputing.

They aren't the best company out there.  My friend is working on reselling the manufacturer directly, which is about 1/3 or 1/4 the price, and they are using open source linux software, which means we might actually have a viable solution.

I have little, well no faith that ncomputing will ever release a professional, solid of their software for linux.  You should see their forums, so many unanswered replies and pleads for help, and they just turn a blind eye.

The guy I spoke to CES last year said he was the administrator of the forums and he just wanted to take them down.  He said he would pull his staff away from it, and it looks like they have.

---

### Post by jhun_jhaye on 2011-02-21
I've been running 5 servers of ubuntu 8.10 on different pc's with different specification. I found out that there are some incompatibility issue with some onboard NIC like sis191 and via rhine onboard nic so with the bug issue on dhcp. Server will set automatically on dhcp even if u set it with static IP.

---

### Post by jhun_jhaye on 2011-02-21
Guys i wanna ask if what the best ncomputing server PC specification that would run 15 terminals in a stable state using ubuntu 8.10 interpid. Thus ncomputing had a limited terminals on ubuntu or they just matter on the server specs u had? i have heard that  windows had limited terminals  on XP.

---

### Post by dyvid on 2011-02-21
I heard 30 can be ran from the x series, but you should be able to get upwards to 100 from the L-series.  Or so they claim, you can't use XP anymore due to a lawsuit against Ncomputing from Microsoft, since it was avoiding licensing.

Now you have to use one of the Longhorn Operating Systems, and you get charged out the nose for each license you use.

Ncomputing, at least when I last used them, could only utilize 2 cores and 2gb or ram...I think they might have boosted it to 4gb of ram.  I don't know if there has been any changes to cores.

But if you want to save on licensing, just use Ubuntu, someone claims you can use an open source thin client software to use Ncomputing, which is claimed to work better than Ncomputing's software.

Regardless, the product was made for Windows, they threw in a little Linux support, which has since died...so GL.

---

### Post by jhun_jhaye on 2011-02-22
wow L Series can go up to 100 terminals but i guess ur server should be  high  end. I been using dual core cpu with 2 gb ram and it work fine with but a little sluggish performance on 6 terminals.  With 1 gb ram cant handle 6 but working  well on 3 terminals. Is there a tweak to improve its performance?

---

### Post by dyvid on 2011-02-22
Not that I know of.

Though the sluggish performance might stem from the fact that the Ncomputing software can't pass through video acceleration like windows, so you're pushing everything to the cpu and ram.  If you notice you can't watch flash...well.  Everything is slow because of the lack of video support.

I guess you could try a lightweight login/gui like xfcx or whatever it is.  Sorry just woke up.

---

### Post by br4d on 2011-12-22
Sorry for the wake up. But I can't resist to answer the question if somebody has successfully using L230 on Ubuntu. I have tried using L230 with Lucid and now quite happy with it. If you have problem with session reconnect, just read [[COLOR="Navy"]**my blog**[/COLOR]]("http://share-and-grow.blogspot.com/2011/12/ncomputing-l230-cant-reconnect-on-lucid.html").

---

