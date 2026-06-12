---
title: "Web Dev Testing in IE6+"
date: 2011-08-19
forum: General Help
---

### Post by in·ter·punct on 2011-08-19
Hello everyone, just made the switch to Ubuntu. Loving it.

So, I like to do some web development in my free time which means I have to test in IE6 and above. I started using IETester which provides IE5.5 all the way to IE9 in one application, but after 2-3 days I realised it is rather buggy and it doesn't mimic the browsers exactly. This is in Windows 7 via VirtualBox. I haven't tried the application in Vista or XP though. Anyway, my main problem is that it doesn't mimic the browsers exactly.

I haven't tried [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") because it only suppports IE5-6 with beta support for IE7, IE8, IE9.

Another option is _[COLOR=RoyalBlue][Linie]("https://code.google.com/p/linie")[/COLOR]_. At the moment it only supports IE7.

There is also the _[User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/")_ add-on for Firefox. For some reason when I click on +Add to Firefox it downloads perpetually (Add-on downloading, Unknown time remaining, 0 bytes transfered (0 bytes/sec)). Has anyone tried this?

As I see it, the only ways to solve this is to:

[LIST=1]
[*]install a guest operating system for each version of IE I need via VirtualBox.
[*]have a dedicated IE testing computer with an operating system for each version of IE starting from IE6.
[/LIST]

The first option is possible, but it'll probably slow down my computer. The second option *might* be possible as I have an old laptop lying around, although I'd have to buy a new adapter and add more RAM.

Your thoughts? Does anyone here do any web development work and if so how do you test for IE?
[COLOR=Black][U]
**EDIT:**[/U][/COLOR][COLOR=DarkOrange][COLOR=Black]

Solution: Read this article: [/COLOR][Reliable Cross-Browser Testing Part 1, IE - Smashing Magazine]("http://coding.smashingmagazine.com/2011/09/02/reliable-cross-browser-testing-part-1-internet-explorer/")[COLOR=DarkSlateBlue] [COLOR=Black]by AOL UI developer Addy Osmani.

Also: [Test Websites in IE 9, 8 and 7 under Linux / Mac OS X ~ Web Upd8: Ubuntu / Linux Blog]("http://www.webupd8.org/2011/09/test-websites-in-internet-explorer-9-8.html")
[/COLOR][/COLOR][/COLOR]

---

### Post by MG&amp;TL on 2011-08-19
You could dual-boot. I don't know if this helps.

---

### Post by in·ter·punct on 2011-08-19
I could dual boot but it's quite time consuming.

---

### Post by MG&amp;TL on 2011-08-19
Not really. OK, though, your choice. Why do you think it is time-consuming? I suppose you do  have to switch over everytime you want to test something.

---

### Post by SavageWolf on 2011-08-19
I'm not sure, but doesn't IE8's webdev tools thing have an IE 6/7 compatibility mode? I remember seeing it on a school computer...

EDIT: Just tested it on my notebook thing, pressing F12 then selecting it from "browser Mode" displays the page differently.

---

### Post by in·ter·punct on 2011-08-19
> **MG&TL said:**
> Not really. OK, though, your choice. Why do you think it is time-consuming? I suppose you do  have to switch over everytime you want to test something.
I would have to install 4 operating systems just for IE, if I'm going to multi boot I might as well create 4 virtual machines instead. I feel like I would be going back and forth, wasting time inbetween. I haven't tried this, but I don't think it would be very efficient. I'm guessing you meant multi boot, right?

> **SavageWolf said:**
> I'm not sure, but doesn't IE8's webdev tools thing have an IE 6/7 compatibility mode? I remember seeing it on a school computer...

EDIT: Just tested it on my notebook thing, pressing F12 then selecting it from "browser Mode" displays the page differently.
That's an interesting thought. Reading a post about it now.

Edit: From what I can gather from the MSDN blog [post]("https://blogs.msdn.com/b/ie/archive/2008/08/27/introducing-compatibility-view.aspx"), you can emulate IE7 in IE8 but not IE6.
Edit2: IE8's IE7 mode is out of the question: [http://stackoverflow.com/questions/4223169/is-ie7-in-ie8s-developer-tools-compatibility-mode-reliable-for-testing-the-front](http://stackoverflow.com/questions/4223169/is-ie7-in-ie8s-developer-tools-compatibility-mode-reliable-for-testing-the-front)
[ ]("https://blogs.msdn.com/b/ie/archive/2008/08/27/introducing-compatibility-view.aspx")

---

### Post by pqwoerituytrueiwoq on 2011-08-19
i believe playonlinux can run IE (dont think it works wiht IE 9 but there is virtual box)
also you could but [this]("http://i53.tinypic.com/1zdpumx.png") icon on your site

---

### Post by in·ter·punct on 2011-08-19
So, to review:

[LIST]
[*][IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") supports IE5-6 with beta support for IE7, IE8, IE9.
[*]_[COLOR=RoyalBlue][Linie]("https://code.google.com/p/linie")[/COLOR]_ supports IE7.
[*] playonlinux supports IE7.
[*] Wine won't be possible to use with IE since none of the versions have a platinum rating.
[/LIST]
   You could probably install IEs4Linux to test in IE5-6 and Linie/playonlinux to test in IE7. Two guest operating systems on VirtualBox would then complete the IE package. Would this work? I've heard of scenarios where installing IE7/IE8 caused IE6 to break, but this was on Windows.

Thanks for all the input so far.

> **pqwoerituytrueiwoq said:**
> ...
also you could but [this]("http://i53.tinypic.com/1zdpumx.png") icon on your site

"Anyone who slaps a 'this page is best viewed with Browser X' label on a  Web page appears to be yearning for the bad old days, before the Web,  when you had very little chance of reading a document written on  another  computer, another word processor, or another network."
   -- [Tim Berners-Lee]("http://www.w3.org/People/Berners-Lee/") in Technology Review, July 1996

---

### Post by zealibib slaughter on 2011-08-19
I've used this website a few times.  It does a ok job at showing you what a website will look like for a ton of browsers: [http://browsershots.org/](http://browsershots.org/)

---

### Post by pqwoerituytrueiwoq on 2011-08-19
> **in·ter·punct said:**
> "Anyone who slaps a 'this page is best viewed with Browser X' label on a  Web page appears to be yearning for the bad old days, before the Web,  when you had very little chance of reading a document written on  another  computer, another word processor, or another network."
   -- [Tim Berners-Lee]("http://www.w3.org/People/Berners-Lee/") in Technology Review, July 1996
perhaps but supporting pre-ie8 will drive you crazy if you are making web apps, maybe you can get them to install google chrome frame

---

### Post by in·ter·punct on 2011-08-19
> **zealibib slaughter said:**
> I've used this website a few times.  It does a ok job at showing you what a website will look like for a ton of browsers: [http://browsershots.org/](http://browsershots.org/)
You have to wait quite a bit for the images to be uploaded.
> **pqwoerituytrueiwoq said:**
> perhaps but supporting pre-ie8 will drive you crazy if you are making web apps, maybe you can get them to install google chrome frame
Google Chrome Frame is interesting, I'll definitely be using it. HTML5 Boilerplate uses it as well.

---

### Post by pqwoerituytrueiwoq on 2011-08-19
> **in·ter·punct said:**
> Google Chrome Frame is interesting, I'll definitely be using it. HTML5 Boilerplate uses it as well.
what it actually does is load the page in chrome like the IE tab addon for firefox (IE tab+chrome tab=chrome tab)
you can use for things as simple as css3 support if you wanted
but odds are if they are using IE6 they cant install chrome frame but you cant inform them chrome does not need admin rights to install (alternatively there is firefox portable)

---

### Post by kaldor on 2011-08-19
> **in·ter·punct said:**
> Your thoughts? Does anyone here do any web development work and if so how do you test for IE?

I'm a web development student, and I do not think it's worth trying to make stuff work for IE6 anymore. If people are too lazy to update to a browser made within the last decade, then they shouldn't be in posession of a computer. Pretty useless comment on my part, but it's how I feel :)

Edit: Should also mention that IE9 is a lot better from standards compliance. If you follow web standards, I would not worry about newer IE releases much.

---

### Post by in·ter·punct on 2011-08-19
> **MG&TL said:**
> You could dual-boot. I don't know if this helps.
Ignore my other replies... I hadn't put much thought into them. The dual boot option could work.

It looks like MS is providing virtual machine hard drives (VHDs) of Windows with IE pre-installed so that you can run multiple version of IE using Win XP mode. The VHDs are free, but here's the catch: you need Windows 7 Professional, Enterprise, or Ultimate edition and the VHDs expire at some point so you'll have to go through the whole process again. Here's a link to their blog post about it: [http://blogs.msdn.com/b/ie/archive/2011/02/04/testing-multiple-versions-of-ie-on-one-pc.aspx](http://blogs.msdn.com/b/ie/archive/2011/02/04/testing-multiple-versions-of-ie-on-one-pc.aspx)

This could be an option as you only need to dual boot as MG&TL suggested.
> **kaldor said:**
> I'm a web development student, and I do not think it's worth trying to make stuff work for IE6 anymore. If people are too lazy to update to a browser made within the last decade, then they shouldn't be in posession of a computer. Pretty useless comment on my part, but it's how I feel :)

