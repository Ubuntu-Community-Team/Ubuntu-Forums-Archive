---
title: "Question about enabling java script in google chrome"
date: 2012-07-10
forum: General Help
---

### Post by imachavel on 2012-07-10
I have a question, I recently made a web site. A simple one. With some tagged photos I uploaded that appear, and a slide show I made with java script and obviously there is a css format. I decided to skip testing this site in local host, and decided not to test if my lamp services are running correctly. I uploaded the site to godaddy.com, and I can see everything perfectly while browsing with firefox. But in google chrome I can't see the slide show, and some photos don't work. I looked in settings, like extensions, and under the hood, the browser settings for google chrome. I cannot for the life of me find a section that says if java is enabled or not. In google chrome I can't seem to find the area where it asks me if I have javascript enabled or not. Do I need to download and install an extension for google chrome to use a java script enabled browsing experience? Sounds like ******** right? Trust me the web page isn't coded incorrectly, but at the same time I have no problem viewing other sites with google chrome and seeing pictures, videos, etc. flash works fine etc.

Does google chrome have an issue with xhtml?

---

### Post by ajgreeny on 2012-07-10
I do not use google chrome, but often use chromium, where java seems to work with no problem except that I have to allow it on pages where it's needed.

You can see if things are blocked and what is going on probably by going to:-
[https://support.google.com/chrome/bin/answer.py?hl=en-GB&answer=1247383&p=ib_blocked_plugin](https://support.google.com/chrome/bin/answer.py?hl=en-GB&answer=1247383&p=ib_blocked_plugin)
and see if the plugin is present at
[http://javatester.org/javascript.html](http://javatester.org/javascript.html)

Using chromium I have to specifically allow java on the second page and other pages at that test site by right clicking in the boxes where the plugin would show or using the "allow" box at the top of the page.

PS:  I assume you have java installed along with the java plugin, either from Oracle, or the openjdk versions, including icedtea plugin.

---

### Post by imachavel on 2012-07-10
strange, I'll check those links. But I threw the web page into local host along with the styled css sheet, and now in local host the thing opens and the slide show works great! Maybe I have some security settings beefed up in my google chromium. I'll have to look at that, since my plug ins to open the site in google chrome locally seem to work just fine. Thanks for the info

lol nevermind I opened it in firefox by mistake, somehow thought I opened local host from chrome. LOLing. I'll try to look into that site for plug in issues. Is it possible for a css feed to style the php while the mark up language, umm, I think imports and marks up the code from php, in one browser, and in another browser it doesn't work well? I think it is incorrectly written css, I can see the slide show in local host. And yet, it's clipped, I see the top quarter of a centimetre sliding. In firefox it works great. Funny, I wonder why a css feed would work in firefox but not chrome. So strange

and yeah the script tester came up fine:

[http://javatester.org/javascript.html](http://javatester.org/javascript.html)

---

