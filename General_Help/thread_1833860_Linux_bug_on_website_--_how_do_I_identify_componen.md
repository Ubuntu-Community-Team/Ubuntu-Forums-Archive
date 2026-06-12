---
title: "Linux bug on website -- how do I identify component for bug report?"
date: 2011-08-26
forum: General Help
---

### Post by nrundy on 2011-08-26
I've noticed a webpage layout bug that only happens when I browse to the page in Linux. The bug is not present when I browse to the page using Windows XP, Windows 7, or Mac OS X.

here's the webpage:  [http://www.bestbuy.com/site/Music-Movies/DVD-Blu-Ray-Movies-TV/cat02015.c?id=cat02015](http://www.bestbuy.com/site/Music-Movies/DVD-Blu-Ray-Movies-TV/cat02015.c?id=cat02015)

The "Go", "Title", and "Person" buttons are partially blocked in Linux by the big banner ad. But these buttons appear above the ad, in-line with the search box, on Windows and Mac.  Here's photos comparing the webpage on Ubuntu and Windows:  [http://imgur.com/a/oCe8P](http://imgur.com/a/oCe8P)

How do I identify what component to report as the source of the bug? This website "layout glitch" is present on every web browser I've tried in Ubuntu. So it isn't specific to any one web browser.

---

### Post by hasardeur on 2011-08-26
Hm, good question. The layout/rendering engine behind FF and many other browsers is Webkit. So that should be the component you are looking for.

Edit: You could try Opera with the Presto engine. If it works there it _might_ be a Webkit issue.

---

### Post by nrundy on 2011-08-26
> **hasardeur said:**
> Hm, good question. The layout/rendering engine behind FF and many other browsers is Webkit. So that should be the component you are looking for.

Edit: You could try Opera with the Presto engine. If it works there it _might_ be a Webkit issue.

Actually, Firefox does not use Webkit. It uses Gecko I believe. But regardless, the issue does not exist when viewing the page in Mac OS X with Safari (which is webkit based).

The issue only exists when viewing the page using web browsers in Linux/Ubuntu.

In Linux, Opera exhibits the same problem as the other browsers. It's a little better in Opera (only "Person" is under the search line, but the issue is still there nonetheless).

---

### Post by hasardeur on 2011-08-26
> **nrundy said:**
> Actually, Firefox does not use Webkit. It uses Gecko I believe.

And Opera exhibits the same problem as the other browsers. It's a little better in Opera (only "Person" is under the search line, but the issue is still there nonetheless).

You're right, my bad. At the very least I can reproduce the issue. When I disable JavaScript the ad/layer (whatever that is anyway) goes away and I see what you describe. Maybe it's a positioning problem originating from the JavaScript engine. But then again the browsers use different engines, so that might not be it. 
Hm... anyone?

Edit: I booted Fedora 15 up, same issue.

---

### Post by haqking on 2011-08-26
> **nrundy said:**
> Actually, Firefox does not use Webkit. It uses Gecko I believe. But regardless, the issue does not exist when viewing the page in Mac OS X with Safari (which is webkit based).

The issue only exists when viewing the page using web browsers in Linux/Ubuntu.

In Linux, Opera exhibits the same problem as the other browsers. It's a little better in Opera (only "Person" is under the search line, but the issue is still there nonetheless).

Works fine for me in Ubuntu 10.10 using firefox, empathy and chromium.

Fired up a virtual machine of 11.04 and it loaded fine too, same in a Debian install.

Nothing wrong with the page at all my end

---

### Post by hasardeur on 2011-08-26
Here some screen shots:


With JS, position is wrong:
[http://imagebin.org/169798]("http://imagebin.org/169798")

Without JS, no ad:
[http://imagebin.org/169799]("http://imagebin.org/169799")

---

### Post by nrundy on 2011-08-26
> **haqking said:**
> Works fine for me in Ubuntu 10.10 using firefox, empathy and chromium.

Fired up a virtual machine of 11.04 and it loaded fine too, same in a Debian install.

Nothing wrong with the page at all my end

I just ran a LIVE CD of ubuntu 11.04 and the issue was present.

@haqking:  what changes have you made to your system?

could the bug only present on certain hardware configs?

---

### Post by sammiev on 2011-08-26
I just tried the addie and can toggle between the two and hit "Go" to load the page. I'm using 11:10 and FF. :)

---

### Post by nrundy on 2011-08-26
> **sammiev said:**
> I just tried the addie and can toggle between the two and hit "Go" to load the page. I'm using 11:10 and FF. :)

what do you mean "tried the addie"? Did the issue present to you?


I can't wait for 11.10. I'm going to install the beta-1 next week =)

---

### Post by sammiev on 2011-08-26
> **nrundy said:**
> what do you mean "tried the addie"? Did the issue present to you?


I can't wait for 11.10. I'm going to install the beta-1 next week =)

