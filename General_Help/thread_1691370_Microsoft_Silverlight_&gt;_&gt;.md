---
title: "Microsoft Silverlight &gt;_&gt;"
date: 2011-02-19
forum: General Help
---

### Post by speedruntrainer on 2011-02-19
Hello.

I want to watch a TV program that I missed >_> but it says I need to install Microsoft Silverlight and I don't want to start my ultraslow Windows for that.
What do I need to do? I searched on Ubuntu software center but it didn't work >.<

Greetings, speedruntrainer

---

### Post by UltraAnders on 2011-02-19
Try here: [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)
Although I still can't watch films on film4od :(

---

### Post by speedruntrainer on 2011-02-19
I downloaded it but I still can't watch the tv program. Black screen now.
Sorry for the late reply, I'm on my Wii because I had some problems loading this site.

---

### Post by synapsys on 2011-02-19
> **speedruntrainer said:**
> I downloaded it but I still can,t watch the tv program. black screen now.
Sorry for the late reply, I,m on my WIi because I had some problems loading this site.

Moonlight has worked fine for me so far... what website are you trying to watch the tv program on?

---

### Post by speedruntrainer on 2011-02-19
[http://www.rtl.nl/xl/#/u/72bbe6ca-e7f8-3555-acf2-34aea949c64c/](http://www.rtl.nl/xl/#/u/72bbe6ca-e7f8-3555-acf2-34aea949c64c/) It's a Dutch program, I like it very much :P

---

### Post by PaulReaver on 2011-02-19
I think moonlight is in one of the repos now...

yup

moonlight-plugin-mozilla

and

moonlight-plugin-chromium



theres a new moonlight coming out soon thats up to date compared to the windows silverlight...
moonlights missing some stuff, some sites don't work :(

---

### Post by speedruntrainer on 2011-02-19
Ok, too bad it didn't work, started Windows and watched it, damn Microsoft won this match again xD

Thanks for the help anyways :)

---

### Post by synapsys on 2011-02-19
> **speedruntrainer said:**
> Ok, too bad it didn't work, started Windows and watched it, damn Microsoft won this match again xD

Thanks for the help anyways :)

Microsoft wins because Silverlight was developed by..... Microsoft..... What's wrong with flash? I don't know....

---

### Post by TheHackOps on 2011-02-19
MegaUpload????, FTW

---

### Post by I&#9829;HTML5 on 2011-02-19
> **synapsys said:**
> Microsoft wins because Silverlight was developed by..... Microsoft..... What's wrong with flash? I don't know....

