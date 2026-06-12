---
title: "thunderbird restoration after fresh install"
date: 2010-03-24
forum: General Help
---

### Post by ubunterooster on 2010-03-24
After a fresh install of Karmic, I am trying to restore thunderbird's emails. I tried to just replace the whole folder but this did not work.

---

### Post by wrose51106 on 2010-03-24
Try file > import

-Bill

---

### Post by ubunterooster on 2010-03-24
the whole folder?

---

### Post by wrose51106 on 2010-03-24
How did you back up your emails exactly?

-Bill

---

### Post by ubunterooster on 2010-03-24
copied the whole .mozilla-thunderbird folder

---

### Post by wrose51106 on 2010-03-24
try the file import and select the folder, lets see what happens.

-Bill

---

### Post by ubunterooster on 2010-03-24
I see no file>import but under tools>import are 3 options. for settings and emails it wants to use a program.

Settings: no programs
Emails: Communicator 4 (?)

---

### Post by wrose51106 on 2010-03-24
Im at work right now so I don't have access to thunderbird, tried my best from memory:(

I would give this a go: [http://www.mozilla.org/support/thunderbird/faq](http://www.mozilla.org/support/thunderbird/faq)

-Bill

---

### Post by ubunterooster on 2010-03-24
giving it a go...

---

### Post by Arand on 2010-03-24
What I normally do is use```
thunderbird -P
```..create a new profile, and point the path of it to the old profile folder. Then load this profile. You can always change profiles by, again, the above command.
- Arand

---

### Post by scouser73 on 2010-03-24
> **ubunterooster said:**
> After a fresh install of Karmic, I am trying to restore thunderbird's emails. I tried to just replace the whole folder but this did not work.

In your Thunderbird folder you should see 2 more folders and a document called profiles.ini, which looks like the image below.

[IMG]http://img683.imageshack.us/img683/4908/screenshotzn.png[/IMG]

Copy those three items to the new Thunderbird folder in your ./home and then start up Thunderbird, you should now have all your emails and accounts back to it's original state.

---

### Post by ubunterooster on 2010-03-24
> **wrose51106 said:**
> Im at work right now so I don't have access to thunderbird, tried my best from memory:(

I would give this a go: [http://www.mozilla.org/support/thunderbird/faq](http://www.mozilla.org/support/thunderbird/faq)

-Bill
The link you provide worked! :D
> **scouser73 said:**
> In your Thunderbird folder you should see 2 more folders and a document called profiles.ini, which looks like the image below.

[IMG]http://img683.imageshack.us/img683/4908/screenshotzn.png[/IMG]

Copy those three items to the new Thunderbird folder in your ./home and then start up Thunderbird, you should now have all your emails and accounts back to it's original state.
Mine fails to have the Crash Reports, did I mess something up? LOL

---

