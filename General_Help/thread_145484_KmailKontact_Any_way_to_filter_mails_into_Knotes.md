---
title: "Kmail/Kontact: Any way to filter mails into Knotes"
date: 2006-03-16
forum: General Help
---

### Post by zi99y on 2006-03-16
I'm rather liking Kontact and at present I'm using it to store email sent to myself containing notes and other stuff, and filter these into specific folders.

Now I was wondering, if, say I send an email with the subject "special" (or whatever), is there a way I can setup a filter (rule) to place the subject and content of this email into a memo in KNotes?

This would be very cool and give Knotes a real purpose for me, instead of just using my email inbox....

ideas anyone? :-k

---

### Post by GeneralZod on 2006-03-16
Intriguing :) I *think* that the "filters" allow you to run incoming e-mails through arbitrary scripts, in which case it would be fairly trivial to knock up a perl script that extracts the subject, body etc and then creates a new note using dcop.  I'll look into this in a couple of hours, when I'm at home :)

---

### Post by zi99y on 2006-03-16
Cool! I appreciate your offer of taking a look.

I can see that Kontact filters allow you to "pipe through" or "execute command" - not sure what that means to me, but I've found that Knotes stores its content in ~/.kde/share/apps/knotes/notes.ics 

The following code is a template of what knotes interprets as a memo: 
```
BEGIN:VJOURNAL
DTSTAMP:20060316T224750Z
ORGANIZER:MAILTO:
X-KDE-KNotes-BgColor:#ffff00
X-KDE-KNotes-FgColor:#000000
X-KDE-KNotes-RichText:true
CREATED:20060316T224744Z
UID:libkcal-992190875.155
SEQUENCE:0
LAST-MODIFIED:20060316T224750Z
DESCRIPTION:<html><head><meta name=\"qrichtext\" content=\"1\"
 /></head><body style=\"font-size:8pt\;font-family:DejaVu Sans\">\n<p>test
 memo</p>\n</body></html>\n
SUMMARY:16/03/2006 22:47
CLASS:PUBLIC
PRIORITY:5
END:VJOURNAL

```
Another idea would be to generate memo's a different colour dependant on the filter text. 

I think this could be very useful - I can't be the only one that sends emails to myself all the time with info and reminders!

---

### Post by carla on 2006-11-10
> **zi99y said:**
> ... ~/.kde/share/apps/knotes/notes.ics 

The following code is a template of what knotes interprets as a memo: 
```
BEGIN:VJOURNAL
DTSTAMP:20060316T224750Z
ORGANIZER:MAILTO:
X-KDE-KNotes-BgColor:#ffff00
X-KDE-KNotes-FgColor:#000000
X-KDE-KNotes-RichText:true
CREATED:20060316T224744Z
UID:libkcal-992190875.155
SEQUENCE:0
LAST-MODIFIED:20060316T224750Z
DESCRIPTION:<html><head><meta name=\"qrichtext\" content=\"1\"
 /></head><body style=\"font-size:8pt\;font-family:DejaVu Sans\">\n<p>test
 memo</p>\n</body></html>\n
SUMMARY:16/03/2006 22:47
CLASS:PUBLIC
PRIORITY:5
END:VJOURNAL

```Another idea would be to generate memo's a different colour dependant on the filter text. 


This jives nicely with a question I have--how can one restyle KNotes' appearance? It seems from the above code that there's a way...

---