One problem with Flash in this type of situation is that Silverlight supports (more) DRM control. For this reason, many "content providers" choose Silverlight over Flash and choose protected content over the (slightly) larger amount of users. I have the same problem with Netflix streaming. :(

---

### Post by UltraAnders on 2011-02-20
> **PaulReaver said:**
> I think moonlight is in one of the repos now...

yup

moonlight-plugin-mozilla

and

moonlight-plugin-chromium



theres a new moonlight coming out soon thats up to date compared to the windows silverlight...
moonlights missing some stuff, some sites don't work :(Worth noting the repo version is 2.0 (or 2.2, it's not entirely clear in Synaptic and I've not installed it from repo), where as the website installed 3.99.0.1 for me.

The film4od website says I've got a high enough version of Silverlight, but then when I try to view the test movie, it comes up with meaningless message "Sorry, you must use a PC or laptop to access this site.", lol. There don't seem to any UK movie streaming sites that work with Ubuntu :(

---

### Post by emarkay on 2011-02-21
What source are you using for content?

There are proprietary formats and programs that make open source applications fail. One that comes to mind is  Netflix - they use a Silverlight codec that must be licensed, and that can not be "cracked" legally, nor "provided" to anyone other than them.  It is configured only to work with Microsoft licenced software (on PC's and on stand alone devices).  

There are, unfortunately many situations like this these days.

Personally, I avoid any site that does that, and anyway, most content is available from other sources if you look hard enough.  Google is always your friend in this case.

---

### Post by UltraAnders on 2011-03-11
> **emarkay said:**
> What source are you using for content?

There are proprietary formats and programs that make open source applications fail. One that comes to mind is  Netflix - they use a Silverlight codec that must be licensed, and that can not be "cracked" legally, nor "provided" to anyone other than them.  It is configured only to work with Microsoft licenced software (on PC's and on stand alone devices).  

There are, unfortunately many situations like this these days.

Personally, I avoid any site that does that, and anyway, most content is available from other sources if you look hard enough.  Google is always your friend in this case.Have to say I've searched pretty hard and haven't come up with any decent legal film download sites that support Ubuntu. Would love to be proved wrong :)

---

### Post by mashdot on 2011-03-12
Well, I hope that someone will find a work around for this. I have the exact same problem on Debian, Moonlight installed fine but you get that strange Film4OD message: 

"Sorry, you must use a PC or laptop to access this site."

Just for the record I even tried defining my browser user agent as Microsoft Windows IE. But this made no difference. It sounds like emarkay could be right in that Film4OD et al are looking at the plugin itself.

If I find out how to get this to work I will let people know.

---

### Post by Frogs Hair on 2011-03-12
There is a newer version of Moonlight than in the repository and can be downloaded from here.
[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

---

### Post by lite1979 on 2011-04-07
Woohoo! Just downloaded the nightly build from the above mentioned  website, and I can finally watch the 13h broadcast on France2.fr! Thank  you! 2.4 wasn't working for me at all...

---

### Post by Urbanmoth on 2011-10-21
> **UltraAnders said:**
> Have to say I've searched pretty hard and haven't come up with any decent legal film download sites that support Ubuntu. Would love to be proved wrong :)

Try Binkbox [www.blinkbox.com]("http://www.blinkbox.com")
everything is flash

---

### Post by MrKappa on 2011-11-13
Hello' I have the following situation:

I have 64 bit Ubuntu 11.10 in a new partion where moonlight does not work and I cannot find it on synaptic and, in parallel another partition with Ubuntu 11.04 where Moonlight is working and it was available on repository.

Firefox profile is shared for both Ubuntu partitions and Moonlight extension is installed (version 3.99.03 currently).
So if I open a web page using Silverlight on 11.04 I can see the multimedia content in Firefox but on 11.10 instead I still see that Silverlight should be installed....(firefox profile is the same).
The only difference is about the missing "moonlight-plugin-core" which seems to be not available in the repository and the package is not available installing through command line.

It has been really removed? How can I install it? 
Thanks

---

### Post by MrKappa on 2011-11-18
I just discovered that the problem I have with moonlight is caused by the firefox profile which is located on ntfs partition where seems that does not have full access to the disk. It's strange but If I move the profile on fat32 partition moonlight is working and on ntfs I don't see folders o files with r/w limitations. 
I like to keep there possibly because I want to share the profile between different operative systems.

---

### Post by Robbo35 on 2012-02-24
Just for interest please see below the reply I received from Love Film when I wrote to complain that I couldn't stream from their website...
 
[B]Thank you for your letter regarding the Silverlight player.
 
Unfortunately the Microsoft Silverlight player does not support Linux, 
Unix and Non-Intel Mac operating systems and you will be unable to use 
the LOVEFiLM Instant service if you are using any of these systems. 
Please visit our websites help section 
[www.lovefilm.com/help/dyn_faqs.html](www.lovefilm.com/help/dyn_faqs.html) under minimum requirements for 
further information.
 
We are very sorry for the inconvenience that this may cause and would 
like to assure you that we are only making this change as the studios 
and copyright holders that we work with have instructed us to do so to 
ensure that their content is as protected as possible. Flash is not 
secure enough to stop copyright infringements and so we have taken this 
action to upgrade our security.
 
We sincerely apologise for any inconvenience caused.
[/B]

---

