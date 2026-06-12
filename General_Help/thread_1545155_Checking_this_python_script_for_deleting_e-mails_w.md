---
title: "Checking this python script for deleting e-mails with currupted head"
date: 2010-08-03
forum: General Help
---

### Post by leorolla on 2010-08-03
Hi all,

I saw the following script at [http://www.google.com/support/forum/p/gmail/thread?tid=3c7a18b612775f4e&hl=en](http://www.google.com/support/forum/p/gmail/thread?tid=3c7a18b612775f4e&hl=en)

Could someone tell me if it is safe?

Will it permanently delete corrupted messages or just move them to trash (or neither)?

Using Thunderbird IMAP is becoming a pain with some corrupted message headers in my gmail account.

```
import imaplib

s = imaplib.IMAP4_SSL("imap.gmail.com")
s.login('xxxYourLogin@gmail.com', 'YourPassword')
s.select()
typ, data = s.search(None, 'All')

for num in data[0].split():

    typ, data = s.fetch(num, '(RFC822)')
    if "".join(data[0]) == 'Some messages could not be FETCHed (Failure)':
        print 'Delete message number %s' % (num)
        print s.store(n, '+FLAGS', '\\Deleted')

    if not (int(num) % 100):
        print num

print "end"
s.expunge()
s.logout()

```
[COLOR=Red][B]
MALICIOUS COMMAND WARNING: I AM JUST ASKING A QUESTION ABOUT THIS SCRIPT, I AM NOT SUGGESTING ANYONE RUNS IT.[/B][/COLOR]

---

### Post by leorolla on 2010-08-09
bump?

---

