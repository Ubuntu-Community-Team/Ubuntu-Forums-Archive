---
title: "Thunderbird opening links strangely"
date: 2012-02-07
forum: General Help
---

### Post by Gannin on 2012-02-07
Ubuntu 10.04

Firefox is set as my default browser.  Before, when I would click a link in Thunderbird, it would open it in Firefox normally.  Now, when I click a link, it still opens it in Firefox, but pops up the window saying the browser isn't default, and would I like to make it so, even though the browser is already set to default in Preferred Applications.

If I click yes to make it the default, then go check Preferred Applications, it says the default browser is set to custom, and the custom command is simply "thunderbird".

I haven't updated any software or installed anything new.

Any ideas on this bizarre behavior?

Edit:

As further information, if I already have Firefox open when I click on a link, it opens it in a new tab in Firefox and doesn't complain.  If Firefox isn't already open, that's when it'll open Firefox and ask about the default browser.

I even went so far as to going into Thunderbird's advanced configuration and setting network.protocol-handler.app.http to point at Firefox, but it didn't change anything.

---

### Post by AlanQ on 2012-02-07
I recently had a similar problem after a Firefox update. Unfortunately the fix was so quick I've forgotten what it was. But it did have something to do with 'Preferred Applications'.

However...

> If I click yes to make it the default, then go check Preferred Applications, it says the default browser is set to custom, and the custom command is simply "thunderbird".

"thunderbird" or 'firefox' ?

Have you tried 'Custom' and in the Command box putting '[FONT="Courier New"]firefox %s[/FONT]' ?

---

### Post by pqwoerituytrueiwoq on 2012-02-07
do you have 2 versions/copies of firefox installed?

---

### Post by Gannin on 2012-02-07
> **AlanQ said:**
> I recently had a similar problem after a Firefox update. Unfortunately the fix was so quick I've forgotten what it was. But it did have something to do with 'Preferred Applications'.

However...



"thunderbird" or 'firefox' ?

Have you tried 'Custom' and in the Command box putting '[FONT="Courier New"]firefox %s[/FONT]' ?

"Thunderbird".  Yes, it actually sets the browser custom command box to "Thunderbird".

I switched the preferred browser to Chromium and then Thunderbird opened Chromium just fine.  Then I switched it back to Firefox and it went back to doing the same thing... asking if I wanted to make it the default.

> **pqwoerituytrueiwoq said:**
> do you have 2 versions/copies of firefox installed?

I do.  However, it's not opening the version I don't use.  When I have the Firefox I want to use set as the default, Thunderbird opens and uses that Firefox... it just still pops up the default question.  I have the default question turned off in the other Firefox anyhow.

Something else interesting.  I downloaded Thunderbird 10 to see if it behaved any differently, and it opens the browser properly without asking about defaults.  Then if I go back to the Thunderbird that's bundled with 10.04, it goes right back to opening the proper Firefox but asking about defaults, and if I say yes set it to default, it actually sets the default to "Thunderbird" as I described before.

---