Edit: Should also mention that IE9 is a lot better from standards compliance. If you follow web standards, I would not worry about newer IE releases much.
All right, let's say we discard IE6. We still need to test for IE7+ though. So how do we go about doing this? dual boot + Win 7 XP Mode or VM? How do *you* test on Ubuntu?

---

### Post by pqwoerituytrueiwoq on 2011-08-19
> **in·ter·punct said:**
> Ignore my other replies... I hadn't put much thought into them. The dual boot option could work.

It looks like MS is providing virtual machine hard drives (VHDs) of Windows with IE pre-installed so that you can run multiple version of IE using Win XP mode. The VHDs are free, but here's the catch: you need Windows 7 Professional, Enterprise, or Ultimate edition and the VHDs expire at some point so you'll have to go through the whole process again. Here's a link to their blog post about it: [http://blogs.msdn.com/b/ie/archive/2011/02/04/testing-multiple-versions-of-ie-on-one-pc.aspx](http://blogs.msdn.com/b/ie/archive/2011/02/04/testing-multiple-versions-of-ie-on-one-pc.aspx)

This could be an option as you only need to dual boot as MG&TL suggested.

All right, let's say we discard IE6. We still need to test for IE7+ though. So how do we go about doing this? dual boot + Win 7 XP Mode or VM? How do *you* test on Ubuntu?I believe anyone that used IE7 will likely be using IE8 now since they apparently update (not that it is much better)

