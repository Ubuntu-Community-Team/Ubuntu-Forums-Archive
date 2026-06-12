---
title: "Google Chrome doesn't bring up homepage"
date: 2011-07-15
forum: General Help
---

### Post by Crazy K on 2011-07-15
It was working fine all day, but out of the blue, when I clicked on Google chrome I get a homepage with the link being this: 

```
file:///home/crazyk/%25U
```

I checked the setting in chrome and everything seems fine. The homepage is still set to google.com and the at startup as well. 

Any idea what I need to do to fix this?

---

### Post by Crazy K on 2011-07-16
Any idea what the problem could be? It's never done this before. 

I really need help with this soon, thanks!

---

### Post by varunendra on 2011-07-16
Did you try clearing all the cookies (clear all browsing data) and retry?

What is reply of (in terminal):
```
nslookup google.com
```

---

### Post by Crazy K on 2011-07-16
I cleared everything. 

Here's the output of the prompt you told me to enter:

```
Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
Name:	google.com
Address: 74.125.225.16
Name:	google.com
Address: 74.125.225.17
Name:	google.com
Address: 74.125.225.18
Name:	google.com
Address: 74.125.225.20
Name:	google.com
Address: 74.125.225.19
```

---

### Post by varunendra on 2011-07-16
Does Firefox have same issue when setting google.com as homepage?

If not, try deleting all contents of **/home/crazyk/.cache/Chromium/default** folder (you will have to enable 'show hidden files' (or ctrl+k) to see **.cache** folder).

If yes, check or post here the contents of your **/etc/hosts** file.

---

### Post by Crazy K on 2011-07-16
It's just google chrome. Chromium brings up the google homepage whenever I start that. It's just the actual google chrome. When I click on the home page button it brings me to google.com

I'm unsure what's wrong with the actual Google Chrome. 

Chromium seems to be working fine.

---

### Post by Crazy K on 2011-07-16
I checked the contents of /home/crazyk/.cache/Google-Chrome/cache and there's 162 MB or so in there. 

I checked the default folder and it has 88.6 MB and the media cache has 5.6 MB. 

Would I be able to delete the files in each folder? Would that cause any problems? They're just pictures and some random files.

---

### Post by varunendra on 2011-07-16
Did you try the same cache delete thing with **/home/crazyk/.cache/google-chrome/default** directory?


**EDIT:**
Sorry, missed your last post. If you are unsure, just temporary move the contents to some other directory to see if has some positive (or negative) effect at all.

---

### Post by Crazy K on 2011-07-16
Do I delete the folder? or the contents? I deleted the contents of all the folders and it didn't seem to change anything.

---

### Post by Crazy K on 2011-07-17
The deleted the contents of said folders worked. It's working fine now. Thanks for the help. :)

---

### Post by varunendra on 2011-07-17
Wow! I was just about to post - "then just remove and reinstall google chrome!!" after reading your 2nd last post :)-> **Crazy K said:**
> Do I delete the folder? or the contents? I deleted the contents of all the folders and it didn't seem to change anything.
So which were the folders earlier whose contents you deleted?:-k

---

