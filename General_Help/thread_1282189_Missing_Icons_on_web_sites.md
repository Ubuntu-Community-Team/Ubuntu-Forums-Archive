---
title: "Missing Icons on web sites??"
date: 2009-10-04
forum: General Help
---

### Post by rob2nd9th on 2009-10-04
Missing Icons on web sites??

Started this thread ( [http://ubuntuforums.org/showthread.php?t=1232520](http://ubuntuforums.org/showthread.php?t=1232520) )
about not being able to kick on an icon link.

This problem has now been pointed out to me by my kids, Some CBeebies games are missing icons that are need for playing games?

I'm running 9.04, Compaq Presario CQ60.

Any Help or pointers, Thanks.

---

### Post by rob2nd9th on 2009-10-06
*Bump*

---

### Post by rob2nd9th on 2009-10-20
No one els has this problem?

---

### Post by mechro on 2009-10-20
Are you using Firefox?

---

### Post by mechro on 2009-10-20
The link button you gave in the other thread seems to be some sort of adobe flash application.

Perhaps you need to install a plug in. Are you able to view YouTube videos? If you can't then that would indicate you are missing the plug ins.

An easy way to get these plug ins is to get **ubuntu restricted extras** via Synaptic or Add/Remove Applications.

Having said that, if the stuff you want to download is a Windows application it may not work in Ubuntu anyway.

---

### Post by rob2nd9th on 2009-10-21
Yep my I use Firefox

have tried the "ubuntu restricted extras" but that not worked.

fill try to find a game on Cbeebies with the same problem and link it.

thanks for the pointers.

---

### Post by mechro on 2009-10-21
Just to double check: In Firefox, go to Tools > Add-ons > Plugins.

Is Shockwave Flash listed?

---

### Post by rob2nd9th on 2009-10-21
> **mechro said:**
> Just to double check: In Firefox, go to Tools > Add-ons > Plugins.

Is Shockwave Flash listed?

Yep 
9.0 r999

---

### Post by rob2nd9th on 2009-10-21
[http://www.bbc.co.uk/cbeebies/fun/shapes.shtml](http://www.bbc.co.uk/cbeebies/fun/shapes.shtml)

this is one of the games the kidds cant play :(

---

### Post by mechro on 2009-10-22
> **rob2nd9th said:**
> 
9.0 r999

Might be worth updating since the Cbeebies game is now using Flash Player 10.

Go to Applications > Add/Remove: search for Adobe Flash Plugin. If it offers you version 10 then install it.

---

### Post by rob2nd9th on 2009-10-22
in Synaptic it says iv got 10 installed, I disabled "Shockwave Flash" so now Cbeebies says Iv not got the correct player installed so followed there help guid to install Flash player 10 - And guess what Its already installed?

---

### Post by mechro on 2009-10-22
```
OK. We need to point firefox in the right direction.

In the firefox address bar enter **about:config**

Where it says **Filter** enter **plugin.expose**

Underneath you should now see an item **plugin.expose_full_path**
Right-click and click **toggle** so that value becomes **true**

In the firefox address bar enter **about:plugins**
Scroll down and you should see an item for Shockwave Flash.
You should see a filename something like
/usr/lib/adobe-flashplugin/libflashplayer.so

Post this filename back here.
```

Edit: anti-smiley action taken by putting my post in [CODE]

---

### Post by rob2nd9th on 2009-10-23
File name: /usr/lib/swfdec-mozilla/libswfdecmozilla.so
    Shockwave Flash 9.0 r999

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes


is that what you need?

---

### Post by mechro on 2009-10-26
> **rob2nd9th said:**
> File name: /usr/lib/swfdec-mozilla/libswfdecmozilla.so
    Shockwave Flash 9.0 r999

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes


is that what you need?

Yes, that's it.

We need to get Firefox to use Flash Player 10. 

Try this...

In Firefox go to Tools > Add-ons > Plugins: Disable the Shockwave Flash plugin. Close Firefox.

In System > Administration > Synaptic Package Manager: Search for **swfdec-mozilla**. Mark for Removal and Apply.

Restart Firefox and check if Tools > Add-ons > Plugins is now showing Flash Player 10. If it's not showing, try Logging-out and Logging-in and/or Reboot.

If that hasn't worked you may have to re-install Flash Player 10 through Add/Remove or Synaptic.

---

### Post by rob2nd9th on 2009-10-27
Well that did it :)

A BIG thanks to Mechro

would mark as solved if i knew how :)

---

