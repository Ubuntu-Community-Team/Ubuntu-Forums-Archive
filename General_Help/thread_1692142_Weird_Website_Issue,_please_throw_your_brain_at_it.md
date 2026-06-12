---
title: "Weird Website Issue, please throw your brain at it..."
date: 2011-02-21
forum: General Help
---

### Post by TNT1 on 2011-02-21
Hi, please see if you can assist me with a strange issue.

I run a website,that I can ping from behind my router, but I cannot get to it via a web-browser.

This is the only website that does this. Also, try going to it yourself, the rest of the world can see it. If I connect via alternate route, say 3G, I can get to it via browser. 

I assume this is a routing issue at my ISP? Thing is, their help desk is staffed by morons, so I need to point them in the right direction.

I have discussed this issue with my hosting company, and they agree this is an ISP issue. Also, my other websites at the same hosting company give no problems.

Please help...

---

### Post by thefasterblueone on 2011-02-21
Maybe try a fresh install of a different browser.
 Also you could run firefox from terminal a see any errors occur, or just check Firefox Error Console, (clear all errors before trying website).

Let us know how it goes.

---

### Post by TNT1 on 2011-02-21
> **thefasterblueone said:**
> Maybe try a fresh install of a different browser.
 Also you could run firefox from terminal a see any errors occur, or just check Firefox Error Console, (clear all errors before trying website).

Let us know how it goes.

That's the thing, I can try from an XP machine running IE, and I cannot hit that website, I can ping it, I can see the rest of the web, but not that site...

Will try ff Error Console though...

---

### Post by TNT1 on 2011-02-21
Firefox Error Console:

Error: uncaught exception: [Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIAutoCompleteController.handleDelete]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: chrome://global/content/bindings/autocomplete.xml :: onKeyPress :: line 437"  data: no]

What on earth might that mean?

---

### Post by CHRSB on 2011-02-21
> **TNT1 said:**
> Firefox Error Console:

Error: uncaught exception: [Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIAutoCompleteController.handleDelete]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: chrome://global/content/bindings/autocomplete.xml :: onKeyPress :: line 437"  data: no]

What on earth might that mean?

It worked for me.

Looks like a Javascipt issue.
Do you have the icedtea6-plugin installed?
> 
sudo apt-get install icedtea6-plugin

Next time please provide your Ubuntu version.

But maybe this was just to get some hits to his website? :^)

---

### Post by TNT1 on 2011-02-21
> **CHRSB said:**
> It worked for me.

Looks like a Javascipt issue.
Do you have the icedtea6-plugin installed?


Next time please provide your Ubuntu version.

But maybe this was just to get some hits to his website? :^)

Hi, I am using Ubuntu 10.04.1, and I don't see how it can be a java issue, as if I use the exact same machine on my work network, I can hit the site.

I'm not trying to get traffic to the site, I simply put it up to prove that you all can hit it, but I can't.

I really need help.

---

### Post by gerowen on 2011-02-21
I live in the US and have Comcast and am having weird issues with it.  In both Firefox and Google Chrome some of the images further down the page are wider than your little content area bar on the background and overlap the text on the right side.  Also for some reason Google Chrome refuses to load the link boxes at the top of the page, but Firefox loads them just fine.  At the top right in both browsers I have a pink box that reads, "The page you are trying to access is restricted or unavailable".  Just figured you'd like to know you're not the only one having problems accessing the site.

---

### Post by Clever_Username on 2011-02-21
So we know the issue isn't with your computer since you can get to the site when you connect your machine to your work's network.
Seems like that leaves a couple of possibilities. Your router or your ISP.
Can you get to the internal page of your router and look at the logs?

---

### Post by CHRSB on 2011-02-21
> **TNT1 said:**
> Hi, I am using Ubuntu 10.04.1, and I don't see how it can be a java issue, as if I use the exact same machine on my work network, I can hit the site.

I'm not trying to get traffic to the site, I simply put it up to prove that you all can hit it, but I can't.
  not c
I really need help.

I do not care what you THINK it is. Did you even check if you had the Icded Tea plug in installed? You might try reinstalling it.

And you are not using the EXACT MACHINE on your work network. It is a different machine. If it was the same machine you would not be having this issue. If you mean that you bring that same computer into work then you should write. "I bring this computer into work and it works fine." Please write more clearly.

You might also try renaming your .mozilla folder in your home folder so firefox can try a blank profile.

---

### Post by TNT1 on 2011-02-21
> **Clever_Username said:**
> 
Seems like that leaves a couple of possibilities. Your router or your ISP.
Can you get to the internal page of your router and look at the logs?

I can, what should I look for? Or just post the log and hope someone smart can help?

---

### Post by TNT1 on 2011-02-21
> **CHRSB said:**
> I do not care what you THINK it is. Did you even check if you had the Icded Tea plug in installed? You might try reinstalling it.

And you are not using the EXACT MACHINE on your work network. It is a different machine. If it was the same machine you would not be having this issue. If you mean that you bring that same computer into work then you should write. "I bring this computer into work and it works fine." Please write more clearly.

You might also try renaming your .mozilla folder in your home folder so firefox can try a blank profile.

Sorry.

Yes. I bring the same laptop that I use at home into work. At home it doesn't connect to that one particular site, although I can ping it. At work, the same exact machine, no changes, using the same exact login and username, and the same exact firefox, can connect to the website via a browser.

---

