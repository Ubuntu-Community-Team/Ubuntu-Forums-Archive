---
title: "What is the best way to run IE in Ubuntu?"
date: 2010-10-25
forum: General Help
---

### Post by CoolJohnB on 2010-10-25
To get into my bank account unfortunately I need Internet explorer although the bank says it works with Firefox it doesn't and when I spoke to their help desk they said I have to have IE.

I have tried IE tabs in Chrome and Firefox but they don't work, I have tried running IE under Wine but that doesn't work I have also tried installing IE with Crossover but that doesn't work either, so if anyone has any suggestions for using IE it would be much appreciated!

Thanks in advance for any help offered.

---

### Post by SavageWolf on 2010-10-25
I'd choose a different bank...

"Lets force our customers to only use a really insecure browser! What could possibly go wrong?!"

Failing that, uh, in what way doesn't it work?

---

### Post by kleskjr on 2010-10-25
+1 to change the bank

if you still want to check something, there was an add-on for chromium to simulate IE, I expect that there is one for FF as well.

---

### Post by Noah0504 on 2010-10-25
What version of IE are you trying to install?  I know IE 8 is pretty much unusable from my experience in WINE or CrossOver.  IE 6 works great, but that may be too old of a version.  7 seems to be okay.  Honestly, I would think about installing a virtual machine.  It may be a little over the top for what you're trying to do, but you know it will work anyway.

But if your bank supports IE 6, try installing that.  I've used it before for work and it works great (other than the fact that it's IE 6 :P ).

---

### Post by endotherm on 2010-10-25
have you tried the FF user agent switcher, to impersonate IE?

---

### Post by CoolJohnB on 2010-10-25
When I run it I just get a "Window" top line says "Wine Internet explorer" the window itself is just white space, nothing in it!  No space even to enter website etc.

---

### Post by ubudog on 2010-10-25
There is this, pretty cool.

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

Sucks that your bank needs IE though.

I hate IT departments sometimes. :)

---

### Post by endotherm on 2010-10-25
> **ubudog said:**
> 

I hate IT departments sometimes. :)
more likely the legal department. I called my bank about fine print in their paperless statements policy about system requirements indicating that a Windows OS was required. they said it was just to limit their liability if i didn't get a statement in a timely fashion while using other software.

---

### Post by gandaran on 2010-10-25
> **CoolJohnB said:**
> When I run it I just get a "Window" top line says "Wine Internet explorer" the window itself is just white space, nothing in it!  No space even to enter website etc.
thats the default wine IE using the gecko engine, you haven't installed the real internet explorer yet.
try this to run the wine IE, open the terminal and copy/paste this
```
"/home/user/.wine/drive_c/Programs/Internet Explorer/iexplore.exe" http://www.google.com/
```
replace the home/ "user"/ to your real user name and hit enter
this command opens google.com in IE, from there you can go to your bank website.

---

### Post by 3togo on 2010-10-25
Install playonlinux

```
wget http://www.playonlinux.com/script_files/PlayOnLinux/3.8.3/PlayOnLinux_3.8.3.deb
sudo dpkg -i PlayOnLinux_3.8.3.deb
playonlinux
```

then install ie7


:)

---

### Post by philinux on 2010-10-25
[https://addons.mozilla.org/en-US/firefox/addon/59/](https://addons.mozilla.org/en-US/firefox/addon/59/)

---

### Post by nynepac on 2010-10-25
Will user-agent switching be enough though?

---

### Post by Old *ix Geek on 2010-10-25
Ditto on switching to a different bank--an enlightened one. My husband's bank made a change recently and he could no longer access it with Firefox. He called and was told he had to use IE, and he told them he doesn't have that piece of crap on his computer. Then I e-mailed them and said that no bank should even encourage its customers to use IE, let alone REQUIRE it, as it's the most insecure browser on earth--and that we'd be switching banks because of this. I also pointed out that they're excluding us Linux users entirely. I used an analogy that I'm going to turn into a design on merchandise on my site, so I don't want to give it away just yet, but I think it's brilliant. :D

---

### Post by philinux on 2010-10-25
> **nynepac said:**
> Will user-agent switching be enough though?

Usually yes, sometimes no. But you have to try it first to find out. ;)

