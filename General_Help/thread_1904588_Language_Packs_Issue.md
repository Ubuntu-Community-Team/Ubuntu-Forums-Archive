---
title: "Language Packs Issue"
date: 2012-01-05
forum: General Help
---

### Post by Dave.YNA on 2012-01-05
Hello All,

I am having an issue with language packs at the moment. Let me start off by apologizing if this is something really obvious but my googling has returned nothing.   

I recently installed 11.10 on a computer and would like to install another language pack (Traditional Chinese). The problem is that when open the language support and select the install/remove languages button on English is available in side. 

The tutorials I have seen all have a large number of languages that I should be able to "tick" in order to download an install. 

Am I missing something really obvious here? 

Thanks in advance

---

### Post by zvacet on 2012-01-05
Watch [http://www.youtube.com/watch?v=WXhQqYZf1aM](http://www.youtube.com/watch?v=WXhQqYZf1aM) and see if is of any help to you.

---

### Post by mcduck on 2012-01-05
> **Dave.YNA said:**
> Hello All,

I am having an issue with language packs at the moment. Let me start off by apologizing if this is something really obvious but my googling has returned nothing.   

I recently installed 11.10 on a computer and would like to install another language pack (Traditional Chinese). The problem is that when open the language support and select the install/remove languages button on English is available in side. 

The tutorials I have seen all have a large number of languages that I should be able to "tick" in order to download an install. 

Am I missing something really obvious here? 

Thanks in advance

Then what do you get when you click the Install/Remove button? Empty window? Just a few languages? Error message?

---

### Post by Dave.YNA on 2012-01-05
The only language present in the "installed languages", the box that appears when I press "install/remove languages..." is English only (which is ticked)...

No other languages are available to tick.

Thanks for replying to me.

---

### Post by mcduck on 2012-01-05
That's strange. Try searching for language packs using Ubuntu Software Center or Synaptic Package Manager...

(if you do it from Software Center, you'll probably have to click the small "Show # technical items"-button in the bottom left corner of the application)

---

### Post by Dave.YNA on 2012-01-05
I have solved it!

Turns out that the server selected for software packages was in a random location. I am guessing this had no packages available as things were failing to download in the software center too. 

To fix, I switched to the main server then;

sudo apt-get update
sudo apt-get upgrade

After the upgrade more languages were available in the list to select. It downloaded then installed without a problem.

---

