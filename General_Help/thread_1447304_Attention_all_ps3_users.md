---
title: "Attention all ps3 users"
date: 2010-04-05
forum: General Help
---

### Post by The Thunder Chimp on 2010-04-05
**[COLOR="Red"]WARNING WARNING WARNING WARNING WARNING[/COLOR]**
*[COLOR="red"]SEE REPLY NUMBER 32 BEFORE DOING _ANYTHING_ THAT IS MENTIONED BELOW [/COLOR]*
[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1447304&page=4[/COLOR]

ONLY APPLICABLE TO PS3 "FAT" (OPPOSITE OF PS3 SLIM)

First of all, DO NOT UPDATE YOUR PS3 TO VERSION 3.21 as there is no advantage in doing so. 

As you may know, Sony is disbanding support for the PS3's "Other OS" feature. It will now be very difficult to install an other Operating System on your PS3, such as Ubuntu.

They tell you to make the following choice:

1) Keep Other OS by not updating. You lose all online access.
2) Update to version 3.21, lose Other OS, and re-gain online access.

 However, there are two ways of bypassing this:

1) A workaround to make older version of PS3 firmware (I have 3.19), able to get online access back without updating. This link will tell you how: [http://boards.ign.com/ps3_general_board/b8267/190758483/p1/?2](http://boards.ign.com/ps3_general_board/b8267/190758483/p1/?2)

2) A workaround that's a little more complex. The link: [http://endlessparadigm.com/forum/showthread.php?tid=22985](http://endlessparadigm.com/forum/showthread.php?tid=22985)

Which one to choose? It's easier to start with the first option as you hook up on a proxy server. The second one makes you create a proxy server yourself.

