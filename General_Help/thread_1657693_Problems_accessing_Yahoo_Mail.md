---
title: "Problems accessing Yahoo Mail"
date: 2011-01-01
forum: General Help
---

### Post by radarfxst on 2011-01-01
I've been using Ubuntu for about 2 years now and love it, with one exception for roughly the last year - and there's no way I'll get my wife off of Windoze as long as this continues to happen.  I periodically have problems accessing Yahoo Mail (or signing into Yahoo at all, even to my.yahoo.com frontpage).

I'm running 11.04 and as I said this problem began about a year ago after an upgrade, although unfortunately I don't remember which one (possibly 10.04 onwards).  The same problem (inability to access yahoo) occurs with FireFox and Chromium, and if I reboot the computer into XP it doesn't happen (in fact it never, ever happens in XP with either Exploder, FF, or Chrome).

In my frustration earlier this morning, I began keeping a log of what happens.  This is the log:

=============================================
[http://my.yahoo.com/](http://my.yahoo.com/) [my home page]

"Firefox can't establish a connection to the server at login.yahoo.com"

I closed Firefox (with "exit," not the X), restarted and now get this:

"Invalid URL
The requested URL "/", is invalid.

Reference #9.be57f6d8.1293897207.ecf6a4b"

Refreshing (F5) didn't work this time, although sometimes it does.  I cleared recent history, closed FF & restarted again, and now I was was able to sign in to yahoo, got the following notice:

"The all-new Yahoo! Mail has not been tested with your operating system.  You can choose to continue anyway, or simply go to Yahoo! Mail Classic."

I chose "continue anyway" and was able to get in.

Signed out, left the computer and came back three hours later.  I got to the main page of my.yahoo.com, but when I clicked the button to sign in, I got:

"Invalid URL
The requested URL "/_ylt=Avy4MDJpqYMq2SfO813mo1ubvZx4/SIG=13uuhu9l6/EXP=1293991602/**https%3A/login.yahoo.com/config/login%3F.src=fpctx%26.intl=us%26.done=http%253A%252F%252Fwww.yahoo.com%252F", is invalid.

Reference #9.3f06fea5.1293905323.8a2336d "

Went back to [www.yahoo.com](www.yahoo.com), clicked sign in and this time it asked me for username and password.  When I entered them, the next page said simply "not found."
===============================================

Also noteworthy - sometimes when I try to go to yahoo.com, what comes up instead is monster.com.  These problems seem to come and go at will.  Sometimes I'll spend time trying to clear the history, and clear the cache, to no avail.  Other times FF won't work but Chromium pops right up, then FF works as well.  There doesn't seem to be any pattern to the problem except it happens only in Ubuntu, with two different browsers, and never happens in Windows.  Also - I have two laptops in addition to this desktop (they connect wirelessly, this connects through a Cat5 cable).  Same problem with the laptops.  Three computers, same problem with Ubuntu, but windoze works (and it PAINS me to say that because I truly love Ubuntu).

One more thing - sometimes this problem occurs every time I sign on for an entire day, other times I can go three or four days without a problem.

Any thoughts?

Thanks, radarfxst

---

### Post by radarfxst on 2011-01-01
I forgot to mention that I've searched the forums and didn't see anything quite like my problem, other than possibly SSL issues (and the thread I saw just said that SSL was set wrong, but didn't say how it was corrected).

---

### Post by Nytram on 2011-01-01
I'm not sure the new Yahoo mail is fully compatible with Linux, which may be the reason you're having problems. Have you tried Yahoo classic, that's what I use and don't have any trouble with it. There's not much difference between the two interfaces, and classic is also faster.

---

### Post by radarfxst on 2011-01-01
I haven't tried that - but I'm switching to classic now.  I'll report how it goes - thanks for the idea.

-radarfxst

---

### Post by dondiego2 on 2011-01-01
That's strange because I have never had problems.  I use the latest Yahoo mail (not the plus) but have no problems at all.  I've been using Ubuntu now for about a year.

---

### Post by perspectoff on 2011-01-01
I have no problems with either regular or Classic from (K)Ubuntu or any Linux (at least through Firefox). I stick with Classic, though, because the new Yahoo Mail is irritating to me as all get out. 

I also extensively filter the Yahoo home page, as I'm sick of being presented with college and high school sports videos and "amazing plays" for other moronic sports, or seeing some cutesy animal trick. (I use random IPs, so don't tell me this is served up based on the tracking of my IP surfing profile). I think Yahoo thinks the lowest common denominator for its home page is amazing sports plays and cutesy animals.

---

### Post by Nytram on 2011-01-01
I was going by the warning yahoo has about the new version "not being tested on linux" but i admit ive not tried it as i prefer classic.

---

### Post by radarfxst on 2011-01-01
So far everything is going good with yahoo classic mail, although as I said sometimes I can go a few days without a hitch.  If I can go one week like this, I'll be sure.

But I just now ran into another, similar, problem.  I got an email that someone posted a facebook comment, and when I clicked on the link to see the comment I got this error page with "Yahoo!" in the tab at the top:

"Sorry, the page you requested was not found.  Please check the URL..." and it went on.  

I got curious, so I closed that tab and opened a new tab (this is in Chromium, BTW).  A fresh tab; I typed in "www.facebook.com" and got the same error as above.  I was looking for facebook and got a Yahoo response...  This doesn't seem to have anything to do with Yahoo mail (since I opened a new tab and tried from scratch).  But it's a similar issue...

---

### Post by radarfxst on 2011-01-01
After I posted the above reply, I went back to the tab (so we're talking maybe 5 minutes), and hit F5.  Went straight to facebook this time.

Weird...  I can live with minor glitches, but not being able to check email was getting to be a serious problem.  I hope Yahoo Classic fixed that for good!

---

### Post by radarfxst on 2011-01-02
Quick update.  I was able to get into Yahoo Mail this time eventually, after a string of weird items.  From my log:

=================================
20110102

1.  Opened Chromium.  My homepage (my.yahoo.com, not signed in) appeared fine.
2.  Clicked "sign in"
3.  The page that appeared had a red background.  The tab said "SSL error", and the page itself said "This is probably not the site you are looking for!
You attempted to reach login.yahoo.com, but instead you actually reached a server identifying itself as edit.yahoo.com. This may be caused by a misconfiguration on the server or by something more serious. An attacker on your network could be trying to get you to visit a fake (and potentially harmful) version of login.yahoo.com. You should not proceed."
--this is incorrect.  There is no SSL error, and it is the page I was looking for.  So I clicked "proceed anyway"
4.  The yahoo login page appeared.  I entered my username and password.
5.  My yahoo homepage came up, with most of the page greyed out and a highlighted box saying "MyYahoo! New content added.  You have added 'My Mail' to you page.  Continue or Cancel".  Since "My Mail" now shows up twice, I hit cancel.
6.  Then I clicked on "mail aggregator" and was able to get in to check my mail.
=================================

I tried Google Chrome right before the above, and got an error about "too many redirects" or something to that affect (I didn't write down the errors in my log).

- Radarfxst

---

### Post by radarfxst on 2011-01-03
Still having problems, now I can't access email again.  I opened Chromium, and tried to logon to [www.yahoo.com](www.yahoo.com), I was told there was a security risk (I didn't write down the details, but similar SSL problem as I describe above).  I said to accept the risk and go anyhow, then I was brought to the sign in page.  I entered my username and password, and after I clicked "sign in" I was brought to the yahoo help page.  

I closed Chromium and tried Firefox.  I typed in [www.yahoo.com](www.yahoo.com), and up came Monster.com.  

I closed FF and tried Chrome, and got the exact same results as Firefox - if I typed in anything to do with yahoo ([www.yahoo.com](www.yahoo.com), my.yahoo,com, mail.yahoo.com) what came up was Monster.com - even though the URL address bar had the address that I typed in.

HELP!  This is very frustrating!

Tom

---

### Post by Nytram on 2011-01-04
when you say that the problems started after an upgrade, was this one of the regular bug-fix/security updates, or a system upgrade such as 9.10 -> 10.04 ?

---

### Post by radarfxst on 2011-01-04
The problems definitely began after an upgrade, and because they began about a year ago I believe it was the upgrade from 9.04 to 9.10.  If not that, then it was the upgrade from 9.10 to 10.04 (although I think it was the former case).

As often as possible, I'm going to keep one of my laptops next to my desktop so that I can verify that when the problem exists on one computer, it exists on the other at the exact same time (or not).  Maybe that will help with troubleshooting.

Thanks...

---

### Post by radarfxst on 2011-01-04
Okay, BIG discovery.  I have my laptop on the desk next to my desktop.  On the desktop I signed off and on yahoo a few times until I got the error.  Then I went to the laptop (which got to Yahoo just fine a few minutes earlier), and it too now had problems.  Two totally different computers (one Dell with a Pentium processor, one Compaq with an AMD Sempron).  Same OS, with same updates, on both.  Desktop is connected to my router through a Cat5 cable, laptop is connected via wireless.

I read in some other threads that someone somewhere had to change ISPs because of a problem similar to this (theirs worked in Windows but not in Ubuntu, like my problem).  Unfortunately, where I live in Georgia, I have Windstream and that's all - so that's not an option for me.  Before I go that route, is there a way to determine if the problem lies with the router?

My connection is computer to router (Linksys WRT160N V3 wireless) to ADSL modem (Speedstream 4200).

---

### Post by Nytram on 2011-01-05
i was going to suggest a clean install of ubuntu, as sometimes upgrades cause trouble, but it would be unusual for 2 computers to have exactly the same problem...

a clean install **may** solve your problem, but no guarantees. it's what i'd try, as you say the problems started after a system upgrade.

---

### Post by oldos2er on 2011-01-08
Since you're using 11.04, any assumption of stability kind of flies out the window. 

I've had no problem running Yahoo mail, the few times I've used it, with Firefox or Chrome. Are you using adblock or noscript or something similar?

---

### Post by radarfxst on 2011-01-09
No, not running any adblock or A/V programs.  I've tried disabling all plugins in both Chrome and FF, and tried resetting all settings to default with no luck.  It is extremely frustrating and I'm currently thinking about switching from Yahoo mail to another (Gmail, Excite, etc.).  I'd really like to figure this out though.

Seems to me a big clue is that when this problem is occuring, I get redirected - IOW, I type in [www.yahoo.com](www.yahoo.com) and Monster.com shows up (that's the common one).  There has to be a way to troubleshoot that (ping or something), but I just don't know enough about networking and IP addressing to figure it out.

---

### Post by CharlesA on 2011-01-09
Try using a different DNS server. Google's DNS are: 8.8.8.8 and 8.8.4.4

---

### Post by radarfxst on 2011-01-09
You went over my head there...  Use a different DNS server (Google's) to access my yahoo mail?  How do I do that?

---

### Post by CharlesA on 2011-01-09
You'd change the DNS servers listed in network manager to those and see if it works.

---

### Post by candtalan on 2011-01-09
I would *avoid* 11.04 because it is simply not ready yet. Are you sure it is 11.04??

I would try using a live CD such as 10.04.1, check it connects to the internet, then yahoo sign on. If you have an option for yahoo classic, also try it too.

Also I would try Ubuntu 9.10 live CD and why not also try Ubuntu 10.10 live cd also, for the same tests.

The live CDs will use you LAN dhcp facility, so you will also be testing  that.

What is your method of connection to the external internet? adsl through a landline to a modem/router, then ethernet cable from router to your PC??

---

### Post by radarfxst on 2011-01-10
If this was radar (my area of expertise) I'd be more able to fix it - but due to my lack of expertise in LANs/networks and my love of Linux, coupled with my frustration trying to check email, I've decided to switch from Yahoo to GMail.  Not the best solution, but an immediate solution none-the-less.  

Thanks everyone for the inputs...

---

### Post by 1492 on 2011-01-18
If you used Evolution would help at all?

---

### Post by xoros on 2011-01-28
I'm on Ubuntu Lucid Lynx 10.04 amd64 bit using Firefox 3.6.13
I've found I cannot login to [Yahoo Mail]("https://login.yahoo.com/config/login_verify2?&.src=ym") 
with [Live Http Headers v0.16]("https://addons.mozilla.org/en-US/firefox/addon/live-http-headers/") addon installed...  
Not sure if that helps any, 
but for some reason the login page will timeout if I don't uninstall /or disable that addon. 

Edit:
It doesn't matter if I'm using / activating the addon or not - It has to be uninstalled or completely disabled before Yahoo Mail login will go through.

---

### Post by radarfxst on 2011-02-01
I threw in the towel and switched over to GMail several weeks ago, and not one problem so far.  It's running flawlessy!

---

### Post by sudeepde on 2011-02-05
i too am having some problems with yahoo. i am unable to log into _My Yahoo ID_ from ubuntu 10.10. However, others can log into their yahoo ID from my lappy on Ubuntu. i can log into my yahoo ID when on windows but not in ubuntu 10.10. my lappy is dual boot. 
i had faced this problem few days  before too but it rectified by itself. but now again i am facing this same problem. i am not able to log in anywhere on yahoo.

i have even installed windows on virtualbox for yahoo messenger. but from there too i am unable to log in.

i just wonder why am i facing this problem but others not when using ubuntu..

some one please help me.. i don't want to use windows again.

---

### Post by psycho5 on 2011-02-05
This is weird but can't one just set up yahoo mail account through thunderbird or evolution mail? Problem solved eh?

---

### Post by Swagman on 2011-02-05
> **psycho5 said:**
> This is weird but can't one just set up yahoo mail account through thunderbird or evolution mail? Problem solved eh?

They would need to go into yahoo mail account and select "pop my account" <---- or something like that

But that **IS** what I did (BtYahoo & Mail.Yahoo.co.uk)

---

### Post by radarfxst on 2011-02-05
Evolution or Thunderbird may have worked, but I check email from several different computers (two windoze and three Ubuntu) and I can't have my email tied down in any way.  I'm accustomed to portable email and like it this way.  

Anyhow, after more than 10 years with Yahoo, I switched to GMail.  I would rather have done that than stop using Ubuntu.  As far as I'm concerned, problem solved for me.

---

### Post by CharlesA on 2011-02-06
Keep in mind that you can use IMAP with gmail, so you can access yer mail from any computer that has an email client that supports it (Thunderbird, etc)

---

### Post by radarfxst on 2011-02-08
Does that mean that Thunderbird would be "synchronized" with GMail?  If so, maybe I'll give it a try (although it's still too late for Yahoo).

---

### Post by CharlesA on 2011-02-08
Yes, but only if you use IMAP, if you use POP3 all messages stay on the gmail servers but are downloaded to the client.

---

