---
title: "Backing Up Programs &amp; Updates"
date: 2010-05-29
forum: General Help
---

### Post by TonyFordz on 2010-05-29
Hello,

I have looked all over the net trying to figure out how to back up downloads & updates from Ubuntu's list of programs & updates. Is there a way that I can download & back them up to DVD or CD so that I can provide the same programs & updates to people I give Ubuntu CD's to & also for those who do not have internet & no other means to install or update?

For example,

Say I want to download KolourPaint so that I can back it up to CD/DVD, and I would also like to backup the updates from Ubuntu so I can use them on other computers.

How can I do this?

---

### Post by TonyFordz on 2010-05-29
Alright,

Here is a list of some of the things I need if anyone can tell me how to get them & back them up to CD/DVD.

* PIXMA MP250 - Drivers for my printer which is one that is not listed in the printers list when it shows up. They have every model but mine listed.

* Codec - I need the codec for the following file types .avi, .mpg, .mp3, .mkv, .wmv, .flv, and a few others. If someone knows where I can download a codec pack for Ubuntu's default Audio/Video programs in the latest version of Ubuntu that would be very helpful. By default nothing offered on the new version plays DVD's so if your not online your basicly screwed.

* Capture Programs - I need some good screen capture programs so that I can record my desktop or open programs. When I say good think Fraps, CamStudio, and so on. If they can record in MKV, FLV, or SWF that would be awesome.

* Image appz - I need some image programs that will allow me to make transparent images & has other good features. Think Paint.net, Microsoft Paintbrush, KolourPaint as I do a lot of abstract arts free hand & have yet to find any I like other then KolourPaint, and Gimp is not one I like.

* Other Appz - I need programs that will allow me to pack/unpack the following & other types .iso, .rar, .zip, .cab, and so on. I also need other programs that may prove useful to students, children, and so on as I will be making DVD's packed with as much freeware programs & content as possible to give away with my Ubuntu CD's that I give away.

The more useful programs & content I can get the better, and keep in mind a lot of these people do not have internet or are on such a slow ISP that they cant update or download these programs themself. So if you know of something that make be useful & is easily installed on Ubuntu please feel free to reply, and be sure to ad the links to where they can be downloaded.

Thank you very much!

---

### Post by garvinrick4 on 2010-05-29
**Method #2  **
Here is away to copy your install and pass it to another install.
 
The second way of doing this doesn't create a large package, but rather a small list of apps that can be used to direct your computer to what to reinstall. This requires no installation of anything to actually run the command, but does require an internet connection. Now, this creates a list of everything, even standard system stuff, so don't get freaked out if theres stuff you've never seen on it before. Any overlap with standard stuff works itself out, it won't reinstall or duplicate things. The really nice thing about this method is that you can manually add or subtract stuff from the list.

To do this, run this command:
 
[LIST]
[*][FONT=inherit]sudo dpkg --get-selections >     installedsoftware[/FONT]
[/LIST]
 [FONT=inherit]Then, all you have to do is copy that folder over to the home f[/FONT]older of the next computer and/or after the clean install, and then run:
 
[LIST]
[*]sudo dpkg --set-selections < installedsoftware
[/LIST]
 Remember, this second method requires an internet connection. I did not copy and paste the first way to do this because it
was a lot of code and looked like quite a pain.

---

### Post by TonyFordz on 2010-06-05
Thank you very much for your reply I will try this later.

---

