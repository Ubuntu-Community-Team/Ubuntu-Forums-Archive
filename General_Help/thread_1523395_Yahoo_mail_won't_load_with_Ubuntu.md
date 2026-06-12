---
title: "Yahoo mail won't load with Ubuntu"
date: 2010-07-03
forum: General Help
---

### Post by amir_zwara on 2010-07-03
So I'm new to this whole Linux thing.
I just downloaded and installed Ubuntu a few days ago (on my Windows Vista Laptop), played around with it, did some trouble shooting (got my wifi card working!)... and am generally enjoying it.
However, I am having issues loading my Yahoo Mail. I am using the newest version of Opera (which I also run on windows), but have tried Firefox as well. I am having absolutely no issues with Yahoo mail when I use Windows (in Opera, firefox, chrome, and IE), but can not get it to load at all with Ubuntu. Basically I can get to the Yahoo home page no problem, and can access any of the links etc., except for Mail. When I click it, I just get an error page (as if there was no Internet connection). I have not had problems with any other sites.
I'm thinking its some kind of scripting/application conflict, but like I said this whole Linux thing is brand new to me. Have only ever really used Windows in the past.
I'm hoping to get these minor issues hashed out, and eventually just drop Windows out of my reality. Anyhow, any troubleshooting help would be awesome. Thanks.

---

### Post by krishnandu.sarkar on 2010-07-03
Well..It's working fine on my side. So the problem is not with Yahoo Mail. Must be some problem on your side. Try some other browsers. Do you face this problem with both FF and Opera(Under Linux)

---

### Post by krishnandu.sarkar on 2010-07-03
Try running sudo dpkg --configure -a

---

### Post by amir_zwara on 2010-07-03
> **krishnandu.sarkar said:**
> Try running sudo dpkg --configure -a

I think it worked!
Or at least Yahoo is working for me now after doing that! Thanks!:D

But... I would like to know what I just did. Why did this fix it? What was up to begin with etc?

---

### Post by krishnandu.sarkar on 2010-07-03
Nothing just a corrupted installation. :)

You just fixed the package with that command. :)

I'm glad that it worked. Enjoy :)

---

### Post by amir_zwara on 2010-07-03
corrupted installation if Ubuntu? or Java? or some kind of yahoo scripts?

---

### Post by amir_zwara on 2010-07-03
so it is now doing the same thing again! Yahoo Mail just won't load.
I tried running sudo dpkg --configure -a again.... and nothing. It is as if I didn't enter anything into the terminal...
any thoughts anyone?

---

### Post by krishnandu.sarkar on 2010-07-03
Re-install Ubuntu. Though I'd say wait for sometime and see what other experienced members replies before a complete reinstall.

---

### Post by amir_zwara on 2010-07-04
ok, thanks.
I was thinking of doing so anyways, as I am dual running Vista and Ubuntu, and Ubuntu has a much smaller memory partition as of now. So I was thinking I would reinstall ubuntu and dedicate most of my hard drive to it making it my main processor.
But before doing that, I will wait for some more replies...

---

### Post by amir_zwara on 2010-07-04
Hmmm... and now when I try the mail link I am getting a pop up saying that basically yahoo is unsecure, and then it gives me a pop up (not yahoos, but either from Opera or Ubuntu asking for login info... but it doesnt go anywhere when I do try to log in. And if I just cancel that login pop up I get a page with this... "Authorization Required
This server could not verify that you are authorized to access the document requested. Either you supplied the wrong credentials (e.g., bad password), or your browser doesn't understand how to supply the credentials required."

weird eh?

---

### Post by krishnandu.sarkar on 2010-07-04
Really wired. Re-install Ubuntu. As other members are not replying I can't suggest anything more than that. Or you can wait for other members to come in and help.

---

### Post by amir_zwara on 2010-07-04
Thought I would let you, or anyone who is gonna help out, that I installed Ubuntu via Wubi through Vista.

---

### Post by krishnandu.sarkar on 2010-07-04
Hmm...Installation through Wubi suffers many times. I'd say to go for a fresh install by booting from CD/USB.

---

### Post by amir_zwara on 2010-07-12
Alright... still having Yahoo Mail issues.
I did a complete reinstall of Ubuntu from CD.
Install went fine, and everything seems to work well...
except I can not access Yahoo Mail. I was able to until this morning... don't know what I did to make it stop. Installed Amarok, then deleted it...
I tried sudo dpkg --configure -a again, and nothing...
anyone else having Yahoo Mail issues? It's only Yahoo Mail, as the rest of the Yahoo sites work just fine. Grr... I even tried to setup Evolution Mail, but it can't access my Yahoo Mail.
Thoughts?

---

### Post by dragos240 on 2010-07-12
> **amir_zwara said:**
> Alright... still having Yahoo Mail issues.
I did a complete reinstall of Ubuntu from CD.
Install went fine, and everything seems to work well...
except I can not access Yahoo Mail. I was able to until this morning... don't know what I did to make it stop. Installed Amarok, then deleted it...
I tried sudo dpkg --configure -a again, and nothing...
anyone else having Yahoo Mail issues? It's only Yahoo Mail, as the rest of the Yahoo sites work just fine. Grr... I even tried to setup Evolution Mail, but it can't access my Yahoo Mail.
Thoughts?

Is it WUBI (install from inside windows)? If so, try booting into the livecd (net touching anything), and then accessing yahoo. If that won't work, it has to do with hardware configuration.

---

### Post by amir_zwara on 2010-07-12
The reinstall is not through Wubi. But from a CD of Ubuntu.
It seems Ubuntuforums.com has also stopped working on Ubuntu... I am now posting through Windows... :(

---

### Post by krishnandu.sarkar on 2010-07-13
Ok....I'm too a noob when it comes to Linux..!! But lemme try..!!

Open /etc/hosts file and post the contents here.

---

### Post by amir_zwara on 2010-07-13
No command 'Open' found, did you mean:
 Command 'pen' from package 'pen' (universe)
 Command 'open' from package 'kbd' (main)
 Command 'open' from package 'console-tools' (universe)
 Command 'open' from package 'open.app' (universe)



Open did not work...
I did seem to get Yahoo Mail to work now though.
I completely deleted all my cookies in Opera and voila!
Let's hope it stays that way.... and now I'm having another Yahoo Mail issue though...
I tried to sign my Yahoo Mail up on Evolution (To see if it would work that way...).
Now about every 5 minutes or so I'm getting a pop up that says:

"Authentication failed for "xxxxxx@yahoo.com"
Server responded: Popgate Unknown Command

After I started getting these, I completely deleted Evolution Mail.... but the pop up is still popping up!

---

### Post by krishnandu.sarkar on 2010-07-14
No....buddy I meant you to open the /etc/hosts file. There is no command called "open". You should have tried to go the /etc/ directory and then open the hosts file. That is what I meant.

Anyway I'm glad that it's working. Well...you can use Yahoo mail from evolution but for that you need to set it up first in right way. And as for the pop-up problem I would suggest to check evolution mail preferences and uncheck anything that says to autostart with ubuntu and other mail preferences.

---

### Post by amir_zwara on 2010-07-14
Hey, thanks for all the help.
I'm actually in the process of Manually partitioning my harddrive, and I'm going to do a fresh install of Ubuntu. See if I can't work the tweaks out.
I had problems with Evolution, even after I deleted Evolution, it was still giving me a yahoo popup, through my Opera browser. Weird eh?
But Ubuntu is not installed as of now, so I may or not get back to you about this issue once I get that all hashed out properly.
Thank a lot for your advice! You've been very helpful.

---

