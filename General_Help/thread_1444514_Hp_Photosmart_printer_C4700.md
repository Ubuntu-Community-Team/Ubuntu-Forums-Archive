---
title: "Hp Photosmart printer C4700"
date: 2010-04-01
forum: General Help
---

### Post by Mr.Kappa on 2010-04-01
Hi guys! apparently I cannot manage to print anything with HP printers. I've tried downloading and compiling hplip from the hp website but nothing changes. When I try to print a pop-up box alerts me that the job has been launched and when it disappears another one comes up telling the job is finished.. but nothing comes out of the printer :confused:
Also the print queue continues to show up the job... What should I do??? I urgently need to print a lot of university material... Please help me!!

---

### Post by Mr.Kappa on 2010-04-02
Anybody?

---

### Post by OzOle on 2010-04-02
Hi, I have two HP PhotoSmart printers: C4280 and a 209A. They both run perfectly under Ubuntu 9.10 using hplip installed via Synaptic. No separate download or compile. Which version of Ubuntu are you running?

---

### Post by Mr.Kappa on 2010-04-02
I'm running karmic. Is it possible that cups is screwed somewhere?

---

### Post by OzOle on 2010-04-02
No, I wouldn't have though so. I have also tried connecting the C4280 (same type of printer as your C4700) to an older PC running Kubuntu 8.04 and I had no problems getting it to work.

Hmmm, I don't really know what to suggest either than deinstall and reinstall the software perhaps including cups. If there is someone else with more knowledge of this who could make some suggestions, then it would be helpful. Sorry, I can't be of much more assistance, other than to confirm that I have got the printer working fine.

**New information!**
After writing the above I found a newer version of HP's driver and control software on their site here:
[http://hplipopensource.com/hplip-web/index.html]("http://hplipopensource.com/hplip-web/index.html")
where they say:
"The current version of the HPLIP solution is version 3.10.2"

I downloaded that onto my Ubuntu 9.10 Karmic Koala PC.
You need to follow their direction carefully and be VERY patient, it takes quite a while for it to install because it makes, compiles and installs the software for you. I had no problems with it, it just took quite a long time, but it works very well.

You decide if you want to try it.

When you have got your printer to work then I suggest you post here what you did, so that others with a similar problem can learn from your experience.

---

### Post by Mr.Kappa on 2010-04-03
Mmmm! I tried removing all my printing drivers and installing the one you suggested from hp. Compiling it was not a problem but still it tells me that the printing job has been completed a few seconds after launching it. :mad:
Amen.. I'll print from my old xp partion!
Still, thank you very much for the suggestions! ):P

---

### Post by Sef on 2010-04-03
Before downloading anything, did you check to see if the printer worked?  Most HPs just need to be plugged in to work.

---

### Post by Mr.Kappa on 2010-04-03
Before upgrading cups (and some libraries I think) the printer worked perfectly. I tried to downgrade it but it didn't work anymore. Is it possible that some configuration files are still around messing things up???

---

### Post by OzOle on 2010-04-03
Howdy, Mr. Kappa,

What do you mean when you say:
"I tried to downgrade it"???

And, if it **_was_** working before, why 'downgrade' it?

There must be an answer to your problem somewhere!

---

### Post by Mr.Kappa on 2010-04-03
Wait. :(The printer since a few weeks ago stopped working after an upgrade of cups and some of its libraries. From then I tried a few options to get the printer working again:

[LIST=1]
[*]downgrading the upgraded cups
[*]installing hplip and hpijs packages
[*]dowloading the hplip packages from HP and compiling them
[*]uninstalling cups & hplip
[/LIST]
Nothing. The printer doesn't work (via usb and network) with my ubuntu karmic os.

Thanks guys for the comprehension :p

---

