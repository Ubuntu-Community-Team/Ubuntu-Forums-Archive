---
title: "How to Fake Web servers into believing you are using IE5.5?"
date: 2009-06-26
forum: General Help
---

### Post by eternal0void on 2009-06-26
I currently work from home doing phone tech support, making just enough to cover the basic expenses.  Recently it was suggested that I go to work for the Missouri Government, as there were better-paying job openings just over the border (I live in Kansas), and friends of mine in Kansas who work in Missouri would be able to carpool me to the jobs.

Unemployment here is rather high, the second highest in Kansas (Wichita and Sedgwick County have the highest unemployment), and the Missouri jobs pay well enough to make up for the problems of figuring out state income tax for two states (its complex because you can deduct what you pay in the "job" state from the "home" state's taxes).

Unfortunately, Missouri's government has decided that only Windows users will be allowed to apply for jobs in Missouri.  They switched to an online application process for all of the computer jobs for which I qualify, and the online application process requires Internet Explorer 5.5.

Is there a way to make FireFox (or any other Linux browser for that matter), fake web servers into believing that FireFox is Internet Explorer?  I seem to recall doing this in the late 1990s with Mozilla but I cannot remember how I did it then.

Before you go into the obvious options, I do not own a car (hence the carpooling being important).  I own a bicycle but the closest library is about an hour by bicycle (and the daytime temperatures are in the 100s around here).  I do not make enough to afford a Windows license to use their OS.  All of my computers run Linux and there hasn't been a problem with this up until now.

---

### Post by billgoldberg on 2009-06-26
IE 5.5?

Wow.

You could try the user agent switcher add on for firefox to fool them into thinking you are using IE.

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

There is also a project known as IE4Linux you could take a look at.

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by hibliss on 2009-06-26
IE4Linux project is probably your best bet. It just uses Wine. Why does it have to be IE 5.5? Not even many Windows users would still have that.

---

### Post by eternal0void on 2009-06-26
> **hibliss said:**
> IE4Linux project is probably your best bet. It just uses Wine. Why does it have to be IE 5.5? Not even many Windows users would still have that.

Sorry, I should clarify that its IE5.5 **or better**.

Wasn't IE 5.5 the most current version that could still work on Windows 98?

---

### Post by RobtA on 2009-06-26
I am sure the original post meant "IE5.5 or newer," not simply IE5.5.

But you might not be able to fake IE5.5 or newer, on Linux. It might be possible with WINE (not sure), but simply changing the user agent string in Firefox will not work. here is why:

IE5.5 was the first IE browser to rely on ActiveX objects that would be downloaded and add specific funtionality to the browser. These ActiveX objects are specific, Windows-platform technology. Some other browsers on the Windows platform can use a software "shim" to bring in an ActiveX object. However, browsers on platforms other than Windows do not have ActiveX technology, unless there is an emulation. Again, maybe WINE can emulate it.

---

### Post by hibliss on 2009-06-26
IE4Linux will work, and Wine Is Not an Emulator (W.I.N.E.).

---

### Post by Cheesemill on 2009-06-26
> **RobtA said:**
>  but simply changing the user agent string in Firefox will not work.

It may well do. I've come across a lot of web sites that don't use ActiveX but still check to see if you're using Internet Explorer.

---

### Post by sedawk on 2009-06-26
Here are more (legal) ideas:

Get a beta of Windows 7 (is there are fix end-of-evaluation date or
is it "30 days after installation"?) which is for free and then
use the IE that is part of Windows 7 to do the job.
(You can try to install it inside virtual PC using VirtualBox
 or free VMware Server).

Here in Europe I just bought a cheap Acer-PC (emachines EL1600)
for 199 Euros including Windows XP.
(not sure a similar (priced) model exists in the US)

Do you have some friends running Windows? They can give
you access via VNC so you use your friends PC with Windows
via remote access to run IE on that PC.

File a law suit and earn a few million bucks because
they might be violating a bunch of laws by forcing you
to use M$ software (non-discriminating or anti-microsoft-monopol
or ...) ;-)

---

### Post by Grenage on 2009-06-26
Agent switcher, simple and easy.

---

### Post by Yellow Pasque on 2009-06-26
Tell the employer that IE is a security risk and it doesn't render web pages anywhere near accurately: [http://en.wikipedia.org/wiki/Acid3](http://en.wikipedia.org/wiki/Acid3)

---

### Post by sedawk on 2009-06-26
> **Grenage said:**
> Agent switcher, simple and easy.

Yes, but lots of time it is not working ...

I have to use a mandatory web application that is IE-only.
It is not enough to switch the agent because JavaScript does
check for the browser too (examining available data structures).
I also tried IE4Linux which didn't work.
I needed a virtual PC, a legal Windows license and the
correct set of patches to make that crap work.

