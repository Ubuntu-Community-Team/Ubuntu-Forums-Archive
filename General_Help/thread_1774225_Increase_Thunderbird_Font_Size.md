---
title: "Increase Thunderbird Font Size"
date: 2011-06-03
forum: General Help
---

### Post by Quarkrad on 2011-06-03
Newbie running 10.10 & Thunderbird 3.1.10.  I can increase the font size of specific emails via Edit, Preferences, Display but more importantly I want to increase the font size of the text in the main Thunderbird window - i.e. the list of emails you see in the right hand pane under 'Subject', 'From', 'Date', etc.  I would also like to increase the font of the left hand pane text 'Inbox', Drafts'. 'Sent'. etc.  I have been googling and there are many solutions including creating a .css file in the Chrome folder in your Thunderbird Profile - also adjusting settings in the about:config list.  None of these work for me.  Is there another way of adjusting the font size of Thunderbird's main text window?

---

### Post by Quarkrad on 2011-06-05
bump - does anybody use Thunderbird?  Can you increase your font size?

---

### Post by pqwoerituytrueiwoq on 2011-06-05
edit-> preferences -> display tab-> advanced button -> look on the right side in the middle

---

### Post by Quarkrad on 2011-06-06
This appears to only change the text size of messages/mails when you open them.  You can change the font size via Edit/Preferences/Display, as you say, and change the text size for mails when you double click/open them.  What I want to do is change the text size of the **list** of unopened mails in your inbox. I.e. the list of opened/unopened mails in the  Subject field.

---

### Post by Quarkrad on 2011-06-10
bump

Anybody use Thunderbird?  When you fire up Thunderbird can you make the whole text screen (font size on the opening screen) look bigger - not just the font size when you create a new mail to send?

---

### Post by Quarkrad on 2011-06-11
For Ubuntu 10.10.  Create a text file in *./Home/.Thunderbird/**your working profile folder***/Chrome* called userChrome.css.  This file name is precise - do not your own user name e.g. fredChrome.css - it must be userChrome.css.  This is the text I used in the file

[B]/* Global UI font */
* { font-size: 12pt !important;
  font-family: Verdana !important; 
} [/B]

 Changing the value of the font size (in my case above, 12) to another number has the effect of changing the whole screen.


**your working profile folder***  your specific profile folder will be named as a long string of letters and numbers.

---