---

### Post by ubudog on 2010-10-25
> **endotherm said:**
> more likely the legal department. I called my bank about fine print in their paperless statements policy about system requirements indicating that a Windows OS was required. they said it was just to limit their liability if i didn't get a statement in a timely fashion while using other software.

Hmm....

---

### Post by ubudog on 2010-10-25
> **3togo said:**
> Install playonlinux

```
wget http://www.playonlinux.com/script_files/PlayOnLinux/3.8.3/PlayOnLinux_3.8.3.deb
sudo dpkg -i PlayOnLinux_3.8.3.deb
playonlinux
```

then install ie7


:)

Never tried that, thanks!  I always used the old way.  :lolflag:

---

### Post by CoolJohnB on 2010-10-25
Thanks for all the replies, tried user-agent that doesn't work, also tried playonlinux that didn't work either.  Because of where I live, South America, there is very little choice of banks that use internet banking, in fact our one has only just started!  Many places are still moving into the 20th Century here, let alone the 21st!

Tried installing IE6 using Crossover it gets half-way through and stops, probably because we have a slow internet connection, which is one of the many reasons I stopped using windows, m-soft seems to think that everyone has a super fast connection!  Automatic updates don't work in windows.  No problems with Ubuntu though.

I checked out IE4Linux but it seems to be fairly old with no refence to Maverick

---

### Post by ubudog on 2010-10-25
> **CoolJohnB said:**
> Thanks for all the replies, tried user-agent that doesn't work, also tried playonlinux that didn't work either.  Because of where I live, South America, there is very little choice of banks that use internet banking, in fact our one has only just started!  Many places are still moving into the 20th Century here, let alone the 21st!

Tried installing IE6 using Crossover it gets half-way through and stops, probably because we have a slow internet connection, which is one of the many reasons I stopped using windows, m-soft seems to think that everyone has a super fast connection!  Automatic updates don't work in windows.  No problems with Ubuntu though.

I checked out IE4Linux but it seems to be fairly old with no refence to Maverick

Pretty sure HSBC has an online banking system.  It is all around the world right?  Was there any error message with ies4linux?

---

### Post by SavageWolf on 2010-10-25
What happens if you visit the site in Fx/Chrome?

---

### Post by CoolJohnB on 2010-10-25
I have an international bank account, but I also need a local one, It doesn't work in IE tab for Chrome

---

### Post by deanjm1963 on 2010-10-25
Change banks - it's a disgrace that you are forced to use "spyware/malware/virus" ridden software to access your accounts.

Your bank should be SHAMED big time. I wonder if they were to refund any money due to theft via malware/spyware/virii etc, or is that the sole responsibility of the end user, but then again, you have been forced to use it.

---

### Post by alanmoore78 on 2010-10-25
I would not trust my banking information to the browser who shall not be named.

+1 on changing banks, or make them sign a paper stating that if you encounter any identity theft or loss of money or information by using their required system, that they will pay you ten percent per diem interest on any lost funds until it is recovered in full.

---

### Post by pqwoerituytrueiwoq on 2010-10-25
Just got the beat idea ever sue for browser discrimination if you win we can say good bye to IE only sites forever 

have the resources on your computer to run a virtual box? if you do not have a legal copy of windows tell the bank if they want your business to buy you one so you can use their system

+1 change bank

---

### Post by ivarn on 2010-10-25
> **pqwoerituytrueiwoq said:**
> Just got the beat idea ever sue for browser discrimination if you win we can say good bye to IE only sites forever 

have the resources on your computer to run a virtual box? if you do not have a legal copy of windows tell the bank if they want your business to buy you one so you can use their system

+1 change bank

Heh, it doesn't work that way, but someone should get sued for this, and that someone is the bank that doesn't give their customers a product that work.

But seriously, can microsoft do all this? I mean, IE, silverlight and DRM?
They are literally owning the rights of product that people are paying for.
I mean I know they do all this to weed out other OS's and stuff but is it really legal?
I mean it can't be. It's like saying monopole to rights they don't even own.
Sorry, I know this is way off topic but I just needed to get this off my chest here :)
Anyway, I think the reason why this bank must use IE is because it uses ActiveX which can not be used in linux even if you install IE.
So a better solution (if you're not gonna change the bank) is to install windows on virtualbox (if that's the case though).
+1 change bank.

