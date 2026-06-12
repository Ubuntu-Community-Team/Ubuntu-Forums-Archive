---
title: "Thunderbird - How to move accounts in the accountlist up and down"
date: 2010-04-09
forum: General Help
---

### Post by drf00 on 2010-04-09
I googled for a while without finding anything about this, so i created an account to make sure that others after me get an actual hit when searching for an answer.

I have 13 email accounts in Thunderbird for work-related stuff. Thunderbird by default just adds accounts in a top-down manner without sorting of any kind, not even alphabetically. For most users this is not an issue, but for me and other powerusers who have multiple accounts with an uncountable amount of subfolders it soon becomes a nuisance to have your latest added mailbox all the way down when you actually check it quite often.

Why Mozilla havent included a simple drag'n'drop feature or similar for this is beyond me, but here is how you do it.

Go to Edit -> Preferences -> Advanced(TAB) -> Config Editor(BUTTON)

Type "accountmanager" in the searchfield.

The string in question we're interested in is called "mail.accountmanager.accounts" and it consists of a single line that should look like: account1,account2,account3,account4 (etc)

From here it's easy, just check your list of accounts, counting from the top down, and move the relevant accounts in the string to the place you want them.

For example if i wanted my latest added account - which is placed all the way at the bottom by default - to instead be placed at the top of the list, i just delete "account4" from the end of the line, and insert it at the front. Make sure that there is no trailing comma and no whitespaces anywhere.

There we go. I hope someone finds this useful, a bunch of my colleagues sure did.

Glad to finally contribute to these great forums, they've helped me hundreds of times in the past. Cheerio all! 
:guitar:

---

### Post by Quarkrad on 2010-04-09
Great - been wondering how to do this.  Unfortunately it didn't work for me (U9.10, Thunderbird 3).  I found, for me, the best way to do this is to download/install the Manually Sort Folders add-on.  It works a treat.

[https://addons.mozilla.org/en-US/thunderbird/addon/15102](https://addons.mozilla.org/en-US/thunderbird/addon/15102)

---

### Post by drf00 on 2010-04-09
> **Quarkrad said:**
> Great - been wondering how to do this.  Unfortunately it didn't work for me (U9.10, Thunderbird 3).  I found, for me, the best way to do this is to download/install the Manually Sort Folders add-on.  It works a treat.

[https://addons.mozilla.org/en-US/thunderbird/addon/15102](https://addons.mozilla.org/en-US/thunderbird/addon/15102)

Ah of course i should have included that this is for Thunderbird 2.0. :) I have edited the topic to reflect this.

---

### Post by lonerunner on 2011-02-10
although this topic is old almost year i just want to say thanks this sure helped me.

---

### Post by jester805 on 2011-04-18
> **Quarkrad said:**
> Great - been wondering how to do this.  Unfortunately it didn't work for me (U9.10, Thunderbird 3).  I found, for me, the best way to do this is to download/install the Manually Sort Folders add-on.  It works a treat.

[https://addons.mozilla.org/en-US/thunderbird/addon/15102](https://addons.mozilla.org/en-US/thunderbird/addon/15102)

Beautiful!  Thanks!

---

### Post by BiggestFish on 2011-06-30
Hey thanks. I have been looking for a solution to this problem for about two years or more. I didn't want to reinstall Thunderbird all over again. Your solution was a lifesaver! It was the first result I found in google and the only one that ansered the question. Where did you pick up this info?

---

### Post by u2nTu on 2011-09-10
An update for TB 6.0.2, just a small change.

An account's order in the list no longer corresponds to it's reference internally.  Ex. An account displayed in the third position may have an internal reference of 5. In this case, positioning the "account3" string as you like will not have the desired effect (because its true reference is 'account5').

So the easiest way to determine which numbers are assigned to which accounts is to type into the filter field: account

Then look in the 'Preference Name' column for: mail.server.serverX.spamActionTargetAccount. The 'X' is the true internal reference number of the account given under 'Value' on the same line. (And there's a non-user-created line for 'local folders' with its own number. Use this to position the Local Folders group.)

After the desired account order is assembled by name, then one only needs to sequentially lookup each account name in the 'Value' column and record its number (the 'X') to form a list which can then be formatted into the accountA,accountB,etc. string to be pasted into the 'mail.accountmanager.accounts' field.

Thanks, drf00 for this thread.

---

