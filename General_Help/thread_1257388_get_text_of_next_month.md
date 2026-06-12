---
title: "get text of next month"
date: 2009-09-03
forum: General Help
---

### Post by approaching on 2009-09-03
I want to insert the next month into the body of a script. I have a little task management bash script that i use, but that part isn't really relevant. I want to have a chron job set up that will do something like this for the command:

task add "this is the body of text to add $ONEMONTHFROMNOW"

though i doubt that specific syntax would work. The bottom line, is that i have a command that takes in text, and i would like to insert the name of the next month. I have found a page that shows how to do such a thing, but i couldn't get it to work for me.
[http://www.simplehelp.net/2008/12/18/the-linux-date-command/](http://www.simplehelp.net/2008/12/18/the-linux-date-command/)

---

### Post by blueridgedog on 2009-09-03
date -d "next month" +"%B"

---