---

### Post by Schrute Farms on 2010-10-25
I was just going to say VirtualBox too (if you have a copy of Windows), but I see the last two posters beat me to it so...

+1 on VirtualBox.

---

### Post by CoolJohnB on 2010-10-26
Well I have emailed the esupport department at my bank telling them I refuse to have an insecure and unsafe browser on my computer and asking if they will make changes so a safer more secure browser can be used.

Having left windows I don't want to put it back on my machine! Even in virtual box. Guess I'll have to check out other banks, at least I still have telephone banking.

Thanks for all the suggestions and interesting comments.

---

### Post by ubudog on 2010-10-26
Strange ies4linux doesn't work....

---

### Post by ivarn on 2010-10-26
> **ubudog said:**
> Strange ies4linux doesn't work....
Not at all. One word: ActiveX.
That's a windows applet.

---

### Post by Old *ix Geek on 2010-10-26
> **CoolJohnB said:**
> Well I have emailed the esupport department at my bank telling them I refuse to have an insecure and unsafe browser on my computer and asking if they will make changes so a safer more secure browser can be used.GOOD FOR YOU! :D If people don't speak up and explicitly tell companies that they do not and will not use IE, the companies have no incentive to change because they think everything's fine.

And that's why I object to fooling sites into thinking you're using IE. Why do that? Why reinforce the idiotic assumption that everybody uses windoze and IE? Instead, contact that site and tell them they're excluding you and you'll go elsewhere if they don't correct the problem.

---

### Post by ubudog on 2010-10-26
> **CoolJohnB said:**
> Well I have emailed the esupport department at my bank telling them I refuse to have an insecure and unsafe browser on my computer and asking if they will make changes so a safer more secure browser can be used.

Having left windows I don't want to put it back on my machine! Even in virtual box. Guess I'll have to check out other banks, at least I still have telephone banking.

Thanks for all the suggestions and interesting comments.

Great! :guitar::guitar::guitar::guitar:

---

### Post by Tristam Green on 2010-10-26
> **deanjm1963 said:**
> Change banks - it's a disgrace that you are forced to use "spyware/malware/virus" ridden software to access your accounts.

Your bank should be SHAMED big time. I wonder if they were to refund any money due to theft via malware/spyware/virii etc, or is that the sole responsibility of the end user, but then again, you have been forced to use it.