And they ignore any complains because even Firefox is
not officially supported - the only reason you don't get
fired for installing firefox is that it is needed by some
testers in our department.

---

### Post by Rallg on 2009-06-26
Sounds like your best bet is to get a cheap laptop with Windows. Perhaps you can find someone with Vista, and offer $50 as waste disposal fee. :)

---

### Post by jimv on 2009-06-26
Holy lord, I just tried the Missouri employment application (for kicks) with the User Agent Switch in Firefox and it was not pretty.  It looks awful and none of the buttons work, so you can't do anything.

Best off trying to use IE.

---

### Post by blueridgedog on 2009-06-26
Well, you could just go to the library and get on-line...

---

### Post by hibliss on 2009-06-26
Read the thread blueridgedog.

OP, I sent you a PM. Download Windows 7 RC1 for free and install in VirtualBox. [http://www.microsoft.com/windows/windows-7/download.aspx]("http://www.microsoft.com/windows/windows-7/download.aspx")

There are other options for acquiring a temp Windows license (30 day evaluation).

---

### Post by blueridgedog on 2009-06-26
> **hibliss said:**
> Read the thread blueridgedog.


Sorry I was so obtuse...

Let me elaborate.  It would be easier to simply go to the library and use a public terminal to complete the application than most of the suggestions made thus far.  If you want to simply "get it done" then life can be simple.

I do read threads before posting.

---

### Post by hibliss on 2009-06-26
> **eternal0void said:**
> 

Before you go into the obvious options, I do not own a car (hence the carpooling being important).  I own a bicycle but the closest library is about an hour by bicycle (and the daytime temperatures are in the 100s around here).

meh

---

### Post by blueridgedog on 2009-06-26
So he should either buy a laptop or install windows versus catching a ride to the library?  Like I said...I read it.

---

### Post by ugm6hr on 2009-06-26
> **hibliss said:**
> IE4Linux project is probably your best bet. It just uses Wine. Why does it have to be IE 5.5? Not even many Windows users would still have that.

Some links:
[https://help.ubuntu.com/community/InstallingInternetExplorer](https://help.ubuntu.com/community/InstallingInternetExplorer)
[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

Hope you get the job.  Good luck!

---

### Post by eternal0void on 2009-06-26
> **blueridgedog said:**
> Well, you could just go to the library and get on-line...

And in the message with which I started this thread, I stated:

"Before you go into the obvious options, **I do not own a car** (hence the carpooling being important). **I own a bicycle but the closest library is about an hour by bicycle (and the daytime temperatures are in the 100s around here).**"

You might as well have said "let him eat cake".

And since some of you live in regions which care enough about their citizens to have public transportation, Johnson County Kansas has no reliable bus transit system.  Seeing a "The JO!" bus is rather like seeing a white tiger.  The bus seems to run from 7am to 8am, then from 5pm to 6pm, with no possibility of using two bus routes to get anywhere.

> **blueridgedog said:**
> So he should either buy a laptop or install windows versus catching a ride to the library?  Like I said...I read it.

Catching a ride to the library.  Thats funny.  Everyone I know is too busy for that during library hours (multiple jobs) and the libraries are cutting back their hours (the recession).  Ironically, if I had the money there are computer shops a short distance away which could provide "a used laptop with Windows" or "a legal copy of Windows".

---

### Post by fugaki on 2009-06-26
Try out VirtualBox, you can run a virtual instance of windows inside linux, and I'm sure you can figure some way to obtain liscensing if think about it. :D

---

### Post by eternal0void on 2009-06-26
> **jimv said:**
> Holy lord, I just tried the Missouri employment application (for kicks) with the User Agent Switch in Firefox and it was not pretty.  It looks awful and none of the buttons work, so you can't do anything.

Best off trying to use IE.

Apparently something not installed by IE4Linux is necessary.  I tried to apply for an account with the Missouri job website, and I can get as far as the form to fill out personal information (SSN, address, contact info, etc.).  When I hit Save, the page jumps to the top of the screen and does nothing.

I'll hunt around for another button but its not looking good.  The site did think that I was using IE6.0.

---

### Post by sschnee on 2009-06-26
I know it was suggested before, but I didn't see whether you had tried it or not.  Did you try downloading Windows 7?  It's good enough to be free.

---

### Post by eternal0void on 2009-06-27
> **sschnee said:**
> I know it was suggested before, but I didn't see whether you had tried it or not.  Did you try downloading Windows 7?  It's good enough to be free.

Unemployment being what it is, I don't want to depend on a "solution" which is going to expire in 30 days.

---

### Post by jimv on 2009-06-27
> **eternal0void said:**
> Unemployment being what it is, I don't want to depend on a "solution" which is going to expire in 30 days.

The Windows 7 Release Candidate is good until June 1 of next year.

---

