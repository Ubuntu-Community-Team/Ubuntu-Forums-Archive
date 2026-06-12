---
title: "Evolution: How to get separate Inbox for each account?"
date: 2012-02-17
forum: General Help
---

### Post by XEtedBear on 2012-02-17
If his is not the appropriate forum category for this post, please advise me:

I'm running 11.10 and have just installed Evolution, trying to match what I had on 10.10. I used to have separate Inbox, etc, folders for each account. But for some reason I can't figure out how to do that now. All the mail across all my accounts comes into the one Inbox, with no obvious indication (aside from subject/content) of which account it was originally addressed to. Logically similar problem on sent mail.

How do customise Evolution to give me unique Inboxes? the help files don't seem to address this requirement.

---

### Post by winh8r on 2012-02-17
I think you need to create new "inbox" folders and then set a filter using the edit tab.

Hang on:

[http://library.gnome.org/users/evolution/stable/mail-filters.html.en]("http://library.gnome.org/users/evolution/stable/mail-filters.html.en")
 might help you some way

---

### Post by dcstar on 2012-02-17
> **XEtedBear said:**
> If his is not the appropriate forum category for this post, please advise me:

I'm running 11.10 and have just installed Evolution, trying to match what I had on 10.10. I used to have separate Inbox, etc, folders for each account. But for some reason I can't figure out how to do that now. All the mail across all my accounts comes into the one Inbox, with no obvious indication (aside from subject/content) of which account it was originally addressed to. Logically similar problem on sent mail.

How do customise Evolution to give me unique Inboxes? the help files don't seem to address this requirement.

Use IMAP.

---

### Post by XEtedBear on 2012-02-17
> **dcstar said:**
> Use IMAP.

Clearly you have more faith in (but less knowledge of) my abilities. The guidance is a bit like telling somebody to use a car when they need an understanding of how to correctly ride a bike!

The mail servers I have for my accounts are all POP mail. I didn't think it was possible to use IMAP (whatever that is) on my Evolution mail client and get a meaningful result when the server is serving POP protocol. Or am I misunderstanding a lot of things here? (Answers on a post-card - I suspect only 3 characters are needed).

---

### Post by philinux on 2012-02-17
> **winh8r said:**
> I think you need to create new "inbox" folders and then set a filter using the edit tab.

Hang on:

[http://library.gnome.org/users/evolution/stable/mail-filters.html.en]("http://library.gnome.org/users/evolution/stable/mail-filters.html.en")
 might help you some way

This is exactly what I do I have 4 accounts so I created a folder for each then used filters to redirect the mail from the main inbox to them.

An alternative would be to use Thunderbird. I prefer Evo.

Edit>Message Filters

---

### Post by dcstar on 2012-02-18
> **XEtedBear said:**
> Clearly you have more faith in (but less knowledge of) my abilities. The guidance is a bit like telling somebody to use a car when they need an understanding of how to correctly ride a bike!

The mail servers I have for my accounts are all POP mail. I didn't think it was possible to use IMAP (whatever that is) on my Evolution mail client and get a meaningful result when the server is serving POP protocol. Or am I misunderstanding a lot of things here? (Answers on a post-card - I suspect only 3 characters are needed).

POP is an ancient, insecure mail client protocol that should only be used when there is no other choice. IMAP is a newer protocol that has far more features and flexibility.

Evolution's implementation of IMAP creates a separate Inbox for each IMAP account.

Whenever you encounter a term you do not understand do a web search, you will usually find a multitude of explanations without having to wait for someone to serve them up to you.

---

