---
title: "evolution wont send email if there is an attachment"
date: 2012-06-05
forum: General Help
---

### Post by didragon on 2012-06-05
recently upgraded to ubuntu 12.04 and since then can receive and send email on evolution but if the email has an attachment of any size it will not send. get a timed out message. settings appear ok ie. SMPT for outgoing mail. My husband has same problem on his netbook. any suggestions as to how to correct this? I'm a novice but can find my way around terminal

---

### Post by sanderj on 2012-06-05
If you sent a 1kB attachment, does that work?

---

### Post by didragon on 2012-06-05
tried 9kb and that didnt go ,couldnt find a file 1kb size. whilst it was sending message was that it has sent 100% complete but froze at that point

---

### Post by sanderj on 2012-06-05
> **didragon said:**
> tried 9kb and that didnt go ,couldnt find a file 1kb size. whilst it was sending message was that it has sent 100% complete but froze at that point

Create a file testing123.txt with just the text "hello world". The try to send that file.

---

### Post by didragon on 2012-06-05
thanks for reply. I am so new to this!!! I sent a reply by quick reply and cant see it in the thread so I hope this works!!.
I couldn't find 1kb attachment but tried 9kb. message said it was sending 100%, but froze. Are you suggesting that ipv6 may solve the problem?

---

### Post by sanderj on 2012-06-05
> **didragon said:**
> thanks for reply. I am so new to this!!! I sent a reply by quick reply and cant see it in the thread so I hope this works!!.
I couldn't find 1kb attachment but tried 9kb. message said it was sending 100%, but froze. Are you suggesting that ipv6 may solve the problem?

Oh ... you're reading and confused by my signature. Ignore my signature.

Can you create an mini mini attachment as described?

---

### Post by didragon on 2012-06-05
ok got the hang of this now. yes test123.txt sent ok

---

### Post by didragon on 2012-06-05
the time on my message isn't advancing. do I need to refresh the page in some way to see if i have a reply?

---

### Post by sanderj on 2012-06-05
> **didragon said:**
> ok got the hang of this now. yes test123.txt sent ok

So a very small attachment works. Hmmm. That might mean the time-out with larger attachments is caused by the MTU size (some very network technical). The MTU is between 1200 and 1550. You could test this by sending the small attachment, edit & enlarge the attachment, send it again, repeat until it does not work anymore.

Increase in steps of 100 letters. Easy way: edit the file and add a line like this:

1234567890 1234567890 1234567890 1234567890 1234567890 1234567890 1234567890 1234567890 1234567890 1234567890

(that's 100 bytes).

If the sending times when you've added between 11 and 16 lines it's the MTU.

Please test and report back.

---

### Post by didragon on 2012-06-05
thanks again for persuing this. ok it wont send 1020 bytes or 917 bytes. by the way my husband can get thunderbird to send attachments, so its only evolution that is misbehaving. ok, 717 bytes will send

---

### Post by didragon on 2012-06-05
ok, on further testing 717 bytes will send

---