---

### Post by in·ter·punct on 2011-08-19
> **pqwoerituytrueiwoq said:**
> I believe anyone that used IE7 will likely be using IE8 now since they apparently update (not that it is much better)
Well, if Google stops support for IE7: [http://googleenterprise.blogspot.com/2011/06/our-plans-to-support-modern-browsers.html](http://googleenterprise.blogspot.com/2011/06/our-plans-to-support-modern-browsers.html)

---

### Post by pqwoerituytrueiwoq on 2011-08-19
fair enough but ie7 is not very popular
[http://www.w3schools.com/browsers/browsers_explorer.asp](http://www.w3schools.com/browsers/browsers_explorer.asp)

---

### Post by kaldor on 2011-08-20
> **in·ter·punct said:**
> All right, let's say we discard IE6. We still need to test for IE7+ though. So how do we go about doing this? dual boot + Win 7 XP Mode or VM? How do *you* test on Ubuntu?

Don't bother dual booting. Get a Windows XP VM and test it that way; that's how I do it. IE8 is probably the main concern, since that's what all new computers come with these days. The only people I know who use IE7 are people who are hyper-reluctant to any slightest bit of change on their machines. But, it's still a common browser.

Also, you may like [_this_]("http://code.google.com/p/html5shiv/").

Edit: Subtle Firefox/Chrome/Opera badges somewhere on the page might help ;)

---

### Post by in·ter·punct on 2011-08-20
> **pqwoerituytrueiwoq said:**
> fair enough but ie7 is not very popular
[http://www.w3schools.com/browsers/browsers_explorer.asp](http://www.w3schools.com/browsers/browsers_explorer.asp)
What I meant was that if Google stops support for IE7 then it's probably a good idea I do too.

Here's an excerpt from the post: "As of August 1st, we will discontinue support for the following browsers and their predecessors: Firefox 3.5, Internet Explorer 7, and Safari 3. In these older browsers you may have trouble using certain features in Gmail, Google Calendar, Google Talk, Google Docs and Google Sites, and eventually these apps may stop working entirely."
> **kaldor said:**
> Don't bother dual booting. Get a Windows XP VM and test it that way; that's how I do it. IE8 is probably the main concern, since that's what all new computers come with these days. The only people I know who use IE7 are people who are hyper-reluctant to any slightest bit of change on their machines. But, it's still a common browser.
...

I've seen old versions of IE being used in schools where the students didn't have administrator privileges to upgrade, this may also be true for employees who are stuck with the browser. IE9 is still lacking.
> **kaldor said:**
> 
...
Also, you may like [_this_]("http://code.google.com/p/html5shiv/").

Edit: Subtle Firefox/Chrome/Opera badges somewhere on the page might help :wink:

Already use it and about the badges, yeah, maybe. :p
[U]
Edit:[/U]
So, I'm following this guide: [http://shapeshed.com/journal/testing_with_ie6_ie7_and_ie8_on_virtualbox/](http://shapeshed.com/journal/testing_with_ie6_ie7_and_ie8_on_virtualbox/).

I don't know much about these things, but MS says this: "Due to the size of the Windows 7 and Windows Vista VHDs, it is split across several files, you'll need to download all files for that version of the Internet Explorer and uncompress them to the same directory to unpack the VHD file." This is from this page: [http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=11575](http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=11575)

I see there are four files for Windows 7 IE8 and seven files for Windows 7 IE9, does that mean I have to download them all?

Windows_7_IE8.part01.exe     700.0 MB
Windows_7_IE8.part02.rar     700.0 MB
Windows_7_IE8.part03.rar     700.0 MB
Windows_7_IE8.part04.rar     553.0 MB

Windows_7_IE9.part01.exe     700.0 MB
Windows_7_IE9.part02.rar     700.0 MB
Windows_7_IE9.part03.rar     700.0 MB
Windows_7_IE9.part04.rar     700.0 MB
Windows_7_IE9.part05.rar     700.0 MB
Windows_7_IE9.part06.rar     700.0 MB
Windows_7_IE9.part07.rar     131.0 MB

The guide I'm following doesn't say much about this, it just talks about the .exe. Any help is much appreciated.

_Edit2:_ I have a Windows XP OS CD that came with an older laptop. It says "Only for distribution with an HP or Compaq PC". It would be fine to install this on a Dell, right?
_Edit3:_ I should probably start a different thread for this in the Virtualization forum.

---