i'm glad you put those in quotes; i'd have had to call shenanigans on some libelous claims :(

oh, and virii is not just unacceptable, it's flat-out [wrong.](http://en.wikipedia.org/wiki/Plural_form_of_words_ending_in_-us#Virus)  lol@trying to sound academic.

---

### Post by endotherm on 2010-10-26
> **Tristam Green said:**
> i'm glad you put those in quotes; i'd have had to call shenanigans on some libelous claims :(

oh, and virii is not just unacceptable, it's flat-out [wrong.]("http://en.wikipedia.org/wiki/Plural_form_of_words_ending_in_-us#Virus")  lol@trying to sound academic.
meh on viruses, but I will call them octopi, until the takosan-tachi come home.

---

### Post by lavinog on 2010-10-26
You can try using the latest version of wine:
Following the instructions on this page: [link](http://www.winehq.org/download/deb):
```

sudo apt-add-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3

```

Once complete use winetricks (run from terminal) to install IE7.

---

### Post by CoolJohnB on 2010-10-26
I tried that IE installed but it said ActivX not working and took ages to get to the website when it got there it said it had to close down as an error had occurred.  It really confirms what a waste of time m-soft and its programs are!

---

### Post by boghadab on 2010-10-26
best is running it with wine or simmilar to wine, why would you want to do that anyways .

---

### Post by lavinog on 2010-10-26
> **CoolJohnB said:**
> I tried that IE installed but it said ActivX not working and took ages to get to the website when it got there it said it had to close down as an error had occurred.  It really confirms what a waste of time m-soft and its programs are!

If the site uses activeX, then you are out of luck.

What really sucks is when government websites require activex.
There was a post office worker on the forums a while back that couldn't access the human resources page to access their pay stubs because it required activex.

---

### Post by amac777 on 2010-10-26
Ubuntu forums should add an "IMPOSSIBLE" tag to use for these types of situations instead of "SOLVED". I saw the thread was solved and got all excited because I have the exact same problem except in my case the bank is in Taiwan......

---

### Post by ubudog on 2010-10-26
> **amac777 said:**
> Ubuntu forums should add an "IMPOSSIBLE" tag to use for these types of situations instead of "SOLVED". I saw the thread was solved and got all excited because I have the exact same problem except in my case the bank is in Taiwan......

Good idea, lol.

---

### Post by Tristam Green on 2010-10-27
> **lavinog said:**
> If the site uses activeX, then you are out of luck.

What really sucks is when government websites require activex.
There was a post office worker on the forums a while back that couldn't access the human resources page to access their pay stubs because it required activex.

If you're a worker in a public service setting, and you know what your employer requires of you at work to access a work-related website, why would you gripe when you try to use an unsupported configuration?

---

### Post by CoolJohnB on 2010-11-10
Some good news, I don't know if it was as a result of my email to them, but my bank has now changed it's website so that it works with Firefox and Chrome, Great!!

---

### Post by Mark Phelps on 2010-11-10
> **Tristam Green said:**
> If you're a worker in a public service setting, and you know what your employer requires of you at work to access a work-related website, why would you gripe when you try to use an unsupported configuration?

Because some folks will never pass up a chance to bash anything related to MS -- even though their products are used by around 90% of the PCs in the world.

---

### Post by SavageWolf on 2010-11-10
IE is only used by 20-90% of people (depends on how "techy" the site is). And seriously, it is not hard to support Fx and Chrome.

---

### Post by ubudog on 2010-11-10
> **SavageWolf said:**
> IE is only used by 20-90% of people (depends on how "techy" the site is). And seriously, it is not hard to support Fx and Chrome.

Totally true.

---

### Post by Mark Phelps on 2010-11-10
> **SavageWolf said:**
> And seriously, it is not hard to support Fx and Chrome.

Yes ... it IS ... if you write stuff depending on ActiveX controls, or Silverlight functions that are not available in alternatives like Moonlight.

Is that bad practice? Yes.  Is it commonplace? Unfortunately, yes, too.

---

### Post by ubudog on 2010-11-10
> **Mark Phelps said:**
> Yes ... it IS ... if you write stuff depending on ActiveX controls, or Silverlight functions that are not available in alternatives like Moonlight.

Is that bad practice? Yes.  Is it commonplace? Unfortunately, yes, too.

I think Firefox has plugins for both. Am I wrong?

---

### Post by dailydetention on 2011-02-10
> **amac777 said:**
> Ubuntu forums should add an "IMPOSSIBLE" tag to use for these types of situations instead of "SOLVED". I saw the thread was solved and got all excited because I have the exact same problem except in my case the bank is in Taiwan......

+1 on this. I'm a newbie on Linux and was checking the forum about this matter and got excited to see "SOLVED". Looks like there is no simple way to make it works, huh. I need to see how a website would render on IE for work.:neutral:

Tried the add-ons for FF and it doesn't work. Kept telling me that a plugin is required to show the page, but didn't give out any specific details on it, like WHAT plugin is missing exactly, etc.

---

### Post by lavinog on 2011-02-11
> **dailydetention said:**
> +1 on this. I'm a newbie on Linux and was checking the forum about this matter and got excited to see "SOLVED". Looks like there is no simple way to make it works, huh. I need to see how a website would render on IE for work.:neutral:

Tried the add-ons for FF and it doesn't work. Kept telling me that a plugin is required to show the page, but didn't give out any specific details on it, like WHAT plugin is missing exactly, etc.

Can you use an IE renderer to check your site:
[http://ipinfo.info/netrenderer/index.php](http://ipinfo.info/netrenderer/index.php)
[http://browsershots.org/](http://browsershots.org/)

---