### Post by CHRSB on 2011-02-21
> **Clever_Username said:**
> So we know the issue isn't with your computer since you can get to the site when you connect your machine to your work's network.
Seems like that leaves a couple of possibilities. Your router or your ISP.
Can you get to the internal page of your router and look at the logs?

Oh, woops, I miss read his first post. It seems obvious it is his router or DNS propagation issue. In that case he is posting this in the wrong place and probably on the wrong website.

Besides, why the heck would I help someone who is selling Avon? A horrible cancerous facade on otherwise beautiful women.

---

### Post by TNT1 on 2011-02-21
> **CHRSB said:**
> Oh, woops, I miss read his first post. It seems obvious it is his router or DNS propagation issue. In that case he is posting this in the wrong place and probably on the wrong website.

Besides, why the heck would I help someone who is selling Avon? A horrible cancerous facade on otherwise beautiful women.

Sorry, man, I am posting here, cause I am desperate... I have posted on several other webmaster forums, and no one can help. I have contacted my ISP, and so far they are stumped.

Your feelings over avon aside, I just need help...

---

### Post by gerowen on 2011-02-21
If you take your router out of the equation and plug straight into your modem can you visit the site?  Can other computers on your network view the site?  I'm trying to browse the site by IP address but it's giving me the IP to your hosting company's site instead, apparently there's some kind of referral going on, if you have it on hand try browsing the site by IP address.

---

### Post by TNT1 on 2011-02-21
> **gerowen said:**
> If you take your router out of the equation and plug straight into your modem can you visit the site?  Can other computers on your network view the site?  I'm trying to browse the site by IP address but it's giving me the IP to your hosting company's site instead, apparently there's some kind of referral going on, if you have it on hand try browsing the site by IP address.

The modem is combined with the router, so no luck. The other computers including the windows machines have the same issue, site not found. Can't browse via IP address, goes to the hosting company's website.

---

### Post by gerowen on 2011-02-21
> **TNT1 said:**
> The modem is combined with the router, so no luck. The other computers including the windows machines have the same issue, site not found. Can't browse via IP address, goes to the hosting company's website.

If you manually add Google's public DNS servers to your network config does that help?  Just go into your network connection settings, go to IPV4 settings, change it from "Automatic (DHCP)" to "Automatic (DHCP) addresses only" and in the DNS servers box enter:

8.8.8.8,8.8.4.4

This should route you through those public DNS servers and around any resolution issues you are having with your home network or ISP.  I have them plugged into my wireless router as static DNS servers.

---

### Post by gerowen on 2011-02-21
Also, depending on your Geography those public DNS servers may respond slowly.  On top of that, you may want to talk to your hosting company about how much of your personal information they put out there for everyone to see.  If I'm reading this right, I have your name, address, how much you pay for hosting, and a little message that says you haven't paid your bill yet.  I'll send you the link in a PM.

---

### Post by CHRSB on 2011-02-21
> **TNT1 said:**
> The modem is combined with the router, so no luck. The other computers including the windows machines have the same issue, site not found. Can't browse via IP address, goes to the hosting company's website.

GAAAAAAAAA!

Wow, THAT information would have helped a long time ago. It is a DNS propagation issue.

The reason your IP is going to the host website is because your website is a virtual host so you need to know the subdirectory name which is usually the user name you singed up with.. 

But yes, as the other person said, a manual DNS would do the trick.

And can I just call you Jason from now on? And I love to cook as well! :^)

---

### Post by Clever_Username on 2011-02-21
Looks like that domain name is flagging on an RBL check too

---

### Post by Clever_Username on 2011-02-21
Screenshot

---

### Post by CHRSB on 2011-02-21
> **gerowen said:**
> Also, depending on your Geography those public DNS servers may respond slowly.  On top of that, you may want to talk to your hosting company about how much of your personal information they put out there for everyone to see.  If I'm reading this right, I have your name, address, how much you pay for hosting, and a little message that says you haven't paid your bill yet.  I'll send you the link in a PM.

HA! Yes, I got that too. But I think SA Telekom has some strict DNS policies.

[http://www.hostcow.co.za/domain-names/domain-name-registration-faq.php#F4](http://www.hostcow.co.za/domain-names/domain-name-registration-faq.php#F4)

---

### Post by TNT1 on 2011-02-21
> **gerowen said:**
> If you manually add Google's public DNS servers to your network config does that help?  Just go into your network connection settings, go to IPV4 settings, change it from "Automatic (DHCP)" to "Automatic (DHCP) addresses only" and in the DNS servers box enter:

8.8.8.8,8.8.4.4

This should route you through those public DNS servers and around any resolution issues you are having with your home network or ISP.  I have them plugged into my wireless router as static DNS servers.

Ok, will try that.

---

### Post by TNT1 on 2011-02-21
> **CHRSB said:**
> HA! Yes, I got that too. But I think SA Telekom has some strict DNS policies.

[http://www.hostcow.co.za/domain-names/domain-name-registration-faq.php#F4](http://www.hostcow.co.za/domain-names/domain-name-registration-faq.php#F4)

Yip...

---

### Post by CHRSB on 2011-02-21
> **Clever_Username said:**
> Screenshot

GAH! I knew he was a spammer! :p

But ewwww, you read Drudge Report?

---

### Post by Clever_Username on 2011-02-21
> **CHRSB said:**
> GAH! I knew he was a spammer! :p

But ewwww, you read Drudge Report?


Haha! You caught me

---

