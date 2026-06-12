---
title: "Weird Behavior of gedit"
date: 2010-12-24
forum: General Help
---

### Post by nosehat on 2010-12-24
I apologize in advance for the very specific nature of this problem/question.  If anyone can suggest a better forum to post a question like this, *please let me know!* :)

I'm working with a bunch of auto-generated text files that are from different sources, including batch conversions from MS Word on a Windows machine.  These files are in plain ascii.

I've noticed that gedit behaves oddly when opening some of these files, and I think the problem is caused by a null byte (00) anywhere in the file.  I've attached a sample file that demonstrates this behavior.   It's a 16 byte text file with the text "Krdoza " followed by a null byte, followed by four Microsoft-style CR/LF pairs.  Open Office has no trouble opening this file, but for some reason gedit gives me some Chinese characters. (?!)  Other files with a null byte won't open at all in gedit.

At this point, I'm just curious as to what's happening.  Any help or pointers in the right direction would be appreciated!

Thanks in advance!

---

### Post by dcstar on 2010-12-25
> **nosehat said:**
> I apologize in advance for the very specific nature of this problem/question.  If anyone can suggest a better forum to post a question like this, *please let me know!* :)

I'm working with a bunch of auto-generated text files that are from different sources, including batch conversions from MS Word on a Windows machine.  **These files are in plain ascii.**

I've noticed that gedit behaves oddly when opening some of these files, and I think the problem is caused by a null byte (00) anywhere in the file.  I've attached a sample file that demonstrates this behavior.   It's a 16 byte text file with the text "Krdoza " followed by a null byte, followed by four Microsoft-style CR/LF pairs.  Open Office has no trouble opening this file, but for some reason gedit gives me some Chinese characters. (?!)  Other files with a null byte won't open at all in gedit.

At this point, I'm just curious as to what's happening.  Any help or pointers in the right direction would be appreciated!

Thanks in advance!

It is not "plain ascii", it is an encoded file that a simple text editor like Gedit cannot handle.

A "plain ascii" file containing "Krdoza " would comprise of 8 bytes.

---

### Post by nosehat on 2010-12-25
Sorry, but it certainly is "plain ascii", just the original 7-bit standard without the extended characters above 127.  The first 8 bytes are the 7 byte string of characters, followed by the troublesome null byte.  The extra 8 bytes are the 4 Carriage Return/Line Feed pairs at the end of the file which I mentioned:  0x0D, 0x0A * 4.  Open it up in a hex editor and you will see.  It's not unicode anything.

---

### Post by sisco311 on 2010-12-25
Try to remove the non-printable characters from the file:
```
tr -cd '\11\12\15\40-\176' < example\ bad\ text\ file.txt > example\ good\ text\ file.txt
```

---

### Post by nosehat on 2010-12-25
> **sisco311 said:**
> Try to remove the non-printable characters from the file

Thanks!  Actually, it seems that just removing the null bytes from the files does the trick.  :)  

However, I'm mostly curious about this behavior of gedit.  Is it a bug?  Or is a null byte somewhere in the middle of the file a standard way to tell a text editor to use a different encoding?  If that's the case, it makes me wonder why MS Word would throw these null bytes into files that are explicitly meant to be plain text!  :x

---

### Post by sisco311 on 2010-12-25
> **nosehat said:**
> However, I'm mostly curious about this behavior of gedit.  Is it a bug?

I don't know much about encoding, but, I think, it's (at least) a *wishlist* bug.

So I would suggest you to report it.

[uhelp]community/ReportingBugs[/uhelp]

---

### Post by H4F on 2010-12-25
Use gvim. which can handle that fine

---

### Post by dcstar on 2010-12-25
> **nosehat said:**
> Sorry, but it certainly is "plain ascii", just the original 7-bit standard without the extended characters above 127.  The first 8 bytes are the 7 byte string of characters, followed by the troublesome null byte.  The extra 8 bytes are the 4 Carriage Return/Line Feed pairs at the end of the file which I mentioned:  0x0D, 0x0A * 4.  Open it up in a hex editor and you will see.  It's not unicode anything.

Yes, you are right on one level - but a "plain ascii" text file by definition would not contain a null byte, because that is not a text character.

IMHO Gedit just believes the same thing and tries to interpret the file as Unicode because it contains these characters that really shouldn't be there.

---

