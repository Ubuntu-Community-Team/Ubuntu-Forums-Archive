---
title: "Move FILTERS in Thunderbird 3?"
date: 2010-01-15
forum: General Help
---

### Post by PDA1 on 2010-01-15
I have a lot of message filters in Thunderbird 3 that put email in proper folders.  Like a utility bill goes to my utility folder.

Thunderbird 3 accesses 2 email accounts.  I want to EASILY move the message filters from email account #1 to email account #2.  

Anyone know how to do it?

---

### Post by mdebusk on 2010-01-16
> **PDA1 said:**
> Thunderbird 3 accesses 2 email accounts.  I want to EASILY move the message filters from email account #1 to email account #2.

From [this MozillaZine knowledge base article]("http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Filters"):
> If you want to duplicate filters from one account to another without manually recreating each individual filter, you can copy "msgFilterRules.dat" from one account subfolder to another. Also note that if you filter based on custom headers you will need to copy the user_pref("mailnews.customHeaders","") line from the prefs.js file in the other profile into your new one.

---

### Post by PDA1 on 2010-01-18
That sounds simple emough.....for someone who understands what they're talking about, because I surely don't.

---

### Post by mdebusk on 2010-01-18
> **PDA1 said:**
> That sounds simple emough.....for someone who understands what they're talking about, because I surely don't.

Thunderbird uses the [mbox]("http://www.qmail.org/man/man5/mbox.html") format for messages. Essentially, every account has a folder which contains one or more files that hold your messages. If you have rules for that account, it'll also contain the file [FONT="Courier New"]MsgFilterRules.dat[/FONT].

You'll need to navigate to your mail folder, which is hidden by default under either ~/.thunderbird or ~/.mozilla-thunderbird, find the [FONT="Courier New"]MsgFilterRules.dat[/FONT] you want, and copy it to the mail folder to which you want to apply the rules.

If it were I, I think I'd use a symbolic link.

---

### Post by josephpmh on 2010-08-27
Unfortunately, moving "msgFilterRules.dat" moves the ALL the filters in Account #1 and overwrites the filters you already have in Account #2.

To move ONE filter:

1 open msgFilterRules.dat from Account #2 in gedit 
2 find the filter you want to move, Each filter looks like this:

```
name="yourfilter"
enabled="yes"
type="17"
action="Move to folder"
actionValue="imap://youremail%40gmail.com@imap.gmail.com/Folderyouwanttomovemailto"
condition="OR (from,contains,whatyourfiltercontains)"

```

Highlight and copy the particular filter you want to copy.

3 Open the msgFilterRules.dat from Account #2 in gedit
4 Paste the filter you just copied at the bottom.
5 Save and close
6 Restart Thunderbird

That's it.

If you're moving something into a particular folder with your filter, you want to make sure that that folder exists.

---

