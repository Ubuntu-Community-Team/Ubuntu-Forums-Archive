---
title: "Online banking that REQUIRES I.E + WINDOWS"
date: 2011-05-11
forum: General Help
---

### Post by smellytoes on 2011-05-11
My bank requires that I use I.E + Windows to load its online banking services. Any browser in Ubuntu will load the pages as a blank.

Having logged onto the online banking services at work from a Windows machine, I've realised that the bank makes me install a .cab file just to be able to access their online services.

Is there anyway I can load the online services with any of the Ubuntu supported browsers? I've tried I.E on wine to no avail.

---

### Post by seawolf167 on 2011-05-11
I'm not sure if they would work, but you could try two things:

Google Chrome

```
sudo apt-get install chromium-browser
```

Firefox [User Agent Switcher ]("https://addons.mozilla.org/en-us/firefox/addon/user-agent-switcher/")extension

Though if you really have to download and run a .cab file there is probably some type of required ActiveX component that is required.

---

### Post by hwttdz on 2011-05-11
IE in a virtual machine should get the job done.  But a bank requiring you to use IE kind of worries me.  I mean, I've gotten enough "We were idiots and leaked your SSN and all info" letters for one lifetime.  

You could also try changing your user agent to claim that you're using IE on windows.  Generally what I do when I encounter problems, but that's usually because people are just being annoying and say "I don't recognize your browser therefore there is no possibility of it working on our most awesomest site ever", here it might actually not work.

---

### Post by AllGamer on 2011-05-11
another possible alternative, same one used to fool HULU is to use Modify Headers 0.7.0.2 (or newer) add-on for firefox, then make it believe you are using IE

[https://addons.mozilla.org/en-US/firefox/addon/modify-headers/](https://addons.mozilla.org/en-US/firefox/addon/modify-headers/)

---

### Post by CoolJohnB on 2011-05-11
I had a similar problem with my bank I told them I didn't want windows or IE on my computer as I want to avoid any security risk.  After that their site changed and I was able to benefit from it using Firefox 4.
Other than that you might have to change your bank.

---

### Post by smellytoes on 2011-05-11
Thanks for the suggestions, but I've already found chrome to be not working, user agent does not help as well (these 2 solutions load a blank page)

The problem is not fooling the server into thinking that i'm using i.e. 

I think what I need is for someway for the .cab to be installed and run on one of the ubuntu browsers.

I.E on wine does not work as the cab download/install does not even popup when I get to the page.

---

### Post by cymbaline42 on 2011-05-11
I used to use an extension called IE Tab to view IE tabs in Firefox on Windows.  I haven't tried it out on Linux though.  

Link: [https://addons.mozilla.org/en-US/firefox/addon/ie-tab/](https://addons.mozilla.org/en-US/firefox/addon/ie-tab/)

---

### Post by tredegar on 2011-05-11
smellytoes,

Your bank is stupid.

Some (10+?) years ago I had this problem with my UK(GB) banks.

I complained to them, but meanwhile used "user agent switcher" or similar, so their sites did not reject my browser as not being IE. Meanwhile they fixed their stupid software up, so for several years, any browser works for me, without me having to spoof the browser name.

So, complain to them (politey, please).

I'd be interested to know what country your bank is in.

---

### Post by smellytoes on 2011-05-19
I totally agree with comments stating that my bank's online system is downright dumb, but because they provide services that other banks in my country (Malaysia) do not provide, i'm pretty much stuck with them.

Looks like i do not have much of a choice. I'll dig up my old windoze laptop and use that for my banking, hope there's no layer of dust on the harddisk platters from sitting in storage for years.

---

### Post by satish_j on 2011-05-19
Where technology has developed so fast and new(and safe) browsers are available,it feels really sad to see some organizations stuck with virus-prone bowsers like IE..

---

### Post by walt.smith1960 on 2011-05-19
It strikes me as irresponsible of the bank to be using  technologies that have been proven to be quite vulnerable to being compromised.  A polite letter perhaps pointing to some recent incidents of an I.E. flaw being responsible for compromised accounts might be useful.  I used to see this in the U.S. years ago but I.E. only public use web sites seem extinct.  Good Riddance!

---

### Post by rg4w on 2011-05-19
> **walt.smith1960 said:**
> It strikes me as irresponsible of the bank to be using  technologies that have been proven to be quite vulnerable to being compromised.  A polite letter perhaps pointing to some recent incidents of an I.E. flaw being responsible for compromised accounts might be useful.  I used to see this in the U.S. years ago but I.E. only public use web sites seem extinct.  Good Riddance!
This can't be stressed strongly enough.  Making public web sites that are platform-specific demonstrates that they do not understand the web.

Such a decision raises legitimate questions about other aspects of their operations.  If they're so disconnected with how the web works when making their site, how disconnected are they from common security practices and other factors related to managing their customers' money across other aspects of their operations?

I would send them a polite letter cluing them into what the web is and how it works.  If they respond with anything less than an apology and assurances that they get it and will be moving to a platform-independent implementation ASAP, for the sake of your money you may be well advice to run from such ineptitude as fast as you can.

Such foolish decision-making can only lead to security issues for their customers or poor investments for their shareholders, either of which can put your money at unnecessary risk.

---

