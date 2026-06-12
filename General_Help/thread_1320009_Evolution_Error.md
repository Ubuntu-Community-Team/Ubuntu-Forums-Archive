---
title: "Evolution Error"
date: 2009-11-08
forum: General Help
---

### Post by Rayve on 2009-11-08
So, Evolution was working beautifully up until about a week or two ago.  I'm still running 9.04, haven't upgraded to Karmic yet (don't think I will until I get my new desktop at the beginning of next year).  I did a --debug run from terminal and here is what I got [tons of code!!]:

This is the beginning -
```

** (evolution:15110): DEBUG: mailto URL command: evolution %s
** (evolution:15110): DEBUG: mailto URL program: evolution
** (evolution:15110): DEBUG: EI: SHELL STARTUP

(evolution:15110): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 32: Invalid UTF-8 encoded text - not valid 'Could not open &apos;\u0008\u001f\xe8    d/Receipts&apos;:
No such folder \u0008\u001f\xe8    d/Receipts
Changes made to this folder will not be resynchronized.'

(evolution:15110): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 32: Invalid UTF-8 encoded text - not valid 'Could not open &apos;\u0008\u001f\xe8    d/Receipts&apos;:
No such folder \u0008\u001f\xe8    d/Receipts
Changes made to this folder will not be resynchronized.'
** (evolution:15110): DEBUG: EI: mail_read_notify
** (evolution:15110): DEBUG: MAIL SERVER: Count changed: 0

```And then it repeats this stuff a ton for each of my folders:
```

camel-imap-provider-Message: Unable to load summary: no such table: Saved/Daffy

```And then this, mainly only for "Receipts" folder:
```

(evolution:10771): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 32: Invalid UTF-8 encoded text - not valid 'Could not open &apos;\u0008\u001f\xe8    d/Receipts&apos;:
No such folder \u0008\u001f\xe8    d/Receipts
Changes made to this folder will not be resynchronized.'

```And then this for each of my folders:
```

(evolution:10771): camel-WARNING **: Error storing 'y02mustang@imap.aol.com:Saved/!The Jackal': Error storing 'y02mustang@imap.aol.com:Saved/!Protege': Error storing 'y02mustang@imap.aol.com:Saved': Error storing 'y02mustang@imap.aol.com:Junk': Error storing 'y02mustang@imap.aol.com:INBOX': Cannot write offline journal for folder 'INBOX': No such file or directory

```There are 30,000+ lines of text in the file I output --debug to!  :(  I'm also getting an error when I first start about "Error while opening folder imap://y02mustang@imap.aol.com/INBOX. Cannot write offline journal for 'INBOX': No such file or directory".

This just worked a few weeks ago, so any suggestions would be greatly appreciated.

---

### Post by Rayve on 2009-11-15
I ended up uninstalling evolution completely and simply using Thunderbird.  :/  I hate not fixing something or understanding the problem.

---

### Post by dcstar on 2009-11-15
> **Rayve said:**
> So, Evolution was working beautifully up until about a week or two ago.  I'm still running 9.04, haven't upgraded to Karmic yet (don't think I will until I get my new desktop at the beginning of next year).  I did a --debug run from terminal and here is what I got [tons of code!!]:
..........
This just worked a few weeks ago, so any suggestions would be greatly appreciated.

[LIST=1]
[*]You use 32-bit Ubuntu and an Evolution file is now over 2GB
[*]Your /home folder is full
[*]There has been some corruption in the .evolution folder
[/LIST]

---

### Post by emigrant on 2009-11-16
instead of IMAP you could use POP

---

