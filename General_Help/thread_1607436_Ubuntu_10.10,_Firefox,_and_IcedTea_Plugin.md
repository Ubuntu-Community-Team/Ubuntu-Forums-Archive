---
title: "Ubuntu 10.10, Firefox, and IcedTea Plugin"
date: 2010-10-27
forum: General Help
---

### Post by RKCole on 2010-10-27
Hello, everyone.

I have had a problem since Ubuntu 10.04, and I am not sure if it is related to the Web site I use or the IcedTea Java Plugin for Firefox.

When I try to login to my student account on my college's [Blackboard Learning System site]("http://blackboard.yosemite.edu/"), Firefox becomes inactive for about 1 minute or so. It eventually logs in, but during the 1 minute, Firefox is completely locked. I cannot switch tabs, click on menus, or anything else of that nature. I decided to do a little tinkering today, and so I disabled the IcedTea plugin in the Add-ons Manager. This solved the login issue; I was able to quickly login to the site without any delays.

It is evident that there is a conflict between the IcedTea plugin and this particular site. I have not seen this issue on any other Web site which I have visited. This is why I think that the problem could be in the site itself, but I am not sure.

How necessary is the IcedTea plugin? Also, what do I need to do to report a bug and who should I report it to? I am not completely convinced that this problem is from the IcedTea plugin, but I am not sure at all. How could I find out?

Thank you for any suggestions.

Take care.

---

### Post by lovinglinux on 2010-10-27
IcedTea is required for sites with Java applets (not javascript) like some chat applications and some uploaders for example. Most sites that use Java offer some alternative method for those without the plugin, but some requires Java to work. I don't even have it installed and never missed it, but that depends on the user browsing habits.

What you could do is to use [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/") extension to block Java applets on site with such problems.

For troubleshooting Firefox see Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by RKCole on 2010-11-11
Here is a quick update on this issue.

I have used NoScript for quite awhile now (at least three to four years). It seems that there is some sort of conflict between NoScript and IcedTea for the particular site posted in my original message.

If I login to this site with IcedTea enabled while NoScript is disabled, all goes well.

If I login to the site with NoScript enabled and IcedTea disabled, all goes well.

If I login with both enabled, it takes a very lengthy amount of time to login to the site.

thanks for the input thus far.

Take care.

---

### Post by lovinglinux on 2010-11-12
> **RKCole said:**
> Here is a quick update on this issue.

I have used NoScript for quite awhile now (at least three to four years). It seems that there is some sort of conflict between NoScript and IcedTea for the particular site posted in my original message.

If I login to this site with IcedTea enabled while NoScript is disabled, all goes well.

If I login to the site with NoScript enabled and IcedTea disabled, all goes well.

If I login with both enabled, it takes a very lengthy amount of time to login to the site.

thanks for the input thus far.

Take care.


You might wanna try to update NoScript and report the issue to the developer: [http://noscript.net](http://noscript.net)

---

