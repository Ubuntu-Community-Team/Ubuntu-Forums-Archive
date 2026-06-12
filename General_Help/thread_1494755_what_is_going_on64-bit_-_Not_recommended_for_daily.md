---
title: "what is going on64-bit - Not recommended for daily desktop usage"
date: 2010-05-27
forum: General Help
---

### Post by necromonger on 2010-05-27
Why does the ubuntu download site say this.64-bit - Not recommended for daily desktop usage.Is there a problem that we are not being told about!

---

### Post by Sub101 on 2010-05-27
> **necromonger said:**
> Why does the ubuntu download site say this.64-bit - Not recommended for daily desktop usage.Is there a problem that we are not being told about!

I expect its to stop new users from running before they can walk!

Its the first time I have taken a look at the new website... looks a lot more friendly.

---

### Post by necromonger on 2010-05-27
It does look good.But if there problems that will give new users trouble we need to open the 64 bit thread up And help them.

---

### Post by Sub101 on 2010-05-27
In all honesty the problems that used to exist with 64-bit aren't really there any more, at least in my experience.

However, I think encouraging new users to the 32-bit rather than 64 is generally a sensible move. 32-bit will work for everyone, 64 may not.

---

### Post by Ozymandias_117 on 2010-05-27
The only problem I'm aware of with 64-bit is the "Pix Frogger" game doesn't work, and when you install flash, you're actually installing the 32-bit with a wrapper. But a new user wouldn't notice, or care, about that one.

---