Please be aware that if you acciddently update your PS3 firmware to 3.21 (without the second link's download) you will not be able to start over. Additionally, if you have already done the 3.21 update, I sadly can't help you.

 If you want to install Ubuntu on the PS3 with Other OS, consider consulting this page: [http://psubuntu.com/wiki/InstallationInstructions](http://psubuntu.com/wiki/InstallationInstructions)

Thanks for reading my first article!
Have a nice day! \\:D/

---

### Post by The Thunder Chimp on 2010-04-05
Posting back so more people may be informed.

---

### Post by Nicolas.Perrault on 2010-04-05
Thanks!

Worked fine for me. I was really annoyed because I wasn't able to get online access since April 1st. This got it back for me. I used the first option by the way. Super Easy.
:D

---

### Post by J V on 2010-04-06
GREAT

Any way to get the second one running on linux (wtb deb file)

Edit: First one isn't working, still wants to update :/

---

### Post by The Thunder Chimp on 2010-04-06
I figured out that the second one does pretty much the same thing as the first one. It's just more complicated. Try the first one first. If it doesn't work, then I'll see what I can do for you with the second one.

[Tested on a Wireless Network]

On your PS3, go to Settings>Network Settings>[3rd down from the list, I just don't remember the name].

From there, choose custom settings. Then click automatic on everything besides the Set DNS part. Choose to do that manually. Set your PRIMARY DNS to 67.202.81.137

Continue to choose automatic settings on all the rest. Test the connection. No reboot recquired, you should now be able to sign in, and use Other_OS. 

Please note that if you choose to later update, you'll have to switch back your IP adress to 00.00.00.00

That should fool them.

Eager to hear how it turned out!

---

### Post by J V on 2010-04-06
Thats what I did but even after reboot it still says I need an update, perhaps the guy with the dns server blocked european IPs?

Edit: No I just remembered the crude message at that IP, maybe he just hasn't got the particular file I need there... WTB set 404 to that file lol :)

---

### Post by The Thunder Chimp on 2010-04-06
> **J V said:**
> Thats what I did but even after reboot it still says I need an update, perhaps the guy with the dns server blocked european IPs?

Edit: No I just remembered the crude message at that IP, maybe he just hasn't got the particular file I need there... WTB set 404 to that file lol :)

It's the Primary DNS adress you must change, not the IP. Where are you from by the way?

What do you mean by "crude message"?

---

### Post by J V on 2010-04-06
The primary DNS is basicly an IP...

From netherlands

Surf to that IP and find out :)

---

### Post by The Thunder Chimp on 2010-04-07
That's an awkward situation. Have you tried the second option? If you do, be careful on success-on-the-first try, as you might not get a second chance.

Tell me, if you had any success!

---

### Post by AerialX on 2010-04-07
> **J V said:**
> Thats what I did but even after reboot it still says I need an update, perhaps the guy with the dns server blocked european IPs?
It should work for any region, if you're still seeing an update that might mean the DNS isn't taking effect at all; if it didn't support a region it really should error rather than tell you 3.21 is available. Do you have a secondary DNS set?

> **J V said:**
> Edit: No I just remembered the crude message at that IP, maybe he just hasn't got the particular file I need there... WTB set 404 to that file lol :)
_[The Offspring](http://www.youtube.com/watch?v=x52sA9IpiAU)_ ftw!

EDIT: Alright, fine, I've had my Offspring fun over the past few years. The IP now redirects to my main domain. Happy?

---

### Post by The Thunder Chimp on 2010-04-07
Yeah, my secondary is set to full zeros.

---

### Post by J V on 2010-04-08
Still getting system update notice...

The IP doesn't need to redirect anywhere, its fine right now, but I think perhaps my particular location has a different path to the list file, setting it as the 404 page would fix this I suppose... Or mabey only under the highest directory possible...

Idk, Other people from holland have also reported that they coulden't get either workaround working... Perhaps I will just have to wait for geo...

---

### Post by The Thunder Chimp on 2010-04-08
It worked flawlessly for me. So what about you tell us exactly what you did, and we might see the flaw (if there is any). Thanks.

---

### Post by J V on 2010-04-08
Started up, went to network connections, changed the settings, set everything to normal, but primary DNS to 67.202.81.137 left secondary to 0.0.0.0

Didn't work, restarted, still didn't work, set secondary to 67.202.81.137 as well, still didn't work, rebooted, still didn't work

Set secondary back to 0.0.0.0, still didn't work, rebooted, still didn't work...

Haven't tried option #2, but from what I've heard it only works half the time too...

---

### Post by The Thunder Chimp on 2010-04-09
Would you please redo everything one more time, reach the end of the network setup, and test connection. Show the results here. Thanks.:)

---

### Post by steev182 on 2010-04-09
Please note: The 2nd workaround does NOT update your PS3. It does similar to the first one, except you're hosting the proxy server yourself.

---

### Post by The Thunder Chimp on 2010-04-09
Yeah, I figured that out too. I said it in one of the earlier posts, I'll update it. Thanks.

---

### Post by DrMelon on 2010-04-09
[http://gizmodo.com/5513235/ps3-owners-may-get-cash-back-after-otheros-uninstall](http://gizmodo.com/5513235/ps3-owners-may-get-cash-back-after-otheros-uninstall)

You can get money for having the update.

---

### Post by The Thunder Chimp on 2010-04-09
> **DrMelon said:**
> [http://gizmodo.com/5513235/ps3-owners-may-get-cash-back-after-otheros-uninstall](http://gizmodo.com/5513235/ps3-owners-may-get-cash-back-after-otheros-uninstall)

You can get money for having the update.

Wow, not bad. Hard choice, but I think I'll keep Linux thank-you. Unless, you send the invoice, collect the money, and do the move to keep Linux! :twisted:

---

### Post by J V on 2010-04-11
Moving house, besides geohot has the cfw now, I'll take it from him if the dns still doesn't work after the move...

Hopefully this sends a message to manufacturers: Mess with linux, get castrated within a week...

---

### Post by The Thunder Chimp on 2010-04-11
Please post the results of your attempts here so more people may be informed.

> **J V said:**
> Hopefully this sends a message to manufacturers: Mess with linux, get castrated within a week...

Haha, you just made my day! I'm putting this as "favorite quotes" on my facebook account!

---

### Post by Sub101 on 2010-04-11
I cant remember the last time I booted into the PS3 OS on my PS3. The high def got fried in a lightning storm so been using it as a server ever since.

---

### Post by The Thunder Chimp on 2010-04-11
> **Sub101 said:**
> I cant remember the last time I booted into the PS3 OS on my PS3. The high def got fried in a lightning storm so been using it as a server ever since.

That's a shame, but just in case you decide to use it later on (Other_OS, I mean), you better do the move to keep Other_OS. Please keep in mind that this keeps you from updating your machine though.

---

### Post by J V on 2010-04-12
If geo releases his CFW you will be able to get other OS back after the next update (Even if you went to 3.21)

---

### Post by Danimoth on 2010-04-12
> **J V said:**
> If geo releases his CFW you will be able to get other OS back after the next update (Even if you went to 3.21)

I am actually waiting for that. Until then, no more buying anything for the PS3 if sony wants to be like this.
I am concerned though, that we will have to customize EVERY update from then on, which is a hassle. In that case, i will need to consider what to do.

---

### Post by Sub101 on 2010-04-12
> **Danimoth said:**
> I am actually waiting for that. Until then, no more buying anything for the PS3 if sony wants to be like this.

I know it isnt good for people like us, but I can completely understand it from Sonys point of view as they make no money (they may even lose money?) on selling PS3s. The only profit they make is from games sales.

That being said, taking away an advertised feature is not the right route to take.

---

### Post by J V on 2010-04-12
And if the PS3 needs to go in for repairs they will require it to have update 3.21, so you can get a refund for every game, accessory, and your ps3, all at once if it breaks...

As for customizing every update, that won't be hard...

3.21 was the first update for months, and the only update that actually warranted discussion of any type in the last 2 years...

Besides, someone will probably make a script so you just pop in one update, click which features you want, and out pops the new and improved one...

---

### Post by ratcheer on 2010-04-12
I am still running 3.15 and I still have online access. When does online access stop if I don't update?

Tim

---

### Post by J V on 2010-04-12
You shoulden't have online access :)

There is a workaround (As posted at the start of this thread)

The workarounds will stop working when sony updates PSN in a manner that requires a change in the protocol (And not just an up to date version)

Then geo's CFW will be used.

---

### Post by The Thunder Chimp on 2010-04-12
> **ratcheer said:**
> I am still running 3.15 and I still have online access. When does online access stop if I don't update?

Tim

Umm, yeah, you shouldn't have online access. If you do however, the only I have to say is: Good for you!

Don't try this technique however as its success is apparently not guaranteed (worked for me), and changing a DNS may (or may not) make you lose all online access. Besides, you don't have any point in doing this do you? ;)

---

### Post by ratcheer on 2010-04-13
> **The Thunder Chimp said:**
> Umm, yeah, you shouldn't have online access. If you do however, the only I have to say is: Good for you!

Don't try this technique however as its success is apparently not guaranteed (worked for me), and changing a DNS may (or may not) make you lose all online access. Besides, you don't have any point in doing this do you? ;)

I went back and double checked. When I start the PS3, PSN tell me I am logged in. System Info says version is 3.15. And my 12-year old is always playing that Playstation Home game where he wanders around in a virtual world.

Tim

---

### Post by The Thunder Chimp on 2010-04-13
[SIZE="4"][COLOR="Red"]WARNING WARNING WARNING WARNING WARNING[/COLOR][/SIZE]

The proxy hack doesn't work anymore. I was kicked from the PS Network, just as this guy warns here: [http://www.haxnetwork.net/2010/04/psn-for-proxy-users-possibly-blocked/](http://www.haxnetwork.net/2010/04/psn-for-proxy-users-possibly-blocked/)

However, this isn't an excuse to update to version 3.21. George Hotz (aka GeoHot) is creating a custom firmware called v3.21OO. This will let you access the PSN and let you keep Other_OS and will even ENABLE it on the PS3 Slims series. So if you're interested in Linux for the PS3 (whether or not you have an Original PS3 or a PS3 Slim) [COLOR="Red"]DO NOT UPDATE TO VERSION 3.21, NO MATTER HOW TEMPTING THIS MAY SEEM. A HACK IS COMING UP SO DON'T GIVE UP HOPE![/COLOR]. Check out this Blog for more information: 

[http://geohotps3.blogspot.com/2010/04/otheros-supported-on-321oo.html](http://geohotps3.blogspot.com/2010/04/otheros-supported-on-321oo.html)

I hope that those (including me) who used Proxy hacks will be able to re-access the PSN after GeoHot's custom firmware.

Until then, don't give up hope. Post any questions or comments below.

By the way Ratcheer: Good for you, you are one lucky guy! Please be thankful for it!


EDIT (August 2010): You may want to update now. GeoHot didn't release it at all, and doesn't have the intention of doing so.

---

### Post by J V on 2010-04-13
Guess geo will be releasing his pup more early... maybe its on tpb?

---

### Post by The Thunder Chimp on 2010-04-13
> **J V said:**
> Guess geo will be releasing his pup more early... maybe its on tpb?

When is it due for?
Will I get access to PSN back?

---

### Post by J V on 2010-04-15
Its not like he set a release date... I'm guessing you can find it somewhere around the web, but only after a significant amount of crawling through the darkest pages of the web *shudders*

Edit: Both methods are now disabled, waiting for "Someone" to release CFW...

---

