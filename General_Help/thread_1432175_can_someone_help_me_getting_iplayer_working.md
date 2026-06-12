---
title: "can someone help me getting iplayer working?"
date: 2010-03-17
forum: General Help
---

### Post by ice60 on 2010-03-17
i want to watch a programme on bbc iplayer, but it doesn't work at all! i'm using intrepid with firefox and opera.

i've tried replacing every version of my flash player
downloading the iplayer downloader - i always get an error. i think it uses ftp and i allowed a direct connection for ftp
disabling my http proxy
replacing my hosts file to default
disabling all ad blockers
downloading and installing the lastest version of ubuntu - it won't even start the boot process even with every possible kernel parameter i can find on the internet
downloading suse - won't boot on my spastic laptop
i even looked for the programme on other download and streaming sites and of course some idiot uploaded it to rapidshare in about 6 parts so i didn't even bother lol

i don't really expect someone to know the answer so i'm getting prepared to go and  massacre everyone at the bbc.

---

### Post by e1f on 2010-03-17
So you're able to navigate to bbc's iplayer page but the videos won't play?  

Do they give you an error or simply show a black box?  

Are you in the UK?

Does any flash content work? i.e youtube

Also are you connected directly to the Internet or do you have to go through a proxy in order to access the web?  If so that may very well be your problem, Flash ignores the system wide proxy settings, you'd need to use VPN or something similar if you don't have a direct connection.

You may be interested in using a console tool named get-iplayer, this will download a flv/mp4 version of bbc content and won't require you to use their web interface.

> sudo apt-get install get-iplayer

---

### Post by ron999 on 2010-03-17
...................

---

### Post by ice60 on 2010-03-17
omg now i can't reply to this thread, i hit submit reply about 10 times and the page keeps timing out. every other page on the site loads fine apart from my other reply lol. if this post works i'll edit it :P

lol if i edit this post with my reply it times out, if i write something else it lets me edit it loooooool.

i'll just say thanks and install that iplayer app :P

---

### Post by ice60 on 2010-03-17
i think that package isn't in intrepid -
[http://packages.ubuntu.com/search?keywords=get-iplayer&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=get-iplayer&searchon=names&suite=all&section=all)

what i tried to post before is i'm in the uk, using a direct connection, with the latest flash player (i tried with a few earlier flash versions too) and the iplayer loads and that little circle thing rotates in the middle of the screen, then i get either a blank screen, or an error about it not working!

i tried with fresh installs of firefox and opera too, by renaming their directories in my home directory to *.bak.

---

### Post by e1f on 2010-03-17
It seems the get-iplayer tool was introduced in karmic:
[http://packages.ubuntu.com/karmic/get-iplayer](http://packages.ubuntu.com/karmic/get-iplayer)

Have you considered that your ISP may have blocked the BBC Iplayer?  I guess it would help if you had another box/OS to try Iplayer on.

[http://www.theregister.co.uk/2009/06/26/isps_against_bbc_iplayer_comment/](http://www.theregister.co.uk/2009/06/26/isps_against_bbc_iplayer_comment/)

---

### Post by ron999 on 2010-03-17
Hi
With Firefox look in Tools > Add-ons > Plugins
See if you have got 'Shockwave Flash' installed.

---

### Post by yakekaj on 2010-03-18
Hello, 

I have similar problems with iplayer... It works when I use windows vista on the same laptop, I have checked for shockwave which is installed.

Another problem that could be related is that websites with flash dropdown boxes doesn't work and neither do things such as Zinga poker on facebook...

I have tried the suggestions above which haven't worked...

Is there any hope?

---

### Post by cpeachey on 2010-03-23
I have the same problem. It works ok with bit 32Karmic and installing iplayer from the BBC iplayer webpage but with 64bit Karmic iplayer the video does'nt load.
Also I noticed it is NOT asking for the default keyring password whereas it does on 32bit (and works)
Chris

---