### Post by Merk42 on 2010-05-27
I wondered that too and filed a bug a few days ago
[https://bugs.launchpad.net/ubuntu-website/+bug/585940](https://bugs.launchpad.net/ubuntu-website/+bug/585940)

---

### Post by nhasian on 2010-05-27
Yeah thats weird.  I would think that Ubuntu 64bit would be the default choice to download since computers have had 64bit architecture for several years now.  Even entry level computers now come with 4 gigs of ram.  I think it is easier for a novice user to just install the 64bit Ubuntu than mess around with installing the PAE kernel to be able to use all their system's memory.

My only gripe is that the flash in the repository is only 32bit and is installed with the ndiswrapper.  I understand though that since adobe hasn't officially released the 64bit adobe flash it cannot be included in the repositories.  I just hope it is officially released in June along with the official release of Flash 10.1 (first week of june i think?)

---

### Post by philinux on 2010-05-27
> **necromonger said:**
> Why does the ubuntu download site say this.64-bit - Not recommended for daily desktop usage.Is there a problem that we are not being told about!

Someone's being ultra cautious there. I've been using 64 bit for ages no problems at all.

---

### Post by Lucky. on 2010-05-27
I use 64 bit, but darn it all each time I do an install I have to screw around to get Flash working properly.  This could be a turn off for tons of users.

---

### Post by sandyd on 2010-05-27
> **Lucky. said:**
> I use 64 bit, but darn it all each time I do an install I have to screw around to get Flash working properly.  This could be a turn off for tons of users.

thats why I created the app (in my sig)

---

### Post by philinux on 2010-05-27
> **Lucky. said:**
> I use 64 bit, but darn it all each time I do an install I have to screw around to get Flash working properly.  This could be a turn off for tons of users.

I have the plugin in ~/.mozilla/plugins and with home on it's own partition it just works when I reinstall.




Moved to Community Cafe.

---

### Post by Ozymandias_117 on 2010-05-27
> **carlee said:**
> thats why I created the app (in my sig)

Your website is broken. When I tried to go there I got > If you can see this page, then the people who manage this server have installed cPanel and WebHost Manager (WHM) which use the Apache Web server software and the Apache Interface to OpenSSL (mod_ssl) successfully. They now have to add content to this directory and replace this placeholder page, or else point the server at their real content.

ATTENTION!

If you are seeing this page instead of the site you expected, please contact the administrator of the site involved. (Try sending an email to <webmaster@domain>.) Although this site is running cPanel, WebHost Manager, and Apache software it almost certainly has no other connection to cPanel Inc. or the Apache Group. Please do not send mail about this site or its contents to cPanel Inc. or the Apache Group.

---

### Post by Swagman on 2010-05-27
Copy & Paste from another forum.. But very apt

> 
Trouble is, everyone will keep telling you that it's it's sinful to use only 32-bit and you're a heretic if you don't use 64-bit yada yada yada.
Well as someone who's used 64-bit for the last 10 years tell them from me that they are are talking out of their behind . Choose 32 or 64-bit and ignore the uneducated idiots 


---

### Post by JDShu on 2010-05-27
> **Lucky. said:**
> I use 64 bit, but darn it all each time I do an install I have to screw around to get Flash working properly.  This could be a turn off for tons of users.

I stopped using 64 bit because of this issue. I don't want to hunt around the internet for instructions if I can help it.

---

### Post by Swagman on 2010-05-27
> **JDShu said:**
> I stopped using 64 bit because of this issue. I don't want to hunt around the internet for instructions if I can help it.


Carlees installer ***DOES*** work.

Remember to uninstall first though

---

### Post by dE_logics on 2010-05-27
> **Sub101 said:**
> I expect its to stop new users from running before they can walk!

Its the first time I have taken a look at the new website... looks a lot more friendly.

Only if they put the md5 hash in the download page...

---

### Post by fluteflute on 2010-05-27
The flash issue is quite major, for example not being able to click elements on YouTube with the default flash install. Still to say it's not recommended seems silly, that's literally the only problem I have. Oh that and the Amazon MP3 client. Silly proprietary software!

---

### Post by oldos2er on 2010-05-27
> **Swagman said:**
> Copy & Paste from another forum.. But very apt

"Trouble is, everyone will keep telling you that it's it's sinful to use only 32-bit and you're a heretic if you don't use 64-bit yada yada yada.
Well as someone who's used 64-bit for the last 10 years tell them from me that they are are talking out of their behind . Choose 32 or 64-bit and ignore the uneducated idiots"

Wow. I can't say that's in any way apt.  :(

---

### Post by Sub101 on 2010-05-27
> **dE_logics said:**
> Only if they put the md5 hash in the download page...

Sorry... how so?

---

### Post by McRat on 2010-05-27
As a new user:

My first try was with the 64 bit version - 

A)  It doesn't come with a GUI, but that is easily fixed.
B)  It reported HDD sizes wrong when partitioned.
C)  It would not work with the 2 different wireless cards I had handy, a Belkin and a Hawkins.

So rather than risk it, I reloaded the 32 bit version.


Now I don't know this for a fact but:

You won't be able at address more than 4GB of memory with a 32bit CPU, nor a HDD larger than 2 TB, IIRC.

So the main reason to run 64 bit is to go past 4GB and 2 TB?

---

### Post by Sub101 on 2010-05-27
> **McRat said:**
> 

Now I don't know this for a fact but:

You won't be able at address more than 4GB of memory with a 32bit CPU, nor a HDD larger than 2 TB, IIRC.

So the main reason to run 64 bit is to go past 4GB and 2 TB?

That is correct.

> **McRat said:**
> 
A) It doesn't come with a GUI, but that is easily fixed.


That is not. Maybe you tried with the server version?

---

### Post by McRat on 2010-05-27
> **Sub101 said:**
> That is correct.



That is not. Maybe you tried with the server version?

Yup.  I was building a file server.  The only two versions I saw were 32 GUI and 64 Server.

---

### Post by McRat on 2010-05-27
> **Sub101 said:**
> That is correct.



...

But it's always hard to say something can't be done.

Remember the 80286 CPU?  That was a 16-bit processor.  In theory it could not address more than 64k.  But it could actually use 640k for program area by paging.  Segmented Addressing?

Could somebody come up with BIOS that could permit a 32bit CPU chip to use paging? Or use a HDD past 2TB?  This I can't say.

