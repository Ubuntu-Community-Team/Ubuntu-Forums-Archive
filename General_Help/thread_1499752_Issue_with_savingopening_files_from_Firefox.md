---
title: "Issue with saving/opening files from Firefox"
date: 2010-06-02
forum: General Help
---

### Post by michael91 on 2010-06-02
Lately, I've been getting annoyed with the way that Firefox opens files for me. I used to have it so that they would come up with a window that asked whether I wished to save files onto the hard drive or simply open them. When choosing to Save, they would go to my Desktop. Because I mainly save files from my Uni website, they are generally .pdf files. Now, for some reason, they open in the Firefox window, so then I have to go to File, Save, then choose where I want to save it. It would be more efficient if it worked the way it did originally. How can I get the settings back to the way they were? I am running Ubuntu 9.04 and Firefox 3.0.19. Because I use a shared computer, I'm not sure whether the version of Firefox has been changed. Thanks in advance.

---

### Post by spotted zebra on 2010-06-02
go to tools>options click on the 'general' tab and under the heading 'downloads' should be what you are looking for.

let me know if this helps or not.

---

### Post by yetiman64 on 2010-06-02
Have you got the firefox extension pdf download installed by any chance (it sounds though you might have). If you have, its quite easy to change the behaviour from Tools > addons >pdf download > preferences and tick the box you require (download).
If not, it may be worth considering installing it.

---

### Post by michael91 on 2010-06-02
Downloaded pdf Download, fiddled with some of the options and it's still behaving the same. Maybe something else is taking priority over pdf Download?

---

### Post by yetiman64 on 2010-06-02
Yes sounds like it, will look into it a bit more. Was using pdf download with hardy and jaunty but haven't used either for a while but am now using lucid and firefox 3.63. So will need to fire up the desktop to get to jaunty install (working from laptop and lucid at the moment). Get back to you soon.

---

### Post by yetiman64 on 2010-06-02
Sorry for double post (need to make sure you see it), can you post a link to a pdf to test ff 3.0.19 and jaunty?

Edit: and extra thought is do you have the adobe reader (with the browser plugin) installed ?

---

### Post by michael91 on 2010-06-02
Found this one on Google:

[http://www.geobacter.org/publications/Rev_Geophys_1995_Aug.pdf](http://www.geobacter.org/publications/Rev_Geophys_1995_Aug.pdf)

---

### Post by michael91 on 2010-06-02
Assuming that you look in the Add-ons, no. Can't find it in there.

---

### Post by yetiman64 on 2010-06-02
Ok, 3.0.19 without pdf download. The link has "open with document viewer" as the default. Look in Edit > Preferences > Applications for "PDF document", Is it there? - this is where you should be able to make changes.

---

### Post by michael91 on 2010-06-02
It already says "Always Ask".

---

### Post by yetiman64 on 2010-06-02
Try changing it to "save file" as I think you originally said you liked (is that right?). And see if any behaviour changes.

---

### Post by michael91 on 2010-06-02
Got it back again. Changed the "Always Ask" to "Save File", then back to "Always Ask". Thanks for the help.

---

### Post by yetiman64 on 2010-06-02
You're welcome, does sound like something somehow hijacked the pdf association in firefox though as I've never seen firefox open a pdf in a window without a plugin installed (adobe is one I've used myself in the past).

A further means of checking if you're interested might be to type "about<:>plugins" (without the quotes - or the <> - there to stop the code here creating a smiley with the : and the p) in the address bar and check through the list to see if anything is capable of opening pdf files (look under "suffixes"). Cheers,   Nev

Edit: If all is working fine please mark your thread as "solved" using the thread tools drop down menu at the top of your browser window.

---