The addressed posted worked great with no problems. :)

---

### Post by nrundy on 2011-08-26
Can you try running a live CD of 11.04 and see if the issue presents then?

I'm curious whether 11.10 fixes the issue, or whether maybe it's hardware based?

---

### Post by sammiev on 2011-08-26
> **nrundy said:**
> Can you try running a live CD of 11.04 and see if the issue presents then?

I'm curious whether 11.10 fixes the issue, or whether maybe it's hardware based?

OK I tried it with a CD with 11.10 and it worked with FF6.
Then tried it with my kids computer with 10.10 and FF6 and it worked as well.

Are you running the add-on NoScript?

---

### Post by nrundy on 2011-08-26
> **sammiev said:**
> OK I tried it with a CD with 11.10 and it worked with FF6.
Then tried it with my kids computer with 10.10 and FF6 and it worked as well.

Are you running the add-on NoScript?

I tried it with a default Live CD of 11.04 and the issue was present (so no, NoScript was not installed).

I have to assume it's hardware based then. Some hardware configs present the problem on Linux. Use the same hardware with Windows though and there's no problem.

---

### Post by Brushstroke on 2011-08-26
On Ubuntu 10.04, it looks fine. 

Here's how it looks on my computer: [Click]("https://lh6.googleusercontent.com/-Xq0s3jo2F5Y/TlhXZBMZbuI/AAAAAAAAACc/hyFWGpoxsg8/s800/Screenshot.png")

---

### Post by nrundy on 2011-08-26
> **Brushstroke said:**
> On Ubuntu 10.04, it looks fine. 

Here's how it looks on my computer: [Click]("https://lh6.googleusercontent.com/-Xq0s3jo2F5Y/TlhXZBMZbuI/AAAAAAAAACc/hyFWGpoxsg8/s800/Screenshot.png")

Yeah. I'd say it's my box, but hasardeur can reproduce, so I'm going with hardware config bringing it out =)

@Hasardeur, how old is your box?

---

### Post by nrundy on 2011-08-26
Just got off the phone with my friend. He's got a brand new Lenovo Notebook with Ubuntu 11.04, which he installed last week.

He's got the screwed up layout when he goes to BestBuy webpage. I wonder what's causing this?

---

### Post by sammiev on 2011-08-26
> **nrundy said:**
> Just got off the phone with my friend. He's got a brand new Lenovo Notebook with Ubuntu 11.04, which he installed last week.

He's got the screwed up layout when he goes to BestBuy webpage. I wonder what's causing this?

I have 3 laptops that seem to work fine on BestBuy and all mine were bought within the last 18 months with one only about 6 months old.

---

### Post by dcstar on 2011-08-27
> **nrundy said:**
> I've noticed a webpage layout bug that only happens when I browse to the page in Linux. The bug is not present when I browse to the page using Windows XP, Windows 7, or Mac OS X.

here's the webpage:  [http://www.bestbuy.com/site/Music-Movies/DVD-Blu-Ray-Movies-TV/cat02015.c?id=cat02015](http://www.bestbuy.com/site/Music-Movies/DVD-Blu-Ray-Movies-TV/cat02015.c?id=cat02015)

The "Go", "Title", and "Person" buttons are partially blocked in Linux by the big banner ad. But these buttons appear above the ad, in-line with the search box, on Windows and Mac.  Here's photos comparing the webpage on Ubuntu and Windows:  [http://imgur.com/a/oCe8P](http://imgur.com/a/oCe8P)

How do I identify what component to report as the source of the bug? This website "layout glitch" is present on every web browser I've tried in Ubuntu. So it isn't specific to any one web browser.

It is a rendering issue solely caused by the designers of the web page and their use of pixel padding. Various native fonts in different OSs have different pixel use and this site has probably not been tested with enough Linux systems to make it render consistently across all platforms.

Chances are it also changes depending on the screen resolution detected looking at some of the Javascript code on the page.

Complain to the website.

---

### Post by hasardeur on 2011-08-27
> **nrundy said:**
> 
@Hasardeur, how old is your box?

Ten years give or take, but the one behind me is a few months old and has the same issues.
I imagine that dcstar could be right. The "SearchBox" seems to be very long and wraps the GO/Tile/Person button/radio box to the next line. I don't really know why this happens on some OS and not on Win...

---

### Post by nrundy on 2011-08-27
> **dcstar said:**
> It is a rendering issue solely caused by the designers of the web page and their use of pixel padding. Various native fonts in different OSs have different pixel use and this site has probably not been tested with enough Linux systems to make it render consistently across all platforms.

