---
title: "I want to create a widget"
date: 2010-09-12
forum: General Help
---

### Post by UDon on 2010-09-12
Hi, I want to create a small simple application that will let me change the Output of the Sounds option to go from speakers to my headphones. I can do this easily enough through System --> Preferences --> Sound, but I'd like to create a GUI front end for me to do this. This is more as a learning exercise than anything else.

What is the best language for me to build the windows to do this? Also, how do I find the commands to let me toggle the sound settings? Where are they documented? I'm using Ubuntu 10.04.

---

### Post by RHTopics on 2010-09-12
A quick way to display gui dialog boxes (widgets) for user input is to use Zenity.

Zenity can be used from command line and from shell scripts like bash.

The "List Dialog" in Zenity allows a column to contain radio buttons for selecting one item from the list.

To learn more about Zenity and see some examples, bring up the Zenity Manual from the Ubuntu Help Center facility.  That is click on the Help icon in the upper panel and then do a search for zenity.  Select the Zenity Manual from the search results.

I don't know where the settings for sound output are stored, so I can't help you with that.

---

### Post by UDon on 2010-09-13
> **RHTopics said:**
> A quick way to display gui dialog boxes (widgets) for user input is to use Zenity.

Zenity can be used from command line and from shell scripts like bash.

The "List Dialog" in Zenity allows a column to contain radio buttons for selecting one item from the list.

To learn more about Zenity and see some examples, bring up the Zenity Manual from the Ubuntu Help Center facility.  That is click on the Help icon in the upper panel and then do a search for zenity.  Select the Zenity Manual from the search results.
[RHTopics]("http://ubuntuforums.org/member.php?u=16941"), thanks for the response. I'll check out Zenity and do some playing around.

---