---

### Post by philinux on 2010-05-27
> **McRat said:**
> 
So the main reason to run 64 bit is to go past 4GB and 2 TB?

You guys may or may not have seen this.
[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by McRat on 2010-05-27
> **philinux said:**
> You guys may or may not have seen this.
[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

Great link!

I'd like to see that broken down by file size though.  It is looking like the bigger the files you process, the more important 64bit is.

But for many users, their computer processing speed is not a bottle neck.

---

### Post by samalex on 2010-05-27
I've been running 64-bit Linux for about a year now (still on 9.04), and the only thing I could see that may stop new users is crummy Flash support.  64-bit 9.04 and I think 10.04 both us 32-bit Flash with a wrapper to work on 64-bit, and this causes LOTS of problems.  64-bit Flash for Linux is out there, but it's still Alpha... though I find it much more stable than using 32-bit Flash w/ wrapper on 64-bit Linux.

Outside of this, I don't know what other problems new users would face since most everything I've seen in the repositories is out there for both 32-bit and 64-bit Linux.

Sam

---

### Post by WinterRain on 2010-05-27
> **Lucky. said:**
> I use 64 bit, but darn it all each time I do an install I have to screw around to get Flash working properly.  This could be a turn off for tons of users.

Screw around with what? Takes me 30 seconds to install. Just put the 64bit libflashplayer.so file into /usr/lib64/mozilla/plugins folder. Easy.

---

### Post by WinterRain on 2010-05-27
> **McRat said:**
> 

A)  It doesn't come with a GUI, but that is easily fixed.


Where have you been? Maybe back in '04 64bit was different, but I can assure you 64bit ubuntu has a gui just like 32bit. There's really no difference.

---

### Post by WinterRain on 2010-05-27
> **JDShu said:**
> I stopped using 64 bit because of this issue. I don't want to hunt around the internet for instructions if I can help it.

Hunt for what? Are you capable of putting a file into /usr/lib64/mozilla/plugins ? If so, that's all you have to do. I don't  know why people make a mountain out of a mole hill.

---

### Post by lisati on 2010-05-27
> **McRat said:**
> But it's always hard to say something can't be done.

Remember the 80286 CPU?  That was a 16-bit processor.  In theory it could not address more than 64k.  But it could actually use 640k for program area by paging.  Segmented Addressing?

Could somebody come up with BIOS that could permit a 32bit CPU chip to use paging? Or use a HDD past 2TB?  This I can't say.

True, but incomplete. My first x86 machine had an 80286. True, the data bus was 16bit, but, if memory serves correctly, the addresses were 24 bit. Have a look here: [http://en.wikipedia.org/wiki/Intel_80286](http://en.wikipedia.org/wiki/Intel_80286)

---

### Post by McRat on 2010-05-27
> **WinterRain said:**
> Where have you been? Maybe back in '04 64bit was different, but I can assure you 64bit ubuntu has a gui just like 32bit. There's really no difference.

When I went to try it, all I saw was 32 bit Desktop and 64 bit Server.  Perhaps I didn't look hard enough at the time.

Today I just looked and it seems to be different from where I downloaded from a month ago.  It does have a 64 bit desktop option.

---

### Post by lisati on 2010-05-27
I think Canonical have recently updated the Ubuntu web site, which could explain things. I noticed yesterday when I went to download a couple of ISO files using a URL I'd bookmarked, and ended up with a "page not found" error.

---

### Post by TheSqueak on 2010-05-27
I've run across a couple of video codecs I can't play in 64 bit, but everything else is fine.

---

### Post by conradin on 2010-05-28
What does 
"64-bit - Not recommended for daily desktop usage"
(shown on [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download))
mean?

is the 64 bit version not stable enough to actually install?
what can I expect from the 64 bit version of lucid and where can I get more information on why daily usage isn't recommended?

---

### Post by Woody1987 on 2010-05-28
The 64bit version is fine. I have been using it for 2 years without much hassle. The only problem i have ever had which was 64bit related was with flash, but that, at least for me is no longer a problem with 10.04. I usually recommend the following dependng on how much memory you have:

<3GB - 32bit
3-4GB - 32bit + pae with free graphics drivers / 64bit with proprietry drivers
>4GB - 64bit

---

### Post by hansdown on 2010-05-28
Hi conradin.

That is a strange message. 

I'm using 64-bit lucid now, and it works very well.

The only thing I've noticed, is firefox runs slower.

---

### Post by jo4hnc on 2010-05-28
I have to agree with Woody and Hansdown. I've been using the 64bit versions for three years now. With the latest version, Lucid, even the flash implementation seems to be much better. And on my machine Firefox does get a bit quirky at times but not really enough to even start to drive me crazy.

---

### Post by vandorjw on 2010-05-28
Website maintainers should remove that message imho.
or change it to: 
32-bit ~ recommended for computers more than 3 years old.
64-bit - recommended for computers less than 3 years old.

(I think all cpu made less than 3 years ago are 64 bit capable)

I would run 64 bit even if you only have 1 gb of ram.

Back in the days, people had 64MB of ram, and ran windows 98 (32 bit)
[i realize that 16 bit is not capable of 64MB, just saying it does no "real" harm]

---

### Post by odius on 2010-05-28
I use an athlon 64 with Lucid and 1 gig of ram. :)

only problem I've had was nautilus suddenly not wanting to arrange by name and the power management not wanting to stay OFF hahaha but xset -dpms took care of that.

---

### Post by v1ad on 2010-05-28
just 64 bit sends 64 bits of instructions to the processor instead of 32 bit.

i think that they never got around to changing it. it is stable and works perfectly. i only use 64 bit.

---

### Post by Frogs Hair on 2010-05-28
A bug report has been filed regarding the message on the website.

---

### Post by gamblor01 on 2010-05-28
I have 9.10 64-bit installed on my desktop but 10.04 32-bit installed on my work laptop.  The 9.04 release was the first time I went with a 64-bit kernel as it seemed like flash was more stable, and wine was working much better (at least under 64-bit Ubuntu).

I honestly think I am going to revert back to 32-bit (with PAE of course) on my desktop.  I have 4GB of RAM and I don't really see the need for anything beyond that.  Flash works way better on a 32-bit kernel, and I still have issues with wine under 64-bit Fedora.

The 64-bit install is definitely stable, and usually if you install the ia32-libs and download the "getlibs" script (which you can find on this forum) then you can get just about any 32-bit app to run just fine without having to do a crazy chroot or something of that nature.

I just don't personally see any point to running a 64-bit kernel so I plan on switching back to 32 for now.  At least until things get more and more geared for 64-bit...

---

### Post by v1ad on 2010-05-28
gamblor use the x64 bit flash. that is very stable in x64 systems.

---

### Post by SDonatas on 2010-05-29
> **v1ad said:**
> gamblor use the x64 bit flash. that is very stable in x64 systems.


I use ubuntu 10.04 x64 on my laptop and have no problems at all. My laptop has 4 gb ram - about 300 or so for GPU. One thing that i noticed on ubuntu x64 system uses more ram space, so in 32 bit system I was able to get more from hardware in terms of RAM space (with PAE, which installs automatically). However x64 is not only about large amount memory support, it theoretically can run programs or games faster. Now, about firefox, I'm sure those who mentioned slow firefox in x64 bit OS have this problem just because they use 32 bit flash. If you install x64 bit OS don't use any 32 bit apps, because then what is the point in having 64 bit Os at all. 32 bit apps run smoother and faster on 32 bit systems, and 64 bit apps run better in x64 bit systems. If the same app is availiable for both systems (like all open source software) it should run faster on 64 bit (although it may be very insignificant speed advantage). And remember it is implementation specific. We need to wait a little bit more, while all software developers will get used to developing apps for x64 bit systems and learn how to use all the benefits provided by 64 bit processing. If ubuntu wants to compete with mac os X (which is 64 bit) it must start to concentrate on x64 bit system, because it is the future.

And one more thing, i run 64 bit ubuntu 10.04 and have no 32 bit wrappers or apps 32 bit apps. There is x64 skype, flash beta, urban terror game, boxee.. So its all good. Just when you for example install some third party apps, check dependencies, because sometimes like in the case of boxee, it will automatically install 32 bit flash (don't recommend) and 32 wrapper. You should avoid that, use only 64 bit staff on your 64 bit OS.

---

### Post by oldos2er on 2010-05-29
> **Frogs Hair said:**
> A bug report has been filed regarding the message on the website.

And if anyone's interested, it's here: [https://bugs.launchpad.net/ubuntu-website/+bug/585940](https://bugs.launchpad.net/ubuntu-website/+bug/585940)

---

### Post by gamblor01 on 2010-05-29
@v1ad and SDonatas:

I ***am*** using the 64-bit Flash already:

```

bdmayes@ubuntubox:~/.mozilla/plugins$ file libflashplayer.so 
libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

```It's not a question of stability (it never seems to crash) it's more a question of functionality.  There are just certain sites that I can't seem to get to load on the 64-bit system.  For example, I tried to load up some NickJr stuff the other day for my son but the pages just didn't load.  The status bar at the bottom said "Done" but there was nothing on the page except for the background stuff.  I also have problems with other flash websites like citicards.com.  Oddly enough it seems to function sometimes but not other times.  Unfortunately, it fails to function more often than not.  The page loads up and I can see everything, but when I click on a link or click to enter my credentials -- nothing happens.  There are some other pages that don't load on my 64-bit system (yet work fine on 32-bit with 32-bit flash), but I can't think of them at the moment.

I have issues beyond flash as well.  For the life of me I haven't been able to get Opera to function on my 64-bit system and I can't get the VPN client for my work to function properly either (even though I have the ia32-libs package and getlibs has retrieved all of the appropriate libs -- or so it says).

If 64-bit works for everything that you do then that's wonderful.  I'm still having problems with it right now and since I don't have or care to have more than 4 gigs of ram right now, I really don't see the point in running it any longer with all of the minor annoyances that I have found.  I moved to 64-bit when 9.04 came out but I don't see any reason to  stick with it at the moment, and I have plenty of reasons to go back to 32-bit instead.  Thus, I plan on wiping my 64-bit install and going with a 32-bit install in the near future.

---

### Post by bodhi.zazen on 2010-05-29
> **gamblor01 said:**
> If 64-bit works for everything that you do then that's wonderful.  I'm still having problems with it right now and since I don't have or care to have more than 4 gigs of ram right now, I really don't see the point in running it any longer with all of the minor annoyances that I have found.  I moved to 64-bit when 9.04 came out but I don't see any reason to  stick with it at the moment, and I have plenty of reasons to go back to 32-bit instead.  Thus, I plan on wiping my 64-bit install and going with a 32-bit install in the near future.

I think this observation sums it up quite well, although such issues with 64 bit are becoming few and far between.

Personally I also have no problems with 64 bit and IMO, to answer the OP, if you have a 64 bit CPU, use a 64 bit OS. If you are then one of the rare few who have problems -

File a bug report and "downgrade" to 32 bit.

---

### Post by MooPi on 2010-05-29
I have only one issue with the 64 bit install, Hulu won't play flash video and is not in the works to function. Hulu is ignoring the problem so it wont get fixed.

---

### Post by oldos2er on 2010-05-29
Hulu desktop works fine here with 64-bit flash. I don't use the website though.

---

### Post by Spr0k3t on 2010-05-29
I've been running 64bit since Dapper.  The only issues I have had over the years is flash.  Now there's a native 64bit client, I have not had any problems.

Frogs Hair: what's the bug report number... I'll 2nd the notion.

---

### Post by howefield on 2010-05-29
> **Spr0k3t said:**
> Frogs Hair: what's the bug report number... I'll 2nd the notion.

Could be this one

[https://bugs.launchpad.net/ubuntu-website/+bug/585940](https://bugs.launchpad.net/ubuntu-website/+bug/585940)


An interesting link posted by philinux earlier is worth a look

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by dcstar on 2010-05-30
> **Spr0k3t said:**
> I've been running 64bit since Dapper.  The only issues I have had over the years is flash.  Now there's a native 64bit client, I have not had any problems.

+1, I have added my comment to the bug report which sums up my opinion on the issue.

---

### Post by KayakJim on 2010-06-01
I just noticed on the Ubuntu download page for the Desktop it says "64-bit - Not recommended for daily desktop usage".

I'm curious if anyone has seen anything from Canonical stating why they don't recommend 64-bit.

---

### Post by Espionage724 on 2010-06-01
I had my mom try to install x64 on my server computer (and were talking about someone who hasn't seen linux, or understands advanced concepts :p) and either she did something wrong, or the installer didn't work, or maybe I led her through it wrong (I'm used to the x86 install only).

So I told her to do x86 and it worked fine. So hmm idk. I have no way of seeing the screen so I can't provide feedback on it, and I know my computer has a x64 CPU and can run XP x64 fine.


Not sure if it pertains directly to this thread, but that was my little x64 experience :p

---

### Post by marshmallow1304 on 2010-06-01
It's probably so people who don't know the difference don't download the 64-bit version and wonder why it doesn't work on their 32-bit processors.  It's not well worded though and is indeed confusing.  It should instead say something like "If you're not sure, choose the 32-bit version."

---

### Post by happyhamster on 2010-06-01
> **KayakJim said:**
> I just noticed on the Ubuntu download page for the Desktop it says "64-bit - Not recommended for daily desktop usage".
My first reaction was "That's probably some ancient, obscure and unofficial whatnot download page you used. Probably off-world too, written in Klingon most likely.". But then I looked it up, and lo and behold: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by KayakJim on 2010-06-01
I have been using the 64-bit version since 8.10 Intrepid and the download page never had a statement by the version selector before.

That is what prompted me to post the question. I know that in the past Flash and a few other programs have problems on the 64-bit platform but there was never a statement that it wasn't suitable for normal use.

Since there has been such a push lately to get people to use the 64-bit version I found that statement counter-productive and wanted to check on what I was missing.

---

### Post by happyhamster on 2010-06-01
There's already a bug open on this:
[https://bugs.launchpad.net/ubuntu-website/+bug/585940](https://bugs.launchpad.net/ubuntu-website/+bug/585940)

---

### Post by cascade9 on 2010-06-01
> **KayakJim said:**
> I'm curious if anyone has seen anything from Canonical stating why they don't recommend 64-bit.

+1. Not like its 2006-7 and 64bit was still a right pain...

---

### Post by VastOne on 2010-06-01
> **marshmallow1304 said:**
> It's probably so people who don't know the difference don't download the 64-bit version and wonder why it doesn't work on their 32-bit processors.  It's not well worded though and is indeed confusing.  It should instead say something like "If you're not sure, choose the 32-bit version."

I agree totally Most computers today are 64bit and other than the ubiquitous 64-bit-flash-alpha solution (which can be found in a million hits on this site alone), it is for everyday use. IMO. 

To answer the OP, 64 bit used everyday, 3 years, 10 computers, all with 0 issues.

---

### Post by jo4hnc on 2010-06-01
The department of redundancy department. Here's another recent thread on the same topic.

[http://ubuntuforums.org/showthread.php?t=1496025](http://ubuntuforums.org/showthread.php?t=1496025)

---

### Post by lavinog on 2010-06-01
One way to look at it though is that if you don't know if you need 32 or 64bit, then you are not going to care about the advantages of 64bit.  Many people use computers to just surf the web...something 32bit does better without needing to resort to an alpha version of flash.

---

### Post by KayakJim on 2010-06-02
> **jo4hnc said:**
> The department of redundancy department. Here's another recent thread on the same topic.

[http://ubuntuforums.org/showthread.php?t=1496025](http://ubuntuforums.org/showthread.php?t=1496025)

I even did a search before posting. Strange that I did not receive any results.

[quote=VastOne]I agree totally Most computers today are 64bit and other than the ubiquitous 64-bit-flash-alpha solution (which can be found in a million hits on this site alone), it is for everyday use. IMO.

To answer the OP, 64 bit used everyday, 3 years, 10 computers, all with 0 issues.[/quote]
Indeed. I have 5 laptops - 3 running 8.10, 1 running 9.04, and 1 running 10.04. All are using the 64-bit desktop version. My only problems, oddly enough, are with 10.04 and it not finding my bluetooth and internal mic.

---

### Post by 3rdalbum on 2010-06-02
Very dumb; Canonical provides support for the 64-bit edition of Ubuntu 10.04 for the next 3 years on the desktop, so that's a little bit daft for them to say that they don't recommend it for "daily usage".

The only problem with 64-bit is that Flash plugin - it often ignores mouse click events on 64-bit. Not an inherent problem with 64-bit, only a problem with Adobe's monkeys.

---

### Post by Spr0k3t on 2010-06-02
> **3rdalbum said:**
> The only problem with 64-bit is that Flash plugin - it often ignores mouse click events on 64-bit. Not an inherent problem with 64-bit, only a problem with Adobe's monkeys.

Actually, that's not a problem with the flash plugin... it's a problem with the 32bit wrapper.  The 64bit version of flash works quite well.

---

### Post by cascade9 on 2010-06-02
> **Spr0k3t said:**
> Actually, that's not a problem with the flash plugin... it's a problem with the 32bit wrapper.  The 64bit version of flash works quite well.

Agreed. I had issues like that when I tried to use 32bit flash in a wrapper, 64bit has been...well, as good as flash ever is.

---

### Post by garvinrick4 on 2010-06-02
I have had quite a few installs of 64 bit and have had zero issues.

---

### Post by Mnemic on 2010-06-02
I do use 64bit version here too... Althought it's only for 1 week. I didnt notice any strange things, it works pretty well i'd say.
Thats on my 'Dayly Desktop'

I also use 64Bit Server Edition at a DELL server. Nothing strange there too.

---

### Post by KayakJim on 2010-06-02
For the server download, it says "64-bit – Recommended for most users" and is selected by default.

Perhaps there are some issues with Gnome or perhaps X on the 64-bit platform? Typically the GUI items are missing from a server.

---

### Post by tad1073 on 2010-06-02
> **garvinrick4 said:**
> i have had quite a few installs of 64 bit and have had zero issues.

+1

---

### Post by KayakJim on 2010-06-02
As the rest of you have stated, there does not appear to be any issues when running a 64-bit desktop system.

I will do some cursory searching to see if the "problem" does indeed have to do with the GUI aspects.

If anyone else comes across some information regarding this or perhaps sees an official statement from Canonical on the subject, it would be great to post the information here.

---

### Post by KayakJim on 2010-06-03
Created a [separate thread]("http://ubuntuforums.org/showthread.php?t=1500618") for additional information.

---

### Post by cascade9 on 2010-06-03
> **KayakJim said:**
> The 64-bit version was installed first. Like my system the bluetooth and internal microphone did not work. In addition, clicking on play buttons within flash videos would intermittently work. Skype was not usable since the internal mic did not work.

No idea on bluetooth or the mic, but that flash issue is (AFAIK) a known problem with running 32bit flash in a wrapper. Install the 64bit version, by whatever method you like (I do it manually) and it should work....as well as flash ever does.

---

### Post by philinux on 2010-06-03
Threads merged.

---

