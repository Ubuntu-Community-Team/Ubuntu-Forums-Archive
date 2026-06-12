---
title: "Linux not supported by bank"
date: 2011-10-26
forum: General Help
---

### Post by Blackbird_13 on 2011-10-26
My bank has informed me that it has decided “[not to] support the Linux operating system”. Whenever I log on I am warned:

> "The browser you’re using is not recommended for our Internet Bank. If you continue, some parts of the bank may not display or work as well as they would in other browsers."After that, the response times for logging on and navigating the site seem normal for my Internet connection (a few seconds). This is the first site I have encountered which is designed not to  operate with Linux. I had naively assumed that web-sites worked  irrespective of operating system - I'm using Lucid and Firefox.  It is very annoying because I am very satisfied with everything else the bank does.

How much work would the bank have to do to support Linux? A bit of tweaking of code, or a wholesale re-write of their web site?

---

### Post by Jacobonbuntu on 2011-10-26
If everything works as usual I would just keep on using it. Good chance that the site itself runs on a Linux server :)
I guess it is kind of a standard statement to keep their help desk as quiet as possible.... they don't want to cope with possible problems their phone talk "scripts" do not include

---

### Post by bvanaerde on 2011-10-26
> **Blackbird_13 said:**
> The browser you&#8217;re using is not recommended for our Internet Bank. If you continue, some parts of the bank may not display or work as well as they would in other browsers.
My guess is they're not fully supporting Firefox, as they don't mention Linux?

---

### Post by mcduck on 2011-10-26
The bank shouldn't need to do anything to support Linux. It rarely matters at all what OS you are running when you browse a web site, it's just a question of what *browser* you are using.

...and supporting browsers like Firefox, for example, isn't hard or any extra work. it only requires them to follow the web standards. That's all. :)

However, I've definitely seen some banks who fail miserably in this kind of stuff, using things like Java applets with hard-coded locations for storing keys in the filesystem (with a path starting with "C:/") and stuff like that. In case you ever run into that kind of stuff, better switch to a better bank. ;)

Anyway, like Jacobonbuntu said, if everything seems to work fine then just ignore the message.

And also if it annoys you, you can use some user agent switcher extension in Firefox to get it recognized as some other browser or running on another OS. That should get rid of the message (although as a downside it also wouldn't give the bank the message that people are actually using other things than just Windows+IE and that they should do what any decently capable company would and just follow the standards and support them all...)

Edit: As the message doesn't actually even mention your OS, only the browser, and since you are running an older Ubuntu release; what is the Firefox version you are using? If you are using the one from the 10.04 repositories it would be a bit outdated and *that* might be the reason for the warning message you are seeing...

---

### Post by PsyclonJohn on 2011-10-26
Try using Firefox and installing 'User Agent Switcher' and changing your user agent to "IE 8" and try accessing the bank site again. This will trick the site into thinking you are running on a Windows machine and Internet Explorer 8. I use this technique whenever a site tells me they can't process my browser or OS info. Works every time!

---

### Post by Blackbird_13 on 2011-10-26
Thanks for the replies. Just to clarify, I queried the Browser Warning" and was informed that:

> Our website is optimised for use with the latest versions of the most commonly used browsers (for example Internet Explorer 8 and Firefox 3)I informed them that I use Firefox 3.6. I was then told:

> I am sorry that we do not support the operating system you are currently using.

I'll give User Agent Switcher a try.

---

### Post by Blackbird_13 on 2011-10-26
User Agent Switcher works a treat.

Many thanks for the rapid assistance.

---

### Post by PsyclonJohn on 2011-10-26
Yeah, when a business limits on OS, they usually can't give the proper support if the client comes across a problem. Since there are so many distro's out there, it makes it hard to give that extra support to clients.

---

### Post by Nixarter on 2011-10-26
I've heard of some banks doing that.

Though you seem to have found a work-around, consider switching to a credit union.  I've never heard of any such complaints from friends who use linux with them.  They also have many other benefits that banks (well, the large ones at least) cannot match.  They are non-profit, member-owned, low-overhead financial institutions that do the same things as banks... but just better and cheaper.  Banks are just popular because they are traditional.  Many people don't know there are alternatives that are, IMO, better.  It's funny how that logic comes up from time to time with us humans :p

---

### Post by mastablasta on 2011-10-26
well do they support Android and mobile banking? Cause Android is based on Linux anyway... :-P
 
anyway it might be that they use .net in their applicaiton (that would be OS based) and in your case maybe they expect you to run latest Firefox (i think it is at 7 now) so it is the most secure possible.

---

### Post by Nixarter on 2011-10-26
In my experience, at a bank I used previously, they had no qualms about me using linux. They said that what they meant by "not supported" is that they don't have any tech support available for linux.  In other words, if you get it to work, fine, but we don't know how to help you if you can't.

Such doesn't seem to be the case in OP's situation, but it is important to point out the distinction.

---

