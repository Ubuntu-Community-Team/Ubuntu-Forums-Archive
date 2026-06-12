---
title: "BIOS Settings Not Accessible"
date: 2012-02-10
forum: General Help
---

### Post by ScottS75 on 2012-02-10
Hi -
I've been using an Acer Revo 1600 as an HTPC for about a year now. Bought it second hand, and it's been working like a champ for my downloaded movies. I have XBMC running on top of 10.04 and movies run great. It's got 2MB of memory.
However, when trying to stream video it runs very slow and stuttery. Watching Hulu is unbearable.
I tried to follow the instructions of a very devoted Revo user and his settings to maximize the little nettop ([http://revohtpc.com/revo-htpc-setup-guide/revo-setup/](http://revohtpc.com/revo-htpc-setup-guide/revo-setup/)). He recommends adjusting memory settings in the BIOS.
I've tried to do it, but pressing ESC, F1, F2 etc, etc, doesn't let me into the BIOS to change the settings.
Any suggestions on accessing the BIOS screens or for the poor streaming performance?
I'm pretty new to the Linux world, but learning as I go!
Thanks,
Scott

---

### Post by Gremlinzzz on 2012-02-10
did you try hitting Delete repeatedly when the machine is first switched on.

[http://www.fixya.com/support/t3046723-get_access_bios_settings](http://www.fixya.com/support/t3046723-get_access_bios_settings)

---

### Post by ajgreeny on 2012-02-10
You can not have read the link you showed us very carefully, as that tells you to hit **Del** at power-on.

The other possibility is that somebody (you?) has put a password on the BIOS, but that would not totally stop you; it would just ask for the password.

---

### Post by drmrgd on 2012-02-10
Have a look at this link:

[http://revohtpc.com/revo-htpc-setup-guide/revo-setup/]("http://revohtpc.com/revo-htpc-setup-guide/revo-setup/")

If you go down to the section about adjusting the video RAM, it does indeed say that 'del' is the key to enter the BIOS.  Granted the information is a bit old, and hopefully they have not significantly changed things since then.

---

### Post by ScottS75 on 2012-02-11
All -

Terrific!  I don't know how I missed that, just too many sources reviewed, I guess.  I was juggling the Ubuntu manual and these instructions and the computer guide too.  Who knows.  Anyway thanks for pointing out the oversight.  I was able to get into the BIOS settings and confirm the options were already set to match the Revo guide suggestions.

I need to do some more fiddling.  Even after downloading Chrome and confirming the latest Flash along with hardware acceleration in the browser, video streaming is barely improved (YouTube, Hulu).

Thanks for helping me past the first hurdle!

Scott

---

### Post by drmrgd on 2012-02-11
> **ScottS75 said:**
> All -

Terrific!  I don't know how I missed that, just too many sources reviewed, I guess.  I was juggling the Ubuntu manual and these instructions and the computer guide too.  Who knows.  Anyway thanks for pointing out the oversight.  I was able to get into the BIOS settings and confirm the options were already set to match the Revo guide suggestions.

I need to do some more fiddling.  Even after downloading Chrome and confirming the latest Flash along with hardware acceleration in the browser, video streaming is barely improved (YouTube, Hulu).

Thanks for helping me past the first hurdle!

Scott

Cool!  Glad that worked.

I'm not sure if this is relevant, since I don't know much about those systems, but you might give [Flash-AID]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") a try.  Even though it's a plugin for FireFox, it will allow you to update the system Flash plugin and will fix Google-Chrome Flash problems as well.  There's also a [Flash-AID megathread]("http://ubuntuforums.org/showthread.php?t=1491268")  where you might be able to get some info and answers to help you fix it.

---

### Post by ScottS75 on 2012-03-19
Sorry, just checked back into the closed thread and found your suggestion for Flash-Aid.
A couple weeks back I ended up installing that and another add-on FlashVideoReplacer.  These have worked great for sites like YouTube.  However, I also want to use my HTPC on Hulu, and Amazon Instant Video, but neither seem to be using video that's interpreted as flash.  The whole browser and OS freeze up and I need to unplug to reboot.
So I'm still working on that aspect, and will submit another question.
Thx again,
Scott

---

