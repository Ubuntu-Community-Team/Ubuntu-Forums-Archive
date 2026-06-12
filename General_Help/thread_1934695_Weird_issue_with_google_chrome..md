---
title: "Weird issue with google chrome."
date: 2012-03-02
forum: General Help
---

### Post by meduser on 2012-03-02
Hi, I am running Kubuntu 11.10. I love it. The biggest issues have been dvd's and this one. 
I use google chrome for my web browser. When ever I go to Yahoo.ca, The first page displays right, but if I click on a link, it takes me to a different page that just has some of the stories from the main page on it, instead of taking me to the story. If I click on the story, I get errors everywhere.

Now, if I use Firefox, which I dislike, the page displays normally, and when I click on a story, it displays right. 

I have 2 diffent pc's running Kubuntu, and have this issue on both pc's.

Any ideas? Am I missing something? The only page I find this on is on yahoo. If I got to say yahoo sports, everything is normal.

---

### Post by meduser on 2012-03-08
So no one is having this issue with yahoo? I like their stories, and have gone there for years.

The problem seems to be related to Chromium. As firefox displays yahoo properly.

I have this happening on 2 different pc's both running Kubunto 11.10

---

### Post by texpat on 2012-03-08
I can repoduce what you are describing in Xubuntu like thus: in ca.yahoo.com I click a story link. With Firefox I get directly to the story, whereas with Chromium I get a list of stories that have nothing to do with the original story I clicked. The URL in the navbar says m.yahoo.com/...and so on. Clicking a story link there does, however, get me a legitimate looking article.

Interesting, but I don't think this has anything to do with buggy browsers or such. Its probably just Yahoo! checking what browser you are using and redirecting you; perhaps based on some sort of business policy?

PS: this only seems to happen on the ca.yahoo site. I tried es.yahoo and de.yahoo and they behave the same in both browsers.

---

### Post by meduser on 2012-03-08
I find it only happens with Chromium or Chrome, and only in a linux based OS. If I use Chrome in Windows 7, it displays correctly. 

I also find that in Linux/chromium on yahoo, the list of unrelated links normally takes you to a page full of errors.

Seems to be a bug, but not sure..lol

---

### Post by meduser on 2012-03-08
Something else on this, if I go to say sports by clicking on the left column, I go there and all the stories and links display correctly. It just seems like it is the main page. I have had this issue since early January, so it is not anything new.

---

### Post by squilookle on 2012-03-08
At this stage, sounds like it could either be a bug in Chrome/Chromium, or with Yahoo. 

Are there any other websites that show similar behavior using this browser? Do Yahoo pages for other regions do the same thing?

---

### Post by meduser on 2012-03-08
The only one I have found to do this is Yahoo..whether that is yahoo.ca or yahoo.com

No other website or forum has had this issue, from what I have seen.

---

### Post by CaseyC on 2012-03-08
This is because yahoo.ca redirects you to a layout that matches your browser. It thinks that you are using a tablet/smartphone browser to view the pages, thats why its stretched like that. The HTTP User-Agent for Chromium I think is Laobubu/1.0 which Yahoo thinks isnt a desktop browser. 

1. Go to [https://chrome.google.com/webstore]("https://chrome.google.com/webstore")

2. Search for and download "**Change HTTP Request Header**" 

3. It will install a little blue button on the top right hand side. Change it to Firefox or IE. And it will then display properly. 


Let us know.


Note: You might have to change it go to Google then go back to yahoo.ca for it to initially work the first time.

---

### Post by meduser on 2012-03-08
> **CaseyC said:**
> This is because yahoo.ca redirects you to a layout that matches your browser. It thinks that you are using a tablet/smartphone browser to view the pages, thats why its stretched like that. The HTTP User-Agent for Chromium I think is Laobubu/1.0 which Yahoo thinks isnt a desktop browser. 


I am having this issue with both Google chrome and Chromium. Chrome is based off of Chromium.

I will try what you have suggested, but I have never had an issue like this before, and I have used Chrome for years, and go to yahoo everyday.

I'll post back with the results.

---

### Post by meduser on 2012-03-08
Thank you. That worked. I installed and then in the drop down box, I clicked on remove, and now yahoo is displaying correctly in both Chromium and Chrome. Thanks you. 

I will mark as solved.

This is why this site is so good. People helping people

---

### Post by CaseyC on 2012-03-08
> **meduser said:**
> Thank you. That worked. I installed and then in the drop down box, I clicked on remove, and now yahoo is displaying correctly in both Chromium and Chrome. Thanks you. 

I will mark as solved.

This is why this site is so good. People helping people

I am glad you feel that way. I am currently a Windows systems engineer converting to the Linux community because of the sheer companionship that is involved in this effort. 

I am also glad I could help you.

---

### Post by meduser on 2012-03-09
> **CaseyC said:**
> I am currently a Windows systems engineer converting to the Linux community because of the sheer companionship that is involved in this effort. 

That's awesome. I just got my certification in MCSE, you kind of need it in today's IT world, but I mainly run Linux. I am new to it, but find it is quite simple to pick up, and I like being in control of the system, instead of the system controlling me. 

Thanks again for the help.

---

