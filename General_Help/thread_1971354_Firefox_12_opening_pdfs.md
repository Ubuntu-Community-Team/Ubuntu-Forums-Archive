---
title: "Firefox 12: opening pdfs"
date: 2012-05-02
forum: General Help
---

### Post by rawlins02 on 2012-05-02
I've now got Firefox 12 running on my Ubuntu 10.04 Lucid Lynx system. Clicking on a pdf link now opens the file in ghostview. Previously they opened in Adobe Reader, which is what I prefer. I'd settle for evince. Under Firefox -> Edit -> Preferences -> Applications I see two entries for PDF Document. One says "Always Ask', the entry below that says 'Use Adobe Reader 9.5 (in Firefox). I recall in the past making a change in mozpluggerrc to get pdfs opened in the browser. 

On related note, I notice that it's not uncommon to lose customizations for Firefox every time there's an upgrade, which happen a lot. For example, my default search engine also has changed. It would be nice if all previous configurations were enabled on upgrades.

---

### Post by rawlins02 on 2012-05-04
Anyone?  Guess this behaviour is uncommon...

---

### Post by Zill on 2012-05-04
> **rawlins02 said:**
> Anyone?  Guess this behaviour is uncommon...
I am running standard Ubuntu 10.04 including the recently upgraded Firefox 12.0 and I have no problems holding the previous configurations.

If you wish to change the "open with" applications in Firefox just open the Edit, Preferences, Applications tab.  Then select your required action from the drop-down list.  If you select the "Use other" option, you can select the appropriate executable file for your preferred application (generally in /usr/bin).

I attach a screenshot of my system for reference.  Note that I use the default Evince PDF reader (Document Viewer) rather than the Adobe reader.

---

### Post by madmax75 on 2012-05-04
I prefer Evince to the Adobe's own PDF Reader. At least on my system, Evince is a lot faster.

---

### Post by rawlins02 on 2012-05-05
OK. Thanks for the replies. I will try to set to Evince. This is for my computer at work, so I'll report back results in a couple days.

---

### Post by Zill on 2012-05-05
> **rawlins02 said:**
> ...I will try to set to Evince...
In your first post you indicated that you preferred the Adobe reader to Evince.  Assuming you actually *have* Adobe reader for Linux installed then you should be able to choose this as the default PDF application in Firefox via the "Use other" option I described in my previous post.

---

### Post by rawlins02 on 2012-05-08
> **Zill said:**
> In your first post you indicated that you preferred the Adobe reader to Evince.  Assuming you actually *have* Adobe reader for Linux installed then you should be able to choose this as the default PDF application in Firefox via the "Use other" option I described in my previous post.


There are two entries for PDF docs as I describe in my OP. The look like this:

```

Content type                           Action

PDF document (application/nappdf)      Use evince
PDF document (application/pdf)         Use Adobe Reader 9.5 (in Firefox)


```

Documents are still opening in ghostview. I suspect some other setting somewhere is getting in the way. I also understand editing this applications table is quite limited/difficult.

---

### Post by Zill on 2012-05-09
> **rawlins02 said:**
> There are two entries for PDF docs as I describe in my OP. The look like this:

```

Content type                           Action

PDF document (application/nappdf)      Use evince
PDF document (application/pdf)         Use Adobe Reader 9.5 (in Firefox)


```
I don't recognise this display.  My display from the Edit, Preferences, Applications tab is as shown in my post [#3]("http://ubuntuforums.org/showpost.php?p=11905571&postcount=3") above.  This gives a pulldown list where the desired application can be selected.

> **rawlins02 said:**
> Documents are still opening in ghostview. I suspect some other setting somewhere is getting in the way. I also understand editing this applications table is quite limited/difficult.
Have you got mozplugger installed?  If so then this may be causing the confusion and so I suggest you remove it.
```
sudo apt-get remove mozplugger
```
I do not use mozplugger and simply set my helper applications directly within Firefox as described earlier.

---

### Post by rawlins02 on 2012-05-09
> **Zill said:**
> I don't recognise this display.  My display from the Edit, Preferences, Applications tab is as shown in my post [#3]("http://ubuntuforums.org/showpost.php?p=11905571&postcount=3") above.  This gives a pulldown list where the desired application can be selected.


I have the same display. I simply typed those lines in my post.

> **Zill said:**
> 
Have you got mozplugger installed?  If so then this may be causing the confusion and so I suggest you remove it.
```
sudo apt-get remove mozplugger
```
I do not use mozplugger and simply set my helper applications directly within Firefox as described earlier.

Success!  Thanks Zill.  Now here's hoping each future Firefox upgrade doesn't keep breaking things...

---

### Post by Zill on 2012-05-09
> **rawlins02 said:**
> ...Success!  Thanks Zill.  Now here's hoping each future Firefox upgrade doesn't keep breaking things...
Great!  I am pleased you have things working again.

Would you now please mark this thread as "Solved".  Use the "Thread Tools" pulldown menu near the top right-hand side of this webpage (only the OP can do this!)

---