Chances are it also changes depending on the screen resolution detected looking at some of the Javascript code on the page.

Complain to the website.

I figured this at first. But I found it strange that it worked on Macs and Windows. 

Thanks for this info.

I'd tried changing the font and screen res, but no joy :(

---

### Post by mcduck on 2011-08-27
> **nrundy said:**
> I figured this at first. But I found it strange that it worked on Macs and Windows. 

Thanks for this info.

I'd tried changing the font and screen res, but no joy :(

Doesn't work correctly on my mac (with either Firefox or Safari). ;)

Anyway, that's clearly just a case of bad web design. If the page works correctly or not depends on what fonts & font sizes you are using. Decrease your font size a step or two (Ctrl- in Firefox) and the radio buttons will move one line upwards next to the search box.

---

### Post by nrundy on 2011-08-27
Decreasing the font in Firefox has no effect on it on my box (using Ctrl -). Problem persists no matter the size.

It works on some Macs and some Linux, but not others. A sign of the website not conforming with HTML standards that's causing this?

---

### Post by grahammechanical on 2011-08-27
I am using 11.04 and Chromium. The only issue I have with that page is that the word "Person" is on the next line. I think that this is caused by the coding of the page and not by the web browsers.

Right click on the page and select View Page Source. Look at the coding between line 924 to 940. I am not a web page composer but I guess that not enough space is being allowed for the search box, the buttons and the labels.

Some web browsers are more compliant with the standards than others. The more compliant browsers are less tolerant of sloppy coding.

Regards.

---

### Post by nrundy on 2011-08-27
The web browser does not seem to matter in my tests. Some computers show the page accurately, others don't, no matter what web browser is being used.

I tried a Mac with Safari, it displayed fine.
Someone else posted here saying Mac did not show page right in Firefox nor Safari.
I can't get the page to display right in Firefox, Opera, or Chrome on Linux. But all these browsers display the page right on Windows XP (dual boot machine).

---

### Post by dino99 on 2011-08-27
simply send this issue to the webadmin, and hope he fix it.

---

### Post by Brucevdk on 2011-08-27
> **dino99 said:**
> simply send this issue to the webadmin, and hope he fix it.

And if you're in a hurry or if they ignore you you could always install [Stylish]("https://addons.mozilla.org/en-US/firefox/addon/stylish/") and fix it using a user stylesheet.

Here's a pretty hackish workaround I whipped up:

```

@namespace url(http://www.w3.org/1999/xhtml);

@-moz-document url-prefix("http://www.bestbuy.com/site/Music-Movies/") {
#ast { /* The input box containing 'Search all Movies & TV Shows' */
    width: 70%;
}
}
```

---

### Post by nrundy on 2011-08-27
Do you guys know exactly what is causing this? Why are some computers affected and not others? OS and browser does not seem to be a contributing factor. So why are some affected and not others?

---

### Post by mcduck on 2011-08-28
> **nrundy said:**
> Do you guys know exactly what is causing this? Why are some computers affected and not others? OS and browser does not seem to be a contributing factor. So why are some affected and not others?

Like already said, different browsers have slightly different padding values for elements, operating systems come with different fonts included and use different methods for font rendering which can cause even same font to use slightly more or less space than on another operating system. And in the end people can have set their browsers to use different fonts, font sizes, and minimum font size limits. Web sites need to be designed to be flexible enough to handle all that variance without breaking the layout.

---

### Post by Wim Sturkenboom on 2011-08-28
> **nrundy said:**
> Do you guys know exactly what is causing this? Why are some computers affected and not others? OS and browser does not seem to be a contributing factor. So why are some affected and not others?

My guess
Invalid html/css

Try to check it with [w3c validator](http://validator.w3.org/check?uri=http%3A%2F%2Fwww.bestbuy.com%2Fsite%2FMusic-Movies%2FDVD-Blu-Ray-Movies-TV%2Fcat02015.c%3Fid%3Dcat02015&charset=%28detect+automatically%29&doctype=Inline&group=0) ;) over 800 errors in the markup

So browsers are free to do what they feel is appropriate.

To my knowledge one can not nest the html tag and only one html tag is allowed to indciate the beginning of the html.
```

<!DOCTYPE html>
**<html>**
<!-- B:226 -->
<!-- B:005 -->
<!-- bbolsp-app01/dlpolsapp11-50-11_8 -->
<!-- E:005 -->
<!-- B:0OC -->
<!-- B:301 -->
<!--B:565-->
<!-- B:0WQ -->
**<html lang="en-US">**
<head>

```
And there is only one html close tag. As these tags needs to have a corresponding end tags, it looks to me that that page is one big piece of crappy html.

PS
Same problem here on firefox 3.6.20 / Ubuntu 10.04

---

